---
title: Aspects
---

Contact groups are called aspects in diaspora\*. Check [the contacts routes][contacts] for information on how to manage contacts within aspects.

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
    "contacts_visible": true,
    "chat_enabled": true
  },
  {
    "id": 2,
    "name": "Friends",
    "contacts_visible": true,
    "chat_enabled": false
  }
]
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
  "contacts_visible": false,
  "chat_enabled": true
}
~~~

## Edit an aspect

### Request

~~~
PATCH /api/v1/aspects/:id
~~~
~~~json
{
  "name": "diaspora community"
}
~~~

### Response

~~~json
{
  "id": 3,
  "name": "diaspora community",
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
