# Job status webhook

Supply URLs that will be called by GoFetch to notify you when the status of a job changes. HTTP GET requests are used for all webhooks.

* [Get the webhook](#get-the-webhook)
* [Update the webhook](#update-the-webhook)
* [Delete the webhook](#delete-the-webhook)


## List webhooks

`GET webhooks/job_status`

Returns your job status webhook.


### Response

```JSON
{
  "url": "https://website.net/example"
}
```

### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```


## Create a webhook

`PUT webhooks/job_status`

Returns empty response.

### Request data


```JSON
{
  "url": "https://website.net/example"
}
```

Save the URL for the job status web hook. GoFetch will send GET request to this URL supplying `job_id` and `job_status` URL parameters, for example:

```
https://website.net/webhook?job_id=b3131f1d&job_status=fetcher_approaching_dropoff
```


### cURL example


```shell
curl -d '{"url": "http://webhook42.net/example"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```


## Remove webhook
