# Job status webhook

Supply URLs that will be called by GoFetch to notify you when the status of a job changes.

* [Show](#show-the-job-status-webhook)
* [Update](#update-the-job-status-webhook)
* [Remove](#remove-the-job-status-webhook)
* [Test](#test-the-job-status-webhook)


## Show the job status webhook

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




## Update the job status webhook

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




## Remove the job status webhook


`DELETE webhooks/job_status`

Remove the job_status webhook if you no longer with to receive the notifications.

### cURL example


```shell
curl -X "DELETE" -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks/job_status
```





## Test the job status webhook


`POST webhooks/job_status/test`

Sends a test HTTP request to your webhook URL. This can be useful for debugging your API integration.

### Request data

Supply the *job_id* and *job_status* values that will be used in the webhook URL. This request will not change the status of the job. It will pretend that the status was changed by sending you a notification with this status.

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

GoFetch server will call back your job status webhook URL with the supplied parameters.
