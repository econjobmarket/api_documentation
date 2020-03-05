## Displaying Ads

You can redisplay econjobmarket ads on your own website if you want. There are three ways to do it. Each uses the public ad display.

It is possible to sell ad space on your website through econjobmarket. A recruiter setting up an ad at econjobmarket is given the option to pay to redisplay ads on specific websites for a fee.  If you arrange this, econjobmarket will provide an authenticated feed which includes only the ads that pay for your service.  This method is used by the econometric society to charge for ads that are displayed on their site (see [http://econometricsociety.org/econjobmarket](http://econometricsociety.org/econjobmarket)).

The recommended way to sell ads like this is to provide a side bar with highlighted ads. If you do this, you will probably want to use the first method to download the ads below, and customize your own website display.

If you wish to sell ad space on your website through econjobmarket, use the econjobmarket support request at [Econjobmarket Support] (https://econjobmarket.org/contacts.php).

## Your Own customized Display

The first is just to write your own display code, then download all the current ads using the rest api.  This requires no authentication.  Use the url
```
https://backend.econjobmarket.org/data/zz_public/xml/Ads
```
You can replace the string "xml" in the url above with "json" to get json encoded output.  You can also use the string "jsonp", which is explained below. 

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
This will return a suitable encoded gif or png which can be set in an image field on your website.
To determine the position type and category, you can use the url
```
https://backend.econjobmarket.org/data/zz_public/xml/PositionTypes
``` 
and check the corresponding json or xml object to determine the rank, etc.  The field can be determined by
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
