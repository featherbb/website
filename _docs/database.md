---
layout: docs
title: Database
permalink: /docs/database/
---

FeatherBB uses a custom ORM to manage its database. It is based on [Idiorm](http://j4mie.github.io/idiormandparis/) and is a lightweight object-relational mapper and fluent query builder.

Built on top of PDO, it is safe to use with its prepared statements throughout to protect against SQL injection attacks.

It supports multiple databases systems such as MySQL, SQLite or PostgreSQL.

The ORM code is located in featherbb/Core/Database.php.

## Query example

Select a subscription:

```php
$is_subscribed = DB::for_table('topic_subscriptions')
                        ->where('user_id', User::get()->id)
                        ->where('topic_id', $topic_id);
                        ->find_one();
```

## Edit queries

All SQL queries can be edited using hooks, since a hook is fired before each query is actually executed.

```php
$query = Container::get('hooks')->fireDB('model.index.query_print_categories_forums', $query);
```

More details can be found on the [plugins](https://featherbb.org/docs/plugins) page.

## Additional information

A documentation more complete is available [here](https://github.com/featherbb/db-layer/tree/master/docs).