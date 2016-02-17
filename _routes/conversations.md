---
title: Conversations
---

{% include toc.md %}

## Get list of all conversations

### Request

~~~
GET /api/v1/conversations
~~~

### Response

~~~json
~~~

## Get information about a single conversation

### Request

~~~
GET /api/v1/conversations/:conversation_guid
~~~

### Response

~~~json
~~~

## Create new conversation

### Request

~~~
POST /api/v1/conversations
~~~

### Response

~~~json
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

### Request

~~~
GET /api/v1/conversations/:conversation_guid/messages
~~~

### Response

~~~json
~~~

## Post new message to a conversation

### Request

~~~
POST /api/v1/conversations/:conversation_guid/messages
~~~

### Response

~~~json
~~~
