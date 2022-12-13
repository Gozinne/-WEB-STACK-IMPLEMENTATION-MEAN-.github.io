# WEB-STACK-IMPLEMENTATION-MEAN-.github.io
</a>

![Contributors](https://img.shields.io/github/contributors/Gozinne/WEB-STACK-IMPLEMENTATION-MEAN-.github.io?style=plastic)
![Forks](https://img.shields.io/github/forks/Gozinne/WEB-STACK-IMPLEMENTATION-MEAN-.github.io)
![Stars](https://img.shields.io/github/stars/Gozinne/WEB-STACK-IMPLEMENTATION-MEAN-.github.io)
![Licence](https://img.shields.io/github/license/Gozinne/WEB-STACK-IMPLEMENTATION-MEAN-.github.io)
![Issues](https://img.shields.io/github/issues/Gozinne/WEB-STACK-IMPLEMENTATION-MEAN-.github.io)

## MEAN Stack Overview

The [MEAN](http://meanjs.org/docs.html) stack is a collection of JavaScript-based technologies used to construct online applications. 
MEAN is a JavaScript application that runs from client to server to a database. 
The MEAN architecture is designed to make working with JSON and developing web apps in JavaScript as simple as possible.

<img
  src="https://user-images.githubusercontent.com/80969889/207283053-7f858cd9-610b-4652-ae44-7cebc70de0a2.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***
MEAN Stack is a collection of four distinct technologies that work together to create dynamic web apps and webpages. It is an abbreviation for
* M: [MongoDB](https://www.mongodb.com/)
* E: [ExpressJS](https://expressjs.com/)
* A: [AngularJS](https://angular.io/)
* N: [Node.js](https://nodejs.org/en/)

This article delves into the fundamentals of the MEAN stack and demonstrates how to build a simple book registration web form.

### Why use MEAN?
* It is budget-friendly due to its low development costs, high flexibility and efficiency.
* MEAN provides isomorphic coding.
* It has the quickest method to arrive at Minimal Viable Product
* Mean has a large collection of JavaScript Modules that are extremely useful to developers and provide cloud compatibility.

### Requirements

The following items are required to begin and complete this project.
* An account logged into the AWS console.
* Open an AWS EC2 instance.
* Run the EC2 instance on Ubuntu-20 and set the network security to: SSH,Port:22; HTTP,Port:80.
* Connect VScode or MobaXterm to the EC2 instance and launch a new terminal.

<img
  src= "https://user-images.githubusercontent.com/80969889/207286912-a1856960-fc3b-4dfe-93c8-cd3cbbc4c38b.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

## Backend Installation
### Install NodeJs

// Update Ubuntu
```
sudo apt update
```
// Upgrade ubuntu
```
sudo apt upgrade
```
There are three ways to install Node.js and npm on Ubuntu 20.04:

* Install Node.js and npm from the Ubuntu repository 
// Run the following commands to update the package index and install Node.js and npm
```
sudo apt update
```
```
sudo apt install nodejs npm
```
// Once done, verify the installation by running
```
nodejs --version
```
The output will be as follows: **v10.19.0**

* Installing Node.js and npm from NodeSource
// Run the following command as a user with sudo privileges to download and execute the NodeSource installation script
```
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```
// Once the NodeSource repository is enabled, install Node.js and npm
```
sudo apt install nodejs
```
The nodejs package contains both the node and npm binaries.
// Verify that the Node.js and npm were successfully installed by printing their versions
```
node --version
```
The output will be as follows: **v14.2.0Copy**
```
npm --version
```
The output will be as follows: **6.14.4**
// To be able to compile native addons from npm you’ll need to install the development tools
```
sudo apt install build-essential
```

* Installing Node.js and npm using NVM
// install the [nvm](https://github.com/nvm-sh/nvm#installing-and-updating) script
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
// Run the following command to use it
```
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
// Once the script is in your PATH, verify that nvm was properly installed by typing
```
nvm --version
```
The output will be as follows: **0.35.3**

// To get a list of all Node.js versions that can be installed with nvm, run
```
nvm list-remote
```
// To install the latest available version of Node.js, run
```
nvm install node
```
The output should look something like this
`
Checksums matched!
Now using node v14.2.0 (npm v6.14.4)
Creating default alias: default -> node (-> v14.2.0)
`
// Once the installation is completed, verify it by printing the Node.js version
```
node --version
```
The output will be as follows: **v14.2.0**
// Let’s install two more versions, the latest LTS version and version 10.9.0
```
nvm install --lts
```
```
nvm install 10.9.0
```
// List the installed Node.js versions by typing
```
nvm ls
```
The output should look something like this:
`
>      v10.9.0
       v12.16.3
        v14.2.0
default -> node (-> v14.2.0)
node -> stable (-> v14.2.0) (default)
stable -> 14.2 (-> v14.2.0) (default)
iojs -> N/A (default)
unstable -> N/A (default)
lts/* -> lts/erbium (-> v12.16.3)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.20.1 (-> N/A)
lts/erbium -> v12.16.3
`
// To change the currently active version enter
```
nvm use 12.16.3
```
// To change the default Node.js version, run the following command
```
nvm alias default <version to be changed to>
```

### Install MongoDB

// Add Certificates
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
```
// Install MongoDB
```
sudo apt install -y mongodb
```
// Start the server
```
sudo service mongodb start
```
// Verify that the service is up and running
```
sudo systemctl status mongodb
```
// Install body-parser package

To handle JSON files sent in requests to the server, we require the 'body-parser' package.
// Install the package
```
sudo npm install body-parser
```
// Create a folder named ‘Books’
```
mkdir Books && cd Books
```
// In the Books directory, Initialize npm project
```
npm init
``` 
// Add a file to it named server.js
```
vi server.js
```
// Copy and paste the web server code below into the server.js file
```
var express = require('express');
var bodyParser = require('body-parser');
var app = express();
app.use(express.static(__dirname + '/public'));
app.use(bodyParser.json());
require('./apps/routes')(app);
app.set('port', 3300);
app.listen(app.get('port'), function() {
    console.log('Server up: http://localhost:' + app.get('port'));
});
```
### Install ExpressJs and set up routes to the server

Mongoose package which provides a straightforward, [schema](vhttps://www.ibm.com/cloud/learn/database-schema)-based solution to model the application data. Also to establish a schema for the database to store data of the book register.

// Install mongoose, a Node.js package that simplifies dealing with MongoDB, to construct a Schema and a model
```
sudo npm install express mongoose
```
// In ‘Books’ folder, create a folder named apps
```
mkdir apps && cd apps
```
// Create a file named routes.js
```
vi routes.js
```  
/ Copy and paste the code below into routes.js
```
var Book = require('./models/book');
module.exports = function(app) {
  app.get('/book', function(req, res) {
    Book.find({}, function(err, result) {
      if ( err ) throw err;
      res.json(result);
    });
  }); 
  app.post('/book', function(req, res) {
    var book = new Book( {
      name:req.body.name,
      isbn:req.body.isbn,
      author:req.body.author,
      pages:req.body.pages
    });
    book.save(function(err, result) {
      if ( err ) throw err;
      res.json( {
        message:"Successfully added book",
        book:result
      });
    });
  });
  app.delete("/book/:isbn", function(req, res) {
    Book.findOneAndRemove(req.query, function(err, result) {
      if ( err ) throw err;
      res.json( {
        message: "Successfully deleted the book",
        book: result
      });
    });
  });
  var path = require('path');
  app.get('*', function(req, res) {
    res.sendfile(path.join(__dirname + '/public', 'index.html'));
  });
};
```
// In the ‘apps’ folder, create a folder named models
```
mkdir models && cd models
```
// Create a file named book.js
```
vi book.js
```
// Copy and paste the code below into ‘book.js’
```
var mongoose = require('mongoose');
var dbHost = 'mongodb://localhost:27017/test';
mongoose.connect(dbHost);
mongoose.connection;
mongoose.set('debug', true);
var bookSchema = mongoose.Schema( {
  name: String,
  isbn: {type: String, index: true},
  author: String,
  pages: Number
});
var Book = mongoose.model('Book', bookSchema);
module.exports = mongoose.model('Book', bookSchema);
```

## Frontend Installation
### Access the routes with AngularJS

// Change the directory back to ‘Books’
```
cd ../..
```
// Create a folder named public
```
mkdir public && cd public
```
// Add a file named script.js
```
vi script.js
``` 
// Copy and paste the Code below (controller configuration defined) into the script.js file
```
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
  $http( {
    method: 'GET',
    url: '/book'
  }).then(function successCallback(response) {
    $scope.books = response.data;
  }, function errorCallback(response) {
    console.log('Error: ' + response);
  });
  $scope.del_book = function(book) {
    $http( {
      method: 'DELETE',
      url: '/book/:isbn',
      params: {'isbn': book.isbn}
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
  $scope.add_book = function() {
    var body = '{ "name": "' + $scope.Name + 
    '", "isbn": "' + $scope.Isbn +
    '", "author": "' + $scope.Author + 
    '", "pages": "' + $scope.Pages + '" }';
    $http({
      method: 'POST',
      url: '/book',
      data: body
    }).then(function successCallback(response) {
      console.log(response);
    }, function errorCallback(response) {
      console.log('Error: ' + response);
    });
  };
});
```
// In the public folder, create a file named index.html
```
vi index.html
``` 
// Copy and paste the code below into index.html file
```
<!doctype html>
<html ng-app="myApp" ng-controller="myCtrl">
  <head>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.4/angular.min.js"></script>
    <script src="script.js"></script>
  </head>
  <body>
    <div>
      <table>
        <tr>
          <td>Name:</td>
          <td><input type="text" ng-model="Name"></td>
        </tr>
        <tr>
          <td>Isbn:</td>
          <td><input type="text" ng-model="Isbn"></td>
        </tr>
        <tr>
          <td>Author:</td>
          <td><input type="text" ng-model="Author"></td>
        </tr>
        <tr>
          <td>Pages:</td>
          <td><input type="number" ng-model="Pages"></td>
        </tr>
      </table>
      <button ng-click="add_book()">Add</button>
    </div>
    <hr>
    <div>
      <table>
        <tr>
          <th>Name</th>
          <th>Isbn</th>
          <th>Author</th>
          <th>Pages</th>
 
        </tr>
        <tr ng-repeat="book in books">
          <td>{{book.name}}</td>
          <td>{{book.isbn}}</td>
          <td>{{book.author}}</td>
          <td>{{book.pages}}</td>
 
          <td><input type="button" value="Delete" data-ng-click="del_book(book)"></td>
        </tr>
      </table>
    </div>
  </body>
</html>
```
// Change the directory back up to Books
```
cd ..
```
// Start the server by running this command:
```
node server.js
```
Now a new port **3300** should be added to **inbound rules** under **security groups** on the EC2 instance in use for the above result to occur: http:public-IP:3300

This is how your WebBook Register Application will look in the browser:







