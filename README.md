# Azure-REST-API
A workspace to help developers interact with the Microsoft Azure REST API. Currently under active development. 

*Please note that this repo is basically a replica of my public Postman workspace. For detailed documentation of each section/call, you can find the workspace here: https://www.postman.com/benramins/workspace/azure-rest-api - and the navigation of documentation is a lot easier!*

/---------------------------------------------------------------------------------

This workspace focuses on the backbone of any app (web, mobile, etc) that is to be developed using Azure's services. Namely, creating an SQL database and implementing a file storage system. 

To be further updated and developed. But, it's a good starting point :)

/—————————————————

This documentation assumes two things:

1) That you have downloaded the Postman app for your machine. 

2) That you have an active Azure account (free tier is perfectly fine for our purposes) 

/—————————————————

1) Create a service principal from your Azure Cloud Shell.

*Visit this link: [https://docs.microsoft.com/en-us/azure/cloud-shell/overview](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) for more details on Azure Cloud Shell. You can use Bash or PowerShell*

*A service principal in Azure is basically an identity that you create to access Azure's resources. You can use this collection with Azure's AD or ADB2C, you'll just have to change the authorization headers and environments, but the calls themselves should more or less stay constant. I would personally recommend using a service principal only for you and other developers on your team, and restricting access level as much as possible.* 

*You can tweak a bunch of stuff with the service principal (identity) that you're creating, particularly its authentication methods and access level. For the sake of this collection, we'll be going with the default settings, but I recommend reading more about these identities here: [https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps](https://docs.microsoft.com/en-us/powershell/azure/create-azure-service-principal-azureps)* 

*In this collection, we'll also be using the browser-based shell experience as I figure it's easiest for anyone who might be reading this.* 

- Go to your Azure portal
- In the top toolbar, click on the Cloud Shell button
- If you have no storage account "mounted", you'll be prompted to create one. Go ahead and create one under your subscription.
- After Azure does its thing, it should open a browser-based terminal.
- Type in this command: (you can call your service principal name whatever you want)

`az ad sp create-for-rbac -n "service principal name"`

- You should now get a list of credentials. Save these securely and protect them. We'll come back to them.
- Get your subscription id by running this command (store it as well):

`az account show --query id`

/—————————————————

2) Edit your environment variables

Now this is a bit funky - some of the credential *names* that you got will not be used the same way but their values will. Here's how they will map out:

- "tenant" will be "tenantID"
- "appId" will be "clientID"
- "password" will be "clientSecret"
- and then you will input your subscription id under "subscriptionID"
- bearerToken remains empty for now

Note: you can also add certain variables like {storageaccountname} and others you'll find in this workspace to your environment variables. I only added the variables that would personally save ME time. I often switch between storage accounts and containers etc and often create new ones, so switching between variables didn't make too much sense. But if it helps you, go for it! You can copy paste the variable names from the urls of the request (such as {storageaccountname}).

/—————————————————

P.S: you may be wondering why there are no monitors in this workspace. The beauty of using Azure is that for 99.99% of use cases, you never have to worry about any down time.

