---
title: Contacts
see_also:
  - aspects
---

Contacts are always managed inside [aspects][aspects].

{% include toc.md %}

## Get list of contacts in an aspect

### Request

~~~
GET /api/v1/aspects/:aspect_id/contacts
~~~

### Response

~~~json
{}
~~~

## Add a user to an aspect

### Request

~~~
PUT /api/v1/aspects/:aspect_id/contacts/:person_guid
~~~

### Response

~~~json
{}
~~~

## Remove a user from an aspect

### Request

~~~
DELETE /api/v1/aspects/:aspect_id/contacts/:person_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

[aspects]: {{ site.baseurl }}/routes/aspects.html
