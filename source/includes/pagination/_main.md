# Pagination

All top-level API resources have support for bulk fetches, these list API methods share a common structure, taking at least these two common query parameters:

### Page

Specify the page of results to return, `page= <number>`, for example:

<span style="text-align: center;display: block;">`https://www.api.dashboard.com/v2/users?page=2`</span>

By retrieving `/v2/users?page=2`, and so on, you may access every available post through the API, one page at a time.

### Per page

Specify the number of records to return in one request, `per_page= <number>`, specified as an integer, for example:

<span style="text-align: center;display: block;">`https://www.api.dashboard.com/v2/users?per_page=1`</span>

Will return only one user in the collection, as go on at each page exists


<aside class="notice">You can combine these parameters, to handle the response data in the most personal and efficient way that you find.</aside>


### Response info

Any API answer that contains multiple resources, will have a meta information, where it will teach the necessary information to know the current state of the listing and paging

```Javascript
"meta": {
    "pagination": {
        "per_page": 25,
        "current_page": 1,
        "total_pages": 1,
        "total_objects": 120
    }
  }
```

Parameter |Description
--------- | -----------
per_page  | How many objects have the response data
curret_page | What page are you currently see
total_page | Total of page for that endpoint
total_objects | Total objects that have the selected endpoint


