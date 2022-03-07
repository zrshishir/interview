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
    include() and include_once():if it does not get the include file then it throws the fatal error but does not
    stop the execution of the script.
    The include_once() statement includes and evaluates the specified file during the execution 
    of the script.
    This is a behavior similar to the include() statement, with the only difference being that
    if the code from a file has already been included,
    it will not be included again. As the name suggests, it will be included just once.

What will be the output - echo print(‘1’)?

    the output is ‘11’ Because print() is return type function so it first print 1 and then it 
    return true to echo and echo has return type so it just print 11. 
    Print has return value 1 and it can be used in expectations. Echo faster and multiple argument

What is Namespace?

    Way of grouping related classes, interfaces, functions and constants.

How many error level available in php?

    There 16 error levels in php. https://www.tutorialrepublic.com/php-reference/php-error-levels.php

Did you use Caching ? What are some processes of caching ?

    https://medium.com/system-design-blog/what-is-caching-1492abb92143

New features for php7?

    - Scalar Type Declaration
        <?php
        // Coercive mode
        function sumOfInts(int ...$ints)
        {
        return array_sum($ints);
        }
        
        var_dump(sumOfInts(2, '3', 4.1));
    - Return type declaration
        <?php

        function arraysSum(array ...$arrays): array
        {
        return array_map(function(array $array): int {
        return array_sum($array);
        }, $arrays);
        }
        
        print_r(arraysSum([1,2,3], [4,5,6], [7,8,9]));
    - Null coalescing operator
        <?php
            // Fetches the value of $_GET['user'] and returns 'nobody'
            // if it does not exist.
            $username = $_GET['user'] ?? 'nobody';
            // This is equivalent to:
            $username = isset($_GET['user']) ? $_GET['user'] : 'nobody';
            
            // Coalescing can be chained: this will return the first
            // defined value out of $_GET['user'], $_POST['user'], and
            // 'nobody'.
            $username = $_GET['user'] ?? $_POST['user'] ?? 'nobody';
        ?>
    - Spaceship operator
        <?php
        // Integers
        echo 1 <=> 1; // 0
        echo 1 <=> 2; // -1
        echo 2 <=> 1; // 1
        
        // Floats
        echo 1.5 <=> 1.5; // 0
        echo 1.5 <=> 2.5; // -1
        echo 2.5 <=> 1.5; // 1
        
        // Strings
        echo "a" <=> "a"; // 0
        echo "a" <=> "b"; // -1
        echo "b" <=> "a"; // 1
        ?>
    - Constant array using define
        <?php
        define('ANIMALS', [
        'dog',
        'cat',
        'bird'
        ]);
        
        echo ANIMALS[1]; // outputs "cat"
        ?>
    - Unicode codepoint escape syntax
        echo "\u{aa}";
        echo "\u{0000aa}";
        echo "\u{9999}";
        
        Output:
        ª
        ª (same as before but with optional leading 0's)
        香
        
        
        And much more……

php 7.4 new features? 

    https://www.php.net/manual/en/migration74.new-features.php

What is the difference between GET and POST?

    - GET displays the submitted data as part of the URL, during POST this information is not shown as it’s encoded in the request.
    - GET can handle a maximum of 2048 characters, POST has no such restrictions.
    - GET allows only ASCII data, POST has no restrictions, binary data are also allowed.
    - Normally GET is used to retrieve data while POST to insert and update.

What are Traits?

    Traits are a mechanism that allows you to create reusable code in languages like PHP where multiple inheritance is not supported. A Trait cannot be instantiated on its own.
    It’s important that a developer knows the powerful features of the language (s)he is working on, and Trait is one of such features.
