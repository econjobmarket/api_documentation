Authentication is done by json web tokens.  These are delivered to users with the client key and secret.  They are long strings, which 
must be supplied with each request for data.  As mentioned previously, when you look at your api information after setup, any available web token will be listed there, along with it's expiry date.  You can copy and paste that token into your browser bar for testing the api.  If there is no access token shown, of if the displayed access token is expired, just click the refresh button to get a new one.

## Testing with access tokens using your web browser


Here is what an access token looks like:

---
```
eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjJkOWU2NmI1NzdlNGNiZGU1ZWRjMTZiZTZkYzc5NzBiYmFkYTg1NjMiLCJqdGkiOiIyZDllNjZiNTc3ZTRjYmRlNWVkYzE2YmU2ZGM3OTcwYmJhZGE4NTYzIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc1Mjk3NTIsImlhdCI6MTU0NzUyNjE1MiwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.B5Qk34Qw_TeDsUB4cwOxqMABQnQbe1ATGyCHmYYOA2gjUqBi1enuS2hJNDwzCLhHtRupT0EAo5-ES2Ml1nzTibs3EPDuSH0oup4nA603h4suJETMhgFVrLhwyKAVDL58aXFbXH5tGldAKMxd6nJpUonFOiEdaATLsyWkoWeEMSMRa8-Bs10Vr6eBa1tsoEpH1-pprzOshCbo7oxt_PSkryCnFgXhXBZ-EzmAXPXjUSYMkzTvk-PECnoBGahYiFNo1nnrEUxsgeuwbHjAIkzkFlK_QI48tXu0BoKQw8sxcroVe3ts7TuXHhmRhS11F4lcaTneO4IkJzsOIJf9N2BRow
```

---
This string appears to have line breaks in it because the display reformats it, but when you submit it, it should be a single long string without spaces of line breaks.


To test your api you would use an url that would look like this

```
https://backend.econjobmarket.org/api/applicants/?access_token=eyJ0eXAiOiJKV1Q........
```

You would paste this url, including the entire access token (not just the short version above, the entire long string) into your browser bar.  All data is returned as json, so you might find it helpful to install a json pretty print extension so you can see the structure of the data a little more clearly.
At this point, you are ready to start start testing the various methods with your web browser.

## Accessing tokens from your own server.

If you want to test the api on your own server, you need to start by adding the ip address of your server to your information on your api information page (the page where you copied the access token).  If you include the full url of your server as well, the system will verify it first, which will help make sure you don't make mistakes.  At that point you can fetch an access token using a script on your server.

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

The simplest way to access the data is to include the access token as part of the authorization header as follows:
```
curl -H 'Accept: application/json' -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjAzNzEyYWY2ZTg5ODBkZTc3NjJiYmU1NWNmYjk5YmQzYzJmMjg2OGQiLCJqdGkiOiIwMzcxMmFmNmU4OTgwZGU3NzYyYmJlNTVjZmI5OWJkM2MyZjI4NjhkIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc5MzI5MDYsImlhdCI6MTU0NzkyOTMwNiwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.Jn2romlRLlh9RtBKSu__adVhkEDblQRAwJ-NKxFkLdCppCzfx3KjeFPaTfIVFKpTmF11bhK19edPqtRxnnPtch8UFsaqlWYSGUmuy5LoIb3qkWRUl9C8asf2OnBvbrOB9xD2DmlbrjaAJsf1gMbhHW4coPoaK1HCY1IObsFqa8czr9z_S-HzWSvVpG6SNUDA1-8HIsnAKQGGY-gXiT08D5WyKw2_W4uSdX0JBxBUu3H8LD-9bnyxFjJZpysubtblWkmDLVzNtQh5XtNgObCck0eOaf34NOlsnYpryy6R9utYUkhNKH2iGxcj8MerTQFqp211IGsTEh610XmcTmFKEw" https://backend.econjobmarket.org/api/applicants
```
If you provide a valid access token, this request will return all your applicants.  Very important - in this curl request, there should be exactly one space between the word 'Bearer' and the beginning of the access token (in this case the string 'eyj').

You can also include your token as part of the data included in a post request, similar to the following implementation in php:
```
<php>
  $curl_session = curl_init();
    curl_setopt($curl_session, CURLOPT_URL, 'https://backend.econjobmarket.org/api/applicants');
    curl_setopt($curl_session, CURLOPT_HEADER, false);
    curl_setopt($curl_session, CURLOPT_RETURNTRANSFER, true);
    $post_array = array (
			 'access_token' => 'eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpZCI6IjAzNzEyYWY2ZTg5ODBkZTc3NjJiYmU1NWNmYjk5YmQzYzJmMjg2OGQiLCJqdGkiOiIwMzcxMmFmNmU4OTgwZGU3NzYyYmJlNTVjZmI5OWJkM2MyZjI4NjhkIiwiaXNzIjoiIiwiYXVkIjoienpfNjdAYmFja2VuZCIsInN1YiI6Inp6XzY3QGJhY2tlbmQiLCJleHAiOjE1NDc5MzI5MDYsImlhdCI6MTU0NzkyOTMwNiwidG9rZW5fdHlwZSI6ImJlYXJlciIsInNjb3BlIjoiYmFzaWMifQ.Jn2romlRLlh9RtBKSu__adVhkEDblQRAwJ-NKxFkLdCppCzfx3KjeFPaTfIVFKpTmF11bhK19edPqtRxnnPtch8UFsaqlWYSGUmuy5LoIb3qkWRUl9C8asf2OnBvbrOB9xD2DmlbrjaAJsf1gMbhHW4coPoaK1HCY1IObsFqa8czr9z_S-HzWSvVpG6SNUDA1-8HIsnAKQGGY-gXiT08D5WyKw2_W4uSdX0JBxBUu3H8LD-9bnyxFjJZpysubtblWkmDLVzNtQh5XtNgObCck0eOaf34NOlsnYpryy6R9utYUkhNKH2iGxcj8MerTQFqp211IGsTEh610XmcTmFKEw',
			 );
    curl_setopt($curl_session, CURLOPT_POST, true);
    curl_setopt ($curl_session, CURLOPT_POSTFIELDS, $post_array);
    if($result = curl_exec($curl_session)) {
      curl_close($curl_session);
      return json_decode($result);
} else {
handle the error
}
</php>
```
At this point you can continue to use the various [methods](methods).