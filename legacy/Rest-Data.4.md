## The Data method

The most basic data fetching operation is to retrieve a list of applicants to your positions on econjobmarket.  When using soap, this method is called getData(), while with ReST, this is referred to with the noun Data. I illustrated how to call this data on the previous page.

 Whichever method you use, if you ask for XML formatted data, it will look like this:
```
<xml>
<applicants>
  <applicant>
    <aid>18213</aid>
    <fname>M</fname> 
    <lname>Peters3</lname> 
    <degreeinst>ubc</degreeinst> 
    <appid>224047</appid>
    <posid>1958</posid>
    <appdate>1358634979</appdate>
    <adtitle>An Assistant Associate Example</adtitle>
  </applicant>
  <applicant> 
    <aid>18212</aid>
    <fname>Michael</fname>
    <lname>Peters2</lname>
    <degreeinst>Queens</degreeinst>
    <appid>224046</appid>
    <posid>1959</posid>
    <appdate>1358634460</appdate>
    <adtitle>An example of a Lecturer Position with a custom form</adtitle>
  </applicant>
</applicants>
</xml>
```

Each individual applicant has an applicant id called appid at econjobmarket. Detailed data about the applicant (email, phone number etc) is retrieved using another method that is described below. It allows you to specify an appid to collect the individuals information. The field "degreeinst" is supposed to be the university from which they are graduating. Appid is the application number of the application the applicant made to the position you posted at econjobmarket. The position is identified by the posid. The title of that ad is included in the field to make it easier for you to identify it visually. The date the applicant is applied is given in the usual unix way as seconds since 01/01/1970.
Similar data in JSON format looks like this:
```
{"aid":"18213","fname":"M","lname":"Peters3","degreeinst":"ubc","appid":"224052","posid":"1960","appdate":"1358638887","adtitle":"Test Ad for Njoyn will not display at EJM"},{"aid":"18212","fname":"Michael","lname":"Peters2","degreeinst":"Queens","appid":"224051","posid":"1961","appdate":"1358638774","adtitle":"Second Test Ad - will not display"}
```
Though these are different applications from those used in the XML example, you can see the same fields aid,appid, posid etc are still there.

Finally, if the data is requested in PHP format, it comes back as a base64_encoded serialized array.  If you take the returned result and base64_decode it before unserializing it, you will get an array of arrays in php format. The same data looks like this when you print out the elements of the main array:
```
Array ( [aid] => 18213 [fname] => M [lname] => Peters3 [degreeinst] => ubc [appid] => 224053 [posid] => 1961 [appdate] => 1358638923 [adtitle] => Second Test Ad - will not display )

Array ( [aid] => 18213 [fname] => M [lname] => Peters3 [degreeinst] => ubc [appid] => 224052 [posid] => 1960 [appdate] => 1358638887 [adtitle] => Test Ad for Njoyn will not display at EJM )
```
The next step is to take one of the applicant ids (or aid) and use it to retrieve all the properties of an applicant.
