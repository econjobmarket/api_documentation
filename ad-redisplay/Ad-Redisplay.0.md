## Displaying Ads

You can redisplay econjobmarket ads on your own website. The ad display is a public api so you can either re-display all the ads, or a subset of ads that are distinguished by different re-seller ids.

When an ad is registered on econjobmarket, the recruiter can choose to have the ad displayed on a number of external websites.  Some of these websites charge for this service.  Each such website has a re-seller id.  For example, the id for the econometric society website is 3.  The list of ads that are to be re-displayed on their website can be retrieved using the endpoint [https://backend.econjobmarket.org/data/zz_public/json/Feature/3](https://backend.econjobmarket.org/data/zz_public/json/Feature/3). The ads end up on their website at [http://econometricsociety.org/econjobmarket](http://econometricsociety.org/econjobmarket).

If you want do this, submit an econjobmarket support request at [Econjobmarket Support] (https://econjobmarket.org/contacts.php).

If you use this method, you don't have to charge, you can just offer the option to recruiters.

If you just want to display all ads, or want to provide a custom listing of ads, you can get them by using the endpoint

```
https://backend.econjobmarket.org/data/zz_public/xml/Ads
```
You can replace the string "xml" in the url above with "json" to get json encoded output.  You can also use the string "jsonp", which is explained below. 

Whichever approach you take, it is up to you to provide custom display code that fits your own website.

A basic ad is encoded as follows:
```
<Ad>
<posid>3625</posid>
<oid>128</oid>
<adtitle>Tenured Position in Business Ethics</adtitle>
<adtext>
The University of British Columbia <br />Sauder School of Business <br />Tenured Position in Business Ethics <br /> <br />The Sauder School of Business at the University of British Columbia (Vancouver Campus) invites applications for a new professorship in the broad area of Business Ethics, an area that includes (but is not limited to) Strategy and Corporate Social,,,, participation. <br />
</adtext>
<categories>32</categories>
<ads_non_ejm>1,2,4</ads_non_ejm>
<postypeid>11</postypeid>
<startdate>2015-11-13 00:00:00</startdate>
<enddate>2016-06-30 00:00:00</enddate>
<position_country>CA</position_country>
<department>
Sauder School of Business, Strategy and Business Economics Divis
</department>
<shortname>UBC Sauder School of Business</shortname>
<blobid>11068</blobid>
<position_type>Tenured Professor</position_type>
<name>University of British Columbia</name>
</Ad>
```

To display the organization gif, use the url

```
https://backend.econjobmarket.org/data/zz_public/json/Blobs/128
```
The number at the end of the url is the organization id `oid` displayed in the xml above. This will return a suitable encoded gif or png which can be set in an image field on your website.

The property `categories` is generally a comma separated list of fields.  To look up the corresponding names of the fields use the endpoint
```
https://backend.econjobmarket.org/data/zz_public/xml/Categories
```
## Method 2 - javascript/jsonp

A second method you can use to display ads uses javascript and a method called jsonp.  This method uses the ReST api to download the list of current ads, then renders a complete web page that displays them. The code for this method is available at github using
```
git clone https://github.com/econjobmarket/ad-display ad-display
```
I won't try to explain jsonp (you can google it to get better explanations than I can give).  The github website describes the setup of the code.

This script displays a complete page of ads. It uses the public ad display.
## Method 3 - RSS
The RSS feed for econjobmarket ads is
```
https://backend.econjobmarket.org/data/zz_public/rss/Ads
```
