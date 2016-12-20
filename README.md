# GoFetch API v1 documentation

Welcome to GoFetch API. This API allows to create delivery jobs and get notified of their progress.

## Sending requests

All requests are sent to `https://go-fetch.com.au/public_api/v1/`.

## Request Headers

| Header | Description |
| --- | --- |
| `X-User-Email: [Your GoFetch email]` | Used for authentication |
| `X-User-Token: [Your access token]` | Used for authentication |
| `Content-Type: application/json` | Required for POST requests |

## Authentication

Anyone with a GoFetch user account can access GoFetch API.

1. First, create an account using either [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/). You will use the login email address in the `X-User-Email` HTTP header.

1. Request your access token by [creating an issue](/GoFetchDeliveries/api-v1/issues/new) and mentioning your email.

