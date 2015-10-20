---
published: true
title: Environment Setup
Description: Installing the environment to start working.
---



Our stack of development is going to be based in the MEAN Stack without the A for Angular. This is because Angular is a hard and difficult technology to learn and we think that what gives to us is not an essential plus to add it to the equation. 

So we're going to use *Node.js, Express and MongoDB* in the backend and *HTML, CSS, Javascript(jQuery)* at the frontend. 

And for the communication between the clients we're going to use *Socket.io*.

Let's setup our environment to work with it.

#Node.js

Node.js is going to be our main platform at the server side. Download it from his site [Node.js](!https://nodejs.org/), and install it.

Open a bash and see if everything gone well trying to find the node version:
	node -v

You should see something like: *v4.2.1*. So we're in! 

Now with Node.js we have installed NPM as well. This is the package manager for Node, which we can install packages to our projects or to our computer. 

Let's create a simple application: An http server. For this create a new folder and initialize it with *npm init*. *npm init* is going to ask us some data about the project and it will create a package.json file which I will explain in the next section. You can simple press enter to accept the default for them. 

	mkdir myapp
    cd myapp
    npm init [follow the process]
    ctrl + c to exit at the end

![npm init](http://i.imgur.com/arQobZz.gif)

Now open the folder in sublime and create a new file called *index.js*. This is our main entry and our file to describe and run the http server.

First we need to require (like *using* in C#) the http module:

	var http = require("http");

After that we create the server and what happens when someone enters to it:

	http.createServer(function (request, response) {

   		// Send the HTTP header 
   		// HTTP Status: 200 : OK
   		// Content Type: text/plain
   		response.writeHead(200, {'Content-Type': 'text/plain'});
   
   		// Send the response body as "Hello World"
   		response.end('Hello World\n');
	}).listen(8081);	
    
The last line blinds the port *8081* to our app. Finally output on the console some info about the port: 

	// Console will print the message
	console.log('Server running at http://127.0.0.1:8081/');


The final *index.js* file should be like this:

    var http = require("http");
    
    http.createServer(function (request, response) {
    
       // Send the HTTP header 
       // HTTP Status: 200 : OK
       // Content Type: text/plain
       response.writeHead(200, {'Content-Type': 'text/plain'});
       
       // Send the response body as "Hello World"
       response.end('Hello World\n');
    }).listen(8081);
    
    // Console will print the message
    console.log('Server running at http://127.0.0.1:8081/');
    

Now on the bash (make sure we are in the folder of the project) type:

	node index.js

And in our browser (mine is Chrome) go to: [localhost:8081](localhost:8081). And see the output.

#Express.js

Now let's install Express. Express is a framework that provide us all the necessary to make Web Applications.

For install it in our application do this:
	npm install express --save

This will install Express in our application, the *--save* flag tells to npm to add it to the *package.json* file. The *package.json* file in addition to having data about our project also have de dependencies (the packages that need to be installed) of the project. 

If we take a look now on the file we will see something like this:

    {
      "name": "httpserver",
      "version": "1.0.0",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "Alex",
      "license": "ISC",
      "description": "simple http server",
      "dependencies": {
        "express": "^4.13.3"
      }
    }
You can see now express in the dependencies array.
