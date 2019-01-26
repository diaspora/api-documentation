---
title: Aspects
see_also:
  - target: contacts
---

{% include toc.md %}

## Get lists of aspects

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

### Request

~~~
GET /api/v1/aspects/:aspect_id
~~~

### Response

~~~json
{
  "id": 1,
  "name": "Family",
  "order": 1,
  "contacts_visible": true,
  "chat_enabled": true
}
~~~

## Create new aspect

### Request

~~~
POST /api/v1/aspects
~~~
~~~json
{
  "name": "diaspora developers",
  "contacts_visible": false,
  "chat_enabled": true
}
~~~

### Response

~~~json
{
  "id": 3,
  "name": "diaspora developers",
  "order": 4,
  "contacts_visible": false,
  "chat_enabled": true
}
~~~

## Edit an aspect

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
| chat_enabled     | boolean | Whether the chat is enabled for this aspect or not.                                                                                             |
| contacts_visible | boolean | Whether the contacts should be able to see each others or not.                                                                                  |
| name             | string  | The aspects name.                                                                                                                               |
| order            | integer | The aspects position in the aspect list. If provided, the aspect will get inserted into the given position and other aspects will be reordered. |

### Response

~~~json
{
  "id": 3,
  "name": "diaspora community",
  "order": 4,
  "contacts_visible": false,
  "chat_enabled": true
}
~~~

## Delete an aspect

### Request

~~~
DELETE /api/v1/aspects/:aspect_id
~~~

### Response

~~~
Status: 204 No Content
~~~

[contacts]: {{ site.baseurl }}/routes/contacts.html
