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

Let's create a simple application: An http server. For this create a new folder and initialize it with *npm init*. *npm init* is going to ask us some data about the project and it will create a package.json file whici I will explain in the next section. You can simple press enter to accept the default for them. 

	mkdir myapp
    cd myapp
    npm init [follow the process]
    ctrl + c to exit at the end

Now open the folder in sublime and create a new file called *index.js*.
	
	