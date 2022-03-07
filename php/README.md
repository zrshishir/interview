### Interviewe Questions
How to achieve multiple inheritance in php?
    
    By using interface or trait
What is the difference between Zend Framework 2 and Zend Framework 1?

- Architecture

  ZF1 is based on MVC , ZF2 is based on MOVE. Huge difference. MOVE = Model Operations Views Events , MVC = Models Views Controllers. More here. Zend Framework 2 uses 100% object-oriented code and utilises most of the new features of PHP 5.3, namely namespaces, late static binding, lambda functions and closures.

        Resource: http://cirw.in/blog/time-to-move-on, http://framework.zend.com/manual/2.0/en/ref/overview.html
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
    Resources: http://framework.zend.com/manual/2.0/en/user-guide/overview.html
- 