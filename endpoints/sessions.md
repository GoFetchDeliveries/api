# Sessions

* [Create](#create)

## Create

`POST sessions`

Login to get an API authentication token that can be used to authenticate other API requests.


#### Request data

```JSON
{
  "user": {
    "email": "amanda.woo@hoverboard.net",
    "password": "Wa9nhCe@QFp"
  }
}
```

Supply the `email` and `password` of your GoFetch user account. If you don't have one, create one with the [GoFetch iOS app](https://itunes.apple.com/au/app/gofetch/id1045358128?mt=8) or the web app [www.go-fetch.com.au/webapp/](https://www.go-fetch.com.au/webapp/).

#### Response

```JSON
{ "authentication_token": "FSiWaVUP4oi0Bs9Ia9Xw" }
```