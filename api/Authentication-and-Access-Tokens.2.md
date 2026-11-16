Authentication is done by json web tokens.  These are delivered to users with the client key and secret.  They are long strings, which 
must be supplied with each request for data.  As mentioned previously, when you look at your api information after setup, any available web token will be listed there, along with the time left before
it expires. 


Here is what an access token looks like (it isn't valid so it won't work):

---
```
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjJkOWU2NmI1NzdlNGNiZGU1ZWRjMTZiZTZkYzc5NzBiYmFkYTg1NjMiLCJqdGkiOiIyZDllNjZiNTc3ZTRjYmRlNWVkYzE2YmU2ZGM3OTcwYmJhZGE4NTYzIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc1Mjk3NTIsImlhdCI6MTU0NzUyNjE1MiwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.B5Qk34Qw_TeDsUB4cwOxqMABQnQbe1ATGyCHmYYOA2gjUqBi1enuS2hJNDwzCLhHtRupT0EAo5-ES2Ml1nzTibs3EPDuSH0oup4nA603h4suJETMhgFVrLhwyKAVDL58aXFbXH5tGldAKMxd6nJpUonFOiEdaATLsyWkoWeEMSMRa8-Bs10Vr6eBa1tsoEpH1-pprzOshCbo7oxt_PSkryCnFgXhXBZ-EzmAXPXjUSYMkzTvk-PECnoBGahYiFNo1nnrEUxsgeuwbHjAIkzkFlK_QI48tXu0BoKQw8sxcroVe3ts7TuXHhmRhS11F4lcaTneO4IkJzsOIJf9N2BRow
```

---
This string appears to have line breaks in it because the display reformats it, but when you submit it, it should be a single long string without spaces of line breaks.


The api reads the access token by looking at the header of the page request. So a simple url with the 
access token as a query parameter will not work.  You can try the developer tools in your browser and
use json to submit a request with custom headers.  This is unlikely to work unless your browser is open
at one of the ip addresses you have allowed access.

The only way to test is to use the methods described below.

## Accessing tokens from your own server.

There are two ways to get an access token that you can use on your own computer.  Both methods require authentication. First login at the 
[api server](https://backend.econjobmarket.org/user).  On your [setup page](https://backend.econjobmarket.org/setup_home), item 7 provides an access token. If you don't see one, click the `Refresh Token` button.  You can copy the whole token by clicking the icon on the 
bottom right hand side of the box that it is in.

Alternatively, if you'd like to do it programmatically, the setup page also provides your client key and secret. 

Here is a curl request that will produce an access token:
```
curl -X POST -d "client_id=******&client_secret=*******&grant_type=client_credentials" https://backend.econjobmarket.org/token/
```
What you need to do is to replace the '******'  strings in the line above with the client_key and client secret which are given on your [api page](https://backend.econjobmarket.org/ejm_setup).  

This is what you will get in return:


```javascript
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjAxMjY4MDIyYzgwZjM5OGM1NzU4MjYwMmYxYTk5Zjk1YzlhYzQxZmEiLCJqdGkiOiIwMTI2ODAyMmM4MGYzOThjNTc1ODI2MDJmMWE5OWY5NWM5YWM0MWZhIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc5MjgxNjUsImlhdCI6MTU0NzkyNDU2NSwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.A-QopUA4_lfwrJm7GK7rjCBWyi57hQqyAq5nKm_pTc95MGz2e_1CfOHcSx73bAxT85u1F-skQIL26QTfE6nZdQ7WCSmhZ0MeUq3RMAtEyPjerr0l8dVdGyTE5kTqtj-zBdiKtVGO2mUgr74HiwCe84RNAnbumx7a7fvn1onIrF_0igzpzY-X4iba3w1pM1xqlPPBvuw2XTkXMujewEfH7sxWOeUmolQV4HPi5ghtwOHVnXJYX9CUThrJN8oH8UDu_tVmB7zgwc983GAJr9CVF1h7FX2LxdpFXxQRL3lkBTZUe2yxQwoOYIR6gVBEFTOwtj8tnLri2AWSjo07AH664g",
    "expires_in": 3600,
    "token_type": "bearer",
    "scope": "basic"
}
```

The returned string will differ in the sense that it will be a single string (coded in json) without the line breaks and formatting that you see above.  You can json decode the string, then use the properties "access_token", "expires in", "token_type", and "scope" in your own script.

If you do something wrong, you should get a json encoded error message instead of a token like the one above.

## Fetching data with the access token

The way to access the data is to include the access token as part of the authorization header in your pageas follows:
```
curl -H 'Accept: application/json' -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjAzNzEyYWY2ZTg5ODBkZTc3NjJiYmU1NWNmYjk5YmQzYzJmMjg2OGQiLCJqdGkiOiIwMzcxMmFmNmU4OTgwZGU3NzYyYmJlNTVjZmI5OWJkM2MyZjI4NjhkIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc5MzI5MDYsImlhdCI6MTU0NzkyOTMwNiwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.Jn2romlRLlh9RtBKSu__adVhkEDblQRAwJ-NKxFkLdCppCzfx3KjeFPaTfIVFKpTmF11bhK19edPqtRxnnPtch8UFsaqlWYSGUmuy5LoIb3qkWRUl9C8asf2OnBvbrOB9xD2DmlbrjaAJsf1gMbhHW4coPoaK1HCY1IObsFqa8czr9z_S-HzWSvVpG6SNUDA1-8HIsnAKQGGY-gXiT08D5WyKw2_W4uSdX0JBxBUu3H8LD-9bnyxFjJZpysubtblWkmDLVzNtQh5XtNgObCck0eOaf34NOlsnYpryy6R9utYUkhNKH2iGxcj8MerTQFqp211IGsTEh610XmcTmFKEw" https://backend.econjobmarket.org/api/applicants
```
If you provide a valid access token, this request will return all your applicants.  Very important - in this curl request, there should be exactly one space between the word 'Bearer' and the beginning of the access token (in this case the string 'eyj').

You can also include your token as part of the data included in a post request, similar to the following implementation in php:
```
<?php
$url = 'https://backend.econjobmarket.org/api/applicants';
$accessToken = 'paste your access token here';
$ch = curl_init();
curl_setopt_array($ch, [
    CURLOPT_RETURNTRANSFER => true, // Return the response as a string
    CURLOPT_HTTPHEADER => [
        'Authorization: Bearer ' . $accessToken,
        'Accept: application/json',
        'User-Agent: MyPHPApp/1.0' // Many APIs reject requests without a User-Agent
    ],
]);
$response = curl_exec($ch);
// Check for cURL errors
if (curl_errno($ch)) {
    echo 'cURL Error: ' . curl_error($ch);
} else {
    $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
    $data = json_decode($response, true); // Decode JSON into an associative array
    print_r($data);
}
curl_close($ch);
?>

```
Finally, here is a python version:
```
import os
import requests
# Retrieve the access token from an environment variable                                                                                             
access_token = "paste your access token here"
url = "https://backend.econjobmarket.org/api/applicants"
# Set up the Authorization header                                                                                                                    
headers = {
    "Authorization": f"Bearer {access_token}",
    "Accept": "application/json"
}
try:
    # Send the GET request with a timeout                                                                                                            
    response = requests.get(url, headers=headers, timeout=10)

    # Raise an exception for HTTP error codes (4xx or 5xx)                                                                                           
    response.raise_for_status()

    # Parse and print the JSON response                                                                                                              
    data = response.json()
    print(data)

except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except requests.exceptions.RequestException as err:
    print(f"Request failed: {err}")

```
At this point you can continue to use the various [methods](methods).