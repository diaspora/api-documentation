---
title: Search
---

{% include toc.md %}

**Limitation on search results**:

Please note that, since diaspora\* is a distributed social network, search results may vary from pod to pod. At the moment, there is no general distribution of content implemented, so a pod is only able to search items explicitly sent to the pod.

## Search for users

Contains users that matches the selected criteria. Please note that, at this moment, only one selector can be enabled at the same time.

Required API scope: `public:read`

Optional API scope: `contacts:read`

### Request

~~~
GET /api/v1/search/users
~~~

### Parameters (one required)

| Name           | Type   | Description                                       |
| -------------- | ------ | ------------------------------------------------- |
| name_or_handle | string | Part or entire profile name or diaspora\* handle. |
| tag            | string | A tag that the person is tagged with.             |

### Response

~~~json
[
  {
    "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
    "diaspora_id": "bob@example.com",
    "name": "Bob Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
  },
  {
    "guid": "83de2fc0b8cc0133e40d406c8f31e210",
    "diaspora_id": "trent@example.com",
    "name": "Trent Bob Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
  }
]
~~~

## Search for posts

Please note that, at this moment, this route only allows searching for posts by tags. However, this may be extended in the future.

Required API scope: `public:read`

Optional API scope: `private:read`

### Request

~~~
GET /api/v1/search/posts
~~~

### Parameters (one required)

| Name | Type   | Description                         |
| ---- | ------ | ----------------------------------- |
| tag  | string | A tag that the post has to contain. |

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
      "comments": 14,
      "likes": 42,
      "reshares": 9
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
