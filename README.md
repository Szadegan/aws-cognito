# aws-cognito
Its a summary of my researchs about cognito user pool and identity pool. You would probably find all of them in internet!

# Token
## Why to use Token?
To Authenticate users and grant access to resources with tokens. 

## What is claim?
Tokens have claims, which are pieces of information about the user. 

## What is ID token?
The ID token contains claims about the identity of the authenticated user, such as name and email. 

## What is Access token?
The Access token contains claims about the Access of the authenticated user, a list of the user's groups, and a list of scopes. 

Other tokens: 
Amazon Cognito also has tokens that you can use to get new tokens or revoke existing tokens. Refresh a token to retrieve a new ID and access tokens. Revoke a token to revoke user access that is allowed by refresh tokens.

# User Pool
Say you were creating a new web or mobile app and you were thinking about how to handle user registration, authentication, and account recovery. This is where Cognito User Pools would come in. Cognito User Pool handles all of this and as a developer you just need to use the SDK to retrieve user related information.
It serves as your own identity provider to maintain a user directory. It supports user registration and sign-in, as well as provisioning identity tokens for signed-in users.

## Authenticating with Token
When a user signs into your app, Amazon Cognito verifies the login information. 
If the login is successful, Amazon Cognito creates a session and returns an ID, access, and refresh token for the authenticated user. 
You can use the tokens to grant your users access to your own server-side resources or to the Amazon API Gateway. 
Or you can exchange them for temporary AWS credentials to access other AWS services.(identity pool)

![user-pool](images/user-pool.jpg?raw=true "user-pool")
