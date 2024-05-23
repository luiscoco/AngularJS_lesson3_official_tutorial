# AngularJS Official Tutorial explained step by step

## 1. Prerequisites

The latest version of AngularJS is 1.8.3

If you are using Angular Framework higher versions you should first uninstall it from your computer

```
npm uninstall -g @angular/cli
```

![image](https://github.com/luiscoco/AngularJS_brief_summary/assets/32194879/b5706ba3-81c3-4721-a823-efa8abf93680)

Now we install the AngularJS in our laptop. Run this command

```
npm install -g angular@1.8.2
```

![image](https://github.com/luiscoco/AngularJS_brief_summary/assets/32194879/617ec53f-ce30-4b18-8c82-4cee87afc305)

## 2. Step 0: Bootstraping

Initialize the project directory

```
mkdir angularjs-app
cd sample2_basic
```

We open VSCode with this command

```
code .
```

Then we initialize/create the **package.json** file ruuning this command (OPTIONAL)

```
npm init -y
```

We install angular dependencies with this command

```
npm install angular
```

We have an optinal way for installing the dependencies: **bootstrap.css** and **angular.js** files

We can create manually the folders structure (with **mkdir**) and then download the libraries with **curl** command

```
mkdir -p lib/bootstrap/dist/css
cd lib/bootstrap/dist/css
curl -O https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.css
```

```
mkdir -p lib/angular
cd lib/angular
curl -O https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.js
```

We create the folders and files project structure

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/d3939a9c-cd21-4164-b3db-3fa832fd8dfb)

We copy the following source code 

**app/index.html**

```html
<!doctype html>
<html lang="en" ng-app>
  <head>
    <meta charset="utf-8">
    <title>My HTML File</title>
    <link rel="stylesheet" href="lib/bootstrap/dist/css/bootstrap.css" />
    <script src="lib/angular/angular.js"></script>
  </head>
  <body>
    <p>Nothing here {{'yet' + '!'}}</p>
  </body>
</html>
```

This is the code architecture explanation

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/6df09bff-0ae6-4d3f-9bd9-35902a827299)

To run the applicaton we right click on the **index.html** file and select the menu option **Open with Live Server**

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/352c0e29-c4bc-44d8-8a43-3810d211a17c)

This is the output we see

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/759b094b-f183-4cdd-9ab2-90dcfc03a304)


## 3.  Step 1: Static Template 

We will create a purely **static HTML page** and then examine how we can turn this HTML code into a **template** that AngularJS will use to **dynamically display** the same result with any set of data

```html
<html lang="en" ng-app>
  <head>
    <meta charset="utf-8">
    <title>Google Phone Gallery</title>
    <link rel="stylesheet" href="lib/bootstrap/dist/css/bootstrap.css" />
    <link rel="stylesheet" href="app.css" />
    <script src="lib/angular/angular.js"></script>
  </head>
  <body>

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

  </body>
</html>
```

```css
body {
    padding-top: 20px;
  }
```

This is the project folders and files structure

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/7f3c2fb7-2fc1-4386-8200-50116cfd1bfc)

Now we can run the application and see the output

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/b5d2cb53-5965-4156-9438-a6d5ce5d2206)

## 4. Step 2: AngularJS Template

Now, it's time to make the **web page dynamic** — with **AngularJS**

We will also add a test that verifies the code for the controller we are going to add

For AngularJS applications, we encourage the use of the **Model-View-Controller (MVC)** design pattern to decouple the code and separate concerns

With that in mind, let's use a little AngularJS and JavaScript to add **models**, **views**, and **controllers** to our app

The list of three phones is now generated **dynamically** from data

This is the application source code

**index.html**

```html
<html lang="en" ng-app="phonecatApp">
  <head>
    <meta charset="utf-8">
    <title>Google Phone Gallery</title>
    <link rel="stylesheet" href="lib/bootstrap/dist/css/bootstrap.min.css" />
    <link rel="stylesheet" href="app.css" />
    <script src="lib/angular/angular.min.js"></script>
    <script src="app.js"></script>
  </head>
  <body ng-controller="PhoneListController">

    <ul>
      <li ng-repeat="phone in phones">
        <span>{{phone.name}}</span>
        <p>{{phone.snippet}}</p>
      </li>
    </ul>

  </body>
</html>
```

**app.css**

```css
body {
    padding-top: 20px;
  }
```

**app.js**

```javascript
'use strict';

// Define the `phonecatApp` module
var phonecatApp = angular.module('phonecatApp', []);

// Define the `PhoneListController` controller on the `phonecatApp` module
phonecatApp.controller('PhoneListController', function PhoneListController($scope) {
  $scope.phones = [
    {
      name: 'Nexus S',
      snippet: 'Fast just got faster with Nexus S.'
    }, {
      name: 'Motorola XOOM™ with Wi-Fi',
      snippet: 'The Next, Next Generation tablet.'
    }, {
      name: 'MOTOROLA XOOM™',
      snippet: 'The Next, Next Generation tablet.'
    }
  ];
});
```

**app.spec.js**

```javascript
'use strict';

describe('PhoneListController', function() {

  beforeEach(module('phonecatApp'));

  it('should create a `phones` model with 3 phones', inject(function($controller) {
    var scope = {};
    var ctrl = $controller('PhoneListController', {$scope: scope});

    expect(scope.phones.length).toBe(3);
  }));

});
```

This is the application architecture

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/db76e45c-12bd-48bd-9d34-853695f2d550)

### How to run the application

We first have to define the project dependencies in the **package.json** file

**package.json**

```json
{
  "name": "angularjs_official_sample_step4",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "dependencies": {
    "bootstrap": "3.3.x"
  },
  "devDependencies": {
    "angular": "^1.8.3",
    "angular-mocks": "^1.8.3",
    "jasmine-core": "^5.1.2",
    "karma": "^6.4.3",
    "karma-chrome-launcher": "^3.2.0",
    "karma-jasmine": "^5.1.0",
    "karma-ng-html2js-preprocessor": "^1.0.0"
  }
}
```

To install the above dependencies we execute the command

```
npm i
```

or 

```
npm install
```

The file **package-lock.json** file will be created

Also the libraries will be installed in **node_modules**

This is the project **folders and files structure**

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/c10ef763-1122-46c6-97ee-1d9aa8bf9f0f)

To run the application we right click on the **index.html** file and selecting the **Open with Live Server** menu option

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/45071574-b9ec-4485-8131-fc0c7e6c8497)

This is the application output

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/3010e7f1-edd5-4600-bda1-26de8318ea02)

### How to run the application tests

Install Karma CLI: Install **Karma's** command-line interface globally

```
npm install -g karma-cli
```

Then install the required **dependencies**:

```
npm install karma karma-jasmine jasmine-core karma-chrome-launcher karma-ng-html2js-preprocessor --save-dev
```

Create a **Karma Configuration File**:

```
karma init karma.conf.js
```

During the setup, answer the prompts as follows:

Testing framework: Jasmine

Use Require.js: No

Capture browsers: Chrome (you can add more browsers later)

Test result reporter: progress (or choose as per your preference)

Other questions: default options should be fine

Modify the karma.conf.js file to **include your application and test files**

```
   // list of files / patterns to load in the browser
    files: [
      'node_modules/angular/angular.js',
      'node_modules/angular-mocks/angular-mocks.js',
      'app/*.js',
      'app/*.spec.js'
    ],
```

To **Run the Tests** execute this command: 

```
karma start karma.conf.js
```

This is the output we get

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/ef75f09d-0a6e-4f05-85f2-2476c570bdf4)

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/96b28446-6299-4da5-88ab-ba4f8393a9a7)

## 5. Step 3: Components

In the previous step, we saw how a controller and a template worked together to convert a static HTML page into a dynamic view

Since this combination (**template + controller**) is such a common and **recurring pattern**, AngularJS provides an easy and concise way to combine them together into reusable and isolated entities, known as **components**

AngularJS will create a so called **isolate scope** for each instance of our component

To create a component, we use the **.component()** method of an **AngularJS module**

This is the project folders and files structure

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/226a882b-6fb9-4838-9a23-e519c2f3fe4f)

This is the applicaiton **source code**

**index.html**
```html
<!DOCTYPE html>
<html lang="en" ng-app="phonecatApp">
<head>
  <meta charset="utf-8">
  <title>Google Phone Gallery</title>
  <link rel="stylesheet" href="../node_modules/bootstrap/dist/css/bootstrap.min.css" />
  <link rel="stylesheet" href="app.css" />
  <script src="../node_modules/angular/angular.min.js"></script>
  <script src="app.js"></script>
  <script src="phone-list.component.js"></script>
</head>
<body>

  <!-- Use a custom component to render a list of phones -->
  <phone-list></phone-list>

</body>
</html>
```

**app.js**
```javascript
'use strict';

angular.module('phonecatApp', []);
```

**app.css**
```css
body {
    padding-top: 20px;
  }
```

**phone-list.component.js**
```javascript
'use strict';

// Register `phoneList` component, along with its associated controller and template
angular.
  module('phonecatApp').
  component('phoneList', {
    template:
        '<ul>' +
          '<li ng-repeat="phone in $ctrl.phones">' +
            '<span>{{phone.name}}</span>' +
            '<p>{{phone.snippet}}</p>' +
          '</li>' +
        '</ul>',
    controller: function PhoneListController() {
      this.phones = [
        {
          name: 'Nexus S',
          snippet: 'Fast just got faster with Nexus S.'
        }, {
          name: 'Motorola XOOM™ with Wi-Fi',
          snippet: 'The Next, Next Generation tablet.'
        }, {
          name: 'MOTOROLA XOOM™',
          snippet: 'The Next, Next Generation tablet.'
        }
      ];
    }
  });
```

**phone-list.component.spec.js**
```javascript
'use strict';

describe('phoneList', function() {

  // Load the module that contains the `phoneList` component before each test
  beforeEach(module('phonecatApp'));

  // Test the controller
  describe('PhoneListController', function() {

    it('should create a `phones` model with 3 phones', inject(function($componentController) {
      var ctrl = $componentController('phoneList');

      expect(ctrl.phones.length).toBe(3);
    }));

  });

});
```

This is the application arthitecture

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/a511e468-49d5-4c1a-b680-578466998534)

