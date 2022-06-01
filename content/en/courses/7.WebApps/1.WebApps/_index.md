---
title: IoT Web apps
description: This course will show you how to develop a Web interface for your IoT application.
---

This course will show you how to develop a Web interface for your IoT application. At first, we will develop a very simple Web application, based solely on HTML and Javascript. We will build on this knowledge to go to the next step: the Web frameworks. We will show the basics of three of the most popular frameworks: ReactJS, Angular and Vue.

Simple Web App
==============

HTML + Javascript
-----------------

The simplest Web application is composed of just HTML + Javascript.
Here is an example:

```
<html>
  <body>
    <script>
      fetch("https://api.waziup.io/api/v2/devices/MyDevice/sensors/TC1")
        .then(res => res.json())
        .then(json => {
           document.getElementById("device_value").innerHTML = "The temperature is: " + json.value.value + " C";
      })
    </script>
    <h1>My Application</h1>
    <div id="device_value">
      Loading...
    </div>
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

```
fetch("https://api.waziup.io/api/v2/devices/MyDevice/sensors/TC1/values")
```

We perform a call on a URL. This URL is the address of a specific sensor called "TC1" mounted on a device called "MyDevice".
Once this fetch is done, the second part kicks off, using the response from the fetch: 

```
  .then(res => res.json())
  .then(json => {
         ...
  })

```

The above code receives the response from the fetch, then proceeds to decode it as JSON.
With the JSON, we call this function:

```
document.getElementById("device_value")
```

This piece of code will give you the element from the HTML page which have the ID "device_value".
Where did you see that ID before? Ah! It's here:

```
    <div id="device_value">
      Loading...
    </div>
```

So, the function `getElementById` will return a pointer to this exact section of the HTML code.
The idea is to change it "on the fly" and insert our sensor value there.
This is done by the next section of the code:

```
.innerHTML = "The temperature is: " + json.value.value + " C";
```

We set the "innerHTML" of the div to `"The temperature is: " + json.value.value + " C"`.
We use the json returned by the fetch and extract the sensor value.
What we are doing is modifying "live" the "virtual DOM".
DOM is "Document Object Model", this is the internal representation of the HTML page in your browser.
So basically, we are modifying the HTML page live, inserting our sensor value.

This is, really, the simplest IoT Web app that you could do!

Web Sockets
-----------

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


Create a graph plot and a map
-----------------------------

It is very common to display IoT data as a time series graph, or as a map for geographical data.
Let's look at some examples.

Please find the [example for a graph](https://github.com/Waziup/WaziApps-examples/blob/master/www/graph/index.html).


```
<html>
  <body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.7.2/Chart.min.js"></script>
    <script>
      fetch("https://api.waziup.io/api/v2/devices/UGB-PILOTS_Sensor200/sensors/TP/values")
        .then(res => res.json())
        .then(values => {
          console.log("data" + JSON.stringify(values));
          var data = [];
          var labels = [];
          for (value of values) {
            data.push(value.value);
            labels.push(value.timestamp);
          }
          new Chart(document.getElementById("myChart").getContext("2d"),
                   {type: "line", data: { labels: labels, datasets: [{label: "Device values", data: data }]}});
        });
    </script>
    <canvas id="myChart" width="800" height="600">Loading...</canvas>
  </body>
</html>
```

We use the same technique as before: We have a HTML tag that will be replace by live content using a script.
Here, we have a "<canvas>" with ID "myChart":

```
<canvas id="myChart" width="800" height="600">Loading...</canvas>
```

It will be replaced by a graph:

```
new Chart(document.getElementById("myChart").getContext("2d"),
          {type: "line", data: { labels: labels, datasets: [{label: "Device values", data: data }]}});
```

The rest of the code is used to fetch the datapoints and put them in the correct shape.

You can find yet another example, creating a map of IoT devices [here](https://github.com/Waziup/WaziApps-examples/blob/master/www/map/index.html).
In that example, we are creating a map, that setting markers on it, corresponding to the location of the Waziup devices.

All the examples are rendered [at this link]().
