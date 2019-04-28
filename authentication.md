---
title: Authentication
---

diaspora\* supports the required set of [OpenID Connect Core 1.0][connect] using either the Authorization Code Flow or the Implicit Flow. OpenID endpoints can be discovered using [OpenID Connect Discovery 1.0][discovery]. Since diaspora\* is decentralized and a manual application registration on a single node is not sufficient, diaspora\* supports [OpenID Connect Dynamic Client Registration 1.0][client-registration].

Please note that, although a brief description about the authentication flow will follow, implementations should refer to the official OpenID specification documents when implementing the protocol or use a supported library.

## OpenID endpoint discovery

OpenID endpoints can be discovered using [OpenID Connect Discovery 1.0][discovery]. In addition to all required endpoints, the response will also include available scopes and other information.

### Request

~~~
GET /.well-known/openid-configuration
~~~

### Response

~~~json
{
  "authorization_endpoint": "http://example.com/api/openid_connect/authorizations/new",
  "claims_parameter_supported": true,
  "claims_supported": [
    "sub",
    "name",
    "nickname",
    "profile",
    "picture"
  ],
  "id_token_signing_alg_values_supported": [
    "RS256"
  ],
  "issuer": "http://example.com/",
  "jwks_uri": "http://example.com/api/openid_connect/jwks.json",
  "registration_endpoint": "http://example.com/api/openid_connect/clients",
  "request_object_signing_alg_values_supported": [
    "none"
  ],
  "request_parameter_supported": true,
  "request_uri_parameter_supported": true,
  "response_types_supported": [
    "id_token",
    "id_token token",
    "code"
  ],
  "scopes_supported": [
    "openid",
    "contacts:read",
    "contacts:modify",
    "conversations",
    "email",
    "interactions",
    "notifications",
    "private:read",
    "private:modify",
    "public:read",
    "public:modify",
    "profile",
    "profile:modify",
    "profile:read_private",
    "tags:read",
    "tags:modify"
  ],
  "subject_types_supported": [
    "public",
    "pairwise"
  ],
  "token_endpoint": "http://example.com/api/openid_connect/access_tokens",
  "token_endpoint_auth_methods_supported": [
    "client_secret_basic",
    "client_secret_post",
    "private_key_jwt"
  ],
  "userinfo_endpoint": "http://example.com/api/openid_connect/user_info",
  "userinfo_signing_alg_values_supported": [
    "none"
  ]
}
~~~

## Client registration

Since diaspora\* is decentralized and a manual application registration on a single node is not sufficient, diaspora\* supports [OpenID Connect Dynamic Client Registration 1.0][client-registration] to enable applications to automatically register on yet unknown pods.

The registration endpoint can be discovered as mentioned above. The response includes the `client_id` and `client_secret` required for further communication with OpenID as well as other information. Please check [the specification][client-registration] for an overview of all available fields and detailed explanations for all response fields.

### Request

~~~
POST http://example.com/api/openid_connect/clients
~~~
~~~json
{
  "client_name": "ExampleApp",
  "redirect_uris": [
    "http://example.com/"
  ]
}
~~~

### Response

~~~json
{
  "application_type": "web",
  "client_id": "c609e9dbb8a4a36d5a3abb99ef5cb2b7",
  "client_name": "ExampleApp",
  "client_secret": "275de5fa9916f3789190a95cd12ee3a9ed56a207657fb537b011327d6707e443",
  "client_uri": null,
  "contacts": null,
  "created_at": "2016-02-11T23:56:27.566Z",
  "grant_types": null,
  "id": 4,
  "jwks": null,
  "jwks_uri": null,
  "logo_uri": null,
  "policy_uri": null,
  "ppid": false,
  "redirect_uris": [
    "http://example.com/"
  ],
  "response_types": null,
  "sector_identifier_uri": null,
  "token_endpoint_auth_method": null,
  "tos_uri": null,
  "updated_at": "2016-02-11T23:56:27.566Z",
  "user_id": null
}
~~~

## Requesting an access token

There are two main ways to request an access token. Specifying the entire flow is beyond the scope of this document, so please refer to the actual specification documents. The two main request flows are:

* The [*Authorization Code Flow*][authcode-flow] which is usually used by native client applications. After authorization, the client receives an authorization code, which can then exchange it for an access token using defined endpoints.
* The [*Implicit Flow*][implicit-flow] which is usually used by browser-based applications. After authorization, the access token is directly returned to the endpoint via the users user agent.

Each access token is requested with a specific set of permissions according to the OpenID Connect specifications which are called "scopes". You can read more about the scopes specified and implemented in diaspora* at the ["Scopes"][scopes] section of this documentation.

## Using access tokens

There are multiple ways of transmitting access tokens:

* as a `GET` parameter: `https://example.com/api/v0/example?access_token=[access token]`
* as an `application/x-www-form-urlencoded` parameter: `access_token=[access token]`
* inside the request header: `Authorization: Bearer [access token]`

## Authentication errors

All API nodes require authentication. If no token or an invlaid token is supplied, the API will always return `401 Unauthorized`.

If the client tries to access an OAuth scope that was not part of the authorization, the API will return `403 Forbidden`.

## Additional information and specifications

* [OpenID Connect Core 1.0][connect] specification including flow descriptions
* [OpenID Connect Discovery 1.0][discovery] specification
* [OpenID Connect Dynamic Client Registration 1.0][client-registration] specification

[authcode-flow]: http://openid.net/specs/openid-connect-core-1_0.html#CodeFlowAuth
[client-registration]: http://openid.net/specs/openid-connect-registration-1_0.html
[connect]: http://openid.net/specs/openid-connect-core-1_0.html
[discovery]: http://openid.net/specs/openid-connect-discovery-1_0.html
[implicit-flow]: http://openid.net/specs/openid-connect-core-1_0.html#ImplicitFlowAuth
[scopes]: {{ site.baseurl }}/scopes.html
