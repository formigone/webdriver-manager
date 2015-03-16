#WebDriver Manager

[![Build Status](https://travis-ci.org/peridot-php/webdriver-manager.png)](https://travis-ci.org/peridot-php/webdriver-manager)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/peridot-php/webdriver-manager/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/peridot-php/webdriver-manager/?branch=master)

The perfect companion for projects with functional tests. Heavily inspired by the webdriver manager that ships with [protractor](https://github.com/angular/protractor). WebDriver Manager allows you to keep Selenium Server binaries up to date as well as a packaged solution for easily starting Selenium Server up.

In addition to an easy to use command line application, WebDriver Manager provides a library for managing Selenium binaries in your own apps and tools.

##Usage

![WebDriver Manager Usage](https://raw.github.com/peridot-php/webdriver-manager/master/img/usage.png "WebDriver Manager Usage")

###clean

Remove all installed binaries.

![WebDriver clean command](https://raw.github.com/peridot-php/webdriver-manager/master/img/clean.png "WebDriver clean command")

###status

List all available binaries and the status. Status shows if the binary is installed, out of date, or missing.

 ![WebDriver status command](https://raw.github.com/peridot-php/webdriver-manager/master/img/status.png "WebDriver status command")

###update

The update command downloads current binaries and deletes old ones.

![WebDriver update command](https://raw.github.com/peridot-php/webdriver-manager/master/img/update.png "WebDriver update command")

###start

Starts Selnium Server with all drivers managed by WebDriver Manager. The start command will run an update at start to make sure drivers are available and up to date.

![WebDriver start command](https://raw.github.com/peridot-php/webdriver-manager/master/img/start.png "WebDriver start command")

##Library Usage

WebDriver manager exposes a really simple interface that makes it easy to leverage in your own applications and tools:

```php
use Peridot\WebDriverManager\Manager;

$manager = new Manager();

$manager->update(); //update all binaries
$manager->update('selenium'); //only update selenium

$manager->clean(); //remove installed binaries

$manager->start(); //start selenium in the foreground on port 4444
$manager->start(false, 9999); //start selenium in the foreground on port 9999
$manager->start(true); //start selenium in the background on port 4444
$manager->start(true, 9999); //start in the background on port 9999 

$path = $manager->getInstallPath(); //where binaries are installed
$manager->setInstallPath(__DIR__); //set the path to install binaries

$manager->addBinary(new MyCustomDriver()); //add a binary
$binaries = $manager->getBinaries(); //get a collection of managed binaries
```

For more information, see the [API docs](http://peridot-php.github.io/webdriver-manager/docs/);