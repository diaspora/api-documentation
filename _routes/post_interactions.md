---
title: Post interactions
see_also:
  - target: comments
  - target: likes
  - target: reshares
---

{% include toc.md %}

## Report a post

### Request

~~~
POST /api/v1/posts/:post_guid/report
~~~

### Response

~~~
Status: 204 No Content
~~~

## Subscribe to a post

The current user will receive notifications for subscribed posts without adding a like or comment.

### Request

~~~
POST /api/v1/posts/:post_guid/subscribe
~~~

### Response

~~~
Status: 204 No Content
~~~

## Mute or unmute a post

The current user will not receive any notifications for this post, even if a comment or like was added.

### Request

~~~
POST /api/v1/posts/:post_guid/mute
~~~
~~~json
{
  "mute": true
}
~~~

### Parameters

| Name | Type    | Description                              |
| ---- | ------- | ---------------------------------------- |
| mute | boolean | Whether the post should be muted or not. |

### Response

~~~
Status: 204 No Content
~~~

## Hide or unhide a post

The given post will be excluded from all streams and search results.

### Request

~~~
POST /api/v1/posts/:post_guid/hide
~~~
~~~json
{
  "hide": true
}
~~~

### Parameters

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| hide | boolean | Whether the post should be hidden or not. |

### Response

~~~
Status: 204 No Content
~~~

[comments]: {{ site.baseurl }}/routes/comments.html
[likes]: {{ site.baseurl }}/routes/likes.html
[reshares]: {{ site.baseurl }}/routes/reshares.html
