---
title: Streams
---

{% include toc.md %}

## Get the main stream

Contains posts from users the currently authenticated user is sharing with as well as posts tagged with tags which the currently authenticated user is following.

### Request

~~~
GET /api/v1/streams/main
~~~

### Response

~~~json
{}
~~~

## Get aspect stream

Contains all posts in some or all aspects. If `aspect_ids` is empty, all aspect will get considered.

### Request

~~~
GET /api/v1/streams/aspects
~~~

### Optional parameters

| Parameter  | Description                      |
| ---------- | -------------------------------- |
| aspect_ids | List of one or more `aspect_id`s |

### Response

~~~json
{}
~~~

## Get activity stream

Contains all posts on which the authenticated user interacted on, ordered by their last activity.

### Request

~~~
GET /api/v1/streams/activity
~~~

### Response

~~~json
{}
~~~

##  Get mentions stream

Contains all posts in which mentioned the currently authenticated user, ordered by their creation time stamp.

### Request

~~~
GET /api/v1/streams/mentions
~~~

### Response

~~~json
{}
~~~

## Get tag stream

Contains posts tagged with one or more tags followed by the authenticated user.

### Request

~~~
GET /api/v1/streams/tags
~~~

### Response

~~~json
{}
~~~
