# Exploring the code

The sample site is broken down into two key folders, **public**, which hosts the client-side or front-end code, and **api**, which hosts the server-side or back-end code. Below we explore the key files which make up the sample.

The code is heavily commented to explain the various components. Below are highlights of the structure of the project and particular files you will want to pay attention to.

## public

**public** holds the client-side code. It is written using HTML and "vanilla" JavaScript, meaning no frameworks are used. You can incorporate any framework you might wish.

> **NOTE:** Most frameworks like Vue.js, React and Angular require a build or bundling process which will place your front-end code into a different folder. Because of this, you may need to [update the location of your client code](troubleshooting.md#configuration) when using a framework.

### index.html

This contains the UI for the site. It consists of a two main elements:

- An unordered list to display tasks
- A textbox and button for adding tasks

### index.css

This is the stylesheet for the site. It sets the primary font and includes two settings:

- `.completed`: Sets line-through for any completed tasks
- `ul`: To remove the dot in front of each item

### local-index.js

This contains the logic for the client side. The code is heavily commented, but at a high level here are the key functions:

- `loadTasks`: Called on load to retrieve all tasks from the server
- `displayTasks`: Called after `loadTasks` to loop through all tasks and add them to the display
- `addTaskToDisplay`: Adds an individual task to the display, setting an event handler for the checkbox (to mark a task as complete) and the `completed` class if the task is completed
- `updateTask`: Event listener for each checkbox; toggles the completed status both locally and on the server by calling the API
- An event listener for `click` on the `task-register` button: Calls the API to save the new task on the server and adds the task to the display

## api

**api** contains the server side code. Our server-side code is written using [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview?WT.mc_id=academic-38860-chrhar), which is part of [Azure Static Web Apps](https://docs.microsoft.com/azure/static-web-apps/overview?WT.mc_id=academic-38860-chrhar). It follows the [standard folder structure for an Azure Function](https://docs.microsoft.com/azure/azure-functions/functions-reference#folder-structure?WT.mc_id=academic-38860-chrhar). Here are the key files which make up the server-side code.

### package.json

JavaScript based Azure Functions are like any normal Node.js application. As such, they use a **package.json** file to manage libraries and other settings. If you wish to add any new package dependencies, you do this through **package.json**. A dependency on [mongoose](https://mongoosejs.com/) has already been added.

### local.settings.json

This was introduced when we [configured our database](configuring-database.md). It contains various settings for our application to use which we can access by calling `process.env`. This file is automatically registered in **.gitignore**, so it won't be published as part of our project. The key entry in here is `CONNECTION_STRING`, which is set to the name of our connection.

### tasks/function.json

**[function.json](https://docs.microsoft.com/azure/azure-functions/functions-reference#function-code)** is the configuration file used for a function. It contains a list of [bindings](https://docs.microsoft.com/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=javascript#example&WT.mc_id=academic-38860-chrhar), which indicate how our function can be called, and what information will be passed in.

The key settings in our **function.json**:

- `methods`: Indicates the [HTTP methods](https://restfulapi.net/http-methods/) our function accepts. We have set it to accept:
  - **GET**: Returns all items
  - **POST**: Create new item
  - **PUT**: Update item
- `route`: Similar to creating routes in Express or Restify, we register routes in our function by using a path string. You can [customize the route](https://docs.microsoft.com/azure/azure-functions/functions-bindings-http-webhook-trigger?tabs=javascript#configuration&WT.mc_id=academic-38860-chrhar) to add additional parameters as needed.

### tasks/index.js

**index.js** contains the code for our Azure function. The code primarily uses [Mongoose](https://mongoosejs.com/), so if you're already familiar with the library you should recognize much of the code. If you haven't used Mongoose, the [Mongoose quick start](https://mongoosejs.com/docs/index.html) is a great starting resource. Here is the general structure of the code:

- Load the **mongoose** library and `connect` to the database
- Create a [schema](https://mongoosejs.com/docs/guide.html) for our task, which will contain `title` and `completed` properties
- Create a [model](https://mongoosejs.com/docs/models.html) for our task, which will act as the client to our database
- Set up the core code for detecting the method, and calling the appropriate function in response
  - **GET**: Calls `getTasks`, which uses the model to return all tasks from the database
  - **POST**: Calls `createTask`, which reads the body from the request, and creates a new task in the database
  - **PUT**: Retrieves the id of an existing task from `bindingData` (which provides access to the URL) and the body, and updates the task in the database
