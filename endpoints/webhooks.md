# Webhooks

Supply URLs that will be called by GoFetch to send you notifications and job status changes. HTTP GET requests are used for all webhooks.

* [Create a webhook](#create-a-webhook)

## Create a webhook

`POST webhooks`

### Request data

```JSON
{
  "name": "job_status",
  "url": "https://website.net/webhook"
}
```

The `name` parameter can be one of the following:

* **job_status**. Sent when the status of your delivery job changes. The job ID and the new state of the job will be passed, for example:

```
https://website.net/webhook?job_id=b3131f1d&state=delivering
```

* **notification**. This webhook is called to send you a notification, same type as the iOS app users get. The job ID and the notification name will be passed, for example:

```
https://website.net/webhook?job_id=b3131f1d&notification=fetcher_approaching_dropoff
```
