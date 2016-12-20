# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress.

## Sending requests

Please send requests to `https://go-fetch.com.au/public_api/v1/`.

## Request Headers

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Authentication |
| `X-User-Token: [Your access token]` | Authentication |
| `Content-Type: application/json` | Required for POST requests |

## Authentication

Anyone with a GoFetch user account can access GoFetch API.

1. First, create an normal user account using either [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/).

1. Request your access token by [creating an issue](https://github.com/GoFetchDeliveries/api-v1/issues/new) and mentioning your GoFetch login email. We will email you your API access token.

1. Send an API request and supply both your email and token in `X-User-Email` and `X-User-Token` HTTP headers.

#### Test access to API


```bash
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' https://go-fetch.com.au/public_api/v1/hello_world
```

## API endpoints

* [Hello World](endpoints/hello_world.md)
* [Jobs](endpoints/jobs.md)

