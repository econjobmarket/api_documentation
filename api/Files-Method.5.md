This will explain how to retrieve the files associated with an application.


If you want a list of all the files that have been submitted to applications to your positions, you can use the url
```
https://backend.econjobmarket.org/api/files
```
(again, always using an access token).  This will produce a list of json objects that look like the following:
```
{
    "file_id": 828205,
    "blobid": 956742,
    "filename": "paper 4.pdf",
    "filesize": 511628,
    "filetype": "application\/pdf",
    "sha1_hash": "75fb1050517312ec299f484548bd152ae52dea17"
}
```
Notice that  this information doesn't include the file itself.  For that, you would use the following:
```
https://backend.econjobmarket.org/api/files/828205
```
This will produce a very big json object that looks like this:
```
{
        "file_id": 828205,
        "blobid": 956742,
        "filename": "paper 4.pdf",
        "filesize": 511628,
        "filetype": "application\/pdf",
        "filecontent": "JVBERi0xLjUNJeLjz9MNCjEgMCBvYmo8PC9QYWdl.....MxZmIxNDNlZTFjZjQ4ODVlM2Y4\nMTMyY2JlNWZlYT5dL1ByZXYgMzM3OSA+Pg0Kc3RhcnR4cmVmDQo1MDg3OTQNCiUlRU9GDQo=",
        "sha1_hash": "75fb1050517312ec299f484548bd152ae52dea17"
}
```
except that I have cut out most of the filecontent entry to make it readable.  The filecontent entry is a base64 encoded version of the pdf file the applicant submitted.  You can either store that directly in your database and decode it once you deliver it to a browser, or decode it first and either save it to your database or store it on your filesystem for future use.  For files you can check for changes by comparing the sha1_hash to the hash you have stored in your database.
