# Presence

## Get presence of place

```ruby
require 'uri'
require 'net/http'

url = URI("https://pull.flameanalytics.com/api/v1/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Content-Type"] = 'application/json'
request["Authorization"] = 'Token token=nugyUyuzq6nqvm_uiesD'

response = http.request(request)
puts response.read_body
```

```shell
curl --request GET \
  --url 'https://pull.flameanalytics.com/api/v1/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h' \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://pull.flameanalytics.com/api/v1/presence/1?from=2017-02-10T0000&to=2017-02-10T2359&res=1h",
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

> Response JSON

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
      "date": "2017-02-10T01:00:00.000Z",
      "visits": 1,
      "passersby": 26,
      "new_visits": 0,
      "comeback_visits": 1,
      "capture_ratio": 3.7,
      "comeback_ratio": 100.0,
      "average_visit_length": 11.8
    },
    {
      "date": "2017-02-10T05:00:00.000Z",
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


