# Jobs

Manage your delivery jobs.

* [Sign in](#sign-in)

## Sign in

`POST users`

Signs in using email and password and returns an authentication token that should be used in the Authorization header.

### Request url

https://go-fetch.com.au/api/v1/jobs/calculate.json?distance_meters=802&seconds=403

### Query Parameters

##### distance_meters

A primary parameter used to calculate the delivery price.

##### seconds (Deprecated)
*Deprecated. Do not use it.*

If distance_meters is not provided, the job will be calculated based on the amount of time it will take to deliver it.

### Response

```JSON
{
  "price_cents": 966
}
```
