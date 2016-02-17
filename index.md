---
---

{% include warning_box.html
   title="This is API fiction!"
   content="This document aims to provide an <strong>API proposal</strong> as a base for discussion for further progress towards a stable and well-designed API for diaspora*. Please note that this is only a proposal and none of the endpoints are implemented at the moment."
%}

# diaspora\* API documentation

diaspora\* aims to offer a sophisticated API for most social networking applications. Because of our decentralized nature, some things might be a little bit different than at most other API implementations, especially regarding authentication. If you experience any issues, feel free to [get in touch][communication] with us.

## Media Types

Currently, the API only supports JSON data exchange, so all requests should have their `accept` header set correctly:

~~~
Accept: application/json
~~~

If, for some reason, setting the `accept` header is not possible, adding `.json` to the call url will also work.

Unless otherwise noted, bodies submitted via `POST` requests should be JSON encoded. Parameters to `GET` routes are simple request URL variables.

## API support

This document specifies API Version 1, which is supported by diaspora\* release X and newer. Version discovery should be done using [nodeinfo][nodeinfo] prior to making any requests to ensure the endpoints are available. If a compatible diaspora\* version was detected once, it is safe to assume a pod will stay compatible.

[communication]: https://wiki.diasporafoundation.org/How_we_communicate
[nodeinfo]: http://nodeinfo.diaspora.software/
