## Search guest wifi users

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/guest_wifi/users?age_range='19-25'&date_from=2019-01-09&dato_to=2019-02-09")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/guest_wifi/users?age_range='19-25'&date_from=2019-01-09&dato_to=2019-02-09 \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/places/13b1be27-0d31-4dff-aa11-27ec1d636ab3/guest_wifi/users?age_range='19-25'&date_from=2019-01-09&dato_to=2019-02-09",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD",
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response example:

```json
{
    "data": [
        {
            "id": "a857a211-a2b9-41b7-9af2-93b81d3b6f93",
            "type": "guest_wifi_user",
            "attributes": {
                "name": "Test name 1",
                "email": "testname1@gmail.com",
                "birthday": "1994-08-06",
                "visit_times": 3,
                "last_seen": "2019-01-30T20:04:54.000Z",
                "provider": "openmesh"
            }
        },
        {
            "id": "65b33111-8871-44ae-ae59-93b81d3b6f93",
            "type": "guest_wifi_user",
            "attributes": {
                "name": "Test name 2",
                "email": "testname2@yahoo.com",
                "birthday": "1964-12-12",
                "visit_times": 14,
                "last_seen": "2019-01-31T18:07:02.000Z",
                "provider": "openmesh"
            }
        }
    ],
    "meta": {
        "pagination": {
            "per_page": 25,
            "current_page": 1,
            "total_pages": 1,
            "total_objects": 2
        }
    }
}
```

Allows obtaining a list of guest wifi users which the user can access and search with the necessary params for query the search.

### HTTP Request

`GET https://api.flameanalytics.com/v2/places/:place_id/guest_wifi/users?age_range='19-25'&date_from=2019-01-09&dato_to=2019-02-09`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | String | Identification of a place
age_range | String | Indicates the age range
visit_times | Number | Indicates the numer of visits od the users
date_from | String | **ISO 8601**, has visits from that date
date_to | String | **ISO 8601**, has visits up to that date
registered_at_from | String | **ISO 8601**, was registered from that date
registered_at_to | String | **ISO 8601**, was registered up to that date
last_visit_at_from | String | **ISO 8601**, has the last visit from that date
last_visit_at_to | String | **ISO 8601**, has the last visit up to that date
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page


### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a guest wifi user
type | String | Type of the retrieve object
attributes | Object | Attributes of that guest wifi user
name | String | Name of the retrieve object
email | String | Email of the retrieve object
birthday | String | Birthday of the guest wifi user
visit_times | Number | Number of visit times
last_seen | String | **ISO 8601**, date of last visit
provider | String | Provider of the retieve object