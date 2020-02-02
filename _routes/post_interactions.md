---
title: Post interactions
see_also:
  - target: comments
  - target: likes
  - target: reshares
---

{% include toc.md %}

## Report a post

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
POST /api/v1/posts/:post_guid/report
~~~
~~~json
{
  "reason": "This post is spam."
}
~~~

### Parameters

| Name   | Type   | Description                            |
| ------ | ------ | -------------------------------------- |
| reason | string | The reason behind reporting this post. |

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 409         | Post has already been reported             |
| 422         | Request invalid, such as a missing reason  |

## Subscribe to a post

The current user will receive notifications for subscribed posts without adding a like or comment.

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
POST /api/v1/posts/:post_guid/subscribe
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 409         | Already subscribed                         |
| 422         | Request invalid                            |


## Mute (unsubscribe from a) a post

The current user will not receive any notifications for this post, even if a comment or like was added.

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
POST /api/v1/posts/:post_guid/mute
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 410         | Was not subscribed to this post            |
| 422         | Request invalid                            |

## Hide or unhide a post

The given post will be excluded from all streams and search results.

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

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

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 409         | Post is already hidden                     |
| 410         | Post is not hidden                         |
| 422         | Request invalid                            |

[comments]: {{ site.baseurl }}/routes/comments.html
[likes]: {{ site.baseurl }}/routes/likes.html
[reshares]: {{ site.baseurl }}/routes/reshares.html
