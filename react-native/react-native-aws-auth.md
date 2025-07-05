---
description: December 2024
icon: bullseye-arrow
---

# AWS Amplify Gen 2 Authentication Setup

This article is aimed at assisting those who may be experiencing difficulty in initializing their React Native and AWS Amplify Gen 2 Authentication Back-End!&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 4.01.18 pm.png" alt=""><figcaption><p>AWS Amplify Authentication Documentation</p></figcaption></figure>

### Amplify Gen 1 versus Gen 2

For those like me who are exploring the world of React Native and AWS services, namely AWS Amplify Gen2 - you would have come across an abundance of documentation, which is great! But, when you're at a beginner level just like I am, it can feel like information overload!

As of December 2024, I am working on implementing the AWS Gen 2 Authentication within my React Native web and mobile application. If you are doing this too, you would surely have come across the below message posted on the official AWS documentation website:&#x20;

<div data-full-width="false"><figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 3.59.50 pm.png" alt=""><figcaption><p>AWS Amplify Gen 2: React Native warning message</p></figcaption></figure></div>

### Why the change?

AWS Amplify has recently transitioned from Amplify Gen 1 which utilises a tooling-first experience, using a CLI/Console based workflow to create the back-end. Whereas Gen 2, utilises a code-first DX, allowing developers to succinctly express app requirements like data models, business logic, and authorization rules in TypeScript.&#x20;

Now that we know a little bit about the background, lets move on!

### Installing your NPM Dependencies

Let's get you the latest NPM packages and dependencies before we initialize your back-end! Follow these steps:

1. Open your preferred code editor - in my case, it's VS Code
2. Navigate to your project folder and open a new terminal
3. Run the commend `git pull origin main` (or master) to ensure you have the latest code on your local device - I would also recommend that you set this as a branch protection rule in your GitHub repo, this is always good practice!
4. Run the command `npm install` to ensure that you have the latest packages installed/audited
5. Run the command `npm create amplify@latest` - this will install an Amplify folder within your working tree with the following Typescript files:

<figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 4.20.47 pm.png" alt=""><figcaption><p>Working Tree after running the npm create amplfy command in your CLI</p></figcaption></figure>

6. The fastest way to get your login experience up and running is to use the AWS Authenticator UI component available in the Amplify UI library. To do this, you need to add the following dependencies to your project:

```
npm add
@aws-amplify/ui-react-native
@aws-amplify/react-native
aws-amplify
@react-native-community/netinfo
@react-native-async-storage/async-storage
react-native-safe-area-context
react-native-get-random-values
react-native-url-polyfill
```

6. Also, copy and paste the following code:

{% code overflow="wrap" %}
```
npm add --save-dev @aws-amplify/backend@latest 
@aws-amplify/backend-cli@latest typescript 
@aws-amplify/ui-react
```
{% endcode %}

### So far so good right?&#x20;

Up until this point, we have been following the official AWS documentation found here:

{% embed url="https://docs.amplify.aws/react-native/start/quickstart/#create-backend-3" %}

{% embed url="https://docs.amplify.aws/react-native/build-a-backend/auth/set-up-auth/" %}

### AWS Organization Setup

Before we can initialize your Amplify back-end, you will need to assign the correct roles and permissions to the users within your organization via the AWS Console.&#x20;

Our AWS Organization structure setup is as follows:

* Root User 🔐
  * Federated User (most of the same permissions/policies as the root user)
    * IAM Users (amplify permissions/policies only)

The above is important because in order to initialize your Amplify back-end, you will need to issue Access Keys to each user within the IAM Console. Once you have done this, we can proceed to the next step.

now for the tricky part, and the part that is not mentioned in the Amplify back-end initialization documentation above.

### How to Initialize your Amplify Gen 2 Back-End

After setting up your AWS environment variables and access credentials, copy them from your AWS account and paste them into your VS Code terminal. They should follow the format below:

<figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 4.56.04 pm.png" alt=""><figcaption><p>AWS Access Key, Secret Key and Session Token (note: keys partially redacted for security)</p></figcaption></figure>

Once the above is complete, copy and paste the following command in to your terminal:&#x20;

```
npx ampx sandbox
```

Now, you should see your Terminal initializing your backend! To confirm this, you can also check your AWS Amplify application Sandbox.&#x20;

To navigate here, follow these steps:

1. Navigate to AWS Amplify from your AWS Console
2. Click on the App that you are working on, it should display the below:

<figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 5.20.41 pm.png" alt=""><figcaption><p>How to navigate to your Sandbox deployments page</p></figcaption></figure>

3. Click on the "Manage Sandboxes" on the top right hand corner
4. You should now see the Sandbox that you created in your VS Code Terminal! If it looks like the below, then congrats 🎉

<figure><img src="../.gitbook/assets/Screenshot 2024-12-09 at 11.03.13 am.png" alt=""><figcaption><p>Successfully deployed AWS Amplify Gen 2 Sandbox</p></figcaption></figure>

5. The final step is to now run `git push` in your terminal to trigger a CI/CD build.

**Mission completed.**



I hope that this article has helped you in some way!&#x20;

Thanks for reading 😊
