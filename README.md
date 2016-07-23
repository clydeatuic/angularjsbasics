## AngularJS Basics
* Verify Node version
  ```
  $ node -v
  ```
* For complete tutorial: [AngularJS PhoneCatApp](https://code.angularjs.org/1.2.28/docs/tutorial)

* The project is preconfigured with a number of npm helper scripts to make it easy to run the common tasks that you will need while developing:

```$ npm start : start a local development web-server```
## Steps
:+1: Download Angular Phonecat
```
$ git clone https://github.com/clydeatuic/angular-phonecat.git
```
:+1: Change your current directory to ```angular-phonecat```.
```
$ cd angular-phonecat
```
:+1: The HTML page that displays "Nothing here yet!" was constructed with the HTML code shown below. The code contains some key Angular elements that we will need as we progress.

```app/index.html:```
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
:+1: Try adding a new expression to the ```index.html``` that will do some math:
```
<p>1 + 2 = {{ 1 + 2 }}</p>
```
:+1: In order to illustrate how Angular enhances standard HTML, you will create a purely static HTML page and then examine how we can turn this HTML code into a template that Angular will use to dynamically display the same result with any set of data.

>In this step you will add some basic information about two cell phones to an HTML page.

>The page now contains a list with information about two phones.
	
```app/index.html:```
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
```<p>Total number of phones: 2</p>```

>Now it's time to make the web page dynamic — with AngularJS. We'll also add a test that verifies the code for the controller we are going to add.

>There are many ways to structure the code for an application. For Angular apps, we encourage the use of the Model-View-Controller (MVC) design pattern to decouple the code and to separate concerns. With that in mind, let's use a little Angular and JavaScript to add model, view, and controller components to our app. The list of three phones is now generated dynamically from data

:+1: View and Template. In Angular, the view is a projection of the model through the HTML template. This means that whenever the model changes, Angular refreshes the appropriate binding points, which updates the view.

	The view component is constructed by Angular from this template. ```app/index.html:```
    
```html
<html ng-app="phonecatApp">
	<head>
      ...
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
    
:+1: Model and Controller. 
>The data model (a simple array of phones in object literal notation) is now instantiated within the ```PhoneListCtrl``` controller. The controller is simply a constructor function that takes a ```$scope``` parameter. ```app/js/controllers.js:```

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
