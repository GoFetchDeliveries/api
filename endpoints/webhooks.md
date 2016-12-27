# Webhooks

Manage your webhooks. A webhook is a URL that GoFetch calls to notify you of something, like a change in a delivery job status.

* [Update job status webhook](#create-a-webhook)

## Update job status webhook

`POST webhooks/job_status`

### Request data

```JSON
{
  "url": "https://website.net/job_status"
}
```

Supply a URL that will be requested when the status of your delivery job changes. GoFetch will send a GET HTTP request to the supplied URL supplying the job ID and the new state of the job. For example:

```
https://website.net/job_status_change?job_id=b3131f1d-b501-4f48-a31d-af8e6302540b&state=delivering
```
