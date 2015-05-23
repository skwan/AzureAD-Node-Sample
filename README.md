#Azure Active Directory SDK for node.js

This Node.js package will give you with a quick and easy way to set up your first app that's integrated with Azure Active Directory. The sample apps included in download are designed to run on any platform. It also provides libraries so you can build your own node.js applications using Passport.js.

Start with either the WS-Federation or SAML 2.0 passport.js strategy, and then access the  Azure Active Directory Graph API. By the end of these walkthroughs, you should be able to build a running HTTP server with the following features:

* WebSSO using WS-Federation or SAML 2.0
* Graph API query capabiltiy using OAuth 2.0

[Refer to our Wiki](https://github.com/MSOpenTech/AzureAD-Node-Sample/wiki) for detailed walkthroughs on how to use this package.

We've released all of the source code for this running example in GitHub under an Apache 2.0 license, so feel free to clone (or even better, fork!) and provide feedback on the forums.

## Quick Start

Getting started with the sample is easy. It is configured to run out of the box with minimal setup. 

### Step 1: Download node.js for your platform
To successfully use this sample, you need a working installation of Node.js.

Install Node.js from [http://nodejs.org](http://nodejs.org). 

### Step 2: Download the sample application and modules

Next, clone the sample repo and install the NPM.

From your shell or command line:

* `$ git clone https://github.com/MSOpenTech/AzureAD-Node-Sample`

### Step 3:  Run the sample application

Using the WS-Federation protocol:

* `$ cd login-wsfed`
* `$ npm install`
* `$ node app.js`

Using the SAML 2.0 protocol:

* `$ cd login-saml`
* `$ npm install`
* `$ node app.js`

The login credentials for the sample application are:

Username: `aaUser@graphDir1.onMicrosoft.com`

Password: `P@ssword1`

### Step 4:  Optional - Register the sample with your Azure Active Directory tenant

After you've tried running the sample using the already-provided Azure AD tenant and user credentials, you can register the application in your own tenant.  To do this you will need:
- An Internet connection
- An Azure subscription (a free trial is sufficient)

Every Azure subscription has an associated Azure Active Directory tenant.  If you don't already have an Azure subscription, you can get a free subscription by signing up at [http://wwww.windowsazure.com](http://www.windowsazure.com).  All of the Azure AD features used by this sample are available free of charge.

#### Step 4.1:  Register the sample with your Azure Active Directory tenant 

1. Sign in to the [Azure management portal](https://manage.windowsazure.com).
2. Click on Active Directory in the left hand nav.
3. Click the directory tenant where you wish to register the sample application.
4. Click the Applications tab.
5. In the drawer, click Add.
6. Click "Add an application my organization is developing".
7. Enter a friendly name for the application, for example "Azure AD Node.js Sample", select "Web Application and/or Web API", and click next.
8. For the sign-on URL, enter the base URL for the sample, which is by default `http://localhost:3000/`.
9. For the App ID URI, enter `https://<your_tenant_name>/AzureAD-Node-Sample`, replacing `<your_tenant_name>` with the name of your Azure AD tenant.  Click OK to complete the registration.
10. While still in the Azure portal, click the Configure tab of your application.
11. Find the Client ID value and copy it aside, you will need this later when configuring your application.
12. Create a new key for the application.  Save the configuration so you can view the key value.  Save the key value aside for when you configure the sample.
13. In the Permissions to Other Applications configuration section, add the Read Directory Data Application Permission to Windows Azure Active Directory.  Save the configuration.

#### Step 4.2:  Configure the sample to use your Azure Active Directory tenant

1. Open the `app.js` file in either the `login-saml` or `login-wsfed` directory.
2. In the `config` var find the `identityMetadata` value and set it to `https://login.microsoftonline.com/<your_tenant_name>/federationmetadata/2007-06/federationmetadata.xml` where `<your_tenant_name>` is the name of your Azure AD tenant, e.g. contoso.onmicrosoft.com.
3. In the `config` var find the `issuer` value and set it to the App ID URI you defined earlier, `https://<your_tenant_name>/AzureAD-Node-Sample`.
4. In the `graphConfig` var find the `tenant` value and set it to `<your_tenant_name>`, e.g. contoso.onmicrosoft.com.
5. In the `graphConfig` var find the `clientid` value and set it to the client ID you saved aside earlier.
6. In the `graphConfig` var find the `clientsecret` value and set it to the secret value you saved aside earlier.


## Detailed Information


###The Technologies In This Demo

The website in this sample app demonstrates the following technologies from the Windows Azure AD from Microsoft, and includes open source modules for each scenario.

- Web Single Sign-In (WebSSO): ``` passport-azure-ad```
- Access to Windows Azure Active Directory through a RESTful Graph API: ```node-waad```


#### Web SSO: [Windows Azure Active Directory Passport.js Plug-In](https://github.com/MSOpenTech/passport-azure-ad)

With Windows Azure AD Web Single Sign-On (WebSSO) you will have the ability to seamlessly integrate your node.js application in to your existing identity platform while using the same credentials you use in the office and online.

For more information on how this module works, refer to the [README](https://github.com/MSOpenTech/passport-azure-ad) in the provided module or read it online.

#### Graph API: [Auth0's Javascript REST library for Windows Azure AD](https://github.com/auth0/node-waad)

Windows Azure AD Graph API lets you build data-driven applications using a REST-based API. You can use this REST API to query your customer data, find relationships in the directory, and customize your apps based on customer data.

For more information on how this module works, see the [README](https://github.com/auth0/node-waad) in the module or read it online.



## About The Code

Code hosted on GitHub under Apache 2.0 license

### Acknowledgements 

We would like to acknowledge the folks who own/contribute to the following projects for their support of Windows Azure Active Directory and their libraries that were used to build this sample. In places where we forked these libraries to add additional functionality, we ensured that the chain of forking remains intact so you can navigate back to the original package. Working with such great partners in the open source community clearly illustrates what open collaboration can accomplish. Thank you!

* Auth0's [WS-Federation and SAML parsing library](https://github.com/auth0/passport-wsfed-saml2)
* Auth0's [Graph API Javascript library](https://github.com/auth0/node-waad)
* Auth0's [SAML-P Library](https://github.com/auth0/node-saml)


[passport-wsfed]: https://github.com/WindowsAzureAD/passport-wsfed-saml2
[node-waad]: https://github.com/WindowsAzureAD/activedirectoryauthenticationlib-sdk-for-node

