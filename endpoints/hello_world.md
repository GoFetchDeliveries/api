# Hello World

Simply returns 'Hello world' message. This endpoint can be used to check access to GoFetch API.

`GET hello_world`


### Response

```JSON
{ "hello": "world" }
```


### cURL example

```shell
curl -H 'X-User-Email: EMAIL' \
  -H 'X-User-Token: TOKEN' \
  https://go-fetch.com.au/public_api/v1/hello_world
```


