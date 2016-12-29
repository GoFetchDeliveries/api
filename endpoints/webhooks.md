🚧 🚧 🚧 Under construction 🚧 🚧 🚧
 
# Webhooks

Supply URLs that will be called by GoFetch to norify you when the status of a job changes. HTTP GET requests are used for all webhooks.

* [Create a webhook](#create-a-webhook)
* [List webhooks](#list-webhooks)
* [Remove webhook](#remove-webhook)


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

The `name` parameter can be one of the following:

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

