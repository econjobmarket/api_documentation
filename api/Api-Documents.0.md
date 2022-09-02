Access to the api is available at [https://backend.econjobmarket.org](https://backend.econjobmarket.org).  If you wish to use the api you'll need to request an account on that server which you can do by logging into [https://econjobmarket.org](https://econjobmarket.org) the going to [https://econjobmarket.org/users/feedback/threads/s](https://econjobmarket.org/users/feedback/threads/s) and requesting access to the backend api.  

This access is only available if you have a recruiter role at econjobmarket. Once you credentials for the web you must set your active role to 'Recruiter' on the main website.  Once you have reset your current role and logged into the website at https://backend.econjobmarket.org, you'll set a link that says "Ejm api Details for your Organization".  The details you need to use the api will appear unless you are at first login.  In that case click the "Get Started" button.  Your keys will be created, and you can start using the api.

The api will only respond to request for data at specific ipaddresses that you can set up once you have set up your key and secret.

Thie documentation applies to the api as of July, 2018.  

Features of the api include:

1. Real time data (no caching).
2. Authentication by oauth.
3. Only five methods, applicant, applications, files, letters, and interviews.
4. Application tokens can be used to fetch information and letters.  

- [Getting Started](Getting-Started.1.md)
- [Using Oauth and access tokens](Authentication-and-Access-Tokens.2.md)
- Methods
  1. [applications](Application-Method.3.md)
  2. [applicants](Applicant-Method.4.md)
  3. [Files](Files-Method.5.md)
  4. [Letters](Recommendation-Letters.6.md)
  6. [Document method](Document-Method.7.md)
  5. [Interviews](Interviews.8.md)
