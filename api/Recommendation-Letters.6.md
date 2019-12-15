Letters are retrieved in exactly the same way as files.   The url
```
https://backend.econjobmarket.org/api/letters
```

will provide an array of json objects that look like
```
{
    "letterid": 130885,
    "blobid": 930189,
    "a_rid": 104055,
    "date": "2018-11-21 07:46:35",
    "expiry_date": "2019-02-19 00:00:00",
    "name": "Reference letter",
    "notes": null,
    "created_at": "2018-11-20 23:46:35",
    "updated_at": "2018-11-20 23:46:35"
}
```


To get the letter itself, you would use

```
https://backend.econjobmarket.org/api/letters/130885
```

This produces an array like this:
```
{
        "letterid": 130885,
        "blobid": 930189,
        "filename": "reference_letter.pdf",
        "filesize": 76714,
        "filetype": "application\/pdf",
        "filecontent": "JVBERi0xLjUNCiW1tbW1DQ........ZWYNCjc2NTM1DQolJUVPRg==",
        "sha1_hash": null
}
```

As with files, the string associated with filecontent with be very long (filesize will give number of characters in the string).  It is base64 encoded.  If you decode it, you will get the binary assocated with the pdf file which you can store in a database, or in your filesystem.


Now you can go on to fetch data about interviews using the [Conferences](letters) method.
