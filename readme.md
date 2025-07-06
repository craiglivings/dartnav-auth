\# DartNav Authentication Redirect



This is the authentication redirect page for DartNav app. It handles OAuth callbacks from Google and redirects back to the mobile app.



\## Setup Instructions



\### 1. Create GitHub Repository

1\. Create a new GitHub repository called `dartnav-auth`

2\. Upload the `index.html` file to the root of the repository



\### 2. Enable GitHub Pages

1\. Go to your repository settings

2\. Scroll down to "Pages" section

3\. Under "Source", select "Deploy from a branch"

4\. Choose "main" branch and "/ (root)" folder

5\. Click "Save"



\### 3. Configure Custom Domain

1\. In the Pages settings, under "Custom domain"

2\. Enter: `auth.dartnav.app`

3\. Check "Enforce HTTPS"

4\. Click "Save"



\### 4. DNS Configuration

Add a CNAME record to your domain:

\- \*\*Name\*\*: `auth`

\- \*\*Value\*\*: `your-username.github.io`

\- \*\*TTL\*\*: 3600 (or default)



\### 5. Update OAuth Client

In Google Cloud Console, update your OAuth 2.0 Client ID:



\*\*Authorized JavaScript Origins:\*\*

```

https://auth.dartnav.app

https://localhost:19006

http://localhost:19006

```



\*\*Authorized Redirect URIs:\*\*

```

https://auth.dartnav.app

https://auth.dartnav.app/

```



\## How It Works



1\. User taps "Sign in with Google" in the app

2\. Google OAuth redirects to `https://auth.dartnav.com`

3\. This page extracts the access token from the URL

4\. Page redirects to `dartmoor://auth?access\_token=...`

5\. App receives the token and completes Firebase authentication



\## Testing



You can test the redirect page by visiting:

`https://auth.dartnav.com?access\_token=test\_token`



It should redirect to: `dartmoor://auth?access\_token=test\_token` 

