---
title: Users
---

{% include toc.md %}

## Get information about the authenticated user

### Request

~~~
GET /api/v1/user
~~~

### Response

~~~json
{}
~~~

## Get information about a single user

Please note that the amount of information you retrieve from this request depends on whether the requested person shares with the authenticated user or not.

### Request

~~~
GET /api/v1/users/:person_guid
~~~

### Response

~~~json
{}
~~~

## Update the currently authenticated users profile

### Request

~~~
PATCH /api/v1/user
~~~
~~~json
{}
~~~

### Response

~~~json
{}
~~~
