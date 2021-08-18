# Azure Static Web Apps and Mongoose starter kit

[Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview) is a great hosting solution for full stack web applications. Static Web Apps supports whatever front-end framework you wish to use (including React, Vue.js, Angular and Svelte), and hosts back-end code on [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview). You can add any services you might like, such as [Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) for AI or [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/) for NoSQL.

This starter kit is designed to help get you up and running with one of the most common scenarios - a Node.js based application using Mongoose. The front-end is built using vanilla JavaScript, allowing you to later incorporate whatever front-end framework you choose. You're also free to continue to build upon this starter, adding AI, modifying the data structure, or whatever else you might like to do!

## Site overview

The sample site is a basic task manager. You have the ability to add tasks to a list, and then check or uncheck them to mark them as completed. It is built with the following technologies:

- Hosting: [Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview?WT.mc_id=academic-38860-chrhar)
- Database: [Azure Cosmos DB (with MongoDB API)](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction?WT.mc_id=academic-38860-chrhar)
- Server API: JavaScript/Node.js on [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview?WT.mc_id=academic-38860-chrhar) (hosted in Azure Static Web Apps)
- Data library: [Mongoose](https://mongoosejs.com/)

## Setup steps

We've provided the necessary steps to configure and deploy the site, as well as setup your local environment for development. It's recommended you start from the top and work your way down.

- [Getting started and deploying the website](docs/getting-started.md)
- [Configuring and deploying the database](docs/configuring-database.md)
- [Exploring the code](docs/exploring-code.md)
- [Running the code locally and making updates](docs/local-dev.md)
- [Troubleshooting and resources](docs/troubleshooting-and-resources.md)

## Creating GitHub and Azure accounts

Azure Static Web Apps integrates with GitHub via [GitHub Actions](https://github.com/features/actions). As such, we'll need both Azure and GitHub accounts. If you're a student, there are a host of free services available with [Azure for Students](https://aka.ms/a4s?WT.mc_id=academic-38860-chrhar)!

- [Sign up for GitHub Student Developer Pack](https://education.github.com/pack?WT.mc_id=academic-38860-chrhar), which grants access to GitHub Pro for free and numerous third party offers
- [Sign up for Azure for Students](https://aka.ms/a4s?WT.mc_id=academic-38860-chrhar), which includes $100 in free credit you can use over the course of the year, and access to several free services
  - If you're not a student, you can still [access $200 on Azure](https://azure.microsoft.com/free?WT.mc_id=academic-38860-chrhar) (valid for 30 days)
