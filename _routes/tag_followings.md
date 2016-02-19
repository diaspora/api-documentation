---
title: Tag followings
---

{% include toc.md %}

## Get list of followed tags

### Request

~~~
GET /api/v1/tag_followings
~~~

### Response

~~~json
[
  "api",
  "development",
  "diaspora"
]
~~~

## Follow a tag

### Request

~~~
POST /api/v1/tag_followings/:tag_name
~~~

### Response

~~~
Status: 204 No Content
~~~

## Unfollow a tag

### Request

~~~
DELETE /api/v1/tag_followings/:tag_name
~~~

### Response

~~~
Status: 204 No Content
~~~
