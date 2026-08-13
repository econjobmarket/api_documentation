## Displaying Ads

You can redisplay econjobmarket ads on your own website. The ad display is a public api so you can either re-display all the ads, or a subset of ads that are distinguished by different re-seller ids.

When an ad is registered on econjobmarket, the recruiter can choose to have the ad displayed on a number of external websites.  Some of these websites charge for this service.  Each such website has a re-seller id.  For example, the id for the econometric society website is 3.  The list of ads that are to be re-displayed on their website can be retrieved using the endpoint [https://backend.econjobmarket.org/data/zz_public/json/Feature/3](https://backend.econjobmarket.org/data/zz_public/json/Feature/3). The ads end up on their website at [http://econometricsociety.org/econjobmarket](http://econometricsociety.org/econjobmarket).

If you want to distribute selected ads on your own website, submit an econjobmarket support request at 
[Econjobmarket Support](https://econjobmarket.org/contacts.php).  If you would rather you can download all the ads, then try to filter them yourself.

If you just want to display all ads, or want to provide a custom listing of ads, you can get them by using the endpoint

```
https://backend.econjobmarket.org/data/zz_public/json/Ads
```
The only transfer protocol that is supported now is json. 

It is up to you to provide custom display code that fits your own website.

A basic ad is encoded as follows:
```
{
"adtitle":"Open Rank Tenure Track or Tenure Eligible Professor | Department of Finance",
"adtext":"<p>The Department of Finance .....</p>",
"startdate":"2025-09-13",
"enddate":"2026-09-07",
"deadline_date":"2026-08-03",
"department":"Finance, Business School",
"name":"University of Miami",
"latitude":25.720054485476062,
"longitude":-80.27660340070726,
"locations":[
	{"addr1":"5250 University Drive",
	"addr2":null,
	"city":"Coral Gables",
	"state":"Florida",
	"zip":"33146",
	"country_code":"US",
	"latitude":25.720054485476,
	"longitude":-80.276603400707
	}
	],
"position_types":[
	{"name":"Assistant Professor"},
	{"name":"Associate Professor"},
	{"name":"Full Professor"}
	],
"categories":[
	{"name":"Finance"}
	],
"url":"https://econjobmarket.org/positions/11776",
"logo":5806,
"logo_url":"https://b\ackend.econjobmarket.org/data/zz_public/json/Logo/5806"
}

```

You can load the json associated with all open ads using the url
```
https://backend.econjobmarket.org/data/zz_public/json/Ads
```
The entire list is an array of json elements like the one above.  Most of the properties of the json are self explanatory.
The fields `position_types` and `categories` are both arrays of json elements.  The example above only has one element in each array,  but each of them can have many elements.  The field `categories` contains all the fields that the hiring institution
is interested in.  The `url` fields is the link to the ad as displayed on econjobmsarket.org.  The `logo_url` is a link to the organization logo.  Clicking that link will display the logo inline so it should be useable in an image definition in html.
