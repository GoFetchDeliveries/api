# Jobs

Manage your delivery jobs.

* [Create a job](#create-job)

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
  "notes_to_fetcher": "Pickup in the ministry. Dropoff: a rickety house with a pink garden gnome."
}
```

### Response

```JSON
{
  "job_id": "b3131f1d-b501-4f48-a31d-af8e6302540b",
  "price_cents": 1275
}
```

The returned `job_id` will be sent as a parameter in webhooks when a status of the deliver changes.

The `price_cents` is an integer (Australian cents). Your credit card will be charged this amount when then item is delivered.
