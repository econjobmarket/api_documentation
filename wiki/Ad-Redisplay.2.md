You can redisplay econjobmarket ads on your own website if you want. There are three ways to do it. Each uses the public ad display.

One way to do it is to sell prominent display space on your website through econjobmarket. If you choose this method, econjobmarket will make your space available to recruiters when they are creating their ads. If a recruiter chooses to pay for your space, econjobmarket will collect the money and transfer it to you.

If you arrange this, econjobmarket will provide an authenticated feed which includes only the ads that pay for your service and you can use this feed to display the ads on your website. 

This method is used by the econometric society to charge for ads that are displayed on their site (see [http://econometricsociety.org/econjobmarket](http://econometricsociety.org/econjobmarket) ).  Their display is perhaps not the optimal way to do it.

The recommended way to sell ads like this is to provide a side bar with highlighted ads. Here is a link that will describe the basics [https://mixergy.com/course-cheat-sheet-selling-ads-on-your-site/](https://mixergy.com/course-cheat-sheet-selling-ads-on-your-site/).

If you wish to sell ad space like this on your website through econjobmarket, use the econjobmarket support request at [Econjobmarket Support](https://econjobmarket.org/contacts.php).

## Customized Display
If you just want to re-display all the ads for informational purpose using custom code on your website, then you can get all the ads without authentication using
```
https://backend.econjobmarket.org/data/zz_public/xml/Ads
```

You can replace the string "xml" in the url above with "json" to get json encoded output.  You can also use the string "jsonp", which is explained below.
Each ad is returned encoded as follows:
```xml
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
```url
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
