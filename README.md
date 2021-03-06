ACSPanel (ACS Control Server Panel)
===================================

Welcome to ACSPanel - The server administration tool written in Symfony2

This document contains information on how to download, install, and start
using ACSPanel.

1) Installing ACSPanel
----------------------

When it comes to installing the ACSPanel, you have the
following options.

### Use Debian Package(*recommended*)

Coming soon

### Download from GIT repository

To install ACSPanel from git repository, you have to clone the project with 
the next command and execute the following commands 

    cd /server_root_directory/

    git clone git@github.com:AltCtrlSupr/acspanel.git


2) Checking your System Configuration
-------------------------------------

Before starting using ACSPanel you should make sure that your local system is properly
configured.

Execute the `check.php` script from the command line:

    php app/check.php

3) Permissions
--------------

To avoid permissions issues after executing console commands you should do the next

    mkdir app/main/cache && mkdir app/main/logs (TODO: check this to be created with the initial files...)
    sudo setfacl -R -m u:www-data:rwX -m u:`whoami`:rwX app/main/cache app/main/logs
    sudo setfacl -dR -m u:www-data:rwx -m u:`whoami`:rwx app/main/cache app/main/logs

4) Setting up ACSPanel
--------------------

Now you set parameters.yml with your database create, you can take parameters.yml.sample as example. (Not necessary when it's installed via deb package).

    cp app/main/config/parameters.yml.sample app/main/config/parameters.yml

You should create your own config_dev.yml, as the parameters you can take config_dev.yml.sample as example.

    cp app/main/config/config_dev.yml.sample app/main/config/config_dev.yml


To install all the dependencies you have to execute composer.phar command.

    php composer.phar self-update (TODO: Be sure if it's the best...)
    php composer.phar install

Then you are ready to create the acspanel basic schema executing the next command:

    php app/console doctrine:schema:create

You can load some basic fixtures doing next, like basic groups and admin to start using the panel:

    php app/main/console doctrine:fixtures:load

You should install the assets as well:

    php app/console assets:install --symlink

(Opcional) Install additional ACSPanel bundles:

Coming soon.

Congratulations! You're now ready to use ACSPanel.

5) Setting up Apache
--------------------

comming soon.

6) Getting started with ACSPanel
-------------------------------

comming soon.

What's inside?
---------------

The Symfony Standard Edition is configured with the following defaults:

  * Twig is the only configured template engine;

  * Doctrine ORM/DBAL is configured;

  * Swiftmailer is configured;

  * Annotations for everything are enabled.

It comes pre-configured with the following bundles:

  * **FrameworkBundle** - The core Symfony framework bundle

  * [**SensioFrameworkExtraBundle**][6] - Adds several enhancements, including
    template and routing annotation capability

  * [**DoctrineBundle**][7] - Adds support for the Doctrine ORM

  * [**TwigBundle**][8] - Adds support for the Twig templating engine

  * [**SecurityBundle**][9] - Adds security by integrating Symfony's security
    component

  * [**SwiftmailerBundle**][10] - Adds support for Swiftmailer, a library for
    sending emails

  * [**MonologBundle**][11] - Adds support for Monolog, a logging library

  * [**AsseticBundle**][12] - Adds support for Assetic, an asset processing
    library

  * [**JMSSecurityExtraBundle**][13] - Allows security to be added via
    annotations

  * [**JMSDiExtraBundle**][14] - Adds more powerful dependency injection
    features

  * **WebProfilerBundle** (in dev/test env) - Adds profiling functionality and
    the web debug toolbar

  * **SensioDistributionBundle** (in dev/test env) - Adds functionality for
    configuring and working with Symfony distributions

  * [**SensioGeneratorBundle**][15] (in dev/test env) - Adds code generation
    capabilities

  * **AcmeDemoBundle** (in dev/test env) - A demo bundle with some example
    code

Enjoy!

[1]:  http://symfony.com/doc/2.1/book/installation.html
[2]:  http://getcomposer.org/
[3]:  http://symfony.com/download
[4]:  http://symfony.com/doc/2.1/quick_tour/the_big_picture.html
[5]:  http://symfony.com/doc/2.1/index.html
[6]:  http://symfony.com/doc/2.1/bundles/SensioFrameworkExtraBundle/index.html
[7]:  http://symfony.com/doc/2.1/book/doctrine.html
[8]:  http://symfony.com/doc/2.1/book/templating.html
[9]:  http://symfony.com/doc/2.1/book/security.html
[10]: http://symfony.com/doc/2.1/cookbook/email.html
[11]: http://symfony.com/doc/2.1/cookbook/logging/monolog.html
[12]: http://symfony.com/doc/2.1/cookbook/assetic/asset_management.html
[13]: http://jmsyst.com/bundles/JMSSecurityExtraBundle/master
[14]: http://jmsyst.com/bundles/JMSDiExtraBundle/master
[15]: http://symfony.com/doc/2.1/bundles/SensioGeneratorBundle/index.html
