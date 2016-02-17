---
title: Posts
---

{% include toc.md %}

## Get information about a single post

### Request

~~~
GET /api/v1/posts/:post_guid
~~~

### Response

~~~json
~~~

## Publish a post

### Request

~~~
POST /api/v1/posts
~~~
~~~json
~~~

### Response

~~~json
~~~

## Delete a post

### Request

~~~
DELETE /api/v1/posts/:post_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

## Report a post

### Request

~~~
POST /api/v1/posts/:post_guid/report
~~~

### Response

~~~
Status: 204 No Content
~~~

## Subscribe to a post

The current user will receive notifications for subscribed posts without adding a like or comment.

### Request

~~~
POST /api/v1/posts/:post_guid/subscribe
~~~

### Response

~~~
Status: 204 No Content
~~~

## Mute a post

The current user will not receive any notifications for this post, even if a comment or like was added.

### Request

~~~
POST /api/v1/posts/:post_guid/mute
~~~

### Response

~~~
Status: 204 No Content
~~~

## Hide a post

The given post will be excluded from all streams and search results.

### Request

~~~
POST /api/v1/posts/:post_guid/hide
~~~

### Response

~~~
Status: 204 No Content
~~~
