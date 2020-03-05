## REST Documentation

You can access all of the methods described on the SOAP documentation page directly over http. 
Each of the methods is accessed using a particular url. To access the data you would use a specially formed url 
that looks like the following 
```
https://backend.econjobmarket.org/rest/(your_database_name)/(encoding_method)/(data_you_want)
```

For example, to see the applications that have been submitted  to an organization with database name my_organization 
as an xml encoded file, one would use the url

```
https://backend.econjobmarket.org/rest/my_organization/XML/Data
```
The response would be an xml file which looks like the following

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

To access this data, you must use https, not http. Standard http access is used, you supply your client key and secret, 
along with the name of your database. If you don't know these, then you can figure out what they are by 
logging into this website using your econjobmarket manager credentials, then following the link to 
"EJM Backend Data -> Machine Account Setup".  This will only work if you have a valid manager account at econjobmarket. 
If you don't you'll have to figure out who in your department created the recruiter account at econjobmarket 
in the first place and ask them for a password.

Data will be encoded in one of three ways - XML - as described above, JSON, or PHP base64 encoded serialized php 
object or array.  The encoding method must be in capitals xml is not the same as XML.

The data available is as follows:

1. Data - as illustrated above - a list of applicants who have applied to the various positions in your organization.
1. Applicant - `https://backend.econjobmarket.org/rest/my_organization/XML/Applicant/(id)`. 
For this method to work, you must supply a valid applicant id, which you would get by accessing your applications 
using the Data resource described above.  This method will deliver all the details of the applications submitted 
by a particular applicant as an object. If you are processing your data using php, use the PHP encoding method, 
then unencode and deserialize the string that is returned to import and object directly into your code.
1. Blob - `https://backend.econjobmarket.org/rest/my_organization/XML/Blob/(id)`. 
Unlike the other resources, this one is returned as a pdf file by all methods. You must supply a valid blob id 
which you would discover by accessing the resources described above.
1. TableNames - `https://backend.econjobmarket.org/rest/my_organization/XML/TableNames/` - A list of tables in your database.
1. TableDescription - `https://backend.econjobmarket.org/rest/my_organization/XML/TableDescription/(tablename)` - 
describes the columns in the table tablename.
1. Table  `https://backend.econjobmarket.org/rest/my_organization/XML/Table/(tablename)` - returns the contents of tablename.