Access to the api is available at [https://backend.econjobmarket.org](https://backend.econjobmarket.org).  If you wish to use the api there are two ways to do it.

First, you can request an account on that server which you can do by logging into [https://econjobmarket.org](https://econjobmarket.org) and going to [https://econjobmarket.org/users/feedback/threads/s](https://econjobmarket.org/users/feedback/threads/s).  Submit a new support request and ask for access to the backend api.

The second way to access the api is to login to your account at [https://econjobmarket.org](econjobmarket.org) amd select your recruiter role to make sure you are acting as a recruiter (this only matters if you have other roles, for example, and applicant role).  Then open [https://backend.econjobmarket.org](backend.econjobmarket.org), and click the login button at the bottom of the right hand sidebar.  Scroll to the bottom of the login page until you see the button that says `Login with Econjobmarket` and click it.  

Your login with econjobmarket will be verfied and your account will be set up if you don't have one already so you can access the api configuration and get your client key and secret.

This second method is faster and ensures you don't have to remember any password for the backend site.  The backend site doesn't store or create any password for you.  If you use this method you'll use your econjobmarket login anytime you want access to the api configuration.

You don't actually have to log in at econjobmarket.org first, you can click the `Login with Econjobmarket` button directly and it will take you to the econjobmarket.org site to authenticate.  If it doesn't return you to the backend.econjpbmarket.org site, it means that your default role at econjobmarket.org is not `recruiter` - maybe your last login there was `reviewer` for example.  In that case, go to econjobmarket, change your role to recruiter, then try the login at backend.econjobmarket.org again.

Once you are logged in to backend.econjobmarket.org, you can access the api setup page by clicking the button on the right hand sidebar that says `Configure your api connection details`.  If you are on your first login, it will direct you create you client key and secret.  Following the link should do that, and bring you back to the setup page where you'll see relevant information.  If you don't see an access token, you can get one by clicking the `Refresh access token` button.

The api will only respond to requests for data at specific ip addresses.  You have to configure these on your own once you have set up your key and secret.

Thie documentation applies to the api as of July, 2025.  

Features of the api include:

1. Real time data (no caching).
2. Authentication by oauth.
3. Only five methods, applicant, applications, files, letters, and interviews.
4. Application tokens can be used to fetch information and letters.  

- [Getting Started](/docs/api/Getting-Started.1.md)
- [Using Oauth and access tokens](/docs/api/Authentication-and-Access-Tokens.2.md)
- Methods
  1. [applications](/docs/api/Application-Method.3.md)
  2. [applicants](/docs/api/Applicant-Method.4.md)
  3. [Files](/docs/api/Files-Method.5.md)
  4. [Letters](/docs/api/Recommendation-Letters.6.md)
  6. [Document method](/docs/api/Document-Method.7.md)
  5. [Interviews](/docs/api/Interviews.8.md)
