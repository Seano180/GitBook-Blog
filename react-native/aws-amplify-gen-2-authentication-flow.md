---
description: March 2025
icon: arrow-progress
---

# AWS Amplify Gen 2 - Authentication Flow

User Authentication - easy, I know how it works.... or at least, that's what I first thought when I first set out on this journey.

User sign-up and login flows may seem straightforward since everyone has navigated them before, and they rarely change. So, why discuss these processes in detail?

As we dive into March 2025, you might have noticed that the AWS Amplify Gen 2 documentation on authentication flows still leaves a bit to be desired, mainly because of the recent transition from Gen 1. So, I thought, why not write up a helpful article to deepen our understanding of these user authentication flows? Let's jump right in and explore together!

Typical user authentication flows are broken down in to 2 main categories:

**New User**

* Lands on the Signup page - fills in details and submits the form
* Is prompted with a One Time Password (OTP) sent to the users mobile or email
* Enters the OTP and then gains access to the application

**Existing/Returning User**

* IF logged in, is directed to the main landing page
* IF logged out, is directed to the Login page
* IF password is forgotten, then the user has the option to reset password etc.

This is nothing we haven't seen before. But understanding how to implement this within React Native code is a lot more challenging.

Firstly, and most importantly, it's essential to understand which parts of your application need to be secured. For example, an unauthenticated user should not be able to access the "Dashboard" page.

If you want to secure the entire app, requiring users to either sign up or log in, you should ensure the Root Layout is wrapped in \<Authenticator /> tags. This guarantees that IF the user is logged out, they can only gain access to the Login screen, and not any other page/screen within the app.

The method described above is the most common approach with regards to app authentication, and the one we use in our React Native application.

To help visualize the OAuth flow, I’ve created the diagram below. This flow uses the default authentication levels in Cognito, where authentication codes are sent to the user only during the Sign-Up and Reset Password stages.

\*\* Please note that this Authentication flow does not include Social and Custom Sign-In/Sign-Up providers like Facebook or Google.

<figure><img src="../.gitbook/assets/AWS (2).png" alt=""><figcaption><p>AWS Amplify (Gen 2) - User Authentication Flow</p></figcaption></figure>

### Steps for Implementing Authentication

Implementing Authentication in the correct order is crucial, if you want to avoid wasting days scratching your head and wondering why your app doesn't work (speaking from experience :joy:)

I had a genius idea to code and implement the Login and Logout screens first. Easy!

Although, it didn't work?&#x20;

The error message in my console kept prompting <mark style="color:red;">"Username does not exist in User Pool"</mark>

But why? what does this mean?

The error message was highlighting that the user (me), does not exist in the AWS Cognito User-Pool. To fix this, there are 2 solutions to the above error message:

1. **(Not Recommended)** - Create a AWS Cognito User-Pool and add a "verified" user to that pool (you can then use this email address to _PARTIALLY_ test the Login screen) however, since this email address does NOT have an assigned password, you will not be able to successfuly Login to your app.
2. **(Recommended)** - Code and Implement your Sign-Up screen _FIRST!_ - By doing this, each time you Sign-Up, the user will be automatically added to your AWS Cognito User-Pool, and will allow you to Login with a password.

Insert cheesy quote below:

> _`Taking the easy road is like ordering dessert first—it's sweet, but it might come back to bite you later!`_

\
Now that we have gotten that out of the way, if you wish to learn about AWS Cognito, and the steps to set it up, feel free to check out my article here:&#x20;

{% content-ref url="aws-cognito-user-pool-creation-and-setup.md" %}
[aws-cognito-user-pool-creation-and-setup.md](aws-cognito-user-pool-creation-and-setup.md)
{% endcontent-ref %}



### AWS Authentication Code

In this section, I will outline some of the AWS API properties used in our app, following AWS naming conventions to ensure they are called correctly.&#x20;

The complete React Native code for each sub-section will be provided via links to help facilitate a quick implementation.

#### <mark style="color:blue;">Sign-Up</mark>

function SignUp ()  {

&#x20;    handleSignUp

&#x20;         signUpResponse

&#x20;    handleSignUpConfirmation

};

:point\_right: **Code Link:** TBC

#### <mark style="color:blue;">Login</mark>

function onSignInPressed()  {

&#x20;    signIn&#x20;

};

:point\_right: **Code Link:** TBC

#### <mark style="color:blue;">Logout</mark>

function handleSignOut()  {

&#x20;    signOut

};

:point\_right: **Code Link:** TBC

#### <mark style="color:blue;">Reset Password</mark>

function ForgotPassword()  {

&#x20;    handleResetPassword

&#x20;         handleResetPasswordNextSteps

&#x20;    handleConfirmResetPassword

};

:point\_right: **Code Link:** TBC
