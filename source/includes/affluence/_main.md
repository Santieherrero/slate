<h1 id="affluence">Affluence</h1>

<h2 id="affluence-index">Index data</h2>

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/affluence?type=average_visits")

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
  --url https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/affluence?type=average_visits \
  --header 'Accept-Encoding: application/json' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/7b85c755-aeba-482b-a07a-f375375c33e4/analytics/affluence?type=average_visits",
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

Allows obtaining a list of affluence analytics per organization which the user can access.

### HTTP Request

- Default: `GET https://api.flameanalytics.com/v2/organizations/:organization_id/analytics/affluence?type=average_visits`
- Not aggregated: `GET https://api.flameanalytics.com/v2/organizations/:organization_id/analytics/affluence?type=average_visits&aggregated=false`
- Place ids: `GET https://api.flameanalytics.com/v2/organizations/:organization_id/analytics/affluence?type=average_visits&place_ids=:place_id,:place_id`

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
avg_visits_per_hour | true | true | Average visits per hour
avg_visits_per_day| true | true | Average visits per day
busiest_day | true | false | Busiest day
busiest_hour | true | false | Busiest hour
busiest_wday | true | false | Busiest week day
visits | true | true | Visits
outs | true | true | Outs
average_visits | true | true | Average visits
affluence_avg_occupation | true | true | Affluence average occupation
affluence_max_occupation | true | true | Affluence maximum occupation
affluence_accomplishment_occupation | true | true | Affluence accomplishment occupation
abandonment_rate | true | true | Abandonment rate
affluence_avg_stay_time | true | true | Affluence average stay time
productivity | true | true | Productivity

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
