---
layout: docs
title: Troubleshooting
permalink: /docs/troubleshooting/
---

In case of trouble, please follow the steps below.

## Requirements

Make sure that your hosting environment fulfils the minimum requirements:

* **Apache** (with mod_rewrite), **Nginx**, or **Lighttpd**
* **MySQL 5.5+**, **MariaDB 10+**, **PostgreSQL 7+** or **SQLite 2+**
* **PHP 5.5+**

## History

You can also check if the bug you are experiencing has already been reported to our [Github issue tracker](https://github.com/featherbb/featherbb/issues)  or on the [community forum](http://forums.featherbb.org).

If it has not, please proceed with the following steps.

## Debug mod

The debug mod can be enabled though the index.php root file:

```php
$feather_settings = array(
    // 'config_file' => 'featherbb/config.php',
    // 'cache_dir' => 'cache/',
    'debug' => 'all'  // 3 levels : false, info (only execution time and number of queries), and all (display info + queries)
);
```

Of course, the 'debug' parameter should be set to 'all' as shown above.

Then, you can force the PHP errors to be shown by adding the following line at the top of the index.php root file:

```php
ini_set('display_errors', 'On');
```

## Report the error

If you did not find how to solve your issue, please collect as much information as you can as described above and report it to our [Github issue tracker](https://github.com/featherbb/featherbb/issues)  or on the [community forum](http://forums.featherbb.org).

Thank you!
