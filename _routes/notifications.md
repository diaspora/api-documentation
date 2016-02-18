---
title: Notifications
---

{% include toc.md %}

## Get list of all notifications

### Request

~~~
GET /api/v1/notifications
~~~

### Response

~~~json
{}
~~~

## Get information about a single notification

Note: This also marks the given notification as read.

### Request

~~~
GET /api/v1/notifications/:notification_id
~~~

### Response

~~~json
{}
~~~

## Mark a notification as unread

### Request

~~~
PUT /api/v1/notifications/:notification_id
~~~
~~~json
{
  "unread": true
}
~~~

### Response

~~~json
{}
~~~
