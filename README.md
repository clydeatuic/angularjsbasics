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
:+1: Experiments. Add another binding to index.html. For example: ```<p>Total number of phones: {{phones.length}}</p>```

:+1: Create a new model property in the controller and bind to it from the template. For example:
	
```$scope.name = "World";```

:+1: Then add a new binding to index.html: ```<p>Hello, {{name}}!</p>```

:+1: Refresh your browser and verify that it says "Hello, World!".

![End of Part 2](https://github.com/clydeatuic/angularjsbasics/blob/master/part2.png)

>__SUMMARY__: You now have a dynamic app that features separate model, view, and controller components

:+1: Experiments: Create a repeater in ```index.html``` that constructs a simple table:

``` html
<table>
  <tr><th>row number</th></tr>
  <tr ng-repeat="i in [0, 1, 2, 3, 4, 5, 6, 7]"><td>{{i}}</td></tr>
</table>
```

:tada: You have already finished second part.

## Steps - Part 3

>We did a lot of work in laying a foundation for the app in the last step, so now we'll do something simple; we will add full text search (yes, it will be simple!). 

>We made no changes to the controller.

:+1: Template. We added a standard HTML ```<input>``` tag and used Angular's filter function to process the input for the ```ngRepeat``` directive.

```app/index.html:```

``` html
<!doctype html>
<html lang="en" ng-app="phonecatApp">
<head>
  ... same codes here

</head>
<body ng-controller="PhoneListCtrl">

    <div class="container-fluid">
      <div class="row">
        <div class="col-md-2">
          <!--Sidebar content-->

          Search: <input ng-model="query">

        </div>
        <div class="col-md-10">
          <!--Body content-->

          <ul class="phones">
            <li ng-repeat="phone in phones | filter:query">
              {{phone.name}}
              <p>{{phone.snippet}}</p>
            </li>
          </ul>

        </div>
      </div>
    </div>

  </body>
</html>
```

>Refresh the page. The app now has a search box. Notice that the phone list on the page changes depending on what a user types into the search box.

:+1: In this step, you will add a feature to let your users control the order of the items in the phone list. The dynamic ordering is implemented by creating a new model property, wiring it together with the repeater, and letting the data binding magic do the rest of the work. 

:+1: Template. We made the following changes to the index.html template:


``` app/index.html: ```


``` html
<!doctype html>
<html lang="en" ng-app="phonecatApp">
<head>
  ... same codes here

</head>
<body ng-controller="PhoneListCtrl">

    <div class="container-fluid">
      <div class="row">
        <div class="col-md-2">
          <!--Sidebar content-->

          Search: <input ng-model="query">
            Sort by:
            <select ng-model="orderProp">
              <option value="name">Alphabetical</option>
              <option value="age">Newest</option>
            </select>

        </div>
        <div class="col-md-10">
          <!--Body content-->

          <ul class="phones">
              <li ng-repeat="phone in phones | filter:query | orderBy:orderProp">
                <span>{{phone.name}}</span>
                <p>{{phone.snippet}}</p>
              </li>
            </ul>

        </div>
      </div>
    </div>

  </body>
</html>
```

>Angular creates a two way data-binding between the select element and the orderProp model. orderProp is then used as the input for the orderBy filter.

:+1: Controller. This is a good time to talk about two-way data-binding. Notice that when the app is loaded in the browser, "Newest" is selected in the drop down menu. This is because we set orderProp to 'age' in the controller. So the binding works in the direction from our model to the UI. Now if you select "Alphabetically" in the drop down menu, the model will be updated as well and the phones will be reordered. That is the data-binding doing its job in the opposite direction — from the UI to the model.


``` app/js/controllers.js: ```


``` javascript
var phonecatApp = angular.module('phonecatApp', []);

phonecatApp.controller('PhoneListCtrl', function ($scope) {
  $scope.phones = [
    {'name': 'Nexus S',
     'snippet': 'Fast just got faster with Nexus S.',
     'age': 1},
    {'name': 'Motorola XOOM™ with Wi-Fi',
     'snippet': 'The Next, Next Generation tablet.',
     'age': 2},
    {'name': 'MOTOROLA XOOM™',
     'snippet': 'The Next, Next Generation tablet.',
     'age': 3}
  ];

  $scope.orderProp = 'age';
});
```

:tada: You have already finished third part.

## Steps - Part 4

## AngularJS Basics Original Link
* For complete tutorial: [AngularJS PhoneCatApp](https://code.angularjs.org/1.2.28/docs/tutorial)

* The project is preconfigured with a number of npm helper scripts to make it easy to run the common tasks that you will need while developing:

```$ npm start : start a local development web-server```
