### Interviewe Questions
How to achieve multiple inheritance in php?
    
    By using interface or trait
What is the difference between Zend Framework 2 and Zend Framework 1?

  - Architecture

    ZF1 is based on MVC , ZF2 is based on MOVE. Huge difference. MOVE = Model Operations Views Events , MVC = Models Views Controllers. More here. Zend Framework 2 uses 100% object-oriented code and utilises most of the new features of PHP 5.3, namely namespaces, late static binding, lambda functions and closures.
    http://cirw.in/blog/time-to-move-on, http://framework.zend.com/manual/2.0/en/ref/overview.html
  - Size of installation

    The latest ZF1 file is approx 30Mb and ZF2 is approx 2.5Mb (Zipped).
  - Dependency

    ZF1 is core set of libraries and very loosely coupled architecture (with respect to its competitor/player - CakePHP). ZF1 does not require much of 'gems' (as in ruby) but, can do better with plugins. ZF2 requires you to know about composer - phar and soon it may out-match any other framework. New concept : Dependency Injection for Zend fans.
      Resources: http://framework.zend.com/manual/2.0/en/tutorials/quickstart.di.html
  - Certification

    Certification is available only for ZF1, however, there are rumors about their talks for ZF2 certs though training material is available online.
  - Conventions

    classname in ZF1 was Zend_Db_Table for class in Zend/Db/Table.php whereas in ZF2, it is class My\Auth\Adapter . Enough said.
  - Community

    ZF1 was backed by Zend Technologies (and few other, unnamed). ZF2 has remarkable supporters including Google and Microsoft.
      Resources: http://framework.zend.com/manual/2.0/en/ref/overview.html
  - Speed

    It took approx 20 times more time to execute "Hello World!" in ZF2. I am not judging here. I could be wrong here. DIY.

  - Which one should I opt for?

    MVC is been around since almost a decade and if you are one of them who are feeling sad for a new architecture altogether then hey! IT is 'your chosen' domain, keep up with the trends and update yourself! Start ZF2 from here.
    http://framework.zend.com/manual/2.0/en/user-guide/overview.html

How to pass data in header while using CURL?

    $A = 'ZAXGHGN';
    $INPUT = '<?xml version="1.0" encoding="utf-8"?><a><b>test data</b></a>'; // is this a valid XML???
    
    $headers = array(
    "Content-type: text/xml",
    "Content-length: " . strlen($INPUT),
    "A: " . $A,
    // like this  if you want to have this value  in the header ... but to put the xml inside the header info...
    "Connection: close"
    );
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 0);
    curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, 0);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_POST, TRUE);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $INPUT); // send xml data using POST
    curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
    $data = curl_exec($ch);
    if(curl_errno($ch))
    print curl_error($ch);
    else
    curl_close($ch);
    echo "<pre>";
    print_r($data);
    exit;

How can we prevent SQL-injection in PHP?
    
    Use prepared statements and parameterized queries. These are SQL statements that are sent to and parsed by the database server separately from any parameters. This way it is impossible for an attacker to inject malicious SQL.
    You basically have two options to achieve this:
        - Using PDO [http://php.net/manual/en/book.pdo.php] (for any supported database driver):

            $stmt = $pdo->prepare('SELECT * FROM employees WHERE name = :name');
            
            $stmt->execute([ 'name' => $name ]);
            
            foreach ($stmt as $row) {
            // Do something with $row
            }
        - Using MySQLi (for MySQL):

            $stmt = $dbConnection->prepare('SELECT * FROM employees WHERE name = ?');
            $stmt->bind_param('s', $name); // 's' specifies the variable type => 'string'
            
            $stmt->execute();
            
            $result = $stmt->get_result();
            while ($row = $result->fetch_assoc()) {
            // Do something with $row
            }
    If you're connecting to a database other than MySQL, there is a driver-specific second option that you can refer to (for example, pg_prepare() and pg_execute() for PostgreSQL). PDO is the universal option.
What is basic difference between require_once(), include_once() and include()?
    
    require_once(): if it does not get the required file then it stops the execution and throws a fatal error.
    include() and include_once():if it does not get the include file then it throws the fatal error but does not stop the execution of the script.
    The include_once() statement includes and evaluates the specified file during the execution of the script.
    This is a behavior similar to the include() statement, with the only difference being that if the code from a file has already been included,
    it will not be included again. As the name suggests, it will be included just once.

