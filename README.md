## Steps - Part 1
:+1: Download Angular Phonecat
```
$ git clone --depth=14 https://github.com/angular/angular-phonecat.git
```
:+1: Change your current directory to ```angular-phonecat```.
```
$ cd angular-phonecat
```
:+1: Verify Node version
```
$ node -v
```
:+1: Once you have Node.js installed on your machine you can download the tool dependencies by running: (Note: This might take a while to download all dependencies, it depends on your internet connection)
```
$ npm install
```
:+1: You are now ready to build the AngularJS phonecat app. In this step, you will become familiar with the most important source code files, learn how to start the development servers bundled with angular-seed, and run the application in the browser.
```
$ git checkout -f step-1
```
:+1: Running Development Web Server
```
$ npm start
```
:+1: This will create a local webserver that is listening to port 8000 on your local machine. You can now browse to the application at:
```
http://localhost:8000
```
:+1: Hit CTRL-C to stop the server
```
CTRL-C
```
:+1: Navigate to ``` angular-phonecat ``` directory and modify the ``` index.html ```
```
app/index.html:
```
:+1: The HTML page that displays "Nothing here yet!" was constructed with the HTML code shown below. The code contains some key Angular elements that we will need as we progress.
``` html
<!doctype html>
<html lang="en" ng-app>
<head>
  <meta charset="utf-8">
  <title>My HTML File</title>
  <link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.css">
  <link rel="stylesheet" href="css/app.css">
  <script src="bower_components/angular/angular.js"></script>
</head>
<body>

  <p>Nothing here {{'yet' + '!'}}</p>

</body>
</html>
```
:+1: Refresh the browser to update the page and The HTML page that displays ``` Nothing here yet! ``` was constructed with the HTML code shown below. The code contains some key Angular elements that we will need as we progress.
```
Nothing here yet! 
```
:+1: Try adding a new expression to the ```index.html``` that will do some math:
```
<p>1 + 2 = {{ 1 + 2 }}</p>
```
:+1: In order to illustrate how Angular enhances standard HTML, you will create a purely static HTML page and then examine how we can turn this HTML code into a template that Angular will use to dynamically display the same result with any set of data.

>In this step you will add some basic information about two cell phones to an HTML page.

>The page now contains a list with information about two phones.
	
``` app/index.html: ```
``` html
<ul>
  <li>
    <span>Nexus S</span>
    <p>
      Fast just got faster with Nexus S.
    </p>
  </li>
  <li>
    <span>Motorola XOOM™ with Wi-Fi</span>
    <p>
      The Next, Next Generation tablet.
    </p>
  </li>
</ul>
```
Try adding more static HTML to index.html. For example:
``` <p>Total number of phones: 2</p> ```

![End of Part 1](https://github.com/clydeatuic/angularjsbasics/blob/master/part1.png)

:tada: You have already finished the first part.

## Steps - Part 2

:+1: Now it's time to make the web page dynamic — with AngularJS. We'll also add a test that verifies the code for the controller we are going to add.

>There are many ways to structure the code for an application. For Angular apps, we encourage the use of the Model-View-Controller (MVC) design pattern to decouple the code and to separate concerns. With that in mind, let's use a little Angular and JavaScript to add model, view, and controller components to our app. The list of three phones is now generated dynamically from data

:+1: View and Template. In Angular, the view is a projection of the model through the HTML template. This means that whenever the model changes, Angular refreshes the appropriate binding points, which updates the view.

	The view component is constructed by Angular from this template. 

``` app/index.html: ```
    
``` html
<!doctype html>
<html lang="en" ng-app="phonecatApp">
<head>
  <meta charset="utf-8">
  <title>My HTML File</title>
  <link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.css">
  <link rel="stylesheet" href="css/app.css">
  <script src="bower_components/angular/angular.js"></script>

  <script src="js/controllers.js"></script>
  
</head>
<body ng-controller="PhoneListCtrl">

    <ul>
      <li ng-repeat="phone in phones">
        {{phone.name}}
        <p>{{phone.snippet}}</p>
      </li>
    </ul>
  </body>
</html>
```
    
:+1: Model and Controller. The data model (a simple array of phones in object literal notation) is now instantiated within the ```PhoneListCtrl``` controller. The controller is simply a constructor function that takes a ```$scope``` parameter. 
>If you don't have ```js``` folder inside ```app/``` , kindly create ```controllers.js``` .

``` app/js/controllers.js: ```

``` javascript
var phonecatApp = angular.module('phonecatApp', []);

phonecatApp.controller('PhoneListCtrl', function ($scope) {
  $scope.phones = [
    {'name': 'Nexus S',
     'snippet': 'Fast just got faster with Nexus S.'},
    {'name': 'Motorola XOOM™ with Wi-Fi',
     'snippet': 'The Next, Next Generation tablet.'},
    {'name': 'MOTOROLA XOOM™',
     'snippet': 'The Next, Next Generation tablet.'}
  ];
});
```
* Experiments

>Add another binding to index.html. For example:

```<p>Total number of phones: {{phones.length}}</p>```

>Create a new model property in the controller and bind to it from the template. For example:
	
```$scope.name = "World";```

>Then add a new binding to index.html:
	
```<p>Hello, {{name}}!</p>```

>Refresh your browser and verify that it says "Hello, World!".

>__SUMMARY__: You now have a dynamic app that features separate model, view, and controller components

## AngularJS Basics Updated Version
* Verify Node version
  ```
  $ node -v
  ```
* For complete tutorial: [AngularJS PhoneCatApp](https://code.angularjs.org/1.2.28/docs/tutorial)

* The project is preconfigured with a number of npm helper scripts to make it easy to run the common tasks that you will need while developing:

```$ npm start : start a local development web-server```
