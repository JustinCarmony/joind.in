Unit Testing Instructions
=========================

1. Getting PHPUnit
------------------
If you haven't done this in the past, get PHPUnit as it is the test tool used
for QA on joind.in.

The easiest way to install PHPUnit is by using the PEAR installer:

```shell
$ pear channel-discover pear.phpunit.de
$ pear channel-discover components.ez.no
$ pear channel-discover pear.symfony-project.com
$ pear install -a phpunit/PHPUnit
```

You can also download and build PHPUnit yourself, but for detailed description
on how to do this, go and check out http://www.phpunit.de.

2. Setting up a test database
-----------------------------
In the file `src/system/application/config/database.php` you need to provide
a secondary database configuration for testing purposes.

You can copy the following lines and modify them for your own settings:

```php
$db['test']['hostname'] = "localhost";
$db['test']['username'] = "joindin_test";
$db['test']['password'] = "j01nd1nV3rRy$3cR3t";
$db['test']['database'] = "joindin_test";
$db['test']['dbdriver'] = "mysql";
$db['test']['dbprefix'] = "";
$db['test']['pconnect'] = TRUE;
$db['test']['db_debug'] = TRUE;
$db['test']['cache_on'] = FALSE;
$db['test']['cachedir'] = "";
$db['test']['char_set'] = "utf8";
$db['test']['dbcollat'] = "utf8_general_ci";
```

Make sure your mysql server has a joindin_test database and user joindin_test
has the correct privileges for creating, dropping, reading and writing to this
database.

3. Running the tests
--------------------
Go to the directory `/src/tests` and issue the following command:

```shell
$ phpunit
```

This should run joindin unit tests cases and if all goes well, no errors or
failures will be shown.

To enable the development mode for better debugging, set a local environment
variable - for example for linux:

```shell
export JOINDIN_DEBUG=on
```