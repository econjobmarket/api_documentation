This method will give you all the details associated with a particular applicant.  The url that will allow you to retrieve information on all of your applicants is
```
https://backend.econjobmarket.org/api/applicants
```
and if you want only the details for one particular applicant, you would use
```
https://backend.econjobmarket.org./api/applicants/38848
```
As before, these urls must be used with a valid access token.

This will produce for each applicant a json object that looks as follows"
```
{
    "error": false,
    "aid": 38848,
    "id": 21599,
    "enrolldate": "2017-11-09 05:01:12",
    "changedate": "2018-06-26 07:49:09",
    "email": "*@***.edu",
    "fname": "***",
    "mname": null,
    "lname": "******",
    "country": "USA",
    "phone": "**********",
    "fax": "",
    "url": "",
    "category_id": 14,
    "categories": "23",
    "primary_field": "Public Economics",
    "degreetype": "Ph.D.",
    "degreeinst": "***** University",
    "degreebegyear": 2008,
    "degreeendyear": 2013,
    "curpos": "tp",
    "curinst": "University of *******",
    "ethnic": "",
    "ethnicity": "",
    "race": "",
    "gender": "withheld",
    "is_contactok": 1,
    "ackdate": "2018-06-26",
    "nationality": "",
    "status": 0,
    "statusinactivedate": null,
    "last_revised_time": "2018-06-26 07:49:09",
    "secondary_fields": {
        "23": "Political Economy,"
    },
    "conferences": {
        "16": "EEA Job Market Meeting",
        "11": "Canadian Economics Employment Exchange",
        "12": "Simposio de la Asociaci\u00f3n Espa\u00f1ola de Econom\u00eda",
        "13": "RES Postgraduate Meeting",
        "15": "Allied Social Sciences Association"
    }
}
```