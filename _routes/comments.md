---
title: Comments
---

{% include toc.md %}

## Get comments for a post

Required API scope: the one which gives read access to the post (`public:read` for public posts and `private:read` for private posts).

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
    "body": "What a wonderful post!",
    "mentioned_people": [],
    "interactions": {
      "likes": [],
      "likes_count": 0
    },
    "reported": false
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
    "body": "Thank you very much, @{alice@example.com}!",
    "mentioned_people": [
      {
        "guid": "f50ffc00b188013355e3705681972339",
        "diaspora_id": "alice@example.com",
        "name": "Alice Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
      },
    ],
    "interactions": {
      "likes": [
        {
          "id": 93,
          "guid": "581caae04ec90139164a2cde48001122",
          "author": {
            "id": 7,
            "guid": "158d9e304884013914942cde48001122",
            "name": "Melory",
            "diaspora_id": "melory@example.com",
            "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
          },
          "created_at": "2021-02-11T19:00:34.652Z"
        }
      ],
      "likes_count":  1
    },
    "reported": false
  }
]
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |

## Delete a comment

Only the current users comments or comments written on the current users posts can be deleted.

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

### Request

~~~
DELETE /api/v1/posts/:post_guid/comments/:comment_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

### Errors

| Status code | Error reason                                  |
| ----------- | --------------------------------------------- |
| 403         | User not allowed to delete the comment        |
| 404         | Post with provided guid could not be found    |
| 410         | Comment not found for the given post          |

## Report a comment

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

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

### Errors

| Status code | Error reason                                     |
| ----------- | ------------------------------------------------ |
| 404         | Post with provided guid could not be found       |
| 404         | Comment not found for the given post             |
| 409         | This item already has been reported by this user |

## Add a comment to a post

Required API scope: `interactions`. Read access to the post must be present too (`public:read` for public posts and `private:read` for private posts).

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
  "body": "Can I use these for my own website?",
  "mentioned_people": []
}
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 422         | User is not allowed to comment             |
| 422         | Couldn't accept or process the comment     |
