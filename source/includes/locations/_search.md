## Search of locations

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.flameanalytics.com/v2/organizations/b61a860e-0df7-4y7c-b0dc-757108181f1872/places?q=Madrid&fields=name")

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
  --url https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/places?q=Madrid&fields=name \
  --header 'Authorization: Token token=nugyUyuzq6nqvm_uiesD' \
  --header 'Content-Type: application/json'
```

```javascript
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.flameanalytics.com/v2/organizations/b61a560e-0df7-4y7c-b0dc-757108181f1872/places?q=Madrid&fields=name",
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

> The above command returns JSON structured like this:

```json
{
    "data": [
    {
        "id": "f871274e-49c1-492c-6f5c-e46f505704d6",
        "type": "place",
        "attributes": {
            "name": "Hermosilla Madrid",
            "address": "Calle de Hermosilla, Madrid",
            "timezone": "Europe/Madrid",
            "rebound_time": 1,
            "admin_or_manager": false,
            "async_weather": false
        }
    },
    {
        "id": "29f62e71b-aa06-4963-b665c-9df9169cf2188",
        "type": "place",
        "attributes": {
            "name": "Madrid Shop One",
            "address": "Calle Serrano, Madrid",
            "timezone": "Europe/Madrid",
            "rebound_time": 1,
            "admin_or_manager": false,
            "async_weather": true
        }
    }],
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

Allows obtaining all the locations for the organization that you are pointing and the user has access to it,
with the necessary params for query the search.

### HTTP Request

`GET https://api.flameanalytics.com/v2/organizations/:organization_id/places?q=:search_text&fields=:column_name`

### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
organization_id | true | Identifier of a organization
q | false | Text query to search
fields | false | Columns for search at database level, only permit this columns: **'name', 'address', 'timezone', 'external_id'**
page | false | Indicates de number page of list
per_page | false | Indicates de number of objets per page

### Return parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Integer | Identifier of a place
type | String | Type of the retrieve object
attributes | Object | Attributes of that place
name | String | Name of the place
address | String | Address for that place
timezone | String | Timezone for that place
async_weather | Boolean | Boolean to indicate if have the weather forecast
