This will explain how to retrieve the files associated with an application.


If you want a list of all the files that have been submitted to applications to your positions, you can use the url
```
https://backend.econjobmarket.org/api/files
```
(again, always using an access token).  This will produce a list of json objects that look like the following:
```
{
    "file_id": 828205,
    "aid": xxxxx,
    "path": null,
    "blobid": 956742,
    "type_id": 20,
    "filename": "paper 4.pdf",
    "filesize": 511628,
    "filetype": "application\/pdf",
    "sha1_hash": "75fb1050517312ec299f484548bd152ae52dea17"
}
```
It is also possible that a file is just a link to externally saved video file.  In that case, the entry will look as follows:
```
{
    "file_id": 828205,
    "aid": xxxxx,
    "path": "https://youtube.com/?XXXXX,
    "blobid": null,
    "type_id": 25,
    "filename": null,
    "filesize": null,
    "filetype": null,
    "sha1_hash": null
}
```
If you want to know which you are dealing eith before you fetch the file itself, you can use the `type_id`.  The values `25` and `75` refer to external links.  All other type_id values refer to blobs.

Notice that  this information doesn't include the file itself.  For that, you would use the following:
```
https://backend.econjobmarket.org/api/files/828205
```
This will produce a very big json object that looks like this when the corresponding file is stored as a blob:
```
{
        "file_id": 828205,
        "blobid": 956742,
        "filename": "paper 4.pdf",
        "filesize": 511628,
        "filetype": "application\/pdf",
        "path": null,
        "type_id": 20,
        "filecontent": "JVBERi0xLjUNJeLjz9MNCjEgMCBvYmo8PC9QYWdl.....MxZmIxNDNlZTFjZjQ4ODVlM2Y4\nMTMyY2JlNWZlYT5dL1ByZXYgMzM3OSA+Pg0Kc3RhcnR4cmVmDQo1MDg3OTQNCiUlRU9GDQo=",
        "sha1_hash": "75fb1050517312ec299f484548bd152ae52dea17"
}
```
except that I have cut out most of the filecontent entry to make it readable.  The filecontent entry is a base64 encoded version of the pdf file the applicant submitted.  You can either store that directly in your database and decode it once you deliver it to a browser, or decode it first and either save it to your database or store it on your filesystem for future use.  For files you can check for changes by comparing the sha1_hash to the hash you have stored in your database.

If the file is a link to an external file, the `path` and `type_id` variables will have values, while the remaining fields, apart from `file_id`  will be null.` 
I
