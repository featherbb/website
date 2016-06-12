---
layout: docs
title: Plugins
permalink: /docs/plugins/
---

Plugins are a convenient way to extend FeatherBB's features easily without touching any code.

## Install a plugin

Head over to the plugins page in the administration panel: the plugins available will be listed.

Click on the Download link, then click on the cross in the Installed plugins menu to activate it: it is installed, no further action is required.

If need be, an archive can be used to import a plugin in the "Upload plugin" section.

Finally, it is possible to install a plugin manually by copying the files in the "plugins" folder.

## Uninstall a plugin

First, disable the plugin by clicking the green tick in the plugin page, click on the Uninstall link.

## Manage a plugin

Some plugins can be configured; to do so, a new page is created in the "Plugins menu" accessible from the admin panel.

## Create a plugin

As a developer, you should never edit the core files: this allows quick updates and make installation of plugins painless.

This means you have to understand and use the system of hooks; they are available throughout the core.

Usually, each function found in a Controller or Model file begins with a hook and ends with another one:

```php
Container::get('hooks')->fire('controller.forum.display');
```

Each hook has an unique name with the following naming scheme: filetype.filename.functionName.

Some can be used to alter a variable; each database query can be altered using this trick.

```php
$moderators = DB::for_table('forums')
                ->where('id', $fid);
$moderators = Container::get('hooks')->fireDB('model.forum.get_moderators', $moderators);
$moderators = $moderators->find_one_col('moderators');
```

This means that the whole query can be modified: adding a field to the SELECT clause, adding a LIMIT or an OFFSET, editing a JOIN... Everything is possible.

To do so, you have to bind the hook you want to call from your plugin using a closure. For example:

```php
Container::get('hooks')->bind('model.forum.get_info_forum_query', function ($cur_forum) {
    $cur_forum = $cur_forum->select('f.num_posts');
    return $cur_forum;
});
```

This example is extracted from the core in the Forum API model. It adds the "f.num_posts" field to the SELECT clause.

Of course, if you do not wish to use closure, you can make a call to a function within your class like:

```php
Container::get('hooks')->bind('admin.plugin.menu', [$this, 'getName']);
```

Please see the official extensions [BBCode Toolbar](https://github.com/featherbb/bbcode-toolbar) and [Private Messages](https://github.com/featherbb/private-messages) to see how to create a plugin properly.

Contact us on the community forum or the chat to add it to the official repository.

If you need to add a specific hook into the core, please ask us - or create a pull request, you know the drill :).