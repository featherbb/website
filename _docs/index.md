---
layout: docs
title: Introduction
permalink: /docs/
---

FeatherBB is an open source forum application released under the GNU General Public Licence.

It is a fork of FluxBB 1.5 based on Slim Framework and designed to be simple and very lightweight.

## Features

* Clear cut MVC architecture
* Object-oriented
* Extensible in a single click
* Easy installation and usage
* Open-source
* Responsive design
* SEO friendly

## Requirements

* A web server: **Apache** (with mod_rewrite), **Nginx**, or **Lighttpd**
* A database server: **MySQL 5.5+**, **MariaDB 10+**, **PostgreSQL 7+** or **SQLite 2+**
* **PHP 5.5+**

## Recommendations

* Make use of a PHP accelerator such as OPCache
* Make sure PHP has the zlib module installed to allow FeatherBB to gzip output

## Installation

Two methods are available. First, you can use composer:

```bash
composer composer create-project featherbb/featherbb --stability=dev
```

Or you can simply [download the archive](https://github.com/featherbb/featherbb/releases) from GitHub, unzip it and follow the instructions.

To enable URL rewriting, make sure that mod_rewrite is enabled for Apache, or add the following in your Nginx configuration:

```bash
location / {
        try_files $uri $uri/ /index.php$is_args$args;
}
```

Do not forget to make the .env unreadable:
```bash
location ~ /\.env {
        deny  all;
}
```

For Lighttpd, add the following line:

```bash
url.rewrite-if-not-file = ("(.*)" => "/index.php/$0")
```

If you use PHP >= 7, make sure the php7.0-xml is installed by running

```bash
sudo apt-get install php7.0-xml
```

If you have any trouble setting up your server, you can refer to [Slim Framework's documentation](http://www.slimframework.com/docs/start/web-servers.html).

## Core Team

* [[adaur](http://github.com/adaur)] Project leader
* [[capkokoon](http://github.com/capkokoon)] contributor
* [[beaver](http://github.com/beaver-dev)] contributor

## Live Support

You can ask our developers directly in case of trouble: use our [Gitter chat](https://gitter.im/featherbb/featherbb).

## Contributing

If you want to contribute, please do not hesitate! Head over to our [Github repository](http://github.com/featherbb/featherbb) and start submitting issues and pull requests.
