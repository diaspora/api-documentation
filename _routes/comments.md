---
title: Comments
---

{% include toc.md %}

## Get comments for a post

### Request

~~~
GET /api/v1/posts/:post_guid/comments
~~~

### Response

~~~json
[
  {
    "guid": "42817320b18c013355e5705681972339",
    "created_at": "2016-02-09T18:52:58.209Z",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    "body": "What a wonderful post!"
  },
  {
    "guid": "9d164700b82f0133e40d406c8f31e210",
    "created_at": "2016-02-09T18:59:01.114Z",
    "author": {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    },
    "body": "Thank you very much, Alice!"
  }
]
~~~

## Delete a comment

Only the current users comments or comments written on the current users posts can be deleted.

### Request

~~~
DELETE /api/v1/posts/:post_guid/comments/:comment_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

## Report a comment

### Request

~~~
POST /api/v1/posts/:post_guid/comments/:comment_guid/report
~~~
~~~json
{
  "reason": "Using my images without my permission."
}
~~~

### Response

~~~
Status: 204 No Content
~~~

## Add a comment to a post

### Request

~~~
POST /api/v1/posts/:post_guid/comments
~~~
~~~json
{
  "body": "Can I use these for my own website?"
}
~~~

### Response

~~~json
{
  "guid": "010fb390b8310133e40d406c8f31e210",
  "created_at": "2016-02-18T05:46:52.649Z",
  "author": {
    "guid": "f50ffc00b188013355e3705681972339",
    "diaspora_id": "alice@example.com",
    "name": "Alice Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
  },
  "body": "Can I use these for my own website?"
}
~~~
