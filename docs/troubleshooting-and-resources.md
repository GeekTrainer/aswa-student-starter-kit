# Resources

If you are looking to learn more about the products and frameworks used in this sample, you can check out the following:

- [Mongoose](https://mongoosejs.com/)
- [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview?WT.mc_id=academic-38860-chrhar)
- [Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview?WT.mc_id=academic-38860-chrhar)
- [Cosmos DB with MongoDB API](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction?WT.mc_id=academic-38860-chrhar)
- [Azure Static Web App Samples](https://github.com/microsoft/static-web-apps-gallery-code-samples?WT.mc_id=academic-38860-chrhar)

## Troubleshooting

Despite our best efforts, nobody writes perfect code. When something goes wrong we need to figure out what happened. Here are a few tips, tricks and resources to help you out.

### Common error messages when running locally

#### Exceeded language worker restart retry count for runtime:node. Shutting down and proactively recycling the Functions Host to recover

At the time of this writing, Azure Functions only supports Node.js 12. If you receive the above error message, it's likely because you have version 14 (or later) installed.

Troubleshooting steps:

- If you are using [nvm](https://github.com/nvm-sh/nvm), execute the following commands

```bash
nvm install 12
nvm use 12
```

- If you are not using nvm, uninstall Node.js 14 and [install Node.js 12](https://nodejs.org/dist/latest-v12.x/)

> **TIP**: Using a tool like nvm makes managing Node.js and packages easier

#### Worker was unable to load function tasks: 'Error: Cannot find module 'mongoose'

This error message (or any other indicating a missing module) typically indicates `npm install` wasn't executed in the directory containing the functions (**api** in our case). We can resolve this by executing the following commands in a terminal or command window in the directory containing our project.

```bash
cd api
npm install
```

#### API returns a 404

When hosting your site locally, the Functions host and Live Server host run on different ports. A proxy needs to be set for Live Server to route requests to your API. You can do this by ensuring the file **.vscode/settings.json** has the following content:

```json
{
    "azureFunctions.deploySubpath": "api",
    "azureFunctions.postDeployTask": "npm install",
    "azureFunctions.projectLanguage": "JavaScript",
    "azureFunctions.projectRuntime": "~3",
    "debug.internalConsoleOptions": "neverOpen",
    "azureFunctions.preDeployTask": "npm prune",
    "liveServer.settings.proxy": {
        "enable": true,
        "baseUri": "/api",
        "proxyUri": "http://127.0.0.1:7071/api"
    }
}
```
