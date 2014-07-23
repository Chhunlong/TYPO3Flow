TYPO3Flow Coding Standards
==========================

Table of Contents
-----------------

-  `Array Bracket Spacing <#Array-Bracket-Spacing>`__
-  `Self Member Reference <#Self-Member-Reference>`__
-  `Duplicate Class Names <#Duplicate-Class-Names>`__
-  `Unconditional If Statements <#Unconditional-If-Statements>`__
-  `Unnecessary Final Modifiers <#Unnecessary-Final-Modifiers>`__
-  `For Loops With Function Calls in the
   Test <#For-Loops-With-Function-Calls-in-the-Test>`__
-  `Empty Statements <#Empty-Statements>`__
-  `Inline Comments <#Inline-Comments>`__
-  `Inline Control Structures <#Inline-Control-Structures>`__
-  `One Class Per File <#One-Class-Per-File>`__
-  `One Interface Per File <#One-Interface-Per-File>`__
-  `Byte Order Marks <#Byte-Order-Marks>`__
-  `Line Endings <#Line-Endings>`__
-  `Opening Brace in Function
   Declarations <#Opening-Brace-in-Function-Declarations>`__
-  `Function Argument Spacing <#Function-Argument-Spacing>`__
-  `Constructor name <#Constructor-name>`__
-  `Constant Names <#Constant-Names>`__
-  `Opening Tag at Start of File <#Opening-Tag-at-Start-of-File>`__
-  `PHP Code Tags <#PHP-Code-Tags>`__
-  `Deprecated Functions <#Deprecated-Functions>`__
-  `PHP Constants <#PHP-Constants>`__
-  `ConcatenationSpacing <#ConcatenationSpacing>`__
-  `Semicolon Spacing <#Semicolon-Spacing>`__

Array Bracket Spacing
---------------------

When referencing arrays you should not put whitespace around the opening
bracket or before the closing bracket.

+-----------------------------------------+----------------------------------------+
| Valid: No spaces around the brackets.   | Invalid: Spaces around the brackets.   |
+-----------------------------------------+----------------------------------------+
| $foo['bar'];                            | $foo [ 'bar' ];                        |
+-----------------------------------------+----------------------------------------+

Self Member Reference
---------------------

The self keyword should be used instead of the current class name,
should be lowercase, and should not have spaces before or after it.

+-------------------------------+---------------------------------+
| Valid: Lowercase self used.   | Invalid: Uppercase self used.   |
+-------------------------------+---------------------------------+
| self::foo();                  | SELF::foo();                    |
+-------------------------------+---------------------------------+

+--------------------------------+------------------------------------+
| Valid: Correct spacing used.   | Invalid: Incorrect spacing used.   |
+--------------------------------+------------------------------------+
| self::foo();                   | self :: foo();                     |
+--------------------------------+------------------------------------+

+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| Valid: Self used as reference.                                                                                        | Invalid: Local class name used as reference.                                                                         |
+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
| class Foo{    public static function bar()    {    }    public static function baz()    {        self::bar();    }}   | class Foo{    public static function bar()    {    }    public static function baz()    {        Foo::bar();    }}   |
+-----------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

Duplicate Class Names
---------------------

Class and Interface names should be unique in a project. They should
never be duplicated.

+-------------------------------+------------------------------------------------------------------+
| Valid: A unique class name.   | Invalid: A class duplicated (including across multiple files).   |
+-------------------------------+------------------------------------------------------------------+
| class Foo{}                   | class Foo{}class Foo{}                                           |
+-------------------------------+------------------------------------------------------------------+

Unconditional If Statements
---------------------------

If statements that are always evaluated should not be used.

+------------------------------------------------------------+------------------------------------------------------+
| Valid: An if statement that only executes conditionally.   | Invalid: An if statement that is always performed.   |
+------------------------------------------------------------+------------------------------------------------------+
| if ($test) {    $var = 1;}                                 | if (true) {    $var = 1;}                            |
+------------------------------------------------------------+------------------------------------------------------+

+------------------------------------------------------------+-----------------------------------------------------+
| Valid: An if statement that only executes conditionally.   | Invalid: An if statement that is never performed.   |
+------------------------------------------------------------+-----------------------------------------------------+
| if ($test) {    $var = 1;}                                 | if (false) {    $var = 1;}                          |
+------------------------------------------------------------+-----------------------------------------------------+

Unnecessary Final Modifiers
---------------------------

Methods should not be declared final inside of classes that are declared
final.

+---------------------------------------------------------+--------------------------------------------------------------+
| Valid: A method in a final class is not marked final.   | Invalid: A method in a final class is also marked final.     |
+---------------------------------------------------------+--------------------------------------------------------------+
| final class Foo{    public function bar()    {    }}    | final class Foo{    public final function bar()    {    }}   |
+---------------------------------------------------------+--------------------------------------------------------------+

For Loops With Function Calls in the Test
-----------------------------------------

For loops should not call functions inside the test for the loop when
they can be computed beforehand.

+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
| Valid: A for loop that determines its end condition before the loop starts.   | Invalid: A for loop that unnecessarily computes the same value on every iteration.   |
+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+
| $end = count($foo);for ($i = 0; $i < $end; $i++) {    echo $foo[$i]."\\n";}   | for ($i = 0; $i < count($foo); $i++) {    echo $foo[$i]."\\n";}                      |
+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------+

Empty Statements
----------------

Control Structures must have at least one statment inside of the body.

+-------------------------------------------------------------+-----------------------------------------------------+
| Valid: There is a statement inside the control structure.   | Invalid: The control structure has no statements.   |
+-------------------------------------------------------------+-----------------------------------------------------+
| if ($test) {    $var = 1;}                                  | if ($test) {    // do nothing}                      |
+-------------------------------------------------------------+-----------------------------------------------------+

Inline Comments
---------------

Perl-style # comments are not allowed.

+------------------------------+-------------------------------+
| Valid: A // style comment.   | Invalid: A # style comment.   |
+------------------------------+-------------------------------+
| // A comment.                | # A comment.                  |
+------------------------------+-------------------------------+

Inline Control Structures
-------------------------

Control Structures should use braces.

+--------------------------------------------------------+-----------------------------------------------------------+
| Valid: Braces are used around the control structure.   | Invalid: No braces are used for the control structure..   |
+--------------------------------------------------------+-----------------------------------------------------------+
| if ($test) {    $var = 1;}                             | if ($test)    $var = 1;                                   |
+--------------------------------------------------------+-----------------------------------------------------------+

One Class Per File
------------------

There should only be one class defined in a file.

+--------------------------------------+--------------------------------------------------+
| Valid: Only one class in the file.   | Invalid: Multiple classes defined in one file.   |
+--------------------------------------+--------------------------------------------------+
| <?phpclass Foo{}                     | <?phpclass Foo{}class Bar{}                      |
+--------------------------------------+--------------------------------------------------+

One Interface Per File
----------------------

There should only be one interface defined in a file.

+------------------------------------------+-----------------------------------------------------+
| Valid: Only one interface in the file.   | Invalid: Multiple interfaces defined in one file.   |
+------------------------------------------+-----------------------------------------------------+
| <?phpinterface Foo{}                     | <?phpinterface Foo{}interface Bar{}                 |
+------------------------------------------+-----------------------------------------------------+

Byte Order Marks
----------------

Byte Order Marks that may corrupt your application should not be used.
These include 0xefbbbf (UTF-8), 0xfeff (UTF-16 BE) and 0xfffe (UTF-16
LE).

Line Endings
------------

Unix-style endlines are preferred ("\\n" instead of "\\r\\n").

Opening Brace in Function Declarations
--------------------------------------

Function declarations follow the "Kernighan/Ritchie style". The function
brace is on the same line as the function declaration. One space is
required between the closing parenthesis and the brace.

+-----------------------------------------------------+----------------------------------------------------+
| Valid: brace on same line                           | Invalid: brace on next line                        |
+-----------------------------------------------------+----------------------------------------------------+
| function fooFunction($arg1, $arg2 = '') {    ...}   | function fooFunction($arg1, $arg2 = ''){    ...}   |
+-----------------------------------------------------+----------------------------------------------------+

Function Argument Spacing
-------------------------

Function arguments should have one space after a comma, and single
spaces surrounding the equals sign for default values.

+---------------------------------------+-------------------------------------+
| Valid: Single spaces after a comma.   | Invalid: No spaces after a comma.   |
+---------------------------------------+-------------------------------------+
| function foo($bar, $baz){}            | function foo($bar,$baz){}           |
+---------------------------------------+-------------------------------------+

+-----------------------------------------------------------------------+---------------------------------------------------------------------+
| Valid: Single spaces around an equals sign in function declaration.   | Invalid: No spaces around an equals sign in function declaration.   |
+-----------------------------------------------------------------------+---------------------------------------------------------------------+
| function foo($bar, $baz = true){}                                     | function foo($bar, $baz=true){}                                     |
+-----------------------------------------------------------------------+---------------------------------------------------------------------+

Constructor name
----------------

Constructors should be named \_\_construct, not after the class.

+-----------------------------------------------------+----------------------------------------------------------+
| Valid: The constructor is named \_\_construct.      | Invalid: The old style class name constructor is used.   |
+-----------------------------------------------------+----------------------------------------------------------+
| class Foo{    function \_\_construct()    {    }}   | class Foo{    function Foo()    {    }}                  |
+-----------------------------------------------------+----------------------------------------------------------+

Constant Names
--------------

Constants should always be all-uppercase, with underscores to separate
words.

+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| Valid: all uppercase                                                              | Invalid: mixed case                                                               |
+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+
| define('FOO\_CONSTANT', 'foo');class FooClass{    const FOO\_CONSTANT = 'foo';}   | define('Foo\_Constant', 'foo');class FooClass{    const foo\_constant = 'foo';}   |
+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------+

Opening Tag at Start of File
----------------------------

The opening php tag should be the first item in the file.

+---------------------------------------------------+------------------------------------------------------------+
| Valid: A file starting with an opening php tag.   | Invalid: A file with content before the opening php tag.   |
+---------------------------------------------------+------------------------------------------------------------+
| <?phpecho 'Foo';                                  | Beginning content<?phpecho 'Foo';                          |
+---------------------------------------------------+------------------------------------------------------------+

PHP Code Tags
-------------

Always use <?php ?> to delimit PHP code, not the <? ?> shorthand. This
is the most portable way to include PHP code on differing operating
systems and setups.

Deprecated Functions
--------------------

Deprecated functions should not be used.

+---------------------------------------------+-------------------------------------------+
| Valid: A non-deprecated function is used.   | Invalid: A deprecated function is used.   |
+---------------------------------------------+-------------------------------------------+
| $foo = explode('a', $bar);                  | $foo = split('a', $bar);                  |
+---------------------------------------------+-------------------------------------------+

PHP Constants
-------------

The *true*, *false* and *null* constants must always be uppercase.

+-------------------------------------------------------------+-------------------------------------------------------------+
| Valid: uppercase constants                                  | Invalid: lowercase constants                                |
+-------------------------------------------------------------+-------------------------------------------------------------+
| if ($var === FALSE \|\| $var === NULL) {    $var = TRUE;}   | if ($var === false \|\| $var === null) {    $var = true;}   |
+-------------------------------------------------------------+-------------------------------------------------------------+

ConcatenationSpacing
--------------------

This standard is about the spacing of concat strings

*String concatenation* operators must be surrounded by spaces

+------------------------------------------------------------+------------------------------------------------------------------------------------------------+
| Valid: String concatenation operator surrounded by space   | Invalid: String concatenation operator is not surrounded by space                              |
+------------------------------------------------------------+------------------------------------------------------------------------------------------------+
| $content  = 'Hello ' . 'world!';                           | $content  = 'Hello '. 'world!';$content  = 'Hello ' .'world!';$content  = 'Hello '.'world!';   |
+------------------------------------------------------------+------------------------------------------------------------------------------------------------+

*String concatenation* operators should be surrounded by only one space

+------------------------------------------------------------------------------+------------------------------------------------------------------------------+
| Valid: String concatenation operator surrounded by one space on every side   | Invalid: String concatenation operator surrounded by multiple spaces         |
+------------------------------------------------------------------------------+------------------------------------------------------------------------------+
| $content  = 'Hello ' . 'world!';                                             | $content  = 'Hello '  . 'world!';$content  = 'Hello '  .         'world!';   |
+------------------------------------------------------------------------------+------------------------------------------------------------------------------+

Semicolon Spacing
-----------------

Semicolons should not have spaces before them.

+-----------------------------------------+----------------------------------------+
| Valid: No space before the semicolon.   | Invalid: Space before the semicolon.   |
+-----------------------------------------+----------------------------------------+
| echo "hi";                              | echo "hi" ;                            |
+-----------------------------------------+----------------------------------------+

Documentation generated on Wed, 23 Jul 2014 13:08:16 +0200 by
`PHP\_CodeSniffer
2.0.0a1 <http://pear.php.net/package/PHP_CodeSniffer>`__
