# Errors

Flame Analytics API uses the following error codes:

Error code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong or not have session.
403 | Forbidden -- The data requested is hidden for administrators only.
404 | Not Found -- The specified data could not be found.
405 | Method Not Allowed -- You tried to access a data with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The data requested has been removed from our servers.
429 | Too Many Requests -- You're requesting too many data! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
