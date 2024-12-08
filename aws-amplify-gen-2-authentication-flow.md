---
icon: arrow-progress
description: December 2024
---

# AWS Amplify Gen 2 - Authentication Flow

\*\* This article in currently in development.

User Authentication - easy, I know how it works.... or at least, that's what I first thought when I first set out on this journey.

User sign-up and login flows may seem straightforward since everyone has navigated them before, and they rarely change. So, why discuss these processes in detail?

As we dive into December 2024, you might have noticed that the AWS Amplify Gen 2 documentation on authentication flows still leaves a bit to be desired, mainly because of the recent transition from Gen 1. So, I thought, why not write up a helpful article to deepen our understanding of these user authentication flows? Let's jump right in and explore together!

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

We need to ensure that the Root Layout is wrapped in < Authenticator /> tags, this ensures that IF the user is logged out, they cannot gain access to any page/screen within the application.&#x20;

<figure><img src=".gitbook/assets/AWS (2).png" alt=""><figcaption></figcaption></figure>
