# Getting started

As you might expect, we'll need a few tools and accounts to get started. Once those are setup, we can focus on setting up our starting site and get to the fun part - coding!

- Install tooling
- Generate the starter site
- Create your Azure Static Web App

## Create GitHub and Azure accounts

Azure Static Web Apps integrates with GitHub via [GitHub Actions](https://github.com/features/actions?WT.mc_id=academic-38860-chrhar). As such, we'll need both Azure and GitHub accounts. If you're a student, there are a host of free services available with Azure for Students!

- [Sign up for GitHub Student Developer Pack](https://education.github.com/pack), which grants access to GitHub Pro for free and numerous third party offers
- [Sign up for Azure for Students](https://aka.ms/a4s?WT.mc_id=academic-38860-chrhar), which includes $100 in free credit you can use over the course of the year, and access to several free services
  - If you're not a student, you can still [access $200 on Azure](https://azure.microsoft.com/free?WT.mc_id=academic-38860-chrhar) (valid for 30 days)

## Install local tooling

We're going to use [Visual Studio Code](https://code.visualstudio.com?WT.mc_id=academic-38860-chrhar) as our development environment. With Code you're able to write apps using whatever language and framework you choose. There's also a robust [marketplace](https://marketplace.visualstudio.com/vscode?WT.mc_id=academic-38860-chrhar) which includes some wonderful extensions, including a few we're going to take advantage of.

- [Git](https://git-scm.com/downloads) (if not already installed)
- [Node.js version **12**](https://nodejs.org/dist/latest-v12.x/)
  - **Only version 12 is supported at the time of this writing**
- [Azure Functions Core Tools](https://www.npmjs.com/package/azure-functions-core-tools)
- [Install Visual Studio Code](https://code.visualstudio.com?WT.mc_id=academic-38860-chrhar) (if not already installed)
- Install extensions
  - [Azure Functions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions?WT.mc_id=academic-38860-chrhar), which we'll use to add server-side resources
  - [Azure Static Web Apps](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurestaticwebapps?WT.mc_id=academic-38860-chrhar), which we'll use to create our Static Web App
  - [Azure Databases](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb?WT.mc_id=academic-38860-chrhar), which we'll use to manage our database
  - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer?WT.mc_id=academic-38860-chrhar), a wonderful extension for local development

## Generate starter repository

To streamline the creation of your app we've created a template with code ready for you to use! You'll create a new repository on GitHub based on this template.

- Navigate to [the GitHub template](https://github.com/geektrainer/aswa-starter/generate)
- Name your new repository
- Click **Create repository from template**

## Clone the repository

With the repository created, let's clone the code locally and open it in Visual Studio Code.Open a command-line or terminal window and execute the following commands.

> **NOTE**: Replace **\<YOUR_GITHUB_ACCOUNT_NAME\>** with your GitHub account name and **\<YOUR_REPOSITORY_NAME\>** with the name of your repository)

```bash
git clone https://github.com/<YOUR_GITHUB_ACCOUNT_NAME>/<YOUR_REPOSITORY_NAME>
cd <YOUR_REPOSITORY_NAME>
code .
```

## Deploying to Azure Static Web Apps

Let's setup our deployment! [Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview?WT.mc_id=academic-38860-chrhar) manages deployment by using a GitHub Action. In a nutshell, every time you push or merge new code into your **main** branch a script will run to redeploy your code. We're going to use Visual Studio Code to set everything up in Azure. 

- Start by clicking the Azure icon on your toolbar

![Azure logo](images/Azure.png)

- In the **STATIC WEB APPS** section, sign in to both GitHub and Azure as prompted
- Click **Create Static Web App**

![Create static web app](images/create-static-webapp.png)

> **IMPORTANT** Make sure there is no forward slash (**/**) in front of **public** when setting the location of client code

- In the dialog box, provide the following information as prompted
  - Name of your site
  - Name of the branch (main by default)
  - **custom** for the build preset
  - **public** for the location of your app
  - **api** for the location of your Azure Functions code
  - Empty the location of your client code (it's already built, so no special folder is needed)
  - Choose a region near you

Congratulations! You've now created and deployed your site! The deployment process will take just a couple of minutes.

## Browsing your site and next steps

After a couple of minutes have passed, right click your new site in the Static Web Apps extension and select **Browse Site**. You can see your site live!

You will receive a message on the site about [configuring your database](configuring-database.md), which is our next step!.

> **NOTE**: You will notice the URL is set to a random couple of words followed by a hex value. Fortunately, you can [setup your own custom domain](https://docs.microsoft.com/azure/static-web-apps/custom-domain?WT.mc_id=academic-38860-chrhar).
