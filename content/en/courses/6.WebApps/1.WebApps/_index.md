---
id: webapps_course
title: IoT Web apps
description: This course will show you how to develop a Web interface for your IoT application.
difficulty: intermediate
duration: 4h
---

# Introduction

This course will show you how to develop a Web interface for your IoT application.
At first, we will develop a very simple Web application, based solely on HTML and Javascript.
We will build on this knowledge to go to the next step: the Web frameworks. We will show the basics of three of the most popular frameworks: ReactJS, Angular and Vue. 

<youtube>e3lnWpQQRpc</youtube>

# Simple Web App

The simplest Web application is composed of just HTML + Javascript.
Here is an example:

```html
<html>
  <body>
    <script>
      fetch("https://api.waziup.io/api/v2/devices/MyDevice/sensors/TC1")
        .then((res) => res.json())
        .then((json) => {
          document.getElementById("device_value").innerHTML =
            "The temperature is: " + json.value.value + " C";
        });
    </script>
    <h1>My Application</h1>
    <div id="device_value">Loading...</div>
  </body>
</html>
```

You recognize some HTML tags: `<html>`, `<body>`, `<div>`...
There is also some Javascript in the middle, in the `<script> </scripts>` tags.
What does this small application do?
Well, if we ignore the script part for the moment, it just have a title (`<h1>`) and a div with displayed "Loading...".
This is what you will see on your screen.
Go ahead and copy this code in a file called "index.html", and open it in your web browser.
After some seconds, this is what you should see:

![yourapp](img/yourapp.png)

Once you open the file, the script part will also be executed.
The first part is:

```js
fetch("https://api.waziup.io/api/v2/devices/MyDevice/sensors/TC1/values");
```

We perform a call on a URL. This URL is the address of a specific sensor called "TC1" mounted on a device called "MyDevice".
Once this fetch is done, the second part kicks off, using the response from the fetch:

```js
  .then(res => res.json())
  .then(json => {
         ...
  })

```

The above code receives the response from the fetch, then proceeds to decode it as JSON.
With the JSON, we call this function:

```js
document.getElementById("device_value");
```

This piece of code will give you the element from the HTML page which have the ID "device_value".
Where did you see that ID before? Ah! It's here:

```html
<div id="device_value">Loading...</div>
```

So, the function `getElementById` will return a pointer to this exact section of the HTML code.
The idea is to change it "on the fly" and insert our sensor value there.
This is done by the next section of the code:

```js
.innerHTML = "The temperature is: " + json.value.value + " C";
```

We set the "innerHTML" of the div to `"The temperature is: " + json.value.value + " C"`.
We use the json returned by the fetch and extract the sensor value.
What we are doing is modifying "live" the "virtual DOM".
DOM is "Document Object Model", this is the internal representation of the HTML page in your browser.
So basically, we are modifying the HTML page live, inserting our sensor value.

This is, really, the simplest IoT Web app that you could do!

# Web Sockets

Web sockets is like HTTP on steroid.
While HTTP is "fire and forget", Web sockets will open a persistent 2-way connection between client and server.
The session will not be closed after the first request.
As can be seen in the next figure, Web Socket extends the HTTP protocol: We will first send a request to "upgrade" the HTTP connection to Web Socket.
After that, the full-duplex channel will be open.

![websockets3](img/websockets3.png)

Let's check [an example using Web Sockets](https://waziup.github.io/WaziApps-examples/www/mqtt/).
Now open the developper's networking tools in you browser, and click on refresh.
You should see:

![websockets1](img/websockets1.png)

You might not have seen the HTTP code "101" before: it mean "Switching protocol".
We are "upgrading" from HTTP to Web Sockets.
In the "response" tab, you should see:

![websockets2](img/websockets2.png)

The channel is open! Client and server are discussing. This is not anymore "fire and forget".
The underlying protocol here is MQTT, but you can use anything else.

# Create a plot and a map

It is very common to display IoT data as a time series graph, or as a map for geographical data.
Let's look at some examples.

Please find the [example for a graph](https://github.com/Waziup/WaziApps-examples/blob/master/www/graph/index.html).

```html
<html>
  <body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.7.2/Chart.min.js"></script>
    <script>
      fetch(
        "https://api.waziup.io/api/v2/devices/UGB-PILOTS_Sensor200/sensors/TP/values"
      )
        .then((res) => res.json())
        .then((values) => {
          console.log("data" + JSON.stringify(values));
          var data = [];
          var labels = [];
          for (value of values) {
            data.push(value.value);
            labels.push(value.timestamp);
          }
          new Chart(document.getElementById("myChart").getContext("2d"), {
            type: "line",
            data: {
              labels: labels,
              datasets: [{ label: "Device values", data: data }],
            },
          });
        });
    </script>
    <canvas id="myChart" width="800" height="600">Loading...</canvas>
  </body>
</html>
```

We use the same technique as before: We have a HTML tag that will be replace by live content using a script.
Here, we have a `<canvas>` with ID "myChart":

```html
<canvas id="myChart" width="800" height="600">Loading...</canvas>
```

It will be replaced by a graph:

```js
new Chart(document.getElementById("myChart").getContext("2d"), {
  type: "line",
  data: { labels: labels, datasets: [{ label: "Device values", data: data }] },
});
```

The rest of the code is used to fetch the datapoints and put them in the correct shape.

You can find yet another example, creating a map of IoT devices [here](https://github.com/Waziup/WaziApps-examples/blob/master/www/map/index.html).
In that example, we are creating a map, that setting markers on it, corresponding to the location of the Waziup devices.

All the examples are rendered [at this link]().

# Bootstrap

Another Web technology you might have heard of is [Bootstrap](https://getbootstrap.com/).
Bootstrap is a framework built on the top of HTML and CSS3, with some optional Javascript.
It contains design templates for forms, buttons, tables, navigation, modals, image carousels...
Here is a basic example for a [three collumns design](https://getbootstrap.com/docs/5.2/layout/grid/):

**Responsive design**
Before getting to understand how bootstrap and other styling works, we need to understand the concept of `responsive designs`. Responsive design is an approach to web design that aims to make web pages render well on a variety of devices and window or screen sizes from minimum to maximum display size to ensure usability and satisfaction. The major categories of screen sizes are,

- Extra-extra large screens (XXL)
- Extra large screens (XL)
- Large screens
- Medium screens
- Small screens
- Extra small screens
- Extra-extra small screens

When designing web pages, you have to account for each screen size. However, in most cases you will use at least 3 screen sizes. Below is an image describing the break points for common designs

![alt text](./img/breakpoints.png)

Bootstrap will take care of this by allocating respective columns in each screen size.

**Installing bootstrap**
You can use a CDN to access bootstrap features. We will be using approach due to its flexibility. You can find other approaches in [this](https://getbootstrap.com/docs/5.3/getting-started/download/) installation tutorial.

```html
<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
  rel="stylesheet"
  integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
  crossorigin="anonymous"
/>
```

```html
<script
  src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
  integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
  crossorigin="anonymous"
></script>
```

**Creating a responsive container using bootstrap**
Create a html skeleton file below. You can get this HTML boiler plate by typing `!` in the code editor. Let's first save the file as `index.html`.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
      crossorigin="anonymous"
    />
    <title>Bootstrap container</title>
  </head>
  <body>
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
      crossorigin="anonymous"
    ></script>
  </body>
</html>
```

We added the `link` and `script` tag in the file to use bootstrap classes.
If you are using vs code, install a live server extension to view the changes we make to our index file.

![Live server](./img/live-server.png)

Add this content to the body context

```html
<div class="container card mt-5 p-2 shadow">
  <h1>Waziup API with Bootsrap</h1>
  <div class="row p-2">
    <div class="col-sm-4">
      <h2>Sensor 1</h2>
      <p id="t1">Loading...</p>
    </div>
    <div class="col-sm-4">
      <h2>Sensor 2</h2>
      <p id="t2">Loading...</p>
    </div>
    <div class="col-sm-4">
      <h2>Sensor 3</h2>
      <p id="t3">Loading...</p>
    </div>
  </div>
</div>
```

![simple-dashboard](./img/simple-dashboard.png)

Finally, we add the response from the request to the t1,t2,t3 IDs.

```html
<script>
  const headers = {
    "Content-Type": "application/json",
  };

  const getTemperature = async () => {
    try {
      //You can create your own devices on the wazicloud dashboard and add sensors
      const fetchTemperatureValue1 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC/values"
      );
      const fetchTemperatureValue2 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC2/values"
      );
      const fetchTemperatureValue3 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC3/values"
      );

      const res1 = await fetchTemperatureValue1.json();
      const res2 = await fetchTemperatureValue2.json();
      const res3 = await fetchTemperatureValue3.json();

      const val1 = res1[0].value;
      const val2 = res2[0].value;
      const val3 = res3[0].value;

      document.getElementById("t1").innerHTML = `Value: ${val1} &degC`;
      document.getElementById("t2").innerHTML = `Value: ${val2} &degC`;
      document.getElementById("t3").innerHTML = `Value: ${val3} &degC`;
    } catch (error) {
      console.log(error);
    }
  };

  getTemperature();
</script>
```

The images below demonstrates the responsiveness at different screen widths:

**Desktop View**

![dashboard1](./img/dashboard1.png)

**Tablet View**

![dashboard2](./img/dashboard2.png)

**Mobile View**

![dashboard3](./img/dashboard3.png)

Lets discuss the bootstrap classes used here

1. container - contain, pad, and align your content within a given device or viewport
2. card - flexible container with borders and border radius
3. row - Rows are wrappers for columns
4. mt-5 - Add margin top of 5px
5. p-2 - Add padding 2px
6. shadow - Adding a box shadow
7. col - width specifiers for rows

In this example, Bootstrap provides the definitions of CSS classes "row" and "col-sm-4".
Bootstrap is reactive by default, so your web page will look good on any screen size.

# Exercise 1.0 - Bootstrap

1. What is Bootstrap and what is it built on top of?
2. Explain the concept of responsive design in web development.
3. Name and describe at least three common screen sizes categories used in responsive design.
4. How can you install Bootstrap for a web project using a CDN? Provide the necessary HTML code snippets.
5. Describe the purpose of the following Bootstrap classes used in the provided example:

  - container
  - card
  - row
  - mt-5
  - p-2
  - shadow
  - col
  - navbar
  - badge
  - btn
  - form-control
  - alert

6. Explain the significance of the link and script tags in the HTML file when using Bootstrap.
How does Bootstrap handle responsiveness by default?


# ReactJS

In this section, we'll overview some Web development frameworks useful for developping IoT applications.

ReactJS is a Javascript library for writing UIs.

We will use `vite` to create the react app. Issue the command below to create and run react app.

```
npm create vite@latest my-app --template react
```

```
cd my-app
```

```
npm install
```

```
npm run dev
```

This starts a simple react app as shown below,

![Vite-react](./img/vite-react.png)

We will re-use the content from the `bootstrap module` to build our react application.

First things first, lets install our bootstrap library in react. Add this link tag to the index.html,

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
  integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN"
  crossorigin="anonymous"
/>
```

After adding the bootstrap link, copy this content to the app.jsx file,

```js
import { useState } from "react";
import "./App.css";
import { useEffect } from "react";

function App() {
  const [sensorVals, setSensorVals] = useState({
    sensor1: null,
    sensor2: null,
    sensor3: null,
  });

  const getSensorValues = async () => {
    try {
      const fetchTemperatureValue1 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC/values"
      );
      const fetchTemperatureValue2 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC2/values"
      );
      const fetchTemperatureValue3 = await fetch(
        "https://api.waziup.io/api/v2/devices/bootstrap/sensors/TC3/values"
      );

      const res1 = await fetchTemperatureValue1.json();
      const res2 = await fetchTemperatureValue2.json();
      const res3 = await fetchTemperatureValue3.json();

      setSensorVals({
        sensor1: res1[0].value,
        sensor2: res2[0].value,
        sensor3: res3[0].value,
      });
    } catch (error) {
      console.log(error);
    }
  };

  useEffect(() => {
    getSensorValues();
  });

  return (
    <>
      <h1>React Waziup Application</h1>
      <div className="card">
        <div className="row p-2">
          <div class="col-sm-4">
            <h2>Sensor 1</h2>
            <p id="t1">
              {sensorVals.sensor1 ? `${sensorVals.sensor1}` : "---"} &deg;C
            </p>
          </div>
          <div className="col-sm-4">
            <h2>Sensor 2</h2>
            <p id="t2">
              {sensorVals.sensor2 ? `${sensorVals.sensor2}` : "---"} &deg;C
            </p>
          </div>
          <div className="col-sm-4">
            <h2>Sensor 3</h2>
            <p id="t3">
              {sensorVals.sensor3 ? `${sensorVals.sensor3}` : "---"} &deg;C
            </p>
          </div>
        </div>
      </div>
    </>
  );
}

export default App;
```

The browser should automatically pull these changes and load them into the app as shown below.

![react-app](./img/react-app.png)

In the above code, we use same context like in bootstrap to fetch the data from waziup API. However there are two main features that are added,

- useEffect hook - We use this hook to tell our app to run the function to fetch data only once
- useState hook - We use this hook to handle the state of our app variables, i.e storing the retrieved values from the API

In the next frameworks let's touch on how to use them. The setup process is similar to that of React framework. However, in the template section, you can use vue, angular.

```
npm create vite@latest my-app --template vue
```

```
npm create vite@latest my-app --template angular
```

# Exercise 1.1 - React

1. What is JSX in React and why is it used?
2. Explain the role of components in React.
3. Explain the purpose of the useEffect and useState hooks used in the React application.
4. What is the purpose of the key attribute in React and why is it important when rendering lists of elements?
5. What are hooks in react. Discuss atleast 5 react hooks.
6. Explain the concept of virtual DOM in React and how it improves performance compared to traditional DOM manipulation.

# Angular

Angular is a powerful framework for building dynamic web applications, offering features for creating interactive user interfaces and managing application state. In this course, you will learn how to leverage Angular to create a web application that fetches data from the Wazigate API, which returns information about devices. Additionally, you'll utilize the Fetch API to make HTTP requests and retrieve data from the Wazigate API endpoints.
The rerturned data will be displayed on cards. To get started quickly with angular, you can use [this](https://angular.io/start) documentation.

[Angular](https://getbootstrap.com/) is built on `Typescript`.
TypeScript is a strongly typed programming language that builds on JavaScript.
That means that Typescript is safer than Javascript, and result in better programs.

Angular uses a templating system directly in the HTML (while ReactJS uses JSX).
Here is an example:

Typescript:

```tsx
import {{ Component }} from "@angular/core";

@Component({
  selector: "hello-world-interpolation",
  templateUrl: "./template.html",
})
export class HelloWorldInterpolationComponent {
  message = "Hello, World!";
}
```

HTML:

```tsx
<p>{message}</p>
```

In the HTML above, you can see some templating marks "{{message}}".
The Angular program will read the template and replace the template marker by its value: 'Hello, World!'.
Angular is also has a system of Modules, Components, and Services.

In this task, we will fetch data from `https://api.waziup.io/api/v2/devices` and populate the data on cards.
We need to have a [Wazicloud](https://dashboard.waziup.io/) account with devices already created by now. The API we will use can be found in this [documentation](https://api.waziup.io/docs)

**Installing Angular**

Follow the steps to set angular cli in your machine. You can use the Angular CLI to create projects, generate application and library code, and perform a variety of ongoing development tasks such as testing, bundling, and deployment.

Issue this command to install angular cli,

```
npm install -g @angular/cli
```

On successful installation, issue the command tocreate a new workspace and initial starter app,

```
ng new my-app
```

To run the application we run the command below,
```
cd my-app
ng serve --open
```


The `ng serve` command launches the server, watches your files, and rebuilds the app as you make changes to those files. The `--open` (or just -o) option automatically opens your browser to [localhost](http://localhost:4200/) at http://localhost:4200/.

![angular-waziup](./img/angular-waziup.png)

In the next step we will create the html cards that we will populate it with the data we query from the API.
First things first, we should locate the main file. The main file is located at `angular-waziup > src > app > app.component.html`

Paste the components html templates and the main template should look like the one showed below:
```html
<style>
  :host {
    --bright-blue: oklch(51.01% 0.274 263.83);
    --electric-violet: oklch(53.18% 0.28 296.97);
    --french-violet: oklch(47.66% 0.246 305.88);
    --vivid-pink: oklch(69.02% 0.277 332.77);
    --hot-red: oklch(61.42% 0.238 15.34);
    --orange-red: oklch(63.32% 0.24 31.68);

    --gray-900: oklch(19.37% 0.006 300.98);
    --gray-700: oklch(36.98% 0.014 302.71);
    --gray-400: oklch(70.9% 0.015 304.04);

    --red-to-pink-to-purple-vertical-gradient: linear-gradient(
      180deg,
      var(--orange-red) 0%,
      var(--vivid-pink) 50%,
      var(--electric-violet) 100%
    );

    --red-to-pink-to-purple-horizontal-gradient: linear-gradient(
      90deg,
      var(--orange-red) 0%,
      var(--vivid-pink) 50%,
      var(--electric-violet) 100%
    );

    --pill-accent: var(--bright-blue);

    font-family: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji",
      "Segoe UI Symbol";
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  h1 {
    font-size: 3.125rem;
    color: var(--gray-900);
    font-weight: 500;
    line-height: 100%;
    letter-spacing: -0.125rem;
    margin: 0;
    font-family: "Inter Tight", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji",
      "Segoe UI Symbol";
  }

  h2 {
    margin: 0;
  }

  p {
    margin: 0;
    color: var(--gray-700);
  }

  main {
    width: 100%;
    min-height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    box-sizing: inherit;
    position: relative;
  }

  .content {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }

  .devices {
    display: flex;
    flex-wrap: wrap;
    max-width: 1200px;
    gap: 1.5rem;
  }

  .device-card {
    width: 20rem;
    height: fit-content;
    box-shadow: 0 0 12px 0 gray;
    border-radius: 4px;
    overflow: hidden;
  }

  .dev-name {
    background-color: #31313a;
    overflow: hidden;
    padding: 0.5rem;
    color: #eeeeee;
    font-size: large;
  }
  .dev-content{
    position: relative;
    padding: 0.5rem;
    display: flex;
    flex-direction: column;
    height: 50%;
    gap: 1.25rem;
    justify-content: center;
  }

  .dev-content div {
    display: flex;
    justify-content: space-between;
  }

  .dev-content div span {
    padding: 4px;
    width: 1rem;
    height: 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fff;
    border-radius: 50%;
    background-color: #31313a;
  }

</style>

<main class="main">
  <div class="content">
    <h1>Angular - Waziup Devices</h1>
    <div class="devices" >
      <div *ngFor="let device of devices" class="device-card">
        <h2 class="dev-name">{{device.name}}</h2>
        <div class="dev-content">
          <div>
            <article>Connected Sensors</article>
            <span>{{device.sensors.length}}</span>
          </div>
          <div>
            <article>Connected Actuators</article>
            <span>{{device.actuators.length}}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</main>
```

**Fetching devices from Wazicloud and displaying it on cards**

To make API call to the wazicloud, we need to change the file at,
 `angular-waziup > src > app > app.component.ts`

Lets install the dependency for making http request,
``` npm install @angular/common
```

Let's now update the app.component.ts file
```ts
import { Component, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common'; 

@Component({
  selector: 'app-root',
  imports:[
    CommonModule
  ],
  standalone: true,
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  devices: any[] = [];

  ngOnInit(): void {
    this.fetchData();
  }

  title = 'angular-waziup';

  fetchData() {
    console.log("Fetching devices...")
    fetch('https://api.waziup.io/api/v2/devices?q=owner==username')
      .then(response => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then(data => {
        this.devices = data;
        console.log(data);
      })
      .catch(error => {
        console.error('There was a problem with the fetch operation:', error);
      });
  }
}
```

<alert type='warning'>
Take note to replace the username with your wazicloud username
</alert>

You can head over to http://localhost:4200/ to view the changes,

![ui-angular](./img/ui-angular.png)

# Exercise 1.2 - Angular
1. We have developed simple cards that display the device in a card and its name and the number of sensors in it. In this exercise we will need you to implement navigation into the device, i.e Clicking on the card takes you to a page with the sensors and actuators connected to the device.
  
    Hint: Use `Angular Router` provides a service that lets you define a navigation path among the different application states and view hierarchies in your application.

# Vue

The third and final Web framework that we'll overview is [Vue](https://vuejs.org/guide/introduction.html).
The Vue.js core library focuses on the ViewModel layer only from the [MVVM pattern](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel).

That means that it focuses on the rendering of information, leaving the business logic ot other components.
It is a "progressive" framework because you can extend its functionality with official and third-party packages, such as Vue Router or Vuex, to turn it into an actual framework.
Here is an example using javascript:

```jsx
import { createApp } from "vue";

createApp({
  data() {
    return {
      count: 0,
    };
  },
}).mount("#app");
```

HTML:

```html
<div id="app">
  <button @click="count++">Count is: {{ count }}</button>
</div>
```

You can note that the templating system is similar with Angular with the `{{ count }}`.

**Vue Installation**

In this task, we will only setup the vue environment for you. This will kickstart you in working on the exercise. We need to first install the `vue cli` using the command,

```
vue create vue-waziup
```

Navigate to your project,

```
cd vue-waziup
```

Run the following command to start the vue project on a development server.

```
npm run serve
```

Vue CLI will compile your project and provide you with a [local](http://localhost:8080/) URL, http://localhost:8080/, where you can view your application in the browser.

![vue-app](./img/vue-app.png)

**Customizing your project**
Now that you have your project up and running, it’s time to customize it and start building your Vue application. Here are a few key areas you can explore:

- `Components` - Create reusable components to build the user interface of your application.
- `Routing` - Set up routes and navigation in your application using Vue Router.
- `Global State` - Use Vuex to manage the global state of your application.
- `Styling` - Add styles to your components using CSS or preprocessors like Sass or Less.
- `API Calls` - Connect to a backend API and make HTTP calls using libraries like Axios.

This concludes our trip through web development. Good programming!

# Exercise 1.3 - Vue
1. In this exercise redo the exercise on Angular, but using Vue framework

    _Milestone 1_

      - The exercise requires you to fetch wazigate API at /devices and display the devices connected to the wazicloud.

    _Milestone 2_

      - Clicking on a device should you navigate to the device and show the sensors and actuators