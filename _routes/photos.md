---
title: Photos
---

{% include toc.md %}

**See also:**
  * [Users (Get photos for a single user)](users.html#get-photos-by-a-single-user)

## Get photos uploaded by the current user

Required API scope: `public:read`

Optional API scope: `private:read`

### Request

~~~
GET /api/v1/photos
~~~

### Response

~~~json
[
  {
    "guid": "0a992a10b9db0133e40e406c8f31e210",
    "post": "b50abae085ff0134029244b301d53d2d",
    "created_at": "2016-11-06T03:43:03.382Z",
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
    "post": "c32c73a085ff0134029244b301d53d2d",
    "created_at": "2016-11-06T03:42:27.807Z",
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

## Get information about a single photo

Required API scope: `public:read` or `private:read` depending on the photo visibility

### Request

~~~
GET /api/v1/photos/:photo_guid
~~~

### Response

~~~json
{
  "guid": "114999c0b9db0133e40e406c8f31e210",
  "post": "c32c73a085ff0134029244b301d53d2d",
  "created_at": "2016-11-06T03:42:27.807Z",
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
~~~

## Upload photo

`pending` might get used if the uploaded photo is intended to get used as a post attachment. Do not upload *unused* images since pending uploads might get deleted after some timeout without further warnings.

Required API scope: `public:modify` or `private:modify` depending on the photo visibility

### Request

~~~
POST /api/v1/photos
~~~

Photo file as POST multipart payload with a matching mime-type (use `application/octet-stream` if in doubt).

### Optional parameters

| Name                | Type    | Description                                                                 |
| ------------------- | ------- | --------------------------------------------------------------------------- |
| pending             | boolean | Set `true` if the photo should not be published but stored for later.       |
| set_profile_picture | boolean | Set `true` if the uploaded photo should be used as the new profile picture. |

### Response

~~~json
{
  "guid": "114999c0b9db0133e40e406c8f31e210",
  "post": "c32c73a085ff0134029244b301d53d2d",
  "created_at": "2016-11-06T03:42:27.807Z",
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
~~~

## Delete a photo

Note that deleting a photo will not remove items where it was attached to, like posts.

Required API scope: `public:modify` or `private:modify` depending on the photo visibility

### Request

~~~
DELETE /api/v1/photos/:photo_guid
~~~

### Response

~~~
Status: 204 No Content
~~~
