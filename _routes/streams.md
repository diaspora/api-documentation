---
title: Streams
---

{% include toc.md %}

## Get the main stream

Contains posts from users the currently authenticated user is sharing with as well as posts tagged with tags which the currently authenticated user is following.

### Request

~~~
GET /api/v1/streams/main
~~~

### Response

~~~json
[
  {
    "guid": "83d406e0b9b20133e40c406c8f31e210",
    "created_at": "2016-02-20T03:46:57.955Z",
    "post_type": "StatusMessage",
    "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a di...",
    "body": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus. Sed sit amet ipsum mauris. Maecenas congue ligula ac quam viverra nec consectetur ante hendrerit. Donec et mollis dolor.",
    "provider_display_name": "ExampleApp",
    "public": true,
    "nsfw": false,
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    "interaction_counters": {
      "comments": 3,
      "likes": 1,
      "reshares": 0
    }
  },
  {
    "guid": "466738b0b9c30133e40e406c8f31e210",
    "created_at": "2016-02-20T05:47:02.694Z",
    "post_type": "StatusMessage",
    "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a di...",
    "body": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus. Sed sit amet ipsum mauris. Maecenas congue ligula ac quam viverra nec consectetur ante hendrerit. Donec et mollis dolor.",
    "public": true,
    "nsfw": false,
    "author": {
      "guid": "19103170b8cc0133e40d406c8f31e210",
      "diaspora_id": "carol@example.com",
      "name": "Carol Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
    },
    "interaction_counters": {
      "comments": 14,
      "likes": 42,
      "reshares": 9
    }
  }
]
~~~

### Errors

No specific errors for this API endpoint.

## Get aspect stream

Contains all posts in some or all aspects. If `aspect_ids` is empty, all aspects are considered.

### Request

~~~
GET /api/v1/streams/aspects
~~~

### Optional parameters

| Name       | Type  | Description                       |
| ---------- | ----- | --------------------------------- |
| aspect_ids | array | List of one or more `aspect_id`s. |

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.

## Get activity stream

Contains all posts on which the currently authenticated user interacted on, ordered by their last activity.

### Request

~~~
GET /api/v1/streams/activity
~~~

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.

##  Get mentions stream

Contains all posts in which the currently authenticated user is mentioned, ordered by their creation timestamp.

### Request

~~~
GET /api/v1/streams/mentions
~~~

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.

## Get tag stream

Contains posts tagged with one or more tags followed by the currently authenticated user.

### Request

~~~
GET /api/v1/streams/tags
~~~

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.

## Get liked stream

Contains posts liked by the currently authenticated user.

### Request

~~~
GET /api/v1/streams/liked
~~~

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.

## Get commented stream

Contains posts commented by the currently authenticated user.

### Request

~~~
GET /api/v1/streams/commented
~~~

### Response

See [Main Stream Response example](#response).

### Errors

No specific errors for this API endpoint.
