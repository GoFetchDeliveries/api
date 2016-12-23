# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress. There are two API servers that you can send HTTP requests to.

* **Test**: `http://test.go-fetch.com.au/public_api/v1/`

* **Production**: `https://go-fetch.com.au/public_api/v1/`

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)


## Getting started

Anyone with a GoFetch user account can access GoFetch API. Here is how to send API requests to the test API server.

1) First, create a user account in the staging [web app](http://www.go-fetch.com.au/webappstaging) and add a card with a test number `4242 4242 4242 4242`.

2) Next, send [create a session](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done once when you setup your API integration, since the authentication token does not change. You can then store your authentication token securely and use it for all other API requests in the future.

3) Check that your authentication works with a `hello_world` request.

```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1
```

4) Finally, send a [create a job](endpoints/jobs.md) request and supply your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers.


## API request haders

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your authentication token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Errors

Error responses contains a single `error` attribute with a text description:

```JSON
{"error": "You need to sign in or sign up before continuing."}
```

## HTTP status codes

GoFetch API returns the following status codes:

| Code | Description |
| --- | --- |
| 2xx Success | Request has succeeded |
| 401 Unauthorized | Authentication error |
| 422 Unprocessable Entity | Request contains incorrect parameters |

## Feedback is welcome

If you have a question or notice a problem with the API or this documentation feel free to submit an issue or a pull request.

