## Presence

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio",
  "method": "GET",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Token token=nugyUyuzq6nqvm_uiesD"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

> Response JSON (Aggregated):

```json
{
    "data": [
        {
            "id": "aa5f56e9-dd1a-4c57-ba43-6465068542b8",
            "type": "kpi",
            "attributes": {
                "name": "Place 1",
                "value": 725
            },
            "relationships": {
                "place": {
                    "data": {
                        "id": "11113d50-fdd8-4f5a-8ef1-485cb5fedf04",
                        "type": "place"
                    }
                }
            }
        },
        {
            "id": "baac906d-93ed-43d7-a5b0-03a7f3961ffe",
            "type": "kpi",
            "attributes": {
                "name": "Place 2",
                "value": 838
            },
            "relationships": {
                "place": {
                    "data": {
                        "id": "111495d3-fb83-431b-adc3-485cb5fedf04",
                        "type": "place"
                    }
                }
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

> Response JSON (Not aggregated):

```json
{
    "data": [
        {
            "id": "616f0487-e67f-4996-be49-485cb5fedf04",
            "type": "graph",
            "attributes": {
                "values": {
                    "2018-12-11": [
                        {
                            "name": "Place 1",
                            "value": 310
                        },
                        {
                            "name": "Place 2",
                            "value": 415
                        }
                    ],
                    "2018-12-12": [
                        {
                            "name": "Place 1",
                            "value": 437
                        },
                        {
                            "name": "Place 2",
                            "value": 401
                        }
                    ]
                }
            },
            "relationships": {
                "places": {
                    "data": [
                        {
                            "id": "11113d50-fdd8-4f5a-8ef1-485cb5fedf04",
                            "type": "place"
                        },
                        {
                            "id": "111495d3-fb83-431b-adc3-485cb5fedf04",
                            "type": "place"
                        }
                    ]
                }
            }
        }
    ]
}
```

Allows obtaining a list of presence analytics per organization which the user can access.

### HTTP Request

- Default: `GET https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio`
- Not aggregated: `GET https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio&aggregated=false`
- Place ids: `GET https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/presence?type=capture_ratio&place_ids=11113d50-fdd8-4f5a-8ef1-485cb5fedf04,111495d3-fb83-431b-adc3-485cb5fedf04`

### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identification of an organization
type | true | Indicates the type of analytic
aggregated | false | Indicates if the analytic is aggregated, by default true
place_ids | false | List of market ids
date_from | false | **ISO 8601**, analytics from this day
date_to | false | **ISO 8601**, analytics until this day
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page

### Type query options

Type | Aggregated | Not aggregated | Description
-----| ---------- | ------------- | -----------
capture_ratio | true | true | Capture ratio
comeback_ratio | true | true | Comeback ratio
comeback_visits | true | true | Comeback visits
new_visits | true | true | New visits
passersby | true | true | Passersby
visits | true | true | Visits
visits_duration | true | true | Visits duration

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of the analytic
type | String | Type of the retrieve object
attributes | Object | Attributes of the analytic
name | String | Name of the analytic place
value | Integer | Value of the analytic
relationships | Object | Relationships of the analytic
id | Integer | Id of the relationship object
type | String | Type of the relationship object
