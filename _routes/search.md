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
GET /api/v1/search/user
~~~

### Parameters (one required)

| Parameter      | Description                                      |
| -------------- | ------------------------------------------------ |
| name_or_handle | Part or entire profile name or diaspora\* handle |
| tag            | A tag that the person is tagged with             |

### Response

~~~json
{}
~~~

## Search for posts

Please note that, at this moment, this route only allows searching for posts by tags. However, this may be extended in the future.

### Request

~~~
GET /api/v1/search/posts
~~~

### Parameters (one required)

| Parameter | Description                        |
| --------- | ---------------------------------- |
| tag       | A tag that the post has to contain |

### Response

~~~json
{}
~~~
