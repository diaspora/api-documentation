---
title: Reshares
---

{% include toc.md %}

## Get reshares for a single post

Required API scope: `public:read`

### Request

~~~
GET /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~json
[
  {
    "guid": "475fc770b8fe0133e40d406c8f31e210",
    "created_at": "2016-02-20T03:46:57.955Z",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    }
  },
  {
    "guid": "4cc33b10b8fe0133e40d406c8f31e210",
    "created_at": "2016-02-20T04:15:21.213Z",
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

Resharing is effectively creating a new post, which is why this method returns a post object.

Required API scope: `public:modify`

### Request

~~~
POST /api/v1/posts/:post_guid/reshares
~~~

### Response

~~~json
{
  "guid": "0a992a10b9db0133e40e406c8f31e210",
  "created_at": "2016-02-20T05:41:40.289Z",
  "post_type": "Reshare",
  "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a di...",
  "body": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus. Sed sit amet ipsum mauris. Maecenas congue ligula ac quam viverra nec consectetur ante hendrerit. Donec et mollis dolor.",
  "provider_display_name": "ExampleApp",
  "public": true,
  "nsfw": false,
  "root": {
    "guid": "72af1170b9b60133e40e406c8f31e210",
    "created_at": "2016-02-20T04:15:21.213Z",
    "author": {
      "guid": "83de2fc0b8cc0133e40d406c8f31e210",
      "diaspora_id": "trent@example.com",
      "name": "Trent Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
    }
  },
  "author": {
    "guid": "f50ffc00b188013355e3705681972339",
    "diaspora_id": "alice@example.com",
    "name": "Alice Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
  },
  "interaction_counters": {
    "comments": 0,
    "likes": 0,
    "reshares": 0
  },
  "own_interaction_state": {
    "liked": false,
    "reshated": false,
    "subscribed": false
  }
}
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 422         | User is not allowed to reshare             |
| 409         | Reshare already exists                     |