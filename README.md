# DUGMuc Demo

Demo installation for DUG Muc presentations.

## Install

You need a local webserver and [composer being installed](https://getcomposer.org/doc/00-intro.md)
on your machine.

1. Setup your local webserver to point to the _web_ directory. We use the local
   domain [dugmucdemo.dev](http://dugmucdemo.dev).
2. Run `composer install`
3. Create `web/sites/default/settings.local.php` and add your database credentials, like:
```php
<?php

$databases['default']['default'] = array (
  'database' => 'dugmucdemo',
  'username' => 'dbuser',
  'password' => 'dbpassword',
  'prefix' => '',
  'host' => 'localhost',
  'port' => '3306',
  'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
  'driver' => 'mysql',
);

```
4. Run `composer site-install`. It then installs Drupal from the configuration stored
   in [environments/_default/config/sync](environments/_default/config/sync).
5. Running `./vendor/bin/drush uli -l dugmucdemo.dev` then will give you a one-time
   login link for the admin.

## Update

Whenever you pull changes from this repo, you will have to make sure the
site's configuration and packages are up to date. Therefore run the following
steps.

1. Run `composer install`.
2. Run `composer site-update` to perform configuration updates.

## References

This project used [drupal-composer/drupal-project](https://github.com/drupal-composer/drupal-project) as a starting point.
Check that project out, in case you have questions on the composer workflow.
