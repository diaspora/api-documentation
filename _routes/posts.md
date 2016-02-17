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

## Get comments for a single post

### Request

~~~
GET /api/v1/posts/:post_guid/comments
~~~

### Response

~~~json
~~~

## Delete a comment

### Request

~~~
DELETE /api/v1/posts/:post_guid/comments/:comment_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

## Get likes for a single post

### Request

~~~
GET /api/v1/posts/:post_guid/likes
~~~

### Response

~~~json
~~~

## Get reshares for a single post

### Request

~~~
GET /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~json
~~~

## Add a comment to a post

### Request

~~~
POST /api/v1/posts/:post_guid/comments
~~~
~~~json
~~~

### Response

~~~json
~~~

## Like a post

### Request

~~~
POST /api/v1/posts/:post_guid/likes
~~~

### Response

~~~json
~~~

## Reshare a post

### Request

~~~
POST /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~json
~~~
