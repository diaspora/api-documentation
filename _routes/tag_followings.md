---
title: Tag followings
---

{% include toc.md %}

## Get list of followed tags

Required API scope: `tags:read`

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

Required API scope: `tags:modify`

### Request

~~~
POST /api/v1/tag_followings/:tag_name
~~~

### Response

~~~
Status: 204 No Content
~~~

## Unfollow a tag

Required API scope: `tags:modify`

### Request

~~~
DELETE /api/v1/tag_followings/:tag_name
~~~

### Response

~~~
Status: 204 No Content
~~~
