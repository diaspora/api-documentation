---
title: Users
---

{% include toc.md %}

## Get information about the authenticated user

### Request

~~~
GET /api/v1/user
~~~

### Response

~~~json
{
  "guid": "5cebd150b82e0133e40c406c8f31e210",
  "name": "Bob Testing",
  "searchable": true,
  "show_profile_info": true,
  "birthday": "January 02 1984",
  "diaspora_id": "bob@example.com",
  "gender": "Example",
  "location": "World",
  "bio": "Lorem ipsum **dolor sit amet**, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat!",
  "avatar": {
    "large": "http://example.com/uploads/images/thumb_large_0fc4bbc68f744c27ed80.jpg",
    "medium": "http://example.com/uploads/images/thumb_medium_0fc4bbc68f744c27ed80.jpg",
    "small": "http://example.com/uploads/images/thumb_small_0fc4bbc68f744c27ed80.jpg"
  },
  "tags": [
    "bobclub",
    "development",
    "diaspora"
  ]
}
~~~

## Update the currently authenticated users profile

### Request

~~~
PATCH /api/v1/user
~~~
~~~json
{
  "location": "My home!",
  "name": "Bob Anonymous"
}
~~~


### Parameters

| Name              | Type    | Description                                                           |
| ----------------- | ------- | --------------------------------------------------------------------- |
| bio               | string  | The profiles long bio text.                                           |
| birthday          | date    | The users birthday.                                                   |
| gender            | string  | The profiles gender.                                                  |
| location          | string  | The users location.                                                   |
| name              | string  | The new profile name.                                                 |
| searchable        | boolean | Whether the profile should be searchable via the profile name or not. |
| show_profile_info | boolean | whether the public info should be publicly visible or not.            |
| tags              | array   | Up to five tags to tag the profile with.                              |

### Response

~~~json
{
  "guid": "5cebd150b82e0133e40c406c8f31e210",
  "name": "Bob Anonymous",
  "searchable": true,
  "show_profile_info": true,
  "birthday": "January 02 1984",
  "diaspora_id": "bob@example.com",
  "gender": "Example",
  "location": "My home!",
  "bio": "Lorem ipsum **dolor sit amet**, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat!",
  "avatar": {
    "large": "http://example.com/uploads/images/thumb_large_0fc4bbc68f744c27ed80.jpg",
    "medium": "http://example.com/uploads/images/thumb_medium_0fc4bbc68f744c27ed80.jpg",
    "small": "http://example.com/uploads/images/thumb_small_0fc4bbc68f744c27ed80.jpg"
  },
  "tags": [
    "bobclub",
    "development",
    "diaspora"
  ]
}
~~~

## Get information about a single user

Please note that the amount of information you retrieve from this request depends on whether the requested person shares with the authenticated user or not.

### Request

~~~
GET /api/v1/users/:person_guid
~~~

### Response

~~~json
{
  "guid": "f50ffc00b188013355e3705681972339",
  "name": "Alice Testing",
  "birthday": "January 02 1984",
  "diaspora_id": "alice@example.com",
  "gender": "Example",
  "location": "My home!",
  "bio": "Lorem ipsum **dolor sit amet**, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat!",
  "block": false,
  "avatar": {
    "large": "http://example.com/uploads/images/thumb_large_0fc4bbc68f744c27ed80.jpg",
    "medium": "http://example.com/uploads/images/thumb_medium_0fc4bbc68f744c27ed80.jpg",
    "small": "http://example.com/uploads/images/thumb_small_0fc4bbc68f744c27ed80.jpg"
  },
  "tags": [
    "development",
    "diaspora"
  ],
  "relationship": "mutual",
  "aspects": [
    {
      "id": 1,
      "name": "Family"
    }
  ]
}
~~~

### Possible relationship states

| State       | Description                                                            |
| ----------- | ---------------------------------------------------------------------- |
| mutual      | Both the current and the selected user are sharing with each other.    |
| not_sharing | No relationship between the current user and the selected user exists. |
| receiving   | The selected user is sharing with the current user.                    |
| sharing     | The current user is sharing with the selected user.                    |

## Get posts by a single user

### Request

~~~
GET /api/v1/users/:person_guid/posts
~~~

### Response

~~~json
{}
~~~
