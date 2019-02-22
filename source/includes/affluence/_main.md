# Affluence

## Index data

```ruby
require 'uri'
require 'net/http'

url = URI("https://pull.flameanalytics.com/api/v1/affluence/f871274e-49c1-492c-6f5c-e46f505704d6?from=2017-02-10T0000&to=2017-02-10T2359&res=1h")

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
  --url 'https://pull.flameanalytics.com/api/v1/affluence/f871274e-49c1-492c-6f5c-e46f505704d6?from=2017-02-10T0000&to=2017-02-10T2359&res=1h' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://pull.flameanalytics.com/api/v1/affluence/f871274e-49c1-492c-6f5c-e46f505704d6?from=2017-02-10T0000&to=2017-02-10T2359&res=1h",
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
  "id": "f871274e-49c1-492c-6f5c-e46f505704d6",
  "name": "Location 1",
  "visits": 805,
  "hour_visits_avg": 67.08,
  "day_visits_avg": 866,
  "data": [
      {
          "date": "2017-02-10T10:00:00.000Z",
          "in": 126,
          "out": 121
      },
      {
          "date": "2017-02-10T11:00:00.000Z",
          "in": 0,
          "out": 0
      },
      {
          "date": "2017-02-10T12:00:00.000Z",
          "in": 58,
          "out": 74
      },
      {
          "date": "2017-02-10T13:00:00.000Z",
          "in": 58,
          "out": 74
      },
      {
          "date": "2017-02-10T14:00:00.000Z",
          "in": 149,
          "out": 147
      },
      {...},
      ...
  ]
}
```

> Response JSON (Days)

```json
{
    "id": "f871274e-49c1-492c-6f5c-e46f505704d6",
    "name": "Location 1",
    "visits": 2175,
    "hour_visits_avg": 55.63,
    "day_visits_avg": 725,
    "data": [
      {
          "date": "2017-02-10",
          "in": 866,
          "out": 867
      },
      {
          "date": "2017-02-11",
          "in": 1309,
          "out": 1336
      },
      {...},
      ...
  ]
}
```

The information that comes from the people counter, for that location that you are selecting. <br>
As presence data, you can see different data information, in hours or days, depending on the **'ref' param**.

<aside class="notice">The information shown will be linked to the schedule of the configured location.</aside>

### HTTP Request

- Default: `GET https://pull.flameanalytics.com/api/v1/affluence/:market_id?from=:date`

- Hours: `GET https://pull.flameanalytics.com/api/v1/affluence/:market_id?from=:date&to=:date&res=1h`

- Days: `GET https://pull.flameanalytics.com/api/v1/affluence/:market_id?from=:date&to=:date&res=1d`


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
visits | Integer | Total visits, number of people entering the location that the camera detects
hour_visits_avg | Decimal | Average of visits per hour, average number of visits in the location that the camera detects at hours
day_visits_avg | Integer | Average of visits per day, average number of visits in the location that the camera detects in total day
data | Array | The data divided by the data resolution indicated, can be divided into hours or days


### Return data parameters

Parameter | Type | Description
--------- | ------- | -----------
date | Date | Date of current data, can be at hours or a specific day
in | Integer | Number of visits that entered at a specific day or in an hour
out | Integer | Number of visits that left at a specific day or in an hour

