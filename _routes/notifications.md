---
title: Notifications
---

{% include toc.md %}

**Possible notification types**:

| Type                 | Description                                                     |
| -------------------- | --------------------------------------------------------------- |
| also_commented       | Someone commented on a post the current user also commented on. |
| commented_on_post    | Someone commented on a post the current user created.           |
| liked                | Someone liked a post the current user created.                  |
| liked_comment        | Someone liked a comment the current user created.               |
| mentioned            | Someone mentioned the current user in a post.                   |
| mentioned_in_comment | Someone mentioned the current user in a comment of a post.      |
| reshared             | Someone reshared one of the current user's posts.               |
| started_sharing      | Someone started sharing with the current user.                  |
| contacts_birthday    | Someone in the contacts of the current user has their birthday. |

"Someone" is defined in `event_creators` which represents one or more user profiles. All types, excluding `started_sharing` and `contacts_birthday` will include a `target` identifying the post the event was created at.
The `target` will always be the related post object, so for `mentioned_in_comment` the post the comment was
created on, for `liked` the post that was liked, for 'liked_comment' the post the liked comment was created on and so on.

## Get list of all notifications

Required API scope: `notifications`

### Request

~~~
GET /api/v1/notifications
~~~

### Optional parameters

| Name        | Type      | Description                                                            |
| ----------- | --------- | ---------------------------------------------------------------------- |
| only_after  | timestamp | If set, only notifications updated after the given time will be shown. |
| only_unread | boolean   | If true, the response will only contain unread notifications.          |
| type        | string    | Only show notifications with the specified type.                       |

### Response

~~~json
[
  {
    "guid": "2d97ab40b8e70133e40d406c8f31e210",
    "type": "started_sharing",
    "read": false,
    "created_at": "2016-02-19T03:41:15.116Z",
    "event_creators": [
      {
        "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
        "diaspora_id": "bob@example.com",
        "name": "Bob Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
      }
    ]
  },
  {
    "guid": "df6e8a20b8e70133e40d406c8f31e210",
    "type": "also_commented",
    "read": false,
    "created_at": "2016-02-19T03:41:25.284Z",
    "target": {
      "guid": "e0a33450b8e70133e40d406c8f31e210",
      "author": {
        "guid": "19103170b8cc0133e40d406c8f31e210",
        "diaspora_id": "carol@example.com",
        "name": "Carol Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
      }
    },
    "event_creators": [
      {
        "guid": "f50ffc00b188013355e3705681972339",
        "diaspora_id": "alice@example.com",
        "name": "Alice Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
      },
      {
        "guid": "83de2fc0b8cc0133e40d406c8f31e210",
        "diaspora_id": "trent@example.com",
        "name": "Trent Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
      }
    ]
  }
]
~~~

## Get information about a single notification

*Note*: This also marks the given notification as read.

Required API scope: `notifications`

### Request

~~~
GET /api/v1/notifications/:notification_id
~~~

### Response

~~~json
{
  "guid": "df6e8a20b8e70133e40d406c8f31e210",
  "type": "also_commented",
  "read": true,
  "created_at": "2016-02-19T03:41:39.858Z",
  "target": {
    "guid": "e0a33450b8e70133e40d406c8f31e210",
    "author": {
      "guid": "19103170b8cc0133e40d406c8f31e210",
      "diaspora_id": "carol@example.com",
      "name": "Carol Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
    }
  },
  "event_creators": [
    {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    {
      "guid": "83de2fc0b8cc0133e40d406c8f31e210",
      "diaspora_id": "trent@example.com",
      "name": "Trent Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
    }
  ]
}
~~~

## Mark a notification as unread

Required API scope: `notifications`

### Request

~~~
PATCH /api/v1/notifications/:notification_id
~~~
~~~json
{
  "read": false
}
~~~

### Response

~~~json
{
  "guid": "df6e8a20b8e70133e40d406c8f31e210",
  "type": "also_commented",
  "read": false,
  "created_at": "2016-02-19T03:41:39.858Z",
  "target": {
    "guid": "e0a33450b8e70133e40d406c8f31e210",
    "author": {
      "guid": "19103170b8cc0133e40d406c8f31e210",
      "diaspora_id": "carol@example.com",
      "name": "Carol Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
    }
  },
  "event_creators": [
    {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    {
      "guid": "83de2fc0b8cc0133e40d406c8f31e210",
      "diaspora_id": "trent@example.com",
      "name": "Trent Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
    }
  ]
}
~~~
