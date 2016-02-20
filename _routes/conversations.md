---
title: Conversations
---

{% include toc.md %}

## Get list of all conversations

### Request

~~~
GET /api/v1/conversations
~~~

### Optional parameters

| Name        | Type      | Description                                                            |
| ----------- | --------- | ---------------------------------------------------------------------- |
| only_after  | timestamp | If set, only conversations updated after the given time will be shown. |
| only_unread | boolean   | If true, the response will only contain unread conversations.          |

### Response

~~~json
[
  {
    "guid": "3ffe3620b89b0133e40c406c8f31e210",
    "subject": "Look, I found a kitten",
    "created_at": "2016-02-18T18:27:54.554Z",
    "read": false,
    "participants": [
      {
        "guid": "f50ffc00b188013355e3705681972339",
        "diaspora_id": "alice@example.com",
        "name": "Alice Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
      },
      {
        "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
        "diaspora_id": "bob@example.com",
        "name": "Bob Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
      }
    ]
  },
  {
    "guid": "59804e90b8cc0133e40d406c8f31e210",
    "subject": "Our meeting tomorrow",
    "created_at": "2016-02-19T00:19:35.154Z",
    "read": true,
    "participants": [
      {
        "guid": "f50ffc00b188013355e3705681972339",
        "diaspora_id": "alice@example.com",
        "name": "Alice Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
      },
      {
        "guid": "19103170b8cc0133e40d406c8f31e210",
        "diaspora_id": "carol@example.com",
        "name": "Carol Testing",
        "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
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

## Get information about a single conversation

### Request

~~~
GET /api/v1/conversations/:conversation_guid
~~~

### Response

~~~json
{
  "guid": "59804e90b8cc0133e40d406c8f31e210",
  "subject": "Our meeting tomorrow",
  "created_at": "2016-02-19T00:19:35.154Z",
  "read": true,
  "participants": [
    {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    {
      "guid": "19103170b8cc0133e40d406c8f31e210",
      "diaspora_id": "carol@example.com",
      "name": "Carol Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_2e1bc500b8cc0133e40d.jpg"
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

## Create new conversation

### Request

~~~
POST /api/v1/conversations
~~~
~~~json
{
  "subject": "Cake recipe",
  "recipients": [
    "f50ffc00b188013355e3705681972339",
    "cb7e4aa0b82f0133e40d406c8f31e210"
  ],
  "body": "Hey Alice, hey bob!\nThanks for the **nice** visit yesterday. Since you both enjoyed the chocolate cake I made for us, here is the recipe so you can have one, too!"
}
~~~

### Response

~~~json
{
  "guid": "f64982a0b8cd0133e40d406c8f31e210",
  "subject": "Cake recipe",
  "created_at": "2016-02-19T00:31:03.500Z",
  "participants": [
    {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    },
    {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    }
  ]
}
~~~

## Ignore and hide a conversation

### Request

~~~
DELETE /api/v1/conversations/:conversation_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

## List messages in a conversation

Note: This also marks the given conversation as read.

### Request

~~~
GET /api/v1/conversations/:conversation_guid/messages
~~~

### Optional parameters

| Name       | Type      | Description                                                       |
| ---------- | --------- | ----------------------------------------------------------------- |
| only_after | timestamp | If set, only messages created after the given time will be shown. |

### Response

~~~json
[
  {
    "guid": "9e27cb70b8d90133e40d406c8f31e210",
    "created_at": "2016-02-19T01:54:31.518Z",
    "body": "Have you received the recipe?",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    }
  },
  {
    "guid": "dcb80d90b8d90133e40d406c8f31e210",
    "created_at": "2016-02-19T01:56:12.790Z",
    "body": "Yeah! Just baking now... ;)",
    "author": {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    }
  },
  {
    "guid": "01868d90b8da0133e40d406c8f31e210",
    "created_at": "2016-02-19T01:57:14.966Z",
    "body": "**Awesome!** Will be there in 15 minutes!",
    "author": {
      "guid": "f50ffc00b188013355e3705681972339",
      "diaspora_id": "alice@example.com",
      "name": "Alice Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
    }
  }
]
~~~

## Post new message to a conversation

### Request

~~~
POST /api/v1/conversations/:conversation_guid/messages
~~~
~~~json
{
  "body": "Cool, see you! ;)"
}
~~~

### Response

~~~json
{
  "guid": "757a89b0b8da0133e40d406c8f31e210",
  "created_at": "2016-02-19T02:00:28.080Z",
  "body": "Cool, see you! ;)",
  "author": {
    "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
    "diaspora_id": "bob@example.com",
    "name": "Bob Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
  }
}
~~~
