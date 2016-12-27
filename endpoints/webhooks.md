# Webhooks

Supply URLs that will be called by GoFetch to send you notifications and job status changes. HTTP GET requests are used for all webhooks.

* [Create a webhook](#create-a-webhook)

## Create a webhook

`POST webhooks`

Returns an empty response.

### Request data

```JSON
{
  "name": "job_status",
  "url": "https://website.net/webhook"
}
```

The `name` parameter can be one of the following:

* **job_status**: sent when the state of your delivery job changes. The job ID and the new state of the job will be passed, for example:

```
https://website.net/webhook?job_id=b3131f1d&state=delivering
```

* **notification**: this webhook is called to send you a notification, same type as the iOS app users get. The job ID and the notification name will be passed, for example:

```
https://website.net/webhook?job_id=b3131f1d&notification=fetcher_approaching_dropoff
```


### cURL example

```shell
curl -d '{"name": "notification", "url": "http://webhook42.net/url"}' -H 'Content-Type: application/json' -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/webhooks
```
