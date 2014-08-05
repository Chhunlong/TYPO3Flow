==============================
TYPO3Flow CodeSniffer standard
==============================


Description
===========

This standard consist of a subset of sniffs from the TYPO3SniffPool and implements the Coding Guidelines for TYPO3Flow. 
 
It contains just a ruleset.xml file in which we refer to the sniffs from PHP_CodeSniffer and from TYPO3SniffPool.


How to get
==========
 
In case you didn't have install the TYPO3SniffPool or the PHP_CodeSniffer yet - no problem. This packages are marked as dependencies of this standard and will install automatically.
 
There are several ways to get the standard, which I am going to describe now. There is no right or wrong. Which way you choose depends on your preferences and at least on your requirements.
 
Composer
--------
 
We also support `Composer <http://getcomposer.org/>`_, a dependency manager for PHP. 
 
Create a composer.json in the root folder of your project and declare this standard as a dependency:
 
::
 
 
        {
                "minimum-stability": "alpha",
                "require": {
                        "typo3-ci/typo3flow": "dev-master"
                }
        }
 
 
Since the package is managed with `Packagist <https://packagist.org>`_ this is all what you need.
 
All these commands will also install the PHP_CodeSniffer and the TYPO3SniffPool into the *vendor/* folder of your project. For more informations about Composer have a look at their `documentation <http://getcomposer.org/doc/00-intro.md>`_.

Git
---
 
The third way is to clone the repository from github. **In this case you have to take care about the dependencies by yourself**.
 
::
        
        $ git clone https://github.com/typo3-ci/TYPO3Flow.git
        $ git clone https://github.com/typo3-ci/TYPO3SniffPool.git
 
There is a 3b way to get the standards in at once. We have an umbrella repository which contains the three standards as subprojects. The subprojects points every time to the latest stable version, never to the master branch but to a tag.
 
::
 
        $ git clone --recursive https://github.com/typo3-ci/TYPO3_CodingStandard.git


How to use
==========

As various the installations methods are, as various the usage is.

Composer
--------
 
Change into your project folder and call the PHP_CodeSniffer from there:
 
::
       
        $ cd myproject
        $ php vendor/squizlabs/php_codesniffer/scripts/phpcs --standard=TYPO3Flow /path/to/folder
 
Its also possible to call this standard with a global installed PHP_CodeSniffer (f.e. via PEAR)
 
::
        
        $ cd myproject
        $ phpcs --standard=vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/TYPO3Flow/ruleset.xml /path/to/folder
 
Git
---
 
After you cloned the standard and it dependencies the usage is nearly the same as above. There are two main methods. 
 
1. Copy the standard into the *Standards/* folder of the PHP_CodeSniffer and call it with *--standard=TYPO3Flow*
 
2. Put the standard at any place you want and call point to it absolutely *--standard=/path/to/TYPO3Flow/ruleset.xml*


Contribution
============
Please have a look at `dedicated  wiki page <https://github.com/typo3-ci/TYPO3SniffPool/wiki#contribute>`_ for information about how you can contribute.

Further informations
====================

* http://forge.typo3.org/projects/team-php_codesniffer/wiki/Using_the_TYPO3_Coding_Standard
* https://github.com/squizlabs/PHP_CodeSniffer
* https://github.com/typo3-ci/TYPO3_CodingStandard

