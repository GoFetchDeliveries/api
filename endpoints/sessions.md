# Sessions

* [Create](#create)

## Create

`POST sessions`

Login to get an API authentication token that can be used to authenticate other API requests.


#### Example request

```JSON
{
  "user": {
    "email": "amanda.woo@hoverboard.net",
    "password": "Wa9nhCe@QFp"
  }
}
```

#### Example response

```JSON
{ "authentication_token": "FSiWaVUP4oi0Bs9Ia9Xw" }
```