# GoFetch API v1 documentation

Welcome to GoFetch API. Anyone with a GoFetch user account can access GoFetch API. This API allows to create delivery jobs and get notified of their progress.

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)
* [Sessions](endpoints/sessions.md)


## Getting started in the test environment

API requests to test server are sent to

```
http://test.go-fetch.com.au/public_api/v1/
```

1) First, create a user account in the staging [web app](http://www.go-fetch.com.au/webappstaging) and add a card with a test number `4242 4242 4242 4242`.

2) Next, send [create a session](endpoints/sessions.md#create) request with your GoFetch email and password and get your API authentication token. This only needs to be done once when you setup your API integration, since the authentication token does not change. You can then store your authentication token securely and use it for all other API requests in the future.

3) Check that your authentication works with a [hello world](endpoints/hello_world.md) request.

```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1
```

4) Finally, send [create a job](endpoints/jobs.md) request and supply your email and authentication token in `X-User-Email` and `X-User-Token` HTTP headers.


## API request haders

Please supply the following headers with your HTTP requests.

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

## Working with production server

API requests to products server are sent to

```
https://go-fetch.com.au/public_api/v1/
```

1) Create a live GoFetch user account with the production [web app]
(https://www.go-fetch.com.au/webapp/) or the [iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) and add a valid credit card. Your credit card will be charged when your jobs are delivered.

2) Retrieve your production authentication token with [create a session](endpoints/sessions.md#create) request.

3) Check that your authentication works with [hello world](endpoints/hello_world.md) request.

4) Finally, send your job creation API requests to the production server.

## Feedback is welcome

If you have a question or notice a problem with the API or this documentation feel free to submit an issue or a pull request.

