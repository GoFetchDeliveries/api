# Jobs

Manage your delivery jobs.

* [Create a job](#create-a-job)
* [Show a job](#show-job)

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

All attributes are required except `notes_to_fetcher`.

### Response

```JSON
{
  "job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b",
  "price_cents": 1275
}
```

The returned `job_id` will be sent as a parameter in webhooks when a status of the delivery changes.

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

Returns information about a delivery job. It can be useful for checking the current state of the job. If the item has been picked up this request will also return the name and phone of the fetcher.

### Response

```JSON
{
  "state": "delivering",
  "fetcher_name": "Kate Eriksson",
  "fetcher_phone": "0243934923"
}
```
Parameters `fetcher_name` and `fetcher_phone` are empty if the item has not been picked up yet.

### cURL example

```shell
curl -H 'X-User-Email: EMAIL' -H 'X-User-Token: TOKEN' http://test.go-fetch.com.au/public_api/v1/jobs/b3131f1d-b501-4f48-a31d-af8e6302540b
```

