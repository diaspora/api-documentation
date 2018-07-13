---
title: Response codes and errors
---

If an error occurs during the handling of an API request, the server will respond with an adequate HTTP status code alongside a JSON body describing the error in more detail.

## Error Response

~~~json
{
  "code": 404,
  "message": "Requested entity wasn't found"
}
~~~

## Error List

| Status code | Status message                          |
| ----------- | --------------------------------------- |
| 400         | Wrong request paramater                 |
| 401         | The API request requires authorizations |
| 403         | Unauthorized                            |
| 404         | Requested entity wasn't found           |
| 409         | Entity already exists                   |
| 422         | Validation errors                       |
