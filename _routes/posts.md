---
title: Posts
see_also:
  - target: comments
  - target: likes
  - target: photos
  - target: post_interactions
  - target: reshares
---

{% include toc.md %}

## Advanced post contents
{:.no_toc}

Posts can contain a wide range of additional contents besides the basic body text. All JSON examples below are extracted for a simplified documentation, the objects would be included in the main `post` object.

### Available post types and Reshares

The `post_type` field in a response could either be `StatusMessage` or `Reshare`. A `StatusMessage` contains available post content fields. A `Reshare` also contains all available content fields, but an additional `root` object with information about the original post author and source. An interface displaying reshares should make clear that the resharing person is not the author of the contents. In addition to the post fields, the reshare's `root` object looks like this:

~~~json
{
  "root": {
    "guid": "72af1170b9b60133e40e406c8f31e210",
    "created_at": "2016-02-20T04:15:21.213Z",
    "author": {
      "guid": "83de2fc0b8cc0133e40d406c8f31e210",
      "diaspora_id": "trent@example.com",
      "name": "Trent Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_8894c7a0b8cc0133e40d.jpg"
    }
  }
}
~~~

### Mentions

Mentioned people will be included in a separate array for advanced displaying. A special syntax for mentions is used in the post content.

~~~json
{
  "body": "Playing a game of Lorem Ipsum with @{bob@example.com}!",
  "mentioned_people": [
    {
      "guid": "cb7e4aa0b82f0133e40d406c8f31e210",
      "diaspora_id": "bob@example.com",
      "name": "Bob Testing",
      "avatar": "http://example.com/uploads/images/thumb_medium_a51bf501fe86c198c0b1.jpg"
    }
  ]
}
~~~

### Photos

One or more photos can be attached to a post. Images are provided in multiple resolutions, so bandwidth usage can be optimized.

| Name   | Max. resolution      |
| ------ | -------------------- |
| raw    | original upload size |
| large  | max. 700px width     |
| medium | 100x100              |
| small  | 50x50                |

~~~json
{
  "photos": [
    {
      "dimensions": {
        "height": 1200,
        "width": 1600
      },
      "sizes": {
        "raw": "http://example.com/uploads/images/f6ce0597695a878c4663.jpg",
        "large": "http://example.com/uploads/images/scaled_full_f6ce0597695a878c4663.jpg",
        "medium": "http://example.com/uploads/images/thumb_medium_f6ce0597695a878c4663.jpg",
        "small": "http://example.com/uploads/images/thumb_small_f6ce0597695a878c4663.jpg"
      }
    },
    {
      "dimensions": {
        "height": 1200,
        "width": 1600
      },
      "sizes": {
        "raw": "http://example.com/uploads/images/c384f99eda7f19dfe78c.jpg",
        "large": "http://example.com/uploads/images/scaled_full_c384f99eda7f19dfe78c.jpg",
        "medium": "http://example.com/uploads/images/thumb_medium_c384f99eda7f19dfe78c.jpg",
        "small": "http://example.com/uploads/images/thumb_small_c384f99eda7f19dfe78c.jpg"
      }
    }
  ]
}
~~~

### Polls

One poll with two or more questions can be attached to a post. A user can participate only once. A `poll` object inside the `post` object looks like this:

~~~json
{
  "poll": {
    "guid": "83d4a140b9b20133e40c406c8f31e210",
    "participation_count": 1,
    "already_participated": true,
    "question": "Want to vote on a poll?",
    "poll_answers": [
      {
        "id": 3,
        "answer": "Yes!",
        "vote_count": 0
      },
      {
        "id": 4,
        "answer": "Sure!",
        "vote_count": 0
      },
      {
        "id": 5,
        "answer": "Hell yeah!",
        "vote_count": 1
      }
    ]
  }
}
~~~

### Location

A location can be added to a post. In addition to the visible `address`, the geo-coordinates will be drawn on a map in the web interface.

~~~json
{
  "location": {
    "address": "Example Road 14, 12345 Example City, Germany",
    "lat": 48.77,
    "lng": 9.17
  }
}
~~~

### Open Graph metadata

The first link in a post is checked for any OpenGraph metadata. If any is found, it's returned in `open_graph_object`. Note only the most useful fields of all possible OpenGraph metadata is returned.

~~~json
{
  "open_graph_object": {
    "title": "Chillhop Essentials Winter 2019, by Chillhop Music",
    "type": "album",
    "image": "https://f4.bcbits.com/img/a1333510142_5.jpg",
    "description": "24 track album",
    "url": "https://chillhop.bandcamp.com/album/chillhop-essentials-winter-2019",
    "video_url": "https://bandcamp.com/EmbeddedPlayer/v=2/album=434373916/size=large/tracklist=false/artwork=small/"
  }
}
~~~

`video_url` is validated against a list of secure providers and as such should be fine to be used as an `<iframe>` source.

## Get information about a single post

Please note that this is a very simple post. See above for additional fields that could be included in this response object.

Required API scope: `public:read` or `private:read` depending on the post visibility

### Request

~~~
GET /api/v1/posts/:post_guid
~~~

### Response

~~~json
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
}
~~~

### Errors

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |

## Publish a post

Required API scope: `public:modify` or `private:modify` depending on the post visibility

### Request

~~~
POST /api/v1/posts
~~~
~~~json
{
  "body": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus. Sed sit amet ipsum mauris. Maecenas congue ligula ac quam viverra nec consectetur ante hendrerit. Donec et mollis dolor.",
  "public": false,
  "aspects": [
    2,
    3
  ]
}
~~~

### Parameters

| Name     | Type     | Description                                                                                          |
| -------- | -------- | ---------------------------------------------------------------------------------------------------- |
| aspects  | array    | Array of aspect IDs to share this post with.                                                         |
| body     | string   | A markdown formatted body with optional [mentions](#mentions).                                       |
| location | Location | [See above](#location).                                                                              |
| photos   | array    | Array of GUIDs from pending photos that should be attached to a post. (See the Photos documentation) |
| poll     | Poll     | [See above](#polls).                                                                                 |
| public   | boolean  | Whether the post should be public or not.                                                            |

### Response

~~~json
{
  "guid": "835b3970b9c20133e40e406c8f31e210",
  "created_at": "2016-02-20T05:41:40.289Z",
  "post_type": "StatusMessage",
  "title": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a di...",
  "body": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec a diam lectus. Sed sit amet ipsum mauris. Maecenas congue ligula ac quam viverra nec consectetur ante hendrerit. Donec et mollis dolor.",
  "provider_display_name": "ExampleApp",
  "public": false,
  "nsfw": false,
  "author": {
    "guid": "f50ffc00b188013355e3705681972339",
    "diaspora_id": "alice@example.com",
    "name": "Alice Testing",
    "avatar": "http://example.com/uploads/images/thumb_medium_83abe5319ef830c2bd84.jpg"
  },
  "interaction_counters": {
    "comments": 0,
    "likes": 0,
    "reshares": 9
  }
}
~~~

### Errors

| Status code | Error reason              | TODO notes                                                                                                                            |
| ----------- | ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 403         | Failed to create the post | This is the status code of the present (non-API) status message controller. Feels sensible to change that to 422 or 400 or something. |


## Delete a post

Required API scope: `public:modify` or `private:modify` depending on the post visibility

### Request

~~~
DELETE /api/v1/posts/:post_guid
~~~

### Response

~~~
Status: 204 No Content
~~~

| Status code | Error reason                               |
| ----------- | ------------------------------------------ |
| 404         | Post with provided guid could not be found |
| 403         | Not allowed to delete the post             |
