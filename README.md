# TYPO3Flow CodeSniffer standard

## Description

This standard contains of a subset of sniffs from the [TYPO3SniffPool](https://github.com/typo3-ci/TYPO3SniffPool) and implements the Coding Guidelines for [TYPO3 Flow](http://flow.typo3.org/). 
 
It contains just a ruleset.xml file in which we refer to the sniffs from [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) and from [TYPO3SniffPool](https://github.com/typo3-ci/TYPO3SniffPool).

## How to get
 
In case you didn't have installed the [TYPO3SniffPool](https://github.com/typo3-ci/TYPO3SniffPool) or the [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) yet - no problem. This packages are marked as dependencies of this standard and will install automatically.
 
There are several ways to get the standard, which I am going to describe now. There is no right or wrong. Which way you choose depends on your preferences and at least on your requirements.
 
### Composer
 
We support [Composer](https://getcomposer.org/), a dependency manager for PHP. 
 
Create a composer.json in the root folder of your project or extend the existing one and declare this package as a dependency:
 
``` 
{
	"minimum-stability": "alpha",
	"require": {
		"typo3-ci/typo3flow": "dev-master"
	}
}
``` 
 
Since the package is managed with [Packagist](https://packagist.org/) this is all what you need.
 
This will install the [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) and the [TYPO3SniffPool](https://github.com/typo3-ci/TYPO3SniffPool) into the *vendor/* folder of your project. For more informations about Composer have a look at their [documentation](http://getcomposer.org/doc/00-intro.md).

For a system-wide installation, you can use:
```
composer global require "typo3-ci/typo3flow=dev-master"
```
Make sure to have ``~/.composer/vendor/bin/`` in your path.

### Git
 
The second way is to clone [the repository](https://github.com/typo3-ci/TYPO3Flow) from github. **In this case you have to take care about the dependencies by yourself**.
 
```
$ git clone https://github.com/typo3-ci/TYPO3Flow.git
$ git clone https://github.com/typo3-ci/TYPO3SniffPool.git
```

## How to use

As various the installations methods are, as various the usage is.

### Composer
 
Change into your project folder and call the PHP_CodeSniffer from there:
 
```
$ cd myproject
$ php vendor/squizlabs/php_codesniffer/scripts/phpcs --standard=TYPO3Flow /path/to/folder
```

Its also possible to call this standard with a global installed PHP_CodeSniffer (f.e. via PEAR)
 
```
$ cd myproject
$ phpcs --standard=vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/TYPO3Flow/ruleset.xml /path/to/folder
```
 
### Git
 
After you cloned the standard and it dependencies the usage is nearly the same as above. There are two main methods. 
 
1. Copy the standard into the *Standards/* folder of the PHP_CodeSniffer and call it with *--standard=TYPO3Flow*
 
2. Put the standard at any place you want and call point to it absolutely *--standard=/path/to/TYPO3Flow/ruleset.xml*

## Contribution

Please have a look at the [dedicated wiki page](https://github.com/typo3-ci/TYPO3SniffPool/wiki#contribute) for information about how **you can contribute** to this project.

## Further informations

* [TYPO3Flow CodeSniffer standard](https://github.com/typo3-ci/TYPO3Flow)
* [TYPO3CMS CodeSniffer standard](https://github.com/typo3-ci/TYPO3CMS)
* [TYPO3 Sniff Pool](https://github.com/typo3-ci/TYPO3SniffPool)
* [Documentation / Wiki of TYPO3 Sniff Pool](https://github.com/typo3-ci/TYPO3SniffPool/wiki)
* [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
