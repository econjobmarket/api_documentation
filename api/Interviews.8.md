## Conferences method

If you use the interview scheduling feature at [econjobmarket.org](https://econjobmarket.org) then you can retrieve information about all your scheduled interviews using this api.

The first url will give you a list of all the conferences at which you have previously scheduled interviews.  For example

```
https://backend.econjobmarket.org/api/conferences
```
gives 
```
[{
    "conference_id": 11,
    "name": "Canadian Economics Employment Exchange",
    "city": "Toronto",
    "country": "Canada",
    "start_date": "2018-12-07 00:00:00",
    "end_date": "2018-12-08 00:00:00",
    "url": "http:\/\/grandhoteltoronto.com",
    "id": 50,
    "room_number": null,
    "room_label": null,
    "description": null,
    "code": null,
    "hotel_name": "Grand Hotel",
    "hotel_full_name": "Grand Hotel",
    "address": "225 Jarvis Street",
    "longitude": -79.3737780000000014979377738200128078460693359375,
    "latitude": 43.65650000000000119371179607696831226348876953125
}, {
    "conference_id": 15,
    "name": "Allied Social Sciences Association",
    "city": "Atlanta",
    "country": "USA",
    "start_date": "2019-01-04 00:00:00",
    "end_date": "2019-01-06 00:00:00",
    "url": "http:\/\/doubletree3.hilton.com\/en\/hotels\/georgia\/the-american-hotel-atlanta-downtown-a-doubletree-by-hilton-ATLSSDT\/index.html",
    "id": 157,
    "room_number": null,
    "room_label": null,
    "description": null,
    "code": null,
    "hotel_name": "American Hotel",
    "hotel_full_name": "The American Hotel Atlanta Downtown-a Double Tree by Hilton",
    "address": "160 Ted Turner Drive NW, 30303",
    "longitude": -84.390116000000006124537321738898754119873046875,
    "latitude": 33.75935100000000232967067859135568141937255859375
}]
```
You can then see all the interviews you scheduled by adding the conference _id to the url as in
```
https://backend.econjobmarket.org/api/conferences/15
```
which will give you  something like
```
[{
    "id": 270608,
    "group_id": 272,
    "name": "Public",
    "location_id": 157,
    "description": null,
    "interviewee_id": 3410,
    "start_datetime": "2019-01-04 09:00:00",
    "end_datetime": "2019-01-04 09:30:00",
    "fname": "******",
    "lname": "******",
    "degreeinst": "University of *******",
    "appid": 648456,
    "aid": 41454,
    "room_label": null,
    "room_number": null,
    "hotel_full_name":"The American Hotel Atlanta Downtown-a Double Tree by Hilton",
    "address":"160 Ted Turner Drive NW, 30303",
    "city":"Atlanta",
}, {
    "id": 270715,
    "group_id": 276,
    "name": "Macro",
    "location_id": 157,
    "description": null,
    "interviewee_id": 3471,
    "start_datetime": "2019-01-06 12:00:00",
    "end_datetime": "2019-01-06 12:30:00",
    "fname": "******",
    "lname": "******",
    "degreeinst": "****** University",
    "appid": 679610,
    "aid": 43298,
    "room_label": null,
    "room_number": null,
    "hotel_full_name":"The American Hotel Atlanta Downtown-a Double Tree by Hilton",
    "address":"160 Ted Turner Drive NW, 30303",
    "city":"Atlanta"
}]
```

Of course, you will typically have many more entries than you see here (most departments will have around 30 interview slots like this). Notice that the applicant id (`aid`) and the application id (`appid`)  are included so that you can link the interview candidates