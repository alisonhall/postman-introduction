# Introduction to Postman

![logo](./assets/logo.png)

Postman is a Chrome add-on and application which is used to fire requests to an API.

Features:

* Very lightweight and fast
* Requests can be organized in groups (called collections) and folders
* Tests can be created with verifications for certain conditions on the response
* Share workspaces or collections with other people or teams
* Publish collections as API documentation
* Run tests on collections (using the Collection Runner or Newman)
* Monitor collections
* Setup mock servers

Download the application here: https://www.getpostman.com/downloads/

------

## Table of Contents

1. [Workspace](#Workspace)
1. [Basic Requests](#Basic-Requests)
1. [Parameterized Data](#Parameterized-Data)
1. [Tests](#Tests)
1. [JSON Schema Validation](#JSON-Schema-Validation)
1. [Collections](#Collections)
1. [Collection Runner](#Collection-Runner)
1. [Newman](#Newman)
1. [Monitors](#Monitors)
1. [Dynamic Workflows](#Dynamic-Workflows)
1. [Mock Servers](#Mock-Servers)

------

## Workspace

The startup screen:

![workspace 1](./assets/workspace-1.png)

Basic interface:

![workspace 2](./assets/workspace-2.png)

1. **New** - This is where you will create a new request, collection or environment.
2. **Import** - This is used to import a collection or environment. There are options such as import from file, folder, link or paste raw text.
3. **Runner** - Automation tests can be executed through the Collection Runner. This will be discussed further in the next lesson.
4. **Open New** - Open a new tab, Postman Window or Runner Window by clicking this button.
5. **My Workspace** - You can create a new workspace individually or as a team.
6. **Invite** - Collaborate on a workspace by inviting team members.
7. **History** - Past requests that you have sent will be displayed in History. This makes it easy to track actions that you have done.
8. **Collections** - Organize your test suite by creating collections. Each collection may have subfolders and multiple requests. A request or folder can also be duplicated as well.
9. **Request tab** - This displays the title of the request you are working on. By default, "Untitled Request" would be displayed for requests without titles.
10. **HTTP Request** - Clicking this would display a dropdown list of different requests such as GET, POST, COPY, DELETE, etc. In testing, the most commonly used requests are GET and POST.
11. **Request URL** - Also known as an endpoint, this is where you will identify the link to where the API will communicate with.
12. **Save** - If there are changes to a request, clicking save is a must so that new changes will not be lost or overwritten.
13. **Params** - This is where you will write parameters needed for a request such as key values.
14. **Authorization** - In order to access APIs, proper authorization is needed. It may be in the form of a username and password, bearer token, etc.
15. **Headers** - You can set headers such as content type JSON depending on the needs of the organization.
16. **Body** - This is where one can customize details in a request commonly used in POST request.
17. **Pre-request Script** - These are scripts that will be executed before the request. Usually, pre-request scripts for the setting environment are used to ensure that tests will be run in the correct environment.
18. **Tests** - These are scripts executed during the request. It is important to have tests as it sets up checkpoints to verify if response status is ok, retrieved data is as expected and other tests.

------

## Basic Requests

The Postman Echo collection is included in your Postman app download. It’s a good way to try out different request types.

https://docs.postman-echo.com/?version=latest

![basic requests 1](./assets/basic-requests-1.png)

### GET Requests

Get requests are used to retrieve information from the given URL.

1. Set your HTTP request to GET.
2. In the request URL field, input the link
3. Click Send
4. You will see 200 OK Message
5. The results in the body are shown at the bottom

![basic requests 2](./assets/basic-requests-2.png)

### POST Requests

Post requests are different from Get request as there is data manipulation with the user adding data to the endpoint.

1. Set your HTTP request to POST.
2. Input the link in request url. Ex. https://jsonplaceholder.typicode.com/users
3. Switch to the Body tab

![basic requests 3](./assets/basic-requests-3.png)

In the Body tab,

1. Click a content type. If sending JSON data, click "raw".

    a. Select a content type (Ex. JSON)

![basic requests 4](./assets/basic-requests-4.png)

Make sure the data that you enter is formatted properly.

![basic requests 5](./assets/basic-requests-5.png)

1. Click Send.
2. For this example, "Status: 201 Created" should be displayed
3. Posted data shows up in the body

![basic requests 6](./assets/basic-requests-6.png)


------

## Parameterized Data

Instead of creating the same requests with different data, you can use variables with parameters. These data can be from a data file or an environment variable. Parameterization helps to avoid repetition of the same tests and iterations can be used for automation testing.

There are two types of variables – global and environment. Global variables are for all requests, environment variables are defined per specific environment which can be selected from a drop-down or no environment can be selected.

Parameters are created through the use of double curly brackets: `{{sample}}`.

![parameterized data 1](./assets/parameterized-data-1.png)

### Environments

To use the parameter, you need to set the environment:

1. Click the eye icon
2. Click edit to set the variable to a global environment which can be used in all collections.

![parameterized data 2](./assets/parameterized-data-2.png)

For global variables

1. Set the name of the variable and the value (which is https://jsonplaceholder.typicode.com in this example)
2. Click Save.

![parameterized data 3](./assets/parameterized-data-3.png)

Note: Always ensure that your parameters have a source, such as an environment variable or data file, to avoid errors.

------

## Tests

For a lot of people, Postman is synonymous with API testing. For some, that might mean sending and inspecting a response. It could also mean writing assertions to validate that an endpoint is returning the appropriate responses. Or, it can also mean setting up logic to mirror your workflow and automating the tests.

The easiest way to get started with writing tests in Postman is to take a look at the snippets on the right side of the Tests tab. Clicking on a snippet will append the JavaScript code into the editor. You can also write your own test code.

The idea is that in many cases you will need to do something with the response and extract a variable from it in order to use it at a later stage. This can be done in “Tests” tab.

Without good tests, it’s impossible to have full confidence in your API’s behavior, consistency, or backward compatibility. As your codebase grows and changes over time, tests will save you time and frustration by spotting breaking changes.

Writing tests in Postman is easy and uses JavaScript syntax. Testing simple things, like HTTP status codes, response times, and headers can each be done in a single line of code

Many people use Postman Collections to document their APIs, either as a collection of example requests that can be easily shared among team members, or as public API documentation for customers. For both of those use cases, it makes sense for your collection to contain detailed explanations for each of your API endpoints, walkthroughs of common API workflows, authentication requirements, lists of possible error responses, etc.

A solid test suite will include many edge cases, intentional bad inputs (to test error handling), and possibly reveal sensitive information, all of which would be irrelevant or confusing for your API’s consumers.

For all of these reasons, it's recommended that you keep your API tests in a separate collection from your API documentation.

Postman Tests are JavaScript codes added to requests that help you verify results such as successful or failed status, comparison of expected results, etc. It usually starts with pm.test. It can be compared to asserts, verify commands available in other tools.

1. Switch to the tests tab. On the right side are snippet codes.
2. From the snippets section, click on "Status code: Code is 200".
3. The example code will appear in the window.

![tests 1](./assets/tests-1.png)

Now click Send. The test result should now be displayed.

![tests 2](./assets/tests-2.png)

To compare the expected result to the actual result:

1. From the snippets section, click on "Response body:JSON value check".

![tests 3](./assets/tests-3.png)

The results:

![tests 4](./assets/tests-4.png)

### Code reuse between requests

It is very convenient for some piece of code to be re-used between a request to prevent having to copy/paste it. It is possible to do it by defining a helper function with verifications which are saved as a global variable in the first request from your test scenario.

Then from other requests, the helpers are taken from global variables and the verification functions can be used.

Setting up helpers:

```js
pm.globals.set("loadHelpers", function loadHelpers() {
    let helpers = {};

    helpers.verifyFoo1 = function verifyFoo1(value) {
        var jsonData = JSON.parse(responseBody);
        tests["Foo1 value is: " + value]
            = jsonData.args.foo1 === value;
    }

    // ...additional helpers

    return helpers;
} + '; loadHelpers();');
```

Using the saved helpers:

```js
var helpers = eval(globals.loadHelpers);
helpers.verifyFoo1('bar1');
```

------

## JSON Schema Validation

Many modern APIs use some form of JSON Schema to define the structure of their requests and responses. Postman includes the tv4 library, which makes it easy to write tests to verify that your API responses comply with your JSON Schema definitions.

Example:

```js
// Define the JSON Schema
const jsonSchema = {
  "required": ["args"],
  "properties": {
    "args": {
      "type": "object",
      "required": ["foo1", "foo2"],
      "properties": {
        "foo1": {
          "type": "string",
          "enum": ["bar1"]
        },
        "foo2": {
          "type": "string",
          "enum": ["bar2"]
        },
        "foo3": {
          "type": "string",
          "enum": ["bar3"]
        }
      }
    }
  }
};

// Test whether the response matches the schema
var jsonData = JSON.parse(responseBody);
tests["Data is valid"] = tv4.validate(jsonData, jsonSchema);
```

Of course, you probably wouldn’t want to hard code your JSON Schema in your test script, especially since you may need to use the same schema for many requests in your collection. So, instead, you could store the schema as a JSON string in a Postman environment variable. Then you can simply use the variable in your test script, like this:

```js
var jsonData = JSON.parse(responseBody);

// Load the JSON Schema
const jsonSchema = JSON.parse(globals.jsonSchema);

// Test if the JSON schema was found within the variables
tests["Schema found"] = !!jsonSchema;

if (jsonSchema) {
    // Test whether the response matches the schema
    tests["Data is valid"] = tv4.validate(jsonData, jsonSchema);
}
```

### Resuse code

You can also reuse JavaScript code the same way by leveraging the eval() function.

There’s no limit to the amount of code that can be stored in a variable and reused this way. In fact, you can use this trick to reuse entire JavaScript libraries, including many third-party libraries from NPM, Bower, and GitHub.

First request in the collection:

```js
// Save common tests in a global variable
postman.setGlobalVariable("commonTests", () => {
  // The Content-Type must be JSON
  tests["Content-Type header is set"] = postman.getResponseHeader("Content-Type") === "application/json";

  // The response time must be less than 500 milliseconds
  tests["Response time is acceptable"] = responseTime < 500;

  // The response body must include an "id" property
  var data = JSON.parse(responseBody);
  tests["Response has an ID"] = data.id !== undefined;
});
```

Other requests in the collection:

```js
Other requests in the collection:
// First, run the common tests
eval(globals.commonTests)();

// Then run any request-specific tests
tests["Status code is 200"] = responseCode.code === 200;
```

------

## Collections

Collections play an important role in organizing test suites. They can be imported and exported, making it easy to share collections amongst a team.

![collections 1](./assets/collections-1.png)

![collections 2](./assets/collections-2.png)

![collections 3](./assets/collections-3.png)

When creating a new request, you can save it directly to a collection.

1. Select the collection
2. Click "Save to ..."

![collections 4](./assets/collections-4.png)

The collection should now contain the new request:

![collections 5](./assets/collections-5.png)

------

## Collection Runner

There are two ways to run a collection which is the Collection Runner and Newman. Let's begin by executing the collection in Collection Runner.

Click on the Runner button found at the top of the page next to the Import button:

![collection runner 1](./assets/collection-runner-1.png)

![collection runner 2](./assets/collection-runner-2.png)

![collection runner 3](./assets/collection-runner-3.png)

![collection runner 4](./assets/collection-runner-4.png)

Results:

![collection runner 5](./assets/collection-runner-5.png)

1. Once tests have finished, you can see the test status if it is Passed or Failed and the results per iteration.
2. You see Pass status for the Get Requests
3. Since we did not have any tests for Post, there should be a message that the request did not have any tests.

------

## Newman

Another way to run a collection is via Newman. The main differences between Newman and Collection Runner are the following:

1. Newman is an add-on for Postman. You will need to install it separately from the Native App.
2. Newman uses the command line while Collection Runner has a GUI.
3. Newman can be used for continuous integration.

To install Newman and run our collection from it, do the following:

1. Install NodeJS using this link: http://nodejs.org/download/
2. Open the command line and enter: `npm install -g newman`

Once Newman has been installed, go back to the Postman workspace. In the Collections box, click on the three dots. Options should now appear. Select Export.

![exporting 1](./assets/exporting-1.png)

Choose Export Collection as Collection v2.1 (Recommended) then click Export.

![exporting 2](./assets/exporting-2.png)

Select your desired location then click Save.

We will also need to export our environment. Click on the eye icon beside the environment dropdown in Global, select Download as JSON. Select your desired location then click Save. It is advisable that the environment should be in the same folder as your collection.

![exporting 3](./assets/exporting-3.png)

### View of Newman running a collection

Now go back to command line and change the directory to where you have saved the collection and environment.
Ex: `cd C:\Users\Asus\Desktop\Postman Tutorial`

Run your collection using this command:
`newman run PostmanTestCollection.postman_collection.json -e Testing.postman_globals.json`

![newman 3](./assets/newman-1.png)

Here is a reference to some basic Newman codes for execution:

1. **Run a collection only**. This can be used if there is no environment or test data file dependency. `newman run <collection name>`
2. **Run a collection and environment**. The -e indicator is for environment. `newman run <collection name> -e <environment name>`
3. **Run a collection with desired no. of iterations**. `newman run <collection name> -n <no.of iterations>`
4. **Run with data file**. `newman run <collection name> --data <file name>  -n <no.of iterations> -e <environment name>`
5. **Set delay time**. This is important as tests may fail if it is run without delay due to requests being started without the previous request completing processing on the endpoint server. `newman run <collection name> -d <delay time>`

------

## Monitors

You can use Postman Monitors to automatically run your Postman tests at regular intervals, such as every night, or every 5 minutes. You’ll automatically be notified if any of your tests ever fail, and you can even integrate with a variety of third-party services, such as PagerDuty, Slack, Datadog, and more.

Postman Monitors shows your test results in the same familiar layout as the Postman collection runner, so it’s easy to compare the results to the Postman app.

![monitors 3](./assets/monitors-1.png)

------

## Dynamic Workflows

By default, the Postman collection runner, Newman, and Postman Monitors will run each request in your collection in order. But you can use the postman.setNextRequest() function to change the order. This allows you to conditionally skip certain requests, repeat requests, terminate the collection early, etc.

```js
var customer = JSON.parse(responseBody);

if (customer.id === undefined) {
  // No customer was returned, so don't run the rest of the collection
  postman.setNextRequest(null);
}
else {
  // Save the customer ID to a Postman environment variable
  postman.setEnvironmentVariable("cust_id", customer.id);

  // The "Edit Customer" request uses the "cust_id" variable
  postman.setNextRequest('Edit Customer');
}
```

------

## Mock Servers

Delays on the front- or back-end make it difficult for dependent teams to complete their work efficiently. Postman's mock servers can alleviate those delays in the development process.

Before sending an actual request, front-end developers can create a mock server to simulate each endpoint and its corresponding response in a Postman Collection. Developers can view potential responses, without spinning up a back end.

Mock servers are public by default. Public mock servers are accessible to anyone.

Private mock servers require users to add a Postman API key in the request header x-api-key, like: x-api-key\:\<your postman API key>.

### Creating a Mock Server

1. In the header toolbar, click the New button.
2. The Create New tab appears.
3. Click "Mock Server".

![mock server 1](./assets/mock-server-1.png)

Follow the rest of the instructions to set up the mock server.

------

## Resources/Tutorials

[Postman Tutorial for Beginners with API Testing Example](https://www.guru99.com/postman-tutorial.html)

[API testing tips from a Postman professional](https://blog.getpostman.com/2017/07/28/api-testing-tips-from-a-postman-professional/)

[Setting up a mock server](https://learning.getpostman.com/docs/postman/mock_servers/setting_up_mock/)

[Setting up a monitor](https://learning.getpostman.com/docs/postman/monitors/setting_up_monitor)

[Command line integration with Newman](https://learning.getpostman.com/docs/postman/collection_runs/command_line_integration_with_newman)
