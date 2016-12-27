# Webhooks

Manage your webhooks. A webhook is a URL that GoFetch uses to notify you of something, like a change in a delivery job status. HTTP GET requests are used for all webhooks.

* [Create a webhook](#create-a-webhook)

## Create a webhook

`POST webhooks/:webhook_name`

### Request data

```JSON
{
  "url": "https://website.net/webhook"
}
```

`:webhook_name` URL parameter can be one of the following:

* `job_status`. The webhook URL will be requested when the status of your delivery job changes. The job ID and the new state of the job will be passed, for example:

```
https://website.net/job_status_change?job_id=b3131f1d-b501-4f48-a31d-af8e6302540b&state=delivering
```

* `notification`. The webhook is called to send you a notification about a job. The job ID and the notification name of the job parameters will be passed, for example:

```
https://website.net/job_status_change?job_id=b3131f1d-b501-4f48-a31d-af8e6302540b&notification=fetcher_approaching_dropoff
```
