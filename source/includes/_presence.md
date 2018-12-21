# Presence

## Presence data

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h")

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
  --url 'https://api.flameanalytics.com/v2/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h",
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

> Response JSON (Hours)

```json
{
  "id": 1,
  "name": "Place 1",
  "passersby": 10706,
  "visits": 830,
  "new_visits": 574,
  "comeback_visits": 256,
  "capture_ratio": 6.51,
  "comeback_ratio": 45.81,
  "visits_duration": 46.49,
  "data": [
    {
      "date": "2017-02-10T06:00:00.000Z",
      "visits": 1,
      "passersby": 26,
      "new_visits": 0,
      "comeback_visits": 1,
      "capture_ratio": 3.7,
      "comeback_ratio": 100.0,
      "average_visit_length": 11.8
    },
    {
      "date": "2017-02-10T07:00:00.000Z",
      "visits": 1,
      "passersby": 24,
      "new_visits": 0,
      "comeback_visits": 1,
      "capture_ratio": 4.0,
      "comeback_ratio": 100.0,
      "average_visit_length": 25.25
    },
    {...},
    ...
  ]
}
```

> Response JSON (Days)

```json
{
  "id": 38,
  "name": "Place 1",
  "passersby": 24846,
  "visits": 1335,
  "new_visits": 917,
  "comeback_visits": 418,
  "capture_ratio": 4.5,
  "comeback_ratio": 32.65,
  "visits_duration": 64.83,
  "data": [
      {
          "date": "2017-02-09",
          "visits": 626,
          "passersby": 10711,
          "new_visits": 437,
          "comeback_visits": 189,
          "capture_ratio": 5.52,
          "comeback_ratio": 30.19,
          "average_visit_length": 51.2311022364217
      },
      {
          "date": "2017-02-10",
          "visits": 78,
          "passersby": 4930,
          "new_visits": 50,
          "comeback_visits": 28,
          "capture_ratio": 1.56,
          "comeback_ratio": 35.9,
          "average_visit_length": 94.3691025641025
      },
    {...},
    ...
  ]
}
```

The information that comes from the wifi tracking, for that location that you are selecting. <br>
You can see different data information, in hours or days, depending on the **'ref' param**.

<aside class="notice">The information shown will be linked to the schedule of the configured location.</aside>

### HTTP Request

- Default: `GET https://api.flameanalytics.com/v2/presence/:market_id?from=:date`

- Hours: `GET https://api.flameanalytics.com/v2/presence/:market_id?from=:date&to=:date&res=1h`

- Days: `GET https://api.flameanalytics.com/v2/presence/:market_id?from=:date&to=:date&res=1d`


### Query parameters

Parameter | Required | Description
--------- | ------- | -----------
place_id | <div class="red center">true</div> | Identifier of location
from | <div class="red center">true</div> | **ISO 8601**, start date of the query interval. <br> If we just passed this parameter, the data returned is only from that day.
to | <div class="center">false</div> | **ISO 8601**, end date of the query interval.
res | <div class"center">false</div> | Data resoultion. It can be 1d (Day) or 1h (Hour). Default: 1d

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of location
name | String | Name of location
passerby | Integer | Total passerby, is a metric that allows you to know the number of people who pass in front of the location and how many of them enter
visits | Integer | Total visits, number of people entering the location with the mobile wireless active
new_visits | Integer | Total new visits, number of people with the Wifi activated that access to the location for the first time.
comeback_visits | Integer | Total of comeback visits, number of people with their mobile Wifi activated, who visit the location again
capture_ratio | Decimal | Total ratio of visits, the rate that measures the total number of people with its active mobile wireless active accessing into the location
comeback_ratio | Decimal | Total ratio of comeback visits, the rate of people, with their mobile Wifi activated, who return to the location after an initial visit.
visits_duration | Decimal | Total average of visits duration, it's the average time that people with the Wifi activated are active inside the location.
data | Array | The data divided by the data resolution indicated, have the same structure as the total and can be divided into hours or days

