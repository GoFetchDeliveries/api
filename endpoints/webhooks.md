🚧 🚧 🚧 Under construction 🚧 🚧 🚧
 
# Webhooks

Supply URLs that will be called by GoFetch to norify you when the status of a job changes. HTTP GET requests are used for all webhooks.

* [Create a webhook](#create-a-webhook)
* [List webhooks](#list-webhooks)
* [Remove webhook](#remove-webhook)
* [Test a webhook](#test-a-webhook)


## List webhooks

`GET webhooks`

Returns your webhooks.

### Response

```JSON
{
  "webhooks": [
    {
      "name": "job_status",
      "url": "https://website.net/notify"
    }
  ]
}
```

### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks
```




## Create a webhook

`POST webhooks`

Creates a webhook, returns empty response.

### Request data

```JSON
{
  "name": "job_status",
  "url": "https://website.net/webhook"
}
```

Currently there is only one accepted value for the `name` parameter:

* **job_status**: sent when the status of your delivery job changes. The job ID and the job status will be passed, for example:

```
https://website.net/webhook?job_id=b3131f1d&job_status=fetcher_approaching_dropoff
```



### cURL example

Create a *job_status* webhook:

```shell
curl -d '{"name": "job_status", "url": "http://webhook42.net/url"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks
```




## Remove webhook

`DELETE webhooks/:name`

Removes a webhook with the specified name. The `:name` parameter should be **job_status**.

### cURL example

Remove the *job status* webhook:

```shell
curl -X "DELETE" -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```


## Test a webhook

`POST webhooks/test/:name`

Sends a test HTTP request to your webhook URL.

### Request data

Supply the *job_id* and *job_status* values that will be used in the webhook URL.

```JSON
{
  "job_id": "b3131f1d",
  "job_status": "fetcher_approaching_dropoff"
}
```

### cURL example

Tests the *job status* webhook. 

```shell
curl -d '{"job_id": "b3131f1d", "job_status": "fetcher_approaching_dropoff"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```

GoFetch server will call back your *job_status* webhook URL with the supplied parameters.
