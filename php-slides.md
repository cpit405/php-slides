# Server-side Scripting in PHP

# CPIT-405
Khalid Alharbi, Ph.D.Last updated Spring 2023

![](img/PHP-MySQL0.png)

![](img/PHP-MySQL1.wmf)

![](img/PHP-MySQL2.png)

# Outline

Server\-side scripting

PHP Syntax and data types

Importing PHP script files

Form handling and validation

Working with databases

Creating a CRUD web app

Creating a CRUD RESTful API

# Server-side Scripting

Server\-side scripting is a technique used in web development that involves running a script on the web server\.

The server\-side script enables you to make your web application more dynamic with a full access to the file system \(e\.g\.\, store and retrieve from a database\)\.

Unlike client\-side scripting\, server\-side scripting hides the source code from client applications\.

The script often results in HTML sent back to the client or produces a structured response \(JSON\) for each client’s request\.

# PHP Programming

PHP is a server\-side or backend scripting language

PHP Stands for the recursive acronym Hypertext Preprocessor

PHP version 1\.0 released in 1995

PHP 8\.x is the current stable release

PHP code may be embedded into HTML and saved as a \.php file

Large\-scale web applications are written in PHP such as Wikipedia\, WordPress\, Etsy\, Tumblr\, and Facebook\*

Many PHP web frameworks \(e\.g\.\, Laravel\, Symfony\, CodeIgniter\, Slim\, and CakePHP\)

\* Facebook uses a derived PHP implementation called Hack for the HipHop Virtual Machine \(HHVM\)

# Installing a local server

* You will need to install the following:
* A web server \(e\.g\.\, Apache HTTP Server\)
  * [https://httpd\.apache\.org](https://httpd.apache.org)
* PHP\, current stable version 8\.2
  * [http://php\.net](http://php.net)
* MySQL Community Server or MariaDB
  * [https://dev\.mysql\.com/downloads/mysql](https://dev.mysql.com/downloads/mysql/)
  * [https://mariadb\.org](https://mariadb.org/)
* Alternatively\, you can install a solution stack such as XAMPP\.
* Postman is a full\-featured HTTP client for working with APIs
  * [https://www\.postman\.com](https://www.postman.com/)

# How to run PHP code?

If your PHP code is inside an HTML page\, then you need a web server that can be configured to execute PHP scripts such as Apache web server httpd\, or PHP’s built in web server:

You may also execute PHP scripts using the php command line:

php –S localhost:4000

php –f path/to/php\-script\.php

# PHP Example

<span style="color:#808080"><\!</span>  <span style="color:#F44747"> DOCTYPE html</span>  <span style="color:#808080">></span>

<span style="color:#808080"><</span>  <span style="color:#569CD6">html</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">lang</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"en"</span>  <span style="color:#808080">></span>

<span style="color:#808080"><</span>  <span style="color:#569CD6">head</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">    </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">title</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4">PHP Example</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">title</span>  <span style="color:#808080">></span>

<span style="color:#808080"></</span>  <span style="color:#569CD6">head</span>  <span style="color:#808080">></span>

<span style="color:#808080"><</span>  <span style="color:#569CD6">body</span>  <span style="color:#808080">></span>

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#D4D4D4">  </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">”\<p>Hi\, I'm a PHP script\!\</p>"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">?></span>  <span style="color:#D4D4D4"> </span>

<span style="color:#808080"></</span>  <span style="color:#569CD6">body</span>  <span style="color:#808080">></span>

<span style="color:#808080"></</span>  <span style="color:#569CD6">html</span>  <span style="color:#808080">></span>

# PHP Basic Syntax

PHP source code files often saved in the file extension “ _\.php”_

PHP script starts with  _<?php _ and ends with  <span style="color:#000000"> _?>_ </span>

In PHP\, variable names are case sensitive but everything else is not\.

PHP supports C\, C\+\+ and Unix shell\-style comments \(//\, /\*  \*/\, or \#\)

PHP Statements end with a semicolon  _;_

Variable names start with the $ sign followed by the name of the variable \(e\.g\.\, $foo = 5\)

PHP uses a dynamic type checking system

echo is a language statement used to output data to the screen

# Variable Scopes

* Unlike C\, global variables are not automatically available to functions
* In PHP\, global variables are accessed inside a function using one of the following two methods:
  * Using the  _global_  keyword inside a function
  * Using the special PHP\-defined and superglobal array  _$GLOBALS_
* Superglobals are built\-in variables that are available in all scopes\.
  * $GLOBALS\, $\_SERVER\, $\_GET\, $\_POST\, $\_FILES\, $\_COOKIE\, $\_SESSION\, $\_REQUEST\, $\_ENV

# 

<span style="color:#569CD6"><?php</span>

<span style="color:#9CDCFE">$foo</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">/\* global scope \*/</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">test</span>  <span style="color:#D4D4D4">\(\)</span>

<span style="color:#D4D4D4">\{</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#9CDCFE">$bar</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">2</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// local scope</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<p></span>  <span style="color:#9CDCFE">$bar</span>  <span style="color:#CE9178">\</p>"</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// Outputs 2</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<p></span>  <span style="color:#9CDCFE">$foo</span>  <span style="color:#CE9178">\</p>"</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// Results in an error</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#608B4E">// Accessing a global variable</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#608B4E">// Method 1: Using the global keyword</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#569CD6">global</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$foo</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<p></span>  <span style="color:#9CDCFE">$foo</span>  <span style="color:#CE9178">\</p>"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#608B4E">// Method 2: Using the </span>  <span style="color:#608B4E">superglobal</span>  <span style="color:#608B4E"> PHP\-defined $GLOBALS array\.</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'foo’</span>  <span style="color:#D4D4D4">\]; </span>  <span style="color:#608B4E">//Outputs 1</span>

<span style="color:#D4D4D4">\}</span>

<span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">test</span>  <span style="color:#D4D4D4">\(\);</span>

<span style="color:#569CD6">?></span>

Variable Scopes in PHP

# Data Types

* PHP supports the following data types:
  * Strings
  * <span style="color:#4472C4">$name </span>  <span style="color:#000000">=</span>  <span style="color:#4472C4"> “CPIT”</span>
  * Integers
  * <span style="color:#4472C4">$number </span>  <span style="color:#000000">=</span>  <span style="color:#4472C4"> 405</span>
  * Floating point numbers
  * <span style="color:#4472C4">$</span>  <span style="color:#4472C4">avg\_gpa</span>  <span style="color:#4472C4"> </span>  <span style="color:#000000">=</span>  <span style="color:#4472C4"> 3\.92</span>
  * Booleans
  * _$offered_  =  _true_

# Data Types (cont.)

* Arrays
  * _$topics = _  <span style="color:#0000FF">array</span>  _\(“html”\, “_  _css_  _”\, “_  _javascript_  _”\)_
* Objects
  * <span style="color:#0000FF">class</span>  <span style="color:#3366FF"> </span>  _Student_  <span style="color:#5B9BD5"> \{ </span>  <span style="color:#0000FF">function </span>  _Student_  <span style="color:#5B9BD5">\($name\) \{ </span>
  * <span style="color:#5B9BD5">                          </span>  <span style="color:#0000FF">$this </span> \->  <span style="color:#5B9BD5">name </span>  <span style="color:#000000">= </span>  <span style="color:#5B9BD5">$name\}\} </span>
  * <span style="color:#5B9BD5">$</span>  <span style="color:#5B9BD5">ali</span>  <span style="color:#5B9BD5"> = </span>  _new_  <span style="color:#5B9BD5"> </span>  _Student_  <span style="color:#5B9BD5">\(“Ali”\)</span>
* Null
  * <span style="color:#4472C4">$x = </span>  <span style="color:#0000FF">null</span>
* Resource
  * A resource is a special variable\, holding a reference to an external resource \(e\.g\.\, a database\)\.

# String Functions

| Function | Description/Example |
| :-: | :-: |
| strlen | Returns the length of the given string.<br /><br />echo strlen("CPIT 405"); // outputs 8 |
| strpos | Find the position of the first occurrence of a substring in a string.<br /><br />$x = “CPIT 201, 305, 405, 498, 499”;<br />echo strpos($x, "405"); // Outputs 15 |
| str_replace | Replace all occurrences of the search string with the replacement string<br /><br />//outputs "CPIT 405”<br /><br />echo str_replace("305", "405", "CPIT 305");  |
| substr | Return part of String<br /><br />echo substr("CPIT", -2); // outputs "IT” |

# Constants

* Constants are global variables whose values can’t be changed
* To create a constant in PHP\, use the  _define\(\) _ function:
  * define\(name\, value\, case\-insensitive\)

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#DCDCAA">    define</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"TITLE"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"CPIT\-405 Fall 2017”</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#569CD6">    function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">f</span>  <span style="color:#D4D4D4">\(\) \{</span>

<span style="color:#D4D4D4">        </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> TITLE; </span>  <span style="color:#608B4E">// outputs "CPIT\-405 Fall 2017"</span>

<span style="color:#D4D4D4">    \}</span>

<span style="color:#DCDCAA">    f</span>  <span style="color:#D4D4D4">\(\);</span>

<span style="color:#569CD6"> ?></span>  <span style="color:#D4D4D4">   </span>

# Operators (I)

Arithmetic Operators:

$x = 5

$y = 2

| Operator | Name | Example | Result |
| :-: | :-: | :-: | :-: |
| + | Addition | $x + $y | 7 |
| - | Subtraction | $x - $y | 3 |
| * | Multiplication | $x * $y | 10 |
| / | Division | $x / $y | 2.5 |
| % | Modulus | $x % $y | 1 |
| ** | Exponentiation | $x ** $y | 25 |

* Assignment Operators are equivalent to JavaScript’s operators\.
* Examples:
  * $x = $y
  * $x \+= $y
  * $x \-= $y
  * $x \*= $y
  * $x /= $y
  * $x %= $y

* Comparison operators are equivalent to JavaScript’s operators\.
* Examples:
  * $x == $y // Equal\. It returns true if $x is equal to $y
  * $x === $y // Identical\. It returns true if both $x is equal to $y\, and they are of the same type\.
  * $x \!= $y // Not equal\. It returns true if $x is not equal to $y
  * $x <> $y // Not equal\. It returns true if $x is not equal to $y
  * $x > $y
  * $x < $y
  * $x >= $y
  * $x <= $y

String concatenation and concatenation  assignment

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#9CDCFE">$x</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">"CPIT"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$y</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">405</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<p>Welcome to "</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$x</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#CE9178">"\-"</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$y</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#CE9178">"\</p>"</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// Outputs "Welcome to CPIT\-405"</span>

<span style="color:#9CDCFE">$x</span>  <span style="color:#D4D4D4">\.=</span>  <span style="color:#9CDCFE">$y</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// Concatenation assignment\. It appends $y to $x</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$x</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#608B4E">// Outputs "CPIT405"</span>

<span style="color:#569CD6">?></span>  <span style="color:#D4D4D4"> </span>

# Control statements

* PHP has the following control statements:
  * if
  * else
  * elseif/else if
  * switch
  * while
  * do\-while
  * for
  * foreach
  * break
  * continue

# Control Statements: if…else

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">testNum</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$a</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#9CDCFE">    $result</span>  <span style="color:#D4D4D4"> =</span>  <span style="color:#CE9178">’’</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">    if</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$a</span>  <span style="color:#D4D4D4"> > </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#9CDCFE">        $result</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">'positive’</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">    \} </span>  <span style="color:#C586C0">else</span>  <span style="color:#D4D4D4"> \{</span>

<span style="color:#9CDCFE">        $result</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">'NOT positive’</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">    \}</span>

<span style="color:#C586C0">    return</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$result</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">\}</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#DCDCAA">testNum</span>  <span style="color:#D4D4D4">\(\-</span>  <span style="color:#B5CEA8">5</span>  <span style="color:#D4D4D4">\)\);</span>

# Control Statements: switch

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#6A9955">/\* The PHP\_OS\_FAMILY is a predefined constant that holds </span>

<span style="color:#6A9955">\* the operating system family name PHP was built for\.</span>

<span style="color:#6A9955">\* One of 'Windows'\, 'BSD'\, 'Darwin'\, 'Solaris'\, 'Linux' or 'Unknown'\.</span>

<span style="color:#6A9955">\*/</span>

<span style="color:#C586C0">switch</span>  <span style="color:#D4D4D4"> \(PHP\_OS\_FAMILY\) \{</span>

<span style="color:#CCCCCC">    </span>  <span style="color:#C586C0">case</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"Windows"</span>  <span style="color:#D4D4D4">:</span>

<span style="color:#DCDCAA">        echo</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#CE9178">"You're running Windows"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#C586C0">        break</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">    case</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"Darwin"</span>  <span style="color:#D4D4D4">:</span>

<span style="color:#DCDCAA">        echo</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#CE9178">"You're running macOS"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#C586C0">        break</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">    default</span>  <span style="color:#D4D4D4">:</span>

<span style="color:#DCDCAA">        echo</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#CE9178">"You're running "</span>  <span style="color:#D4D4D4"> \. PHP\_OS\_FAMILY\);</span>

<span style="color:#D4D4D4">\}</span>

# Control Statements: for

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#C586C0">for</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> <= </span>  <span style="color:#B5CEA8">10</span>  <span style="color:#D4D4D4">; </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">\+\+\) \{</span>

<span style="color:#DCDCAA">    echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">\}</span>

# Control Statements: while

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">while</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> <= </span>  <span style="color:#B5CEA8">5</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#CCCCCC">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">\+\+; </span>  <span style="color:#6A9955">/\* prints $</span>  <span style="color:#6A9955">i</span>  <span style="color:#6A9955"> then</span>  <span style="color:#CCCCCC"> </span>  <span style="color:#6A9955">increments $</span>  <span style="color:#6A9955">i</span>  <span style="color:#6A9955"> </span>

<span style="color:#6A9955">                  \(post\-increment\) \*/</span>

<span style="color:#D4D4D4">\}</span>

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">do</span>  <span style="color:#D4D4D4"> \{</span>

<span style="color:#DCDCAA">    echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">\+\+; </span>  <span style="color:#6A9955">/\* prints $</span>  <span style="color:#6A9955">i</span>  <span style="color:#6A9955"> then increments $</span>  <span style="color:#6A9955">i</span>  <span style="color:#6A9955"> </span>

<span style="color:#6A9955">                  \(post\-increment\) \*/</span>

<span style="color:#D4D4D4">\} </span>  <span style="color:#C586C0">while</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> <= </span>  <span style="color:#B5CEA8">5</span>  <span style="color:#D4D4D4">\);</span>

# Equality check (==) vs Identity check (===)

== compares value with type conversion while === compares value and type with no type conversion

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">;</span>  <span style="color:#6A9955">// == value comparison with type conversion\.</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">==</span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">\);    </span>  <span style="color:#6A9955">// bool\(true\)</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">==</span>  <span style="color:#CE9178">'1’</span>  <span style="color:#D4D4D4">\);  </span>  <span style="color:#6A9955">// bool\(true\)</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">==</span>  <span style="color:#569CD6">true</span>  <span style="color:#D4D4D4">\); </span>  <span style="color:#6A9955">// bool\(true\)</span>

<span style="color:#6A9955">// === value and type comparison with no type conversion is done\.</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">===</span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">\);     </span>  <span style="color:#6A9955">// bool\(true\)</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">===</span>  <span style="color:#CE9178">'1’</span>  <span style="color:#D4D4D4">\);  </span>  <span style="color:#6A9955">// bool\(false\)</span>

<span style="color:#DCDCAA">var\_dump</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">i</span>  <span style="color:#D4D4D4">===</span>  <span style="color:#569CD6">true</span>  <span style="color:#D4D4D4">\); </span>  <span style="color:#6A9955">// bool\(false\)</span>

# Functions

Functions may use default parameter\. Example:

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">set\_department</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$dept</span>  <span style="color:#D4D4D4">= </span>  <span style="color:#CE9178">"IT"</span>  <span style="color:#D4D4D4">\)\{</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#C586C0">return</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<p>Department name: "</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$dept</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#CE9178">"\</p>"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">\}</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">set\_department</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">'CS'</span>  <span style="color:#D4D4D4">\); </span>  <span style="color:#608B4E">// Outputs "Department name: CS"</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">set\_department</span>  <span style="color:#D4D4D4">\(\); </span>  <span style="color:#608B4E">// Outputs "Department name: IT"</span>

<span style="color:#569CD6">?></span>  <span style="color:#D4D4D4"> </span>

# Arrays

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#9CDCFE">$topics</span>  <span style="color:#D4D4D4"> =</span>  <span style="color:#DCDCAA">array</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"HTML"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"CSS"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"JavaScript”</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"I know "</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$topics</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#CE9178">”</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$topics</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#CE9178">"\, "</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$topics</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#B5CEA8">2</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#CE9178">”\.”</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">?></span>  <span style="color:#D4D4D4"> </span>

# Importing PHP Script Files (I)

We can save multiple PHP scripts in external files and import them using the  _include_  _ _ or  _require_  _ statements:_

The difference between the two statements is that  _require_  will  produce an error and stop the script upon failure\, while  _include_  _ _ will result in a warning and the script will continue running\.

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#C586C0">include</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\./file1\.php'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">require</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\./file2\.php'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">?></span>

We can also import a PHP script using the  _include\_once_  _ _ or  _require\_once_  _ statements:_

Again\, both  __include__  and  __require__  are identical\, but they handle errors differently\. Include will result in a warning and required in an error\.

__include\_once __ and  __require\_once __ is also similar except PHP will check if the file has already been included/required\, then it won’t include/require it again\.

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#C586C0">include\_once</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\./file1\.php'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">require\_once</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\./file2\.php'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">?></span>

# Form Handling

PHP is often used to handle HTML forms submitted by the user

This includes server\-side form validation for security and application reasons

There are two PHP superglobals used to collect HTML form data: $\_POST and $\_GET

Both $\_POST and $\_GET contain an array of form data in name and value pairs

$\_GET is used when form data is passed to PHP via URL parameters

$\_POST is used when form data is passed to PHP via the HTTP POST method

# Form Handling: GET vs POST

* Two HTTP methods are often used for submitting and receiving data between the client and the server: HTTP GET and HTTP POST
* GET
  * Often used to request data from the server
  * URL contains query string \(e\.g\.\, ?name=CPIT\)
  * Query string is sent in the URL of the HTTP GET request
  * URL example: http://example\.com/my\_form\.php?name=CPIT&number=405
  * The URL of the request is often added to the browser’s history
  * GET requests should be only used to retrieve data from the server and NOT submitting data especially sensitive data

# Form Handling: GET vs POST (cont.)

* POST
  * Often used to submit data from the client to the server\.
  * Query string is not sent in the URL of the HTTP POST request
  * Form data is sent in the body of the POST request
  * Request example:
  * The URL of the POST request is not added to the browser’s history
  * Reloading the page will result in re\-submitting the data to the server

_POST_  <span style="color:#569CD6"> </span>  _/courses/_  _add\_course\.php_  _  _  <span style="color:#569CD6">HTTP/1\.1</span>

<span style="color:#8FAADC">HOST: </span>  <span style="color:#FFE699">example\.com</span>

<span style="color:#DCDCAA">course</span>  <span style="color:#CE9178">=</span>  <span style="color:#CE9178">cpit</span>  <span style="color:#DCDCAA">&number</span>  <span style="color:#CE9178">=405</span>

# Form Handling: Example (index.html)

<span style="color:#D4D4D4"> </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">form</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">id</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">myForm</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">action</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">myform\.php</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">method</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"post"</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">label</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">for</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">userNameInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4">User name:</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">label</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">input</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"text"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">id</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">userNameInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">name</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"uname"</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">label</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">for</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">emailInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4">E\-mail:</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">label</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">input</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">id</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">emailInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">name</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">label</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">for</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">passwordInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4">Password:</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">label</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">input</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"password"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">id</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">passwordInput</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">name</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"pw"</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4">        </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">input</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"submit"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">value</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"signup"</span>  <span style="color:#808080">></span>

<span style="color:#D4D4D4"> </span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">form</span>  <span style="color:#808080">></span>

# Form Handling: Example (myform.php)

<span style="color:#808080"><</span>  <span style="color:#569CD6">body</span>  <span style="color:#808080">></span>

<span style="color:#808080"><</span>  <span style="color:#569CD6">p</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4">Thank you\, </span>  <span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$\_POST</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"uname"</span>  <span style="color:#D4D4D4">\]</span>  <span style="color:#569CD6">?></span>  <span style="color:#D4D4D4">\, for signing up\!</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">p</span>  <span style="color:#808080">></span>

<span style="color:#808080"><</span>  <span style="color:#569CD6">p</span>  <span style="color:#808080">></span>  <span style="color:#D4D4D4"> Please check your email: </span>  <span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">$\_POST</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#D4D4D4">\] </span>  <span style="color:#569CD6">?></span>  <span style="color:#D4D4D4"> </span>

<span style="color:#D4D4D4">to complete registration and confirm your email</span>  <span style="color:#808080"></</span>  <span style="color:#569CD6">p</span>  <span style="color:#808080">></span>

<span style="color:#808080"></</span>  <span style="color:#569CD6">body</span>  <span style="color:#808080">></span>

# Form Validation

* Input elements in HTML forms should be validated both on client and server sides\.
* Client–side validation is done using JavaScript
  * Provide better user experience/feedback to the user
  * Users can see errors immediately as they enter the form
  * But you should not rely or trust client\-side validation
  * Client\-side validation can be easily bypassed and manipulated
* Server\-side validation must be always done for all forms
  * Perform input validation and sanitization on the server to protect against malicious data \(e\.g\.\, SQL injection\)\.

# Form Validation (client-side)

Using HTML5 validation attributes: type and required

Email: \<input type="text" type="email" name="email" email><br>

Or using JavaScript

<span style="color:#D4D4D4">Email: </span>  <span style="color:#808080"><</span>  <span style="color:#569CD6">input</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"text"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">type</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">name</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">required</span>  <span style="color:#808080">></span>

<span style="color:#569CD6">var</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#9CDCFE">uname</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">document</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">forms</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">myForm</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">\]\[</span>  <span style="color:#CE9178">"username"</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#9CDCFE">value</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">  if</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">uname</span>  <span style="color:#D4D4D4"> && </span>  <span style="color:#9CDCFE">uname</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#DCDCAA">trim</span> \(\) <span style="color:#D4D4D4"> == </span>  <span style="color:#CE9178">""</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#9CDCFE">     </span>  <span style="color:#9CDCFE">document</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#DCDCAA">getElementById</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">errorSection</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">\)\.</span>  <span style="color:#9CDCFE">innerText</span>  <span style="color:#D4D4D4">= </span>  <span style="color:#D4D4D4">                                </span>  <span style="color:#CE9178">"username is required"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#C586C0">     return</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">false</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">  \}</span>

# Form Validation (server-side I)

<span style="color:#569CD6"><?php</span>  <span style="color:#D4D4D4"> </span>

<span style="color:#6A9955">// Clean the input \(remove whitespaces </span>

<span style="color:#6A9955">// and strip unnecessary characters\.\)</span>

<span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#DCDCAA">trim</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$\_POST</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"email"</span>  <span style="color:#D4D4D4">\]\);</span>

<span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#DCDCAA">stripslashes</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#DCDCAA">htmlspecialchars</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#6A9955">// Validate the input</span>

<span style="color:#C586C0">if</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#DCDCAA">filter\_var</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$email</span>  <span style="color:#D4D4D4">\, FILTER\_VALIDATE\_EMAIL\)\) \{</span>

<span style="color:#D4D4D4">  </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"Valid email address\."</span>  <span style="color:#D4D4D4">; </span>

<span style="color:#D4D4D4">\} </span>  <span style="color:#C586C0">else</span>  <span style="color:#D4D4D4">\{</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"Invalid email address\."</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">\}</span>

* Forms may be validated using PHP built\-in functions:
  * filter\_var\(\) uses a set of predefined filters
  * preg\_match\(\) performs regular expression matching
* Third\-party libraries are also available
  * Example: [https://github\.com/Respect/Validation](https://github.com/Respect/Validation)
  * In some cases\, it is better to use a library that has been rigorously tested in the wild than writing your own regular expressions\.

# PHP MySQL CRUD Web Application

# Create, Read, Update, and Delete (CRUD)

# Creating a CRUD Web App in PHP

CRUD stands for  _C_ reate\,  _R_ ead\,  _U_ pdate\, and  _D_ elete

We will create a simple “To Do” app in PHP that communicates with a MySQL database

The server\-side code will make a connection to the database server

The client application sends requests to create\, retrieve\, update\, and delete items

The server\-side code will handle all CRUD requests using PHP and communicates with our MySQL database and returns html to the client\.

![](img/PHP-MySQL3.jpg)

# Warning!

* Embedding PHP in HTML is bad\!\!
* It breaks the fundamental concept of “separation of concerns”\.
* Server logic should not be mixed with presentation code \(HTML\)
* This example is only for demonstration purposes\.
* What we should do instead is have our PHP server code communicates with the database and return JSON to the client\.
  * We will see this right after this demo\.

# Creating a To Do List Web App

# MySQL

* Connect to the database server using the command line or a GUI tool \(e\.g\.\, PHP admin\)
* Command Line Interface \(CLI\)
  * $ mysql –u username –p
* Create a database with the following table and columns:

| Field | Type | Null | Key | Extra |
| :-: | :-: | :-: | :-: | :-: |
| id | MEDIUMINT(9)  | No | Primary Key | auto_increment |
| task | VARCHAR(255) | No |  |  |
| date_added | DATETIME | No |  |  |
| done | TINYINT(1) | No |  |  |

# Creating a Database in MySQL (I)

<span style="color:#569CD6">CREATE</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">DATABASE</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#D4D4D4">todo\_db</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">USE</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#D4D4D4">todo\_db</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#569CD6">CREATE</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">TABLE</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#D4D4D4">todo\_task</span>  <span style="color:#D4D4D4">\(</span>

<span style="color:#D4D4D4">       id MEDIUMINT </span>  <span style="color:#569CD6">NOT</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4"> AUTO\_INCREMENT\, </span>

<span style="color:#D4D4D4">       task </span>  <span style="color:#569CD6">VARCHAR</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#B5CEA8">255</span>  <span style="color:#D4D4D4">\) </span>  <span style="color:#569CD6">NOT</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4">\, </span>

<span style="color:#D4D4D4">       </span>  <span style="color:#D4D4D4">date\_added</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">DATETIME</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">NOT</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4">\,</span>

<span style="color:#D4D4D4">       done </span>  <span style="color:#569CD6">TINYINT</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">\) </span>  <span style="color:#569CD6">NOT</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4"> DEFAULT </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">\,</span>

<span style="color:#569CD6">       PRIMARY</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#569CD6">KEY</span>  <span style="color:#D4D4D4"> \(id\)\);</span>

<span style="color:#D4D4D4">mysql</span>  <span style="color:#D4D4D4">> DESCRIBE </span>  <span style="color:#D4D4D4">todo\_task</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">\+</span>  <span style="color:#608B4E">\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\+\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+</span>

<span style="color:#D4D4D4">| Field      | </span>  <span style="color:#569CD6">Type</span>  <span style="color:#D4D4D4">         | </span>  <span style="color:#569CD6">Null</span>  <span style="color:#D4D4D4"> | </span>  <span style="color:#569CD6">Key</span>  <span style="color:#D4D4D4"> | Default | Extra          |</span>

<span style="color:#D4D4D4">\+</span>  <span style="color:#608B4E">\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\+\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+</span>

<span style="color:#D4D4D4">| id         | </span>  <span style="color:#D4D4D4">mediumint</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#B5CEA8">9</span>  <span style="color:#D4D4D4">\) | </span>  <span style="color:#569CD6">NO</span>  <span style="color:#D4D4D4">   | PRI | </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4">    | </span>  <span style="color:#D4D4D4">auto\_increment</span>  <span style="color:#D4D4D4"> |</span>

<span style="color:#D4D4D4">| task       | </span>  <span style="color:#569CD6">varchar</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#B5CEA8">255</span>  <span style="color:#D4D4D4">\) | </span>  <span style="color:#569CD6">NO</span>  <span style="color:#D4D4D4">   |     | </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4">    |                |</span>

<span style="color:#D4D4D4">| </span>  <span style="color:#D4D4D4">date\_added</span>  <span style="color:#D4D4D4"> | </span>  <span style="color:#569CD6">datetime</span>  <span style="color:#D4D4D4">     | </span>  <span style="color:#569CD6">NO</span>  <span style="color:#D4D4D4">   |     | </span>  <span style="color:#569CD6">NULL</span>  <span style="color:#D4D4D4">    |                |</span>

<span style="color:#D4D4D4">| done       | </span>  <span style="color:#569CD6">tinyint</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#B5CEA8">1</span>  <span style="color:#D4D4D4">\)   | </span>  <span style="color:#569CD6">NO</span>  <span style="color:#D4D4D4">   |     | </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">       |                |</span>

<span style="color:#D4D4D4">\+</span>  <span style="color:#608B4E">\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\+\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\+\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\+</span>

# Connecting to the Database (db_connection.php)

<span style="color:#569CD6"><?php</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">servername</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">"localhost"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$username</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">db\_user</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$password</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">db\_pw</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$database</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">todo\_db</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#6A9955">// Create connection object and connect to the database</span>

<span style="color:#9CDCFE">$conn</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#569CD6">new</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#4EC9B0">mysqli</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">servername</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$username</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$password</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$database</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#6A9955">// Check connection</span>

<span style="color:#C586C0">if</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$conn</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#9CDCFE">connect\_error</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#C586C0">die</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"Connection failed: "</span>  <span style="color:#D4D4D4"> \. </span>  <span style="color:#9CDCFE">$conn</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#9CDCFE">connect\_error</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">\}</span>

<span style="color:#569CD6">?></span>

# Using the database connection

We can use the database connection object defined in db\_connection\.php in any other webpage using require\_once:

Now\, the conn object can be accessed anywhere in the PHP script that required it:

<span style="color:#DCDCAA">require\_once</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">'\./</span>  <span style="color:#CE9178">db\_connection\.php</span>  <span style="color:#CE9178">'</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'conn'</span>  <span style="color:#D4D4D4">\]</span>

# Retrieving data from MySQL

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">get\_all\_todos</span>  <span style="color:#D4D4D4">\(\)</span>

<span style="color:#D4D4D4">\{</span>

<span style="color:#D4D4D4">  </span>  <span style="color:#9CDCFE">$query\_stmt</span>  <span style="color:#D4D4D4">= </span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">SELECT</span>  <span style="color:#CE9178"> </span>  <span style="color:#CE9178">id\,task\,date\_added\,done</span>  <span style="color:#CE9178"> </span>  <span style="color:#569CD6">FROM</span>  <span style="color:#CE9178"> tasks </span>  <span style="color:#569CD6">WHERE</span>  <span style="color:#CE9178"> done</span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178"> </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#CE9178">;"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">  </span>  <span style="color:#9CDCFE">$response</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'conn'</span>  <span style="color:#D4D4D4">\]\-></span>  <span style="color:#DCDCAA">query</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$query\_stmt</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">  </span>  <span style="color:#C586C0">if</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$response</span>  <span style="color:#D4D4D4"> && </span>  <span style="color:#9CDCFE">$response</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#9CDCFE">num\_rows</span>  <span style="color:#D4D4D4"> > </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4">     </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\<ul id="my\-list">'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">     </span>  <span style="color:#C586C0">while</span>  <span style="color:#D4D4D4"> \(</span>  <span style="color:#9CDCFE">$row</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">$response</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">fetch\_array</span>  <span style="color:#D4D4D4">\(\)\) \{</span>

<span style="color:#D4D4D4">        </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">"\<li>"</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#CE9178">'<input type="checkbox"</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#CE9178">             "name="</span>  <span style="color:#CE9178">checkBoxList</span>  <span style="color:#CE9178">\[\]"</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#D4D4D4">             </span>  <span style="color:#CE9178">“value="'</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#9CDCFE">$row</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"id"</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#CE9178">'">\<span>'</span>  <span style="color:#D4D4D4">\.</span>  <span style="color:#D4D4D4">             </span>  <span style="color:#9CDCFE">$row</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">"task"</span>  <span style="color:#D4D4D4">\]\.</span>  <span style="color:#CE9178">"\</span>\</li>"</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">    \}</span>  <span style="color:#DCDCAA"> echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\</ul>'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">  \} </span>  <span style="color:#C586C0">else</span>  <span style="color:#D4D4D4"> \{ </span>  <span style="color:#DCDCAA">echo</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#CE9178">'\<h2>Your </span>  <span style="color:#CE9178">ToDo</span>  <span style="color:#CE9178"> list is empty\!\</h2>’</span>  <span style="color:#D4D4D4">;\}</span>

<span style="color:#D4D4D4">\}</span>

# Inserting Data into MySQL

You need to take proper precautions when inserting data into MySQL\.

Input data should be validated and sanitized before attempting to insert data into your database\.

SQL injection is a popular attack method for adversaries where an attack inserts SQL code in form fields \(e\.g\.\, “; OR ‘1’=‘1’”\)

The PHP’s MySQL driver extension provides a mechanism called “prepared statements” to create MySQL insert statements that are not prone to SQL injection

Use the prepare method to create your Insert statement

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">insert\_task</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$task</span>  <span style="color:#D4D4D4">\)\{</span>

<span style="color:#608B4E">// use prepared statement to protect against SQL injections</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">insert\_stmt</span>  <span style="color:#9CDCFE"> </span>  <span style="color:#D4D4D4">= </span>  <span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'conn'</span>  <span style="color:#D4D4D4">\]\-></span>  <span style="color:#DCDCAA">prepare</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">INSERT</span>  <span style="color:#CE9178"> </span>  <span style="color:#569CD6">INTO</span>  <span style="color:#CE9178"> tasks </span>  <span style="color:#CE9178">\(task\, </span>  <span style="color:#CE9178">date\_added</span>  <span style="color:#CE9178">\, done\) </span>  <span style="color:#569CD6">VALUES</span>  <span style="color:#CE9178">\(?\, </span>  <span style="color:#569CD6">now</span>  <span style="color:#CE9178">\(\)\,</span>  <span style="color:#B5CEA8">0</span>  <span style="color:#CE9178">\);"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#C586C0">if</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">insert\_stmt</span>  <span style="color:#D4D4D4">\)\{</span>

<span style="color:#608B4E">// Bind our variable to the prepared statement as a parameter</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">insert\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">bind\_param</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"s"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$task</span>  <span style="color:#D4D4D4">\); </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">insert\_statement</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">execute</span>  <span style="color:#D4D4D4">\(\);</span>  <span style="color:#608B4E">// close the prepared statement</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">insert\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">close</span>  <span style="color:#D4D4D4">\(\);</span>

<span style="color:#D4D4D4">\}</span>

# Updating Data in MySQL

<span style="color:#608B4E">// Iterate through a list of ids of the </span>  <span style="color:#608B4E">todo</span>  <span style="color:#608B4E"> items</span>

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">mark\_as\_done</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">checkBoxList</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4"> </span>  <span style="color:#C586C0">foreach</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">checkBoxList</span>  <span style="color:#D4D4D4"> as </span>  <span style="color:#9CDCFE">$value</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#9CDCFE"> $</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'conn'</span>  <span style="color:#D4D4D4">\]\-></span>  <span style="color:#DCDCAA">prepare</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">UPDATE</span>  <span style="color:#CE9178"> tasks </span>  <span style="color:#569CD6">SET </span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">  </span>  <span style="color:#D4D4D4">\+</span>  <span style="color:#CE9178"> </span>  <span style="color:#CE9178">                                         </span>  <span style="color:#CE9178">                                        "done </span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178"> </span>  <span style="color:#B5CEA8">1</span>  <span style="color:#CE9178"> </span>  <span style="color:#569CD6">WHERE</span>  <span style="color:#CE9178"> id </span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178"> ?"</span>  <span style="color:#D4D4D4">\);</span>  <span style="color:#D4D4D4">    </span>  <span style="color:#C586C0">if</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4"> \-></span>  <span style="color:#DCDCAA">bind\_param</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"s"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$value</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#C586C0">if</span>  <span style="color:#D4D4D4"> \(\!</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4"> \-></span>  <span style="color:#DCDCAA">execute</span>  <span style="color:#D4D4D4">\(\)\) \{</span>

<span style="color:#D4D4D4">           </span>  <span style="color:#DCDCAA">print\_r</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">'Error: '</span>  <span style="color:#D4D4D4"> \. </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4"> \-></span>  <span style="color:#9CDCFE">err</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">           </span>  <span style="color:#C586C0">return</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">       \}</span>

<span style="color:#608B4E">       </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">update\_stmt</span>  <span style="color:#D4D4D4"> \-></span>  <span style="color:#DCDCAA">close</span>  <span style="color:#D4D4D4">\(\);</span>

<span style="color:#D4D4D4">\}\}\}</span>

# Deleting Data from MySQL

<span style="color:#569CD6">function</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#DCDCAA">delete\_item</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">checkBoxList</span>  <span style="color:#D4D4D4">\)\{</span>

<span style="color:#D4D4D4">  </span>  <span style="color:#C586C0">foreach</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">checkBoxList</span>  <span style="color:#D4D4D4"> as </span>  <span style="color:#9CDCFE">$value</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#608B4E">// create a prepared update statement</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#D4D4D4">    </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">$GLOBALS</span>  <span style="color:#D4D4D4">\[</span>  <span style="color:#CE9178">'conn'</span>  <span style="color:#D4D4D4">\]\-></span>  <span style="color:#DCDCAA">prepare</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">DELETE</span>  <span style="color:#CE9178"> </span>  <span style="color:#569CD6">FROM</span>  <span style="color:#CE9178"> tasks</span>  <span style="color:#CE9178">"</span>    <span style="color:#D4D4D4">\+</span>  <span style="color:#CE9178"> </span>  <span style="color:#CE9178">                 </span>  <span style="color:#CE9178">                                             </span>  <span style="color:#CE9178">"</span>   <span style="color:#569CD6">WHERE</span>  <span style="color:#CE9178"> id </span>  <span style="color:#D4D4D4">=</span>  <span style="color:#CE9178"> ?"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">    </span>  <span style="color:#C586C0">if</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4">\) \{</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">bind\_param</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"s"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$value</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#C586C0">if</span>  <span style="color:#D4D4D4"> \(\!</span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">execute</span>  <span style="color:#D4D4D4">\(\)\) \{</span>

<span style="color:#D4D4D4">          </span>  <span style="color:#DCDCAA">print\_r</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">'Error : '</span>  <span style="color:#D4D4D4"> \. </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#9CDCFE">err</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#D4D4D4">          </span>  <span style="color:#C586C0">return</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#D4D4D4">       \}</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#608B4E">// close the prepared statement</span>

<span style="color:#D4D4D4">       </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">delete\_stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">close</span>  <span style="color:#D4D4D4">\(\);</span>

<span style="color:#D4D4D4">\}</span>   <span style="color:#D4D4D4">\} \}</span>

# Demo

[https://gitlab\.com/kalharbi/todo\-php\-mysql](https://gitlab.com/kalharbi/todo-php-mysql)

# Our CRUD app is now complete

* Refer to the complete source code at:
  * [https://gitlab\.com/kalharbi/todo\-php\-mysql](https://gitlab.com/kalharbi/todo-php-mysql)
* Next\, fork the repository and add additional features:
  * Add a button to mark all items/tasks as done
  * Group the items by the date they were added on \(e\.g\.\, today\, last week\, etc\.\)
  * Show the tasks that were marked as done in a different web page

# More on SQL injection (I)

https://xkcd\.com/327/

![](img/PHP-MySQL4.png)

Prepared/Parameterized statements are used to execute SQL statements with high efficiency and protect against SQL injections\.

<span style="color:#569CD6"><?</span>  <span style="color:#569CD6">php</span>

<span style="color:#9CDCFE">$conn</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#569CD6">new</span>  <span style="color:#D4D4D4"> </span>  <span style="color:#4EC9B0">mysqli</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">example\.com</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"user"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"password"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#CE9178">"database"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#6A9955">// Prepared statement</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">stmt</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#9CDCFE">$conn</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">prepare</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#569CD6">INSERT INTO</span>  <span style="color:#CE9178"> tasks \(task\, </span>  <span style="color:#CE9178">date\_added</span>  <span style="color:#CE9178">\, done\) </span>  <span style="color:#569CD6">VALUES</span>  <span style="color:#CE9178">\(?\, ?\, ?\)"</span>  <span style="color:#D4D4D4">\);</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">task\_var</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#CE9178">'buy milk'</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">date\_var</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#DCDCAA">date</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">'Y\-m\-d </span>  <span style="color:#CE9178">H:i:s</span>  <span style="color:#CE9178">'</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#DCDCAA">time</span>  <span style="color:#D4D4D4">\(\)\);</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">done\_var</span>  <span style="color:#D4D4D4"> = </span>  <span style="color:#B5CEA8">0</span>  <span style="color:#D4D4D4">;</span>

<span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">stmt</span>  <span style="color:#D4D4D4">\-></span>  <span style="color:#DCDCAA">bind\_param</span>  <span style="color:#D4D4D4">\(</span>  <span style="color:#CE9178">"</span>  <span style="color:#CE9178">ssi</span>  <span style="color:#CE9178">"</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">task\_var</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">date\_var</span>  <span style="color:#D4D4D4">\, </span>  <span style="color:#9CDCFE">$</span>  <span style="color:#9CDCFE">done\_var</span>  <span style="color:#D4D4D4">\); </span>  <span style="color:#6A9955">/\* "</span>  <span style="color:#6A9955">ssi</span>  <span style="color:#6A9955">" means that </span>

<span style="color:#6A9955">                                                            </span>  <span style="color:#6A9955">$</span>  <span style="color:#6A9955">task\_var</span>  <span style="color:#6A9955"> is bound as a String\,</span>

<span style="color:#6A9955">                                                            $</span>  <span style="color:#6A9955">date\_var</span>  <span style="color:#6A9955"> as a string\, and</span>

<span style="color:#6A9955">                                                            $</span>  <span style="color:#6A9955">done\_var</span>  <span style="color:#6A9955"> as an integer</span>

# CRUD REST API with PHP & MariaDB

# Create a CRUD REST API with PHP & MariaDB

* We will create a RESTful API in PHP that communicates with the database and returns JSON to the client\.
* The API will have the following endpoints:
  * POST /api/create Create a new ToDo item
  * GET /api/readAll\.php Get all Todos
  * GET /api/readOne\.php Get a single Todo item
  * PUT /api/update Update a ToDo item by its id
  * DELETE /api/delete Delete a ToDo item by its id

# REST API with PHP & MariaDB [Video]

# Demo

[https://gitlab\.com/cpit405/php\-mysql\-rest\-api](https://gitlab.com/cpit405/php-mysql-rest-api)

# Wrapping up!

* PHP is a powerful server\-side scripting language\.
* We learned the basics of writing PHP scripts: syntax and structure\.
* We created a CRUD web application with PHP and MySQL
* We also created a CRUD REST API with PHP and MariaDB
* Next\, create web apps that include both server\-side logic in PHP and client\-side code in JavaScript and add:
  * Authentication\.
  * Session management\.

