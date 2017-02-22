# Pagination

Endpoints that return array of objects also include pagination data. For example:

```JSON
{
  "meta": {
    "pagination": {
      "current_page": 2,
      "next_page": 3,
      "prev_page": 1,
      "total_pages": 5,
      "total_objects": 120
    }
  }
}
```


## Page size

By default, we return 25 objects per page. You can change the page size by including a `per_page` URL parameter:

```
http://test.go-fetch.com.au/public_api/v1/jobs?per_page=50
```

## Viewing other pages

You can view other pages by adding a `page` URL parameter:

```
http://test.go-fetch.com.au/public_api/v1/jobs?page=2
```