# Jobs

Your delivery jobs.

* [Create a job](#create-job)

## Create job

Creates a delivery job that is immediatelly available to fetchers.

`POST /jobs`

#### Example request data

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
  "notes_to_fetcher": "Pickup in a restaurant at the bar. Dropoff: purple house with a big tree."
}