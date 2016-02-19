---
title: Reshares
---

{% include toc.md %}

## Get reshares for a single post

### Request

~~~
GET /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~json
[
  {
    "guid": "475fc770b8fe0133e40d406c8f31e210",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    }
  },
  {
    "guid": "4cc33b10b8fe0133e40d406c8f31e210",
    "author": {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    }
  }
]
~~~

## Reshare a post

### Request

~~~
POST /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~
Status: 204 No Content
~~~
