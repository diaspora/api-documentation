---
title: Access scopes
---

The diaspora* API features access scopes (or just 'scopes') in order to implement resource access management for API clients.

Scopes are part of [OAuth 2.0 specification][oauth2] which is a base for [OpenID Connect Core 1.0][connect] implemented by diaspora*.

When the API client requests an access token it sends the list of scopes it wants to get access to according to the selected authorization flow (see ["Authentication"][authentication]).

Granted scopes may differ from what was requested by the client.

[OpenID Connect Core 1.0][connect] defines a few scopes which are specific for getting the authorized user information. API clients must include the `openid` scope to the scope request list. The `openid` scope gives access to using OpenID Connect authentication and if missing the API authentication will fail.

diaspora* also supports the `profile` and `email` scopes according to [OpenID Connect Core 1.0][connect-scopes].

Other scopes are diaspora* API specific. All scopes besides `openid` are optional.

There is a special case scope `public:read` which is always granted even if not explicitly required. The `public:read` scope gives access to data which is public anyway and sometimes available even with no authorization at all, so it is available to every authorized client too, there is no reason to allow opt out for it.

Also it is possible that scopes depend on other scopes. It means that requesting and granting of a specific scope is only possible along with the scope it depends on. For example the `private:read` and `private:modify` scope which grants reading private posts permission depends on `contacts:read` scope.

Each API endpoint requires at least one scope to be granted. If the access token used for making a request wasn't granted the scope of the respective endpoint then the response will have a `403` status code and no actual content.

In this specification each endpoint description contains the name of the scope required to access this endpoint. Most of the time this is only one scope. However for some types of data like posts the required scope depends on the data visibility (public vs private). Besides this, for some endpoints, like streams the dataset in response depends on the set of granted scopes.

## Scopes

### contacts:read

This scope gives access to the following requests:
* Read aspect list
* Read aspects membership
* Read private user profiles of contacts
* Read contacts of contacts when allowed by contact's aspect setting
* User search will include contacts who are hidden from public search

### contacts:modify

This scope gives access to the following requests:
* Add new aspects
* Rename aspects and change aspects properties
* Delete aspects
* Add/remove person to/from aspects

### conversations

This scope gives access to private messaging, i.e. the following requests:
* Create conversations
* Send private messages

### email

This scope is defined by the OpenID Connect spec. It allows reading user's own email address using the UserInfo route or from the ID Token.

### interactions

This scope gives access to the following requests:
* Create/delete comments
* Report posts/comments
* Post/remove likes
* Subscribe/mute posts
* Hide posts from streams
* Voting in polls

### notifications

This scope gives access to reading notifications.

### openid

This scope is defined by the OpenID Connect spec. This is a mandatory scope. It allows using OpenID Connect authentication.

### private:read

This scope gives access to the following requests:
* Read private posts
* Read private posts interactions (likes, comments)
* Reading streams: main stream, aspects stream, mention stream, activity stream, liked stream, commented stream

Note: the `private:read` scope depends on `contacts:read` and can only be granted when `contacts:read` is granted too.

### private:modify

This scope gives access to the following requests:
* Create private posts
* Post photos privately
* Delete private posts
* Delete private photos

Note: the `private:modify` scope depends on `contacts:read` and can only be granted when `contacts:read` is granted too.

### public:read

This scope gives access to the following requests:
* Read public profiles of users
* Perform search among publicly searchable profiles
* Read public posts
* Read reshares
* Read public posts interactions (likes, comments)

Note: The `public:read` scope is granted to any authorized entity even when not explicitly requested.

### public:modify

This scope gives access to the following requests:
* Create public posts/reshares
* Post photos
* Delete public posts
* Delete public photos

### profile

This scope is defined by the OpenID Connect spec. It allows reading user claims (user properties). Claims are read using UserInfo route or from the ID Token.

User claims as defined by the OpenID Connect are somewhat similar to a users own profile data. Generally this scope means "Allow reading a user's own profile". Besides user claims defined by the standard this scope also gives access to the "read own profile" diaspora* API endpoint.

The `profile` scope gives read access to the following claims supported by diaspora*:

| claim      | meaning                                             |
| ---------- | --------------------------------------------------- |
| name       | Full name                                           |
| nickname   | The left part of diaspora handle before `@` sign    |
| profile    | User's profile URL address                          |
| picture    | User avatar URL address                             |
| gender     | Gender profile field                                |
| birthdate  | Birth date profile field                            |
| locale     | UI language selection specified in account settings |
| updated_at | Date of last profile edit                           |

### profile:modify

This scope gives access to updating a user's own profile

### tags:read

This scope gives access to reading tag followings and reading tags stream.

### tags:modify

This scope gives access to creation and deletion of tag followings.


[connect]: http://openid.net/specs/openid-connect-core-1_0.html
[connect-scopes]: https://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims
[oauth2]: https://tools.ietf.org/html/rfc6749#section-3.3
[authentication]: authentication.html
