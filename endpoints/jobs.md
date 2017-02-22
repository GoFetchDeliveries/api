# Jobs

Manage your delivery jobs.

* [Create a job](#create-a-job)
* [Show job](#show-job)
* [Show jobs](#show-jobs)

## Create a job

`POST jobs`

Creates a job that is immediately available for delivery.


### Request data

```JSON
{
  "pickup": {
    "latitude": -37.858103,
    "longitude": 144.973972,
    "full_address": "20 Loch St, St Kilda West, VIC 3182",
    "contact_name": "Amanda Woo",
    "contact_phone": "0403853234"
  },
  "dropoff": {
    "latitude": -37.812173,
    "longitude": 145.007532,
    "full_address": "9 Leslie St, Richmond, VIC 3121",
    "contact_name": "Saida Kronecker",
    "contact_phone": "040191332"
  },
  "notes_to_fetcher": "Please pickup in the ministry. Dropoff at a rickety house with a pink garden gnome."
}
```

All attributes are required except `latitude`, `longitude` and `notes_to_fetcher`. If you don't supply `latitude` and `longitude` GoFetch will geocode them from the `full_address` text field.

### Response

```JSON
{
  "job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b",
  "price_cents": 1275
}
```

The returned `job_id` will be sent as a parameter in webhooks to notify you about the job's progress.

The `price_cents` is an integer, it's the price of delivery in Australian cents. Your credit card will be charged this amount when the item is delivered.

### cURL example

```shell
curl -H 'Content-Type: application/json' \
  -H 'X-User-Email: EMAIL' \
  -H 'X-User-Token: TOKEN' \
  http://test.go-fetch.com.au/public_api/v1/jobs \
  -d @- << EOF
{
  "pickup": {
    "latitude": -37.858103,
    "longitude": 144.973972,
    "full_address": "20 Loch St, St Kilda West, VIC 3182",
    "contact_name": "Amanda Woo",
    "contact_phone": "0403853234"
  },
  "dropoff": {
    "latitude": -37.812173,
    "longitude": 145.007532,
    "full_address": "9 Leslie St, Richmond, VIC 3121",
    "contact_name": "Saida Kronecker",
    "contact_phone": "040191332"
  },
  "notes_to_fetcher": "Please pickup in the ministry. Dropoff at a rickety house with a pink garden gnome."
}
EOF
```

## Show job

`GET jobs/:job_id`

Returns information about a delivery job.

### Response

```JSON
{
  "id": "e2c5e27d-fb56-498c-b5f5-ed70adf64be6",
  "state": "delivered",
  "notes_to_fetcher": "Please pickup in the ministry. Dropoff at a rickety house with a pink garden gnome.",
  "price_cents": 980,
  "created_at": "2016-01-22T03:12:01.607+11:00",
  "picked_up_at": "2017-02-22T09:46:01.607+11:00",
  "delivered_at": "2020-01-17T09:46:01.607+11:00",
  "fetcher": {
    "name": "Magna Perkovitch",
    "phone": "0303111222"
  },
  "pickup": {
    "latitude": -37.813068,
    "longitude": 144.995311,
    "full_address": "52 Lennox St, Richmond VIC 3121",
    "contact_name": "Amanda Woo",
    "contact_phone": "0403853234"
  },
  "dropoff": {
    "latitude": -37.858191,
    "longitude": 144.973841,
    "full_address": "20 Loch St, St Kilda West, VIC 3182",
    "contact_name": "Saida Kronecker",
    "contact_phone": "040191332"
  }
}
```

Attribute `fetcher` is empty if the item has not been picked up yet. The `state` attribute contains the current [state of the job](https://github.com/GoFetchDeliveries/api-v1/blob/master/job_states.md).

### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/jobs/b3131f1d-b501-4f48-a31d-af8e6302540b
```

## Show jobs

`GET jobs`

Returns all jobs starting with most recent ones. This endpoint is [paginated](https://github.com/GoFetchDeliveries/api-v1/blob/master/pagination.md).

### Response

```JSON
{
  "jobs": [
    {
      "id": "e2c5e27d-fb56-498c-b5f5-ed70adf64be6",
      "state": "delivered",
      "notes_to_fetcher": "Please pickup in the ministry. Dropoff at a rickety house with a pink garden gnome.",
      "price_cents": 980,
      "created_at": "2016-01-22T03:12:01.607+11:00",
      "picked_up_at": "2017-02-22T09:46:01.607+11:00",
      "delivered_at": "2020-01-17T09:46:01.607+11:00",
      "fetcher": {
        "name": "Magna Perkovitch",
        "phone": "0303111222"
      },
      "pickup": {
        "latitude": -37.813068,
        "longitude": 144.995311,
        "full_address": "52 Lennox St, Richmond VIC 3121",
        "contact_name": "Amanda Woo",
        "contact_phone": "0403853234"
      },
      "dropoff": {
        "latitude": -37.858191,
        "longitude": 144.973841,
        "full_address": "20 Loch St, St Kilda West, VIC 3182",
        "contact_name": "Saida Kronecker",
        "contact_phone": "040191332"
      }
    }
  ]
}
```


### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/jobs
```

### Filtering jobs

One can filter the jobs by state or creation date by adding `state`, `created_from` or `created_to` URL parameters. For example:

```
http://test.go-fetch.com.au/public_api/v1/jobs?state=pending&created_from=2019-01-22&created_to=2020-06-01
```


