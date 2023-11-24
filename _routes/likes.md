---
title: Likes
---

{% include toc.md %}

## Get likes for a post

Required API scope: the one which gives read access to the post (`public:read` for public posts and `private:read` for private posts).

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

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |

## Get likes for a comment

Required API scope: the one which gives read access to the post (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
GET /api/v1/posts/:post_guid/comments/:comment_guid/likes
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

### Errors

| Status code | Error reason                                          |
| ----------- | ----------------------------------------------------- |
| 404         | Post or comment with provided guid could not be found |


## Like a post

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
POST /api/v1/posts/:post_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 422         | User is not allowed to like                |
| 409         | Like already exists                        |

## Like a comment

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
POST /api/v1/posts/:post_guid/comments/:comment_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                                          |
| ----------- | ----------------------------------------------------- |
| 404         | Post or comment with provided guid could not be found |
| 422         | User is not allowed to like                           |
| 409         | Like already exists                                   |

## Unlike a post

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
DELETE /api/v1/posts/:post_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 410         | Like doesn't exist                         |

## Unlike a comment

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
DELETE /api/v1/posts/:post_guid/comments/:comment_guid/likes
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                                          |
| ----------- | ----------------------------------------------------- |
| 404         | Post or comment with provided guid could not be found |
| 410         | Like doesn't exist                                    |
