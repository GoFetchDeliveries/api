# Webhooks

Manage your webhooks. A webhook is a URL that GoFetch calls when to notify you of something, like a change in a delivery job status.

* [Update job status webhook](#create-a-webhook)

## Update job status webhook

`PATCH webhooks/job_status`

### Request data

```JSON
{
  "url": "https://website.net/job_status_change"
}
```

Supply a URL or nil if you want to remove the webhook. When a state of the job changes, GoFetch will send a GET HTTP request to the supplied URL supplying the job id and the state of the job. For exammple:

```
https://website.net/job_status_change?job_id=b3131f1d-b501-4f48-a31d-af8e6302540b&state=delivering
```