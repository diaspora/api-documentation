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
{}
~~~

## Follow a tag

### Request

~~~
POST /api/v1/tag_followings
~~~
~~~json
{}
~~~

### Response

~~~json
{}
~~~

## Unfollow a tag

### Request

~~~
DELETE /api/v1/tag_followings/:tag_following_id
~~~

### Response

~~~
Status: 204 No Content
~~~
