Most of the methods that have been discussed previously are for bulk downloads and updates accomplished using automated scripts.  If you know the application id you can fetch all the relevant information for the application using that id.  One way to learn the application id is just to ask the applicant to provide it for you when they register on your own automated application system.  This way you can have the applicant transmit his or her personal details and files while you are registering an applicant.  The application id can then be used later to pick up reference letters whenever they arrive.


Similarly if you are taking applications by email, but you want the reference letters submitted separately, then you can again ask the applicant to provide their application id on econjobmarket, then use the object method to fetch all the letters at once.


The object method works slightly differently than the bulk methods mentioned before.  Now the url will consist of the document keyword, and application id, and the particular data that you want.   Here are the four possible urls:
```
https://backend.econjobmarket.org/api/document/620310/applicant
https://backend.econjobmarket.org/api/document/620310/application
https://backend.econjobmarket.org/api/document/620310/files
and
https://backend.econjobmarket.org/api/document/620310/letters
```

Notice that each of the urls must be accompanied by an application id (and, as always, an access token).  Each of these requests returns data like the data returned in the bulk methods in cases where you provide an id.  In other words, the files and letters urls will return the full documents (base64 encoded).