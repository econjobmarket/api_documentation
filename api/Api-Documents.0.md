Access to the api is available at [https://backend.econjobmarket.org](https://backend.econjobmarket.org).  If you wish to use the api you'll need to request an account on that server which you can do by logging into [https://econjobmarket.org](https://econjobmarket.org) and going to [https://econjobmarket.org/users/feedback/threads/s](https://econjobmarket.org/users/feedback/threads/s).  Submit a new support request and ask for access to the backend api.  

This access is only available if you have a recruiter role at econjobmarket for one or more organizations. Once you have credentials for the backend.econjobmarket.org server, use the main website econjobmarket.org and set your active role to 'Recruiter' for whatever organization you are trying to manage.  This step verifies your recruiter credentials and informs the backend.econjobmarket.org website which organization you are working on.

The details you need to use the api will appear unless you are at first login.  In that case click the "Get Started" button.  Your keys will be created, and you can start using the api.

The api will only respond to requests for data at specific ip addresses that you can set up once you have set up your key and secret.

Thie documentation applies to the api as of July, 2018.  

Features of the api include:

1. Real time data (no caching).
2. Authentication by oauth.
3. Only five methods, applicant, applications, files, letters, and interviews.
4. Application tokens can be used to fetch information and letters.  

- [Getting Started](/api/Getting-Started.1.md)
- [Using Oauth and access tokens](Authentication-and-Access-Tokens.2.md)
- Methods
  1. [applications](Application-Method.3.md)
  2. [applicants](Applicant-Method.4.md)
  3. [Files](Files-Method.5.md)
  4. [Letters](Recommendation-Letters.6.md)
  6. [Document method](Document-Method.7.md)
  5. [Interviews](Interviews.8.md)
