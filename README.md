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
1. What's the difference between a Base URL and an Endpoint?
    * Base URL is the part of the URL that won't change, no matter
      which resource we want to get from the API
    * Endpoint specifies exactly which resource we want to get
      from the API

Given the following URLs from an example API:
* https://blahblahblah.com/api/v2/users
* https://blahblahblah.com/api/v2/products
* https://blahblahblah.com/api/v2/products/123

2. Which part is the Base URL?<br>
https://blahblahblah.com/api/v2

3. What are the available endpoints?<br>
/users, /products, /products/(some-id-of-a-product-here)<br>
NOT /products/123

#### Methods
![alt-text](/images/methods.png)
HTTP defines a set of request **methods** to indicate the purpose of the request and what is expected if the request is successful.
**Challenge - GET**
```JavaScript
/**
Challenge: 

Fetch a list of todos from the JSON Placeholder API:

BaseURL: https://apis.scrimba.com/jsonplaceholder/
Endpoint: /todos

This time however, explicitly set the request method to "GET"
console.log the results
*/
//Rememeber that 'GET' is the default for 'fetch'
fetch("https://apis.scrimba.com/jsonplaceholder/todos", {method: "GET"}) //now has 2 parameters - explicitly saying you want the method to be a GET request
    .then(response => response.json())
    .then(data => console.log(data))
```
**Challenge - GET**
```JavaScript
/**
 Challenge:
 
 GET a list of blog posts from the JSON Placeholder API.
 
 BaseURL: https://apis.scrimba.com/jsonplaceholder/
 Endpoint: /posts
 
 Since there's so many posts, let's limit the array to just 5 items.
 You can use the `.slice()` array method to just grab the first 5 objects
 from the data array that comes back from the API
 
 Log the 5 items to the console
 */
fetch("https://apis.scrimba.com/jsonplaceholder/posts")
    .then(response => response.json())
    .then(data => {
        //console.log(data)
        const postsArr = data.slice(0, 5)
        console.log(postsArr)
    })
```
#### Body
![alt-text](/images/body.png)

#### Headers
![alt-text](/images/headers.png)

## REST - REepresentational State Transfer
**REST** is a design pattern to provide a standard way for clients and servers to communicate.<br>

### Principles of REST:
#### 📌 - Client & Server 
![alt-text](/images/client-server-sep.png)
 
1. How would you describe what REST is to your non-technical friend❓<br>
A standardized way to have your computer, like your laptop, 
get or send information to another computer (like a server)

2. What does a RESTful API usually return in response to incoming requests❓<br>
JSON data

3. What kind of client devices can make use of a RESTful API❓<br>
All the devices - any device connected to the internet (smartwatch, smart fridge, smart vacuum, laptop, phone, tablet etc.)

#### 📌 - Statelessness
When a client makes a request to a server, the server doesn't maintain any memory of that request.<br> 
So when a request is sent to the server, the server fulfills that request if it can, sends back a response, and then forgets everything about that request and the client that made that request.

#### 📌 - Accessing "Resources"
![alt-text](/images/resources.png)<br>
In the above example, when using a noun, you'll be getting an array or a collection of the data, which in this case is the bikes<br>

#### 📌 - Nested Resources
![alt-text](/images/nested-resources.png)<br>
In the above example, when using a noun, you'll be getting an array or a collection of the data, which in this case is the reviews of that specific bike.<br>

* **Quiz**
1. How is a nested resource URL like /bikes/123/reviews
   different from an endpoint like /reviews ❓<br>
    * `/bikes/123/reviews` - return an array of reviews about that specific bike
    * `/reviews` - return an array of all reviews on the site

2. What URL might you use to GET the review with an ID of 5 on the bike
   with the ID of 123❓<br>
    
    * `/bikes/123/reviews/5`

3. Describe a "URL Parameter" in your own words:❓
    * Variable inside the URL that acts as a placeholder for the real value (oftentimes they replace the ID of the resource)
