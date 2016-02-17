---
title: Comments
---

{% include toc.md %}

## Get comments for a post

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

## Report a comment

### Request

~~~
POST /api/v1/posts/:post_guid/comments/:comment_guid/report
~~~

### Response

~~~
Status: 204 No Content
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

