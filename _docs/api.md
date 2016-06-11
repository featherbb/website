---
layout: docs
title: API
permalink: /docs/api/
---

FeatherBB provides a simple API, allowing you to build easily third-party applications interacting with any FeatherBB forum.

## Authentication

The API uses token-based authentication. However, for some actions, you do not need to be authenticated.

First, grab your token in your profile in the Personal section. It will look like:

```
867a4077f6a889685dc77789a1303eb4d6958547
```

Then you have to provide the user ID or the username along the token for every request you make.

```
GET /api/something?id=2&token=867a4077f6a889685dc77789a1303eb4d6958547
```

or

```
GET /api/something?username=adaur&token=867a4077f6a889685dc77789a1303eb4d6958547
```

The following commands are given without the authentication part, but you have to include it.

## Forum

Get some information about a forum.

```
GET /api/forum/:id
{
    "forum_name": "Test forum",
    "redirect_url": null,
    "moderators": false,
    "num_topics": "1",
    "sort_by": "0",
    "post_topics": null,
    "is_subscribed": null,
    "num_posts": "1",
    "forum_url": "test-forum"
}
```

Post a new topic; returns the error message or the topic message API.

```
POST /api/forum/:id
{
    "req_subject": "Subject",
    "req_message": "Message"
}
```

## Topic

Display a topic.

```
GET /api/topic/:id
{
    "subject": "Test topic",
    "closed": "0",
    "num_replies": "0",
    "sticky": "0",
    "first_post_id": "1",
    "forum_id": "1",
    "forum_name": "Test forum",
    "moderators": false,
    "post_replies": null,
    "is_subscribed": null
}
```

Post a reply; returns the error message or the message API.

```
POST /api/topic/:id
{
    "req_message": "Message"
}
```

You can quote a message with the following endpoint:

```
POST /api/topic/:id/quote/:qid
{
    "req_message": "Message"
}
```

## Post

Display a post.

```
GET /api/post/:id
{
    "fid": "1",
    "forum_name": "Test forum",
    "moderators": false,
    "redirect_url": null,
    "post_topics": null,
    "tid": "1",
    "subject": "Test topic",
    "posted": "1465414787",
    "first_post_id": "1",
    "sticky": "0",
    "closed": "0",
    "poster": "test",
    "poster_id": "2",
    "message": "You have successfully installed FeatherBB, congratulations! Now log in and head over to the administration control panel to configure your forum.",
    "hide_smilies": "0"
}
```

Delete a post.

```
DELETE /api/post/:id
```

Edit a post.

```
PUT /api/post/:id
{
    "req_subject": "Subject",
    "req_message": "Message"
}
```

Of course, the req_subject parameter should be submitted only if the user has the rights to edit it.

## User

Display an user.

```
GET /api/user/:id
{
    "id": "2",
    "group_id": "1",
    "username": "test",
    "title": null,
    "realname": null,
    "url": null,
    "location": null,
    "signature": null,
    "num_posts": "9",
    "last_post": "1465405242",
    "registered": "1465404187",
    "g_id": "1",
    "g_user_title": "Administrator",
    "prefs": {
        "disp.topics": "3",
        "disp.posts": "3",
        "post.min_interval": "0",
        "search.min_interval": "0",
        "email.min_interval": "0",
        "report.min_interval": "0",
        "promote.min_posts": "0",
        "promote.next_group": "0",
        "timezone": "0",
        "dst": "0",
        "time_format": "H:i:s",
        "date_format": "Y-m-d",
        "language": "English",
        "style": "FeatherBB",
        "show.smilies.sig": "1",
        "show.smilies": "1",
        "show.img": "1",
        "show.img.sig": "0",
        "show.avatars": "1",
        "show.sig": "1",
        "email.setting": "1",
        "notify_with_post": "0",
        "auto_notify": "0"
    }
}
```
