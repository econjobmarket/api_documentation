## Documentation

<font color='red'>Note that the soap server has been deprecated.  Only the rest methods described in this 
documentation still work</font>

To begin, login here with your econjobmarket credentials. The login link will redirect you to econjobmarket 
where you can use your econjobmarket recruiter credentials to authenticate.  
Once you have authenticated, you will be returned here to continue.

Once you have logged in, you should see some additional menu items. To discover your client key and secret, click on the link 
[https://backend.econjobmarket.org/ejm_setup](https://backend.econjobmarket.org/ejm_setup) in the menu bar.  
You will need to know the key and secret in order to have access to your data.

Next you will need some kind of client software to interpret the output from the server.  If you know what that means then you can proceed on your own to query the server. If not, I'll explain below how you can acquire the software you need, and how you can use it.

The location of the soap server is [https://backend.econjobmarket.org/soap/server1.php](https://backend.econjobmarket.org/soap/server1.php).  At the time of writing the soap server delivers serialized objects and arrays suitable for use with php, or xml encoded data suitable for use with javascript.

There are 4 methods available on the server to fetch applicant data, each returns a  single string that is either a base64 encoded serialized php object, or a base64 endoded serialized php array. If you are using php to interpret the data, then you base64_decode it first, then unserialize it. 

The method getBlob returns a pdf (binary) file, the method getData returns a list of applications for your organization as an array whose elements are associative arrays. The method getTable returns an array consisting of the contents of a mysql table, with each element being an associative array (except for the table myblobs since it contains large binary objects. For the myblobs table the method returns all the elements of a row except for the blob itself, which must then be fetched separately using getBlob). Finally, getApplicant returns a php object that contains all the data in your table associated with a particular candidate (except actual pdf files).

To retrieve this information, you need to supply your machine account username and password (which might not be the same as your username and password) and the name of your database. That information alone will get you a list of applicants. If you want more information, then you need to supply either the name of a table,  an applicant id,  or a blobid.

There is some software to help you interpret the soap response, but if you just want to get started and see what the response looks like, you can download the  file <a href="/backend_files/docs/ejm/request.xml" title="xml file">request.xml</a> and store it in some directly of your computer. Edit the file and replace the database name, machine account username and password with the correct ones for your organization.
From the command line (in the same directory), run the command

```
curl https://backend.econjobmarket.org/soap/server1.php/# -H 'Content-type: text/xml' -d @request.xml
```

By default, this will produce a base64 encoded string representing a serialized array of applications to your organization. You can save the string to a file, and interpret it later. If you change the method in the request.xml file from 'PHP' to "XML" you will instead get the same list encoded as xml. You should url-decode the string and strip the soap tags first in order to see xml. 

The string that is returned by these methods will  be pretty long, and  will be completely incomprehensible. You can save the string to a file, strip out the soap xml code so that you have only one long string, then run base64 -d on the string. You should see a serialized array.

If you use php, you can unserialize the string, then print_r to see the array. One way to use the data in this array is to load the array, check the applicant ids that it contains, then use the method getApplicant to read in the data from the applicants various applications.  The applicant object contains the various questions and answers that the applicant supplied on his ejm application form. The answers to questions that ask for a file are given as blobids that need to be fetched using the getBlob method.
