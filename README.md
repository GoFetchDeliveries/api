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

