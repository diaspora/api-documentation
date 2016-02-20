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

Please note that the amount of information you retrieve from this request depends on whether the requested person shares with the currently authenticated user or not.

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
  "relationship": {
    "receiving": true,
    "sharing": false
  },
  "aspects": [
    {
      "id": 1,
      "name": "Family"
    }
  ]
}
~~~

## Get contacts from a single user

Please note that, depending on the users aspect settings, you might not see other contacts and get an empty response instead.

### Request

~~~
GET /api/v1/users/:person_guid/contacts
~~~

### Response

~~~json
[
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
~~~

## Get posts by a single user

### Request

~~~
GET /api/v1/users/:person_guid/posts
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
  }
]
~~~

## Get photos by a single user

### Request

~~~
GET /api/v1/users/:person_guid/photos
~~~

### Response

~~~json
[
  {
    "guid": "0a992a10b9db0133e40e406c8f31e210",
    "dimensions": {
      "height": 1200,
      "width": 1600
    },
    "sizes": {
      "large": "http://example.com/uploads/images/scaled_full_f6ce0597695a878c4663.jpg",
      "medium": "http://example.com/uploads/images/thumb_medium_f6ce0597695a878c4663.jpg",
      "small": "http://example.com/uploads/images/thumb_small_f6ce0597695a878c4663.jpg"
    }
  },
  {
    "guid": "114999c0b9db0133e40e406c8f31e210",
    "dimensions": {
      "height": 1200,
      "width": 1600
    },
    "sizes": {
      "large": "http://example.com/uploads/images/scaled_full_c384f99eda7f19dfe78c.jpg",
      "medium": "http://example.com/uploads/images/thumb_medium_c384f99eda7f19dfe78c.jpg",
      "small": "http://example.com/uploads/images/thumb_small_c384f99eda7f19dfe78c.jpg"
    }
  }
]
~~~
