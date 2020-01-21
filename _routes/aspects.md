---
title: Aspects
see_also:
  - target: contacts
---

{% include toc.md %}

## Get lists of aspects

Required API scope: `contacts:read`

### Request

~~~
GET /api/v1/aspects
~~~

### Response

~~~json
[
  {
    "id": 1,
    "name": "Family",
    "order": 1
  },
  {
    "id": 2,
    "name": "Friends",
    "order": 2
  }
]
~~~

## Get information about an aspect

Required API scope: `contacts:read`

### Request

~~~
GET /api/v1/aspects/:aspect_id
~~~

### Response

~~~json
{
  "id": 1,
  "name": "Family",
  "order": 1
}
~~~

## Create new aspect

Required API scope: `contacts:modify`

### Request

~~~
POST /api/v1/aspects
~~~
~~~json
{
  "name": "diaspora developers"
}
~~~

### Response

~~~json
{
  "id": 3,
  "name": "diaspora developers",
  "order": 4
}
~~~

## Edit an aspect

Required API scope: `contacts:modify`

### Request

~~~
PATCH /api/v1/aspects/:aspect_id
~~~
~~~json
{
  "name": "diaspora community"
}
~~~

### Parameters

| Name             | Type    | Description                                                                                                                                     |
| ---------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| name             | string  | The aspects name.                                                                                                                               |
| order            | integer | The aspects position in the aspect list. If provided, the aspect will get inserted into the given position and other aspects will be reordered. |

### Response

~~~json
{
  "id": 3,
  "name": "diaspora community",
  "order": 4
}
~~~

## Delete an aspect

Required API scope: `contacts:modify`

### Request

~~~
DELETE /api/v1/aspects/:aspect_id
~~~

### Response

~~~
Status: 204 No Content
~~~

[contacts]: {{ site.baseurl }}/routes/contacts.html
