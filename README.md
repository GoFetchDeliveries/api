# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress. 

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)

## Getting started

Anyone with a GoFetch user account can access GoFetch API.

1. First, create an normal user account using either [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/).

1. Next, send a [POST sessions](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done only once when you setup your API integration, since the authentication token does not change. You can then store your authentication token securely and use it for all other API requests in the future.

1. Finally, supply both your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers when calling all other GoFetch API endpoints.

#### Test access to the API

```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' https://go-fetch.com.au/public_api/v1/hello_world
```

## API requests

API requests are sent to `https://go-fetch.com.au/public_api/v1/` with the following headers:

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your authentication token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Errors

Errors responses contains a single `error` attribute with a text description:

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

