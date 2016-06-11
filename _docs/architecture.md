---
layout: docs
title: Architecture
permalink: /docs/architecture/
---

## Middlewares

FeatherBB uses middlewares extensively, located in the featherbb/Middleware folder.

The **CSRF** is the first to be invoked, used to ensure that a CSRF attack cannot succeed.

Then, the **Auth** middleware is invoked to log the current user. Meanwhile, it checks the bans, updates the online information and displays a maintenance message if need be.

Finally, the **Core** middleware is invoked to ensure that all the variables used thoughout the application are setup.

## Router

FeatherBB uses a router to redirect each URL to its controller. It is located in featherbb/routes.php.

Note that some routes are protected by a middleware, such as the admin panel.

## Controllers

Controllers are the "glue" between models and views. Each route redirects to a function in a controller.

They are located in the featherbb/Controller folder.

Each controller function has the following signature:

```php
public function function_name($req, $res, $args)
```

$req stands for request (headers, etc)
$res for response (body content, etc)
$args for arguments (POST and GET)

At some point, each controller function needing to access data stored in database will call a model function.

## Models

Models functions are used to access data stored in database.

They usually return the data needed by the controller calling it.

## Views

Once the controller has all the data it requires, it calls for a view.

The View library is based on Slim Framework 2, located in featherbb/Core/View.php.

Sample code:

```php
View::setPageInfo(array(
                'title' => array(Utils::escape(ForumSettings::get('o_board_title')), __('Search')),
                'active_page' => 'search',
                'is_indexed' => true,
                'forums' => $this->model->get_list_forums(),
            ))->addTemplate('search/form.php')->display();
```

The templates are located in the featherbb/View folder.

New themes must be stored in /styles/themes/new_theme_name. They must contain a valid style.css file.

If need be, they can contain one or multiple template based on the default templates detailed above. Each new template should be stored in a view folder in the theme folder, like: /styles/themes/new_theme_name/view. If one template is available in the current theme folder, it will be loaded instead of the default template. It can be useful to create a new template for theme authors in order to rearrange some elements' order such as the header navlinks.

## Database

Please see the [database page](https://featherbb.org/docs/database).