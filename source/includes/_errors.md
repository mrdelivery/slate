# Errors


The MrD API uses the following error codes:


Error Code | Meaning
---------- | -------
404 | Not Found -- The specified resource could not be found
409 | Conflict -- Resource has been updated by someone else. You need to get it again.
500 | Internal Server Error -- We had a problem with our server. Try again later.
<!--
400 | Bad Request -- Your request sucks
#401 | Unauthorized -- Your API key is wrong
#403 | Forbidden -- The kitten requested is hidden for administrators only
#405 | Method Not Allowed -- You tried to access a kitten with an invalid method
#406 | Not Acceptable -- You requested a format that isn't json
#410 | Gone -- The kitten requested has been removed from our servers
#418 | I'm a teapot
#429 | Too Many Requests -- You're requesting too many kittens! Slow down!
#503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
-->
