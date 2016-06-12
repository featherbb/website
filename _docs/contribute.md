---
layout: docs
title: Contribute
permalink: /docs/contribute/
---

Thank you for your interest in FeatherBB. If you want to help with the development of FeatherBB, there are several ways to do that.

First of all, please note that having an account on [Github](https://github.com/) will greatly help.

## Report Bugs

Unfortunately, if you find a bug, the first thing to do is to make sure that it is reproducible.

If it is, please search if it has already been reported to our [Github issue tracker](https://github.com/featherbb/featherbb/issues)  or on the [community forum](http://forums.featherbb.org).

If it has never been seen before, you can open a new issue on Github or create a new post on our forum. Please include a detailed report on how to reproduce the issue, when and why it happens as well as screenshots if need be.

If you know how to fix it, you are welcome to create a pull request.

## Contribute to code

The easiest way to contribute to the code is to create a new pull request for each new modification you would like to do.

Please open your pull request against the development branch, not the master one and squash your commits as much as possible.

## Security Report

If you have found a security vulnerability, please do not make it public or do not mention it on the Github issue tracker or on the community forum.

Please contact FeatherBB's developers directly at admin[@]featherbb[.]org.

## Coding Style

We decided to follow the PSR-2 coding style. A complete guide [can be found here](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md).

All pull requests must follow this convention.

Sample code:

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // method body
    }
}
```

## Plugins

A great way to contribute to FeatherBB is to create new plugins. See the [plugins page](https://featherbb.org/docs/plugins) for more information.

