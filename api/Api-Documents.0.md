Access to the api is available at [https://backend.econjobmarket.org](https://backend.econjobmarket.org).  If you wish to test the api and use it you will need to go there and login with econjobmarket.  Once you have logged in, use the link that says "Ejm api Details for your Organization".  The details you need to use the api will appear unless you are at first login.  In that case click the "Get Started" button.  Your keys will be created, and you will need to enter the ipaddresses of the computers that will access the api.

As of July, 2018, applicant data is delivered by a simpler api which is documented here.  The older api is described at [https://backend.econjobmarket.org/legacy](https://backend.econjobmarket.org/legacy).

Features of the new api include:

1. Real time data (no caching).
2. Authentication by oauth.
3. Only five methods, applicant, applications, files, letters, and interviews.
4. Application tokens can be used to fetch information and letters.

If you are using the older api, pre July 2018, follow the Legacy Api link on the right menu.  

- [Getting Started](Getting-Started.1.md)
- [Using Oauth and access tokens](Authentication-and-Access-Tokens.2.md)
- Methods
  1. [applications](Application-Method.3.md)
  2. [applicants](Applicant-Method.4.md)
  3. [Files](Files-Method.5.md)
  4. [Letters](Recommendation-Letters.6.md)
  6. [Document method](Document-Method.7.md)
  5. [Interviews](Interviews.8.md)
