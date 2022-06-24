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

![user-pool](images/user-pool.jpg?raw=true "user-pool")[^1]

# Identity Pool
Cognito Identity Pool (or Cognito Federated Identities) on the other hand is a way to authorize your users to use the various AWS services. Say you wanted to allow a user to have access to your S3 bucket so that they could upload a file; you could specify that while creating an Identity Pool. And to create these levels of access, the Identity Pool has its own concept of an identity (or user). The source of these identities (or users) could be a Cognito User Pool or even Facebook or Google.

# User Pool vs. Identity Pool
Notice how we could use the User Pool, social networks, or even our own custom authentication system as the identity provider for the Cognito Identity Pool. The Cognito Identity Pool simply takes all your identity providers and puts them together (federates them). And with all of this it can now give your users secure access to your AWS services, regardless of where they come from.
So in summary; the Cognito User Pool stores all your users which then plugs into your Cognito Identity Pool which can give your users access to your AWS services.

![id-pool](images/idpool.jpg?raw=true "id-pool")[^2]

# Adding user pool sign-in through a third party
Your app users can sign in either directly through a user pool, or federate through a third-party identity provider (IdP). The user pool manages the overhead of handling the tokens that are returned from social sign-in through Facebook, Google, Amazon, and Apple, and from OpenID Connect (OIDC) and SAML IdPs. With the built-in hosted web UI, Amazon Cognito provides token handling and management for authenticated users from all IdPs. This way, your backend systems can standardize on one set of user pool tokens.

## How federated sign-in works in Amazon Cognito user pools

Sign-in through a third party (federation) is available in Amazon Cognito user pools. This feature is independent of federation through Amazon Cognito identity pools (federated identities).

Amazon Cognito is a user directory and an OAuth 2.0 identity provider (IdP). When you sign in native users to the Amazon Cognito directory, your user pool is an IdP to your app. Native users are those who sign up or who your administrator creates directly in your user pool.
When you connect Amazon Cognito to social, SAML, or OpenID Connect (OIDC) IdPs, your user pool acts as a bridge between multiple service providers and your app. To your IdP, Amazon Cognito is a service provider (SP). Your IdPs pass an OIDC ID token or a SAML assertion to Amazon Cognito. Amazon Cognito reads the claims about your user in the token or assertion and maps those claims to a new user profile in your user pool directory.

![federated](images/federated.jpg?raw=true "federated")[^3]

Amazon Cognito then creates a user profile for your federated user in its own directory. Amazon Cognito adds attributes to your user based on the claims from your IdP and, in the case of OIDC and social identity providers, an IdP-operated public userinfo endpoint. Your user's attributes change in your user pool when a mapped IdP attribute changes. You can also add more attributes independent of those from the IdP.
After Amazon Cognito creates a profile for your federated user, it changes its function and presents itself as the IdP to your app, which is now the SP. Amazon Cognito is a combination OIDC and OAuth 2.0 IdP. It generates access tokens, ID tokens, and refresh tokens. For more information about tokens, see Using tokens with user pools.
You must design an app that integrates with Amazon Cognito to authenticate and authorize your users, whether federated or native.


[^1] image: [Link](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-identity-federation.html)
[^2] image: [Link](https://serverless-stack.com/chapters/cognito-user-pool-vs-identity-pool.html)
[^3] image: [Link](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pools-identity-federation.html)
