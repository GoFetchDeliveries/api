# Jobs

Manage your delivery jobs.

* [Create a job](#create-job)

## Create a job

`POST jobs`

Creates a job that is immediately available for delivery.


### Request data

```JSON
{
  "job": {
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
}
```
