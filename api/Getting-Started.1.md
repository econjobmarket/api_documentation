Choose the option on the front page that says Login with Econjobmarket.  Use your username (email) and password at econjobmarket, they will be checked at [econjobmarket.org](https://econjobmarket.org).  You must be a valid recruiter at econjobmarket to use this api.


After login, use the link in the navigation section at the right of the page called 'EJM Api api details for your organization'.  Click on it.  On the next page, click the 'Get Started' button.
The page that follows will, after a few warings, allow you to click the button that creates your api account.  After creation, you'll be taken to a page that will show you 
your client key and secret.  Any software you create to download information will eventually need to access these,  though you won't need them for your initial testing.


The is an 'Refresh Access token' button you can click, which will generate an initial token you can use for testing.  If you get an 'invalid token' error, come back to this 
page an renew your token.  You'll submit the token as part of your url when you test.


After you understand what is going on and you are ready to set up your own download software, you will have to add some ip addresses which will be enabled to 
get access tokens and request data.  In other words, you'll need to have a server with a fixed ipaddress to access the data automatically.  You can add as many ip addresses
as you like.


Now go on to use the page on [Access Tokens](Authentication-and-Access-Tokens.2.md) to learn how to explore the api before you start.
