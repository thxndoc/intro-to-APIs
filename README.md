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

