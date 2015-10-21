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

Node.js is going to be our main platform at the server side. Download it from his site [Node.js](https://nodejs.org/), and install it.

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
{% highlight javascript %}

	var http = require("http");
{% endhighlight %}

After that we create the server and what happens when someone enters to it:
{% highlight javascript %}

http.createServer(function (request, response) {
    
    // Send the HTTP header 
    // HTTP Status: 200 : OK
    // Content Type: text/plain
    response.writeHead(200, {'Content-Type': 'text/plain'});
    
    // Send the response body as "Hello World"
    response.end('Hello World\n');
}).listen(8081);	
{% endhighlight %}

The last line blinds the port *8081* to our app. Finally output on the console some info about the port: 
{% highlight javascript %}

// Console will print the message
console.log('Server running at http://127.0.0.1:8081/');
{% endhighlight %}


The final *index.js* file should be like this:
{% highlight javascript %}

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
{% endhighlight %}


Now on the bash (make sure we are in the folder of the project) type:

	node index.js

And in our browser (mine is Chrome) go to: [localhost:8081](localhost:8081). And see the output.

#Express.js

Now let's install Express. Express is a framework that provide us all the necessary to make Web Applications.

For install it in our application do this:
	npm install express --save

This will install Express in our application, the *--save* flag tells to npm to add it to the *package.json* file. The *package.json* file in addition to having data about our project also have de dependencies (the packages that need to be installed) of the project. 

If we take a look now on the file we will see something like this:
{% highlight javascript %}

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
{% endhighlight %}

You can see now express in the dependencies array.

Furthermore we can install Express globally for use it wherever in our system. For example, there is a package called *Express Generator* that scaffolds an express application for us. 

Let's go change our first app to use Express on it. Open the *index.js* file again and delete everything in it. 

First require express and create and initialize it:
{% highlight javascript %}
var express = require('express');
var app = express();
{% endhighlight %}

After that, create one route for our application. This is, when the users goes to localhost:3000/ url we will send back 'Hello World!':    
{% highlight javascript %}
app.get('/', function (req, res) {
	res.send('Hello World!');
});
{% endhighlight %}

    
Now initialize the server in the port 3000 and print it in the console: 
{% highlight javascript %}
var server = app.listen(3000, function () {
    var host = server.address().address;
    var port = server.address().port;
    
    console.log('Example app listening at http://%s:%s', host, port);
});
{% endhighlight %}

    
So the final file is like this:

{% highlight javascript %}
var express = require('express');
var app = express();

app.get('/', function (req, res) {
	res.send('Hello World!');
});

var server = app.listen(3000, function () {
    var host = server.address().address;
    var port = server.address().port;
    
    console.log('Example app listening at http://%s:%s', host, port);
});
{% endhighlight %}

Now go to [http://localhost:3000/](http://localhost:3000/) and see what happens.


#MongoDB
MongoDB is going to be our database system. In difference from others like *mySql* or *SQL Express*, this is a no-SQL database which means that we won't use SQL queries or the common structure of the SQL databases with rows, columns, etc. MongoDB stores documents in JSON-like format. Is faster and easier to use, but its not suitable for all the applications where we want to have a huge amount of relation between documents because it became inconsistent. You can read more of *where don't use MongoDb* in [this](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/) article. 

By the moment its suitable for our application because we are not going to make relations between the users, only save statics and data about themselfs. Also, we will use database to store games but not relationships between them or with the users, and if we do its not going to be the *big* thing in our app. 

Let's move from this and let's install MongoDb. First go to [https://www.mongodb.org/](https://www.mongodb.org/) and downolad it. The common download is the *Windows 64-bit 2008 R2+* version if you are in a Windows 64bit based system. After downloading, open the installer and choose the *Custom* installation, and change the Location to *C:\mongodb*, and just click next. 

MongoDB have to be run from the Command Line so for doing that we have to add the PATH of the executable to our Environment Variables in Windows. For doing this **rihgt-click on My Computer/This PC > Properties > Advanced System Settings > Advanced TAB > Environment Variables**, now search in the System Variables box the variable *Path* and click on *Edit* and add this to the end (each path should be separated by one semicolon, so make sure to write it before the C) **;C:\mongodb\bin**. Now accept everything and go to the bash (restart it if it was opened). Write **mongo** and it should show some data about our mongo app. If not we have done something wrong. 

We need a folder for MongoDB to save our data, as our is going to be for testing and development pourposes we can create it on: **C:/data/db** (just create the two folders in C:/). 

## Running it and creating a database

Now let's turn on our MongoDB server typing in the bash **mongod**. Anytime we want to access the database we have to write this in a console and let the window open, if not we will close the session and we couldn't access to the DB. So, now open a new bash window and type: **mongo**. We're now inside the db, working in the Test database. For creating one new write **use newtestdb**, and now we are working in the new db.

## Adding some stuff to our database

We have a newdatabase, but anything in there, so we want to add something to it. If we want to add an user, for example:

{% highlight javascript %}

{
    "username" : "alex",
    "email" : "alex@alex.com"
}
{% endhighlight %}

So, in order for doing this we have to type in the console this: 

	db.usercollection.insert({ "username" : "alex", "email" : "alex@alex.com" })
    
And for looking if is inserted correctly:

	db.usercollection.find().pretty()

And in the output we should see the user inserted before. We can also use a visual editor for mongo as [Robomongo](http://robomongo.org/). 


# Joining the things together

We want to add the *mongo* to our *express* app. So open the project again in sublime and let's make some changes. First we need to add a framework to manage the *mongo* database from our app. We're going to use *mongoose*, so let's install it with *npm*:

	npm install mongoose --save

Once is installed we need to modify the app. We are going to add new Users to our database, so first we need to require mongoose and connect to the MongoDB database:

{% highlight javascript %}
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/test');

{% endhighlight %}

After that we must create a model for our Users: 

{% highlight javascript %}
var User = mongoose.model('User', { name: String});
{% endhighlight %}
	
Now, we need to create a new Route for when we create a new User. Inside this Route we will get the parameter in the url *(req.params.user)* and create a new User object (from our Model). After that we will save it using the Mongoose function *save*. This function will return us an error or an user. One of the both will be null, if there is an error the user is null, if there is user the error will be null. So we only get one of the both, so let's comprove if there is any error or not, if not we send back the user created. 

{% highlight javascript %}
app.get('/:user', function (req, res){
	var newUser = new User({name: req.params.user});
	console.log('The user is: '+newUser);

	newUser.save(function(error, user){
		if(error)
			console.log(error);
		else
			res.send(user);
	});
	
	res.send(500);
});

{% endhighlight %}

So the final file must be something like this:

{% highlight javascript %}
var express = require('express');
var app = express();

var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/test');

var User = mongoose.model('User', { name: String});

app.get('/:user', function (req, res){
	var newUser = new User({name: req.params.user});
	console.log('The user is: '+newUser);

	newUser.save(function(error, user){
		if(error)
			console.log(error);
		else
			res.send(user);
	});
	
	res.send(500);
});

app.get('/', function (req, res) {
  	res.send('Hello World!');
});


var server = app.listen(3000, function () {
	var host = server.address().address;
	var port = server.address().port;

	console.log('Example app listening at http://%s:%s', host, port);
});

{% endhighlight %}


Now let's start the app. Remember that we need to have **mongod** running before we start the app. When we have it, just type **node index.js** and we will have it running. Go to [http://localhost:3000/userName](http://localhost:3000/userName). And you we will create a new user called *userName*. Change the endpoint (the *userName* string) and we will create another user called whatever you want. 

# Useful links and tutorials that you should take a look

[ScotchIO - Express API](https://scotch.io/tutorials/build-a-restful-api-using-node-and-express-4): This is a must for our project. 

[ScotchIO - Mongoose](https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications): Great to know how to work with mongoose.

[ScotchIO - Authentication with Node](https://scotch.io/tutorials/easy-node-authentication-setup-and-local): We are going to use something similar to this.

[ScotchIO - Single-App with Angular](https://scotch.io/tutorials/setting-up-a-mean-stack-single-page-application): Great for learning AngularJS.

----

[ExpressJS Documentation](http://expressjs.com/)

[Mongoose Documentation](http://mongoosejs.com/)


