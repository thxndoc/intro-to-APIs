# intro-to-APIs
Lessons on APIs

## API - Application Programming Interface
An API is any tool that helps connect your program to someone else's program.<br>

It's like a waiter in a restaurant:

* You (the user) don't go to the kitchen (the complex backend) directly.
* Instead, you interact with the waiter (the API).
* The waiter takes your order to the kitchen and brings back what you need.

APIs work similarly by defining how programs can request services from other programs, exchange data, or interact with external systems, all without the user needing to understand the intricate details of how these systems work internally.<br>

**API examples:**<br>
* **Getting data from a server** - the server hosts an API with exposed "endpoints" we can access for getting data from the server.<br>
Note that the server doesn't give us access to *everything*(because of security), just the things they want us to have.

* **Pre-written code that does cool stuff** - e.g DOM API `(.getElementById)`

## Clients - what is a client?
Any device that connects to the internet to get data from somewhere(makes a "request" to a server) - e.g laptop, phone, tablet, smartwatch...any smart device.

## Servers - what is a server?
Basically just a computer that accepts request a from clients asking for something, then responds to the client with that thing (e.g an HTML page, an image, file, or just plain data in a JSON format).

## The request-response cycle
**What is a request?**<br>
* When a client asks for a "resource" (data, image, HTML page, authentication token etc.).
* Requires a connection to the internet somehow, because it needs to send the request to the server somewhere.

**What is a response?**<br>
* A reply to the request.
* Could contain the resource asked for by the client.
* Could contain a response saying the client isn't authorized to receive the resource.<br>
![screenshot](/images/request-response.png)

## JSON
Remember that for an object in JSON, the **keys** are surrounded by ""
```JavaScript
{
    "name": "Thando Chibi",
    "age": 30,
    "gender": "Female",
    "hobbies": [
        "netball",
        "drifting",
        "biking"
    ]
}
```
## Fetch JSON data with JavaScript fetch API
```JavaScript
fetch("https://dog.ceo/api/breeds/image/random")//fetch the resource - in this case, insert URL wrapped in ""
    .then(response => response.json())// with the response that comes back, change the body of the response from JSON to JavaScript 
    .then(data => console.log(data))//once you have access to the data, console log the data
```
* **Another example**
```JavaScript
fetch("https://apis.scrimba.com/bored/api/activity")
    .then(response => response.json())
    .then(data => {
        console.log(data)
        const activityName = document.getElementById("activity-name")//in HTML, you create an <h1> element and give it an ID of activity-name
        activityName.textContent = data.activity
    })
```
In this case, you don't need `appendChild()` because you're working with an existing element in the DOM, rather than creating a new one. Here's why:<br>

* `document.getElementById`("activity-name") selects an existing element from your HTML that has the id "activity-name".
* You're directly modifying the `textContent` of this existing element.
* Since the element is already part of the DOM tree, you don't need to append it anywhere.

## Asynchronous JavaScript
This means that its happening out of order / out of time

## HTTP - HyperText Transfer Protocol
A protocol is an agreed upon, standard way of doing something.<br>
HTTP is a protocol for determining how HyperText(text) should be transferred over the internet.<br>
![alt-text](/images/request-components.png)
### More on components of a request
![alt-text](/images/path-url.png)