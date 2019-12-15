Methods are just the various urls you can use to access your data.  The api provides access to five resources, applications, applicants, files. letters and interviews.
## Applications

When you use the api to do bulk download, the best way is probably to start with the applications.  This will provide you with a list of all the applications to your organization that haven't been retired.  Each application provides a list of id numbers and dates that will allow you to decide whether you need to get more information.  The application id for each application is also a token that you can use to retrieve all the data (or selected bits of the data) associated with an application.  This is discussed later in the section on [documents](documents).

To retrieve the list of applications you would use the url
```
https://backend.econjobmarket.org/api/applications
```
Remember that you can only retrieve this information with a valid access token (see the section on [access_tokens](access_tokens)).  For testing, you can use your browser along with the token that is provided on your [api page](ejm_setup).  This method will deliver you an array of json objects that resemble the following:

```
{
    "appid": 620310,
    "aid": 38848,
    "fname": "******",
    "lname": "*******",
    "degreeinst": "Harvard University",
    "posid": 5164,
    "appdate": "2018-10-07 09:10:25",
    "changedate": "2018-06-26 07:49:09",
    "adtitle": "Assistant Professor 2019",
    "files": [{
        "file_id": 731790,
        "posting_doc_id": 14385,
        "description": "Curriculum vitae",
        "created_at": "2018-10-29 10:11:05",
        "updated_at": "2018-10-29 10:11:05",
        "aid": 38848,
        "type": "cv",
        "blobid": 840328,
        "type_id": 10,
        "name": "cv",
        "long_description": "Curriculum Vitae September 2018"
    }, {
        "file_id": 731460,
        "posting_doc_id": 14386,
        "description": "Job market paper",
        "created_at": "2018-10-29 10:11:05",
        "updated_at": "2018-10-29 10:11:05",
        "aid": 38848,
        "type": "cv",
        "blobid": 839959,
        "type_id": 20,
        "name": "jmpaper",
        "long_description": "Representative Paper "
    }, {
        "file_id": 742958,
        "posting_doc_id": 14390,
        "description": "Teaching statement",
        "created_at": "2018-10-29 10:11:05",
        "updated_at": "2018-10-29 10:11:05",
        "aid": 38848,
        "type": "cv",
        "blobid": 853523,
        "type_id": 50,
        "name": "teachingstatement",
        "long_description": "Teaching Statement"
    }],
    "questions": [{
        "id": 7210,
        "question": "Are you a Canadian citizen or Permanent Resident of Canada?",
        "type_id": "check-boxes",
        "instructions": null,
        "sort_order": 1,
        "response": "{\"16694\":\"1\"}",
        "response_id": 16694,
        "created_at": "2018-10-29 10:10:48",
        "updated_at": "2018-10-29 10:10:48",
        "response_text": "No"
    }],
    "recommendations": [{
        "recid": 517,
        "email": "****@****",
        "fname": "****",
        "lname": "****",
        "institution": "University of ****",
        "department": "Department of Economics",
        "last_reverified": "2018-07-02 06:12:48",
        "reverified_by": null,
        "letterid": 117896,
        "blobid": 839961,
        "created_at": "2018-09-11 20:58:31",
        "updated_at": "2018-09-11 20:58:31"
    }, {
        "recid": 774,
        "email": "*****@****.edu",
        "fname": "****",
        "lname": "****",
        "institution": "***** University",
        "department": "Department of Economics",
        "last_reverified": "2018-07-02 16:45:42",
        "reverified_by": null,
        "letterid": 117695,
        "blobid": 838004,
        "created_at": null,
        "updated_at": "2018-11-02 18:11:58"
    }, {
        "recid": 847,
        "email": "****@****.edu",
        "fname": "*****",
        "lname": "******",
        "institution": "**** University",
        "department": "Department of Economics",
        "last_reverified": "2017-10-18 07:23:13",
        "reverified_by": null,
        "letterid": 117765,
        "blobid": 838477,
        "created_at": "2018-07-31 13:56:14",
        "updated_at": "2018-11-02 12:17:09"
    }]
}
```

The fields with asterisks in them will, of course, contain text strings with real information.  This list is relatively compact and is intended to point you toward additonal information you might need.  There are a couple of  important bits of information at this point- the properties `aid`,  which is the id number you would use to fetch all details about the applicant,  and `appid`, which is the application number.  There is an array that gives answers to any custom questions you have in your application form.  There is an array of files with some details, and an array of references.  To get the actual files and letters so that you can view them, you'll need to make a couple more requests.  At this point, notice that each of the objects has an updated_at field included which will allow you to tell whether you need to refresh the entry in your own database.  To retrieve more information on the applicant, you'll use the [applicant method](applicant), files are retrieved using the [files method](application_files), while recommendations can be fetched using the [letters method](recommendation_letters).


The recommended way to use this data to update your database is to loop through the list checking whether you have stored the application already in your own database.  If you have you can look at the `changedate` property and check it against your local database to see whether you need to update applicant details.  If you don't have the application at all, then you will need to send another request to receive full details about the application, the applicant, their files and their letters.


If you want to you can fetch this information for a single application you would use the url:

```
https://backend.econjobmarket.org/api/applications/620310
```

where the number at the end of the url is as appid similar to the one in the listing above. 


This particular url will return the json object that appears above.


The [Letters](letters) interface works in a very similar way.