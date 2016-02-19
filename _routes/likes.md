---
title: Likes
---

{% include toc.md %}

## Get likes for a post

### Request

~~~
GET /api/v1/posts/:post_guid/likes
~~~

### Response

~~~json
[
  {
    "guid": "b6098440b8e00133e40d406c8f31e210",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    }
  },
  {
    "guid": "cf6a25b0b8e00133e40d406c8f31e210",
    "author": {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    }
  }
]
~~~

## Like a post

### Request

~~~
POST /api/v1/posts/:post_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~

## Unlike a post

### Request

~~~
DELETE /api/v1/posts/:post_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~
