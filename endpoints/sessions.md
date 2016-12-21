# Sessions

## Create

`POST sessions`

Supply your GoFetch email and password to get your API authentication token. The token can then be used to authenticate other API requests.


### Request data

```JSON
{
  "user": {
    "email": "amanda.woo@hoverboard.net",
    "password": "Wa9nhCe@QFp"
  }
}
```

Supply the `email` and `password` of your GoFetch user account. If you don't have one, it can be created in the [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/).

### Response

```JSON
{ "authentication_token": "FSiWaVUP4oi0Bs9Ia9Xw" }
```

The returned authentication token is passed in the `X-User-Token` HTTP header to access other API endpoints. Authentication token will not change. The token needs to be stored securely.

### Curl example

```shell
curl -H 'Content-Type: application/json' \
  -d '{"user": {"email": "your@email.com", "password": "@9LFpShfE$yA"}}' \
  https://go-fetch.com.au/public_api/v1/sessions
```