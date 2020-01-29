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
POST /api/v1/tag_followings
~~~
~~~json
{
  "name": "cats"
}
~~~

### Parameters

| Name | Type   | Description                         |
| ---- | ------ | ----------------------------------- |
| name | string | The name of the tag to be followed. |

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason             |
| ----------- |------------------------- |
| 409         | Tag was already followed |

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

### Errors

| Status code | Error reason         |
| ----------- |--------------------- |
| 410         | Tag was not followed |
