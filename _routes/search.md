---
title: Search
---

{% include toc.md %}

## Search for users

Contains users that matches the selected criteria. Please note that, at this moment, only one selector can be enabled at the same time.

{% include warning_box.html
   title="Limitations on user search"
   content="Insert note about decentralized issues here."
%}

### Request

~~~
GET /api/v1/search/users
~~~

### Parameters (one required)

| Name           | Description                                      |
| -------------- | ------------------------------------------------ |
| name_or_handle | Part or entire profile name or diaspora\* handle |
| tag            | A tag that the person is tagged with             |

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

### Request

~~~
GET /api/v1/search/posts
~~~

### Parameters (one required)

| Name | Description                        |
| ---- | ---------------------------------- |
| tag  | A tag that the post has to contain |

### Response

~~~json
{}
~~~
