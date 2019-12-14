Access to the api is available at [https://backend.econjobmarket.org](https://backend.econjobmarket.org).  If you wish to test the api and use it you will need to go there and login with econjobmarket.

As of July, 2018, applicant data is delivered by a simpler api which is documented here.  The older api is described at [https://backend.econjobmarket.org/legacy](https://backend.econjobmarket.org/legacy).

Features of the new api include:

1. Real time data (no caching).
2. Authentication by oauth.
3. Only five methods, applicant, applications, files, letters, and interviews.
4. Application tokens can be used to fetch information and letters.

If you are using the older api, pre July 2018, follow the Legacy Api link on the right menu.  

- [Getting Started](Getting-Started|api|1)
- [Using Oauth and access tokens](Authentication-and-Access-Tokens|api|2)
- [Methods](methods)
  1. [applications](Application-Method|api|3)
  2. [applicants](Applicant-Method|api|4)
  3. [Files](Files-Method|api|5)
  4. [Letters](Recommendation-Letters|api|6)
  5. [Interviews](Interviews|api|8)
  6. [Document method](Document-Method|api|7)
