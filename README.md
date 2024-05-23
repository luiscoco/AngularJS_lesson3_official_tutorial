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

Then we initialize/create the package.json file ruuning this command

```
npm init -y
```

We install angular dependencies with this command

```
npm install angular
```

We create the folders and files project structure

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/9aa48697-7ae5-45d8-b02c-edf7e64dc975)

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

![image](https://github.com/luiscoco/AngularJS_lesson3_official_tutorial/assets/32194879/b5b3e471-8f6d-4dd8-962f-37e6b944ce9c)

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





