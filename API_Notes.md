# Part 1 — API Fundamentals & Web Services

This part builds the **foundation**. Since you are new to API testing, don't worry about Postman or test cases yet. First understand **how applications communicate with each other**.

---

# 1. What is a Client?

A **client** is a software application or device that sends a request to another system to get some service or data.

### Simple definition

> **Client is the requester.**

### Examples

When you:

* Open Chrome and visit Google → Chrome is the client.
* Open a banking app and check your balance → Banking app is the client.
* Use the Amazon mobile application → Amazon app is the client.
* Send a request from Postman → Postman is acting as a client.

### Real-world example

Suppose you open:

```text
www.google.com
```

Your browser sends a request to Google's server.

```text
Browser
   |
   | Request
   ↓
Google Server
```

Here:

**Browser = Client**

---

# 2. What is a Server?

A **server** is a computer/system or software application that receives requests from clients, processes them, and sends responses.

### Simple definition

> **Server is the system that receives and processes the client's request.**

For example:

```text
Client                     Server
Browser  ───── Request ───→ Google
Browser  ←──── Response ─── Google
```

The server may:

* Receive requests
* Validate requests
* Execute business logic
* Communicate with a database
* Process data
* Send a response

---

# 3. Client vs Server

| Client                               | Server                    |
| ------------------------------------ | ------------------------- |
| Sends request                        | Receives request          |
| Requester                            | Provider                  |
| Usually used by end user/application | Provides services/data    |
| Example: Browser                     | Example: Web server       |
| Example: Postman                     | Example: API server       |
| Initiates communication              | Responds to communication |

### Easy way to remember

> **Client asks → Server processes → Server responds**

---

# 4. What is Client-Server Architecture?

**Client-server architecture** is a system architecture in which the client and server have different responsibilities.

The client requests a service, and the server provides that service.

### Basic architecture

```text
                 CLIENT
        ┌────────────────────┐
        │ Browser            │
        │ Mobile App         │
        │ Desktop App        │
        │ Postman            │
        └─────────┬──────────┘
                  │
                  │ Request
                  ↓
        ┌────────────────────┐
        │      SERVER        │
        │                    │
        │ Business Logic     │
        │ API                │
        │ Application        │
        └─────────┬──────────┘
                  │
                  ↓
        ┌────────────────────┐
        │     DATABASE       │
        │                    │
        │ Users              │
        │ Products           │
        │ Orders             │
        └────────────────────┘
```

The server may communicate with a database to obtain or store information.

---

# 5. How Client and Server Communicate

Let's take an example of an online shopping application.

You open an application and request your orders.

### Step 1 — Client sends request

```text
Mobile App
    |
    | "Give me my orders"
    ↓
Server
```

### Step 2 — Server processes request

The server may:

1. Verify the user
2. Check authorization
3. Query the database
4. Retrieve orders
5. Prepare the response

### Step 3 — Server sends response

```text
Server
   |
   | Order information
   ↓
Mobile App
```

So:

```text
CLIENT
   ↓
REQUEST
   ↓
SERVER
   ↓
BUSINESS LOGIC
   ↓
DATABASE
   ↓
SERVER
   ↓
RESPONSE
   ↓
CLIENT
```

This basic flow is extremely important for API testing.

---

# 6. What is a Request?

A **request** is a message sent by a client to a server asking the server to perform some operation or provide some information.

For example:

```text
GET /users/101
```

The client is asking:

> "Give me the details of user 101."

A request can contain things such as:

* URL
* HTTP method
* Headers
* Parameters
* Request body
* Authentication information

We'll study these in detail in **Part 2**.

---

# 7. What is a Response?

A **response** is the message sent by the server back to the client after processing the request.

For example:

```text
HTTP/1.1 200 OK
```

Response body:

```json
{
  "id": 101,
  "name": "Ankitha",
  "city": "Hyderabad"
}
```

So:

```text
Request
   ↓
Server
   ↓
Response
```

---

# 8. What is an API?

Now we reach the most important concept.

**API** stands for:

> **Application Programming Interface**

An API is a defined interface that allows one software application to communicate with another software application.

### Simple definition for interview

> **An API is a mechanism that allows two software applications to communicate with each other by sending requests and receiving responses.**

---

# 9. Simple Real-World Example of API

Suppose you are using a food delivery application.

You want to see restaurants near you.

The mobile application doesn't necessarily directly access the restaurant company's database.

Instead:

```text
Food App
   |
   | API Request
   ↓
Restaurant API
   |
   ↓
Database
   |
   ↓
Restaurant API
   |
   | API Response
   ↓
Food App
```

The API acts as the communication interface between the applications.

---

# 10. API as a Waiter Example

A very common interview-friendly analogy is a **restaurant**.

Imagine:

```text
Customer → Waiter → Kitchen
```

The customer doesn't go into the kitchen and directly prepare the food.

Instead:

1. Customer gives an order to waiter.
2. Waiter sends order to kitchen.
3. Kitchen prepares food.
4. Waiter brings food to customer.

Similarly:

```text
Client → API → Server
Client ← API ← Server
```

### Mapping

| Restaurant | Software      |
| ---------- | ------------- |
| Customer   | Client        |
| Waiter     | API           |
| Kitchen    | Server        |
| Food       | Response/data |
| Order      | Request       |

So the API acts as an **interface between the client and the server**.

---

# 11. Why Do We Need APIs?

APIs are needed because applications frequently need to communicate with other applications or systems.

### Major reasons

### 1. Communication between applications

Example:

```text
Mobile App ↔ Backend Server
```

### 2. Data sharing

One application can request data from another application.

### 3. Integration

Different systems can work together.

Example:

```text
E-commerce Application
        ↓
Payment API
        ↓
Payment Gateway
```

### 4. Security

The client doesn't necessarily need direct access to the database.

Instead:

```text
Client
  ↓
API
  ↓
Business Logic
  ↓
Database
```

The API can enforce authentication, authorization and validation.

### 5. Reusability

The same API can be used by multiple clients.

For example:

```text
             ┌── Web Application
             │
API Server ──┼── Mobile Application
             │
             └── Third-party Application
```

---

# 12. Why is API Testing Important?

As a QA, you need to verify that the API behaves correctly.

Suppose a login API is:

```text
POST /login
```

You need to verify:

* Correct credentials
* Incorrect credentials
* Missing username
* Missing password
* Invalid password
* Empty values
* Response status
* Response body
* Error message
* Authentication token
* Response time

API testing allows us to test the **backend functionality directly**, without depending entirely on the UI.

---

# 13. What is a Web Service?

A **web service** is a software service that enables applications to communicate over a network, commonly using web technologies and standardized communication mechanisms.

For example:

```text
Application A
      |
      | Request
      ↓
Web Service
      |
      ↓
Application B
```

HTTP-based web services can allow different applications to communicate even when they are built using different technologies. ([ServiceNow][1])

For example:

```text
Java Application
       ↓
     API
       ↓
Python Application
```

The applications don't necessarily need to be written in the same programming language.

---

# 14. API vs Web Service

This is an important interview question.

### API

API is a **broader concept**.

It provides an interface through which software components communicate.

APIs can exist in many forms, including APIs that are not web-based.

### Web Service

A web service is a type of service designed for communication over a network/web using web-oriented technologies.

### Easy interview answer

> **Every web service can be considered an API, but not every API is necessarily a web service.**

For example, a local library API inside a Java application can allow classes to communicate without any network communication.

---

# 15. Types of Web Services / API Approaches

For your syllabus, focus on these major approaches:

### 1. SOAP

```text
SOAP
 ↓
XML-based messaging
```

SOAP is a messaging protocol that uses XML and has a defined specification for exchanging structured information. ([Postman Blog][2])

### 2. REST

```text
REST
 ↓
Resources + HTTP
 ↓
Usually JSON
```

REST is an architectural style centered around resources and commonly uses HTTP methods such as GET and POST. ([Postman Blog][2])

### 3. GraphQL

```text
GraphQL
 ↓
Client specifies required data
```

GraphQL is a query language for APIs with a strongly typed schema, allowing clients to request the fields they need. ([GraphQL][3])

### 4. gRPC

```text
gRPC
 ↓
Remote Procedure Calls
 ↓
Protocol Buffers
 ↓
HTTP/2
```

gRPC allows clients to call remote methods and commonly uses Protocol Buffers for defining services and messages. ([gRPC][4])

---

# 16. SOAP — Introduction

**SOAP** stands for:

> **Simple Object Access Protocol**

SOAP is a **messaging protocol** used for communication between applications.

A key characteristic is that SOAP messages use **XML**.

Example structure:

```xml
<soap:Envelope>
    <soap:Header>
    </soap:Header>

    <soap:Body>
        <GetUser>
            <UserId>101</UserId>
        </GetUser>
    </soap:Body>
</soap:Envelope>
```

Don't worry about memorizing this structure yet. We'll study SOAP in detail later.

---

# 17. REST — Introduction

**REST** stands for:

> **Representational State Transfer**

REST is an **architectural style**, not a protocol.

REST APIs commonly use HTTP to work with resources.

For example:

```text
GET /users/101
```

means:

> Retrieve user 101.

Another example:

```text
POST /users
```

means:

> Create a new user.

REST is widely used because it works naturally with HTTP and has a large ecosystem. ([Postman Blog][2])

---

# 18. GraphQL — Introduction

GraphQL allows the **client to specify what data it wants**.

Suppose the server has:

```text
User
 ├── name
 ├── email
 ├── phone
 └── address
```

The client might request only:

```graphql
{
  user {
    name
    email
  }
}
```

The response can contain just those requested fields.

This helps reduce **over-fetching** and lets clients retrieve related data in a structured request. ([GraphQL][3])

---

# 19. gRPC — Introduction

gRPC stands for **gRPC Remote Procedure Calls**.

It is commonly used for communication between services, especially in distributed systems and microservices.

Instead of thinking primarily in terms of resources such as:

```text
/users/101
```

gRPC is centered around calling defined service methods.

For example:

```text
GetUser()
CreateUser()
UpdateUser()
```

Services and request/response messages can be defined using Protocol Buffers.

Example:

```text
Client
   |
   | GetUser()
   ↓
gRPC Server
   |
   ↓
Response
```

gRPC uses Protocol Buffers and is designed for efficient communication; its ecosystem supports multiple programming languages. ([gRPC][4])

---

# 20. SOAP vs REST vs GraphQL vs gRPC — Quick Understanding

| Feature              | SOAP                      | REST                 | GraphQL                       | gRPC                                              |
| -------------------- | ------------------------- | -------------------- | ----------------------------- | ------------------------------------------------- |
| Type                 | Protocol                  | Architectural style  | Query language/runtime        | RPC framework                                     |
| Common data format   | XML                       | JSON commonly        | JSON commonly                 | Protobuf/binary commonly                          |
| Main idea            | Structured messaging      | Resource-based       | Client asks for required data | Call remote methods                               |
| Common use           | Enterprise/legacy systems | Web/mobile APIs      | Flexible data fetching        | High-performance service-to-service communication |
| Learning difficulty  | Higher                    | Easier               | Medium                        | Medium                                            |
| Common testing tools | SoapUI/Postman            | Postman/REST Assured | Postman/GraphQL tools         | gRPC tools/Postman                                |

The choice depends on the application's requirements; REST, GraphQL and gRPC solve somewhat different API design problems rather than one universally replacing the others. ([Postman Blog][2])

---

# 21. Most Important Concept to Remember

Don't try to memorize everything yet. Remember this flow:

```text
                    SOFTWARE APPLICATION
                            │
                            │
                         CLIENT
                            │
                            │ API REQUEST
                            ↓
                           API
                            │
                            ↓
                          SERVER
                            │
                            ↓
                         DATABASE
                            │
                            ↓
                          SERVER
                            │
                            │ API RESPONSE
                            ↓
                           API
                            │
                            ↓
                          CLIENT
```

### In API testing

Your job is mainly to verify:

```text
REQUEST
   ↓
Is it correct?
   ↓
SERVER PROCESSING
   ↓
RESPONSE
   ↓
Is it correct?
```

You will later validate:

* Status code
* Response body
* Headers
* Response time
* Data
* Business rules
* Authentication
* Authorization
* Error handling

---

# 22. Interview Questions — Part 1

### Q1. What is a client?

**Answer:**

> A client is an application or system that sends a request to a server to access a service or data.

### Q2. What is a server?

> A server is a system or application that receives client requests, processes them and returns responses.

### Q3. What is client-server architecture?

> Client-server architecture is a model in which the client requests services or data from a server, and the server processes the request and returns a response.

### Q4. What is an API?

> API stands for Application Programming Interface. It provides an interface that allows software applications or components to communicate with each other.

### Q5. Why do we need APIs?

> APIs are used for communication, integration, data exchange, security, and reusability between software applications.

### Q6. What is a web service?

> A web service is a network-accessible software service that enables applications to communicate using web technologies and defined communication mechanisms.

### Q7. Is every API a web service?

> No. API is a broader concept. An API can be local or network-based, whereas a web service is designed for communication over a network using web technologies.

### Q8. What is SOAP?

> SOAP is an XML-based messaging protocol used for communication between applications.

### Q9. What is REST?

> REST is an architectural style for designing networked APIs around resources and commonly using HTTP methods for operations on those resources.

### Q10. What is GraphQL?

> GraphQL is a query language for APIs and a server-side runtime that allows clients to request the specific data they need.

### Q11. What is gRPC?

> gRPC is a high-performance RPC framework that allows clients to call methods on remote services, commonly using Protocol Buffers and HTTP/2.

---

## ⭐ Interview Tip

If the interviewer asks:

**"Explain API in simple terms."**

Don't give only the definition.

Say:

> "API stands for Application Programming Interface. It acts as an interface between two software applications and allows them to communicate through requests and responses. For example, when a mobile application wants user details, it sends a request to the backend API. The API processes the request and returns the required data to the mobile application."

That's much stronger than simply saying **"API means Application Programming Interface."**

---

# Part 2 — REST, HTTP, URLs, Methods & Status Codes

Part 1 covered the basic concepts of **Client, Server, API, Web Services, SOAP, REST, GraphQL and gRPC**.

Now we move into the **most important practical section for API testing**.

By the end of Part 2, you should understand:

> **How to read an API URL → how to send a request → which HTTP method to use → how to understand the response/status code.**

---

# 1. What is REST?

**REST** stands for:

> **Representational State Transfer**

REST is an **architectural style** used to design APIs.

REST APIs commonly use HTTP methods such as:

```text
GET
POST
PUT
PATCH
DELETE
```

to perform operations on resources. ([MDN Web Docs][1])

### Example

Suppose we have an Event API.

```text
GET https://api.example.com/events
```

This could mean:

> Get the list of events.

And:

```text
GET https://api.example.com/events/101
```

could mean:

> Get event 101.

---

# 2. What is a Resource?

A **resource** is the data or object that an API provides access to.

Examples:

```text
Users
Products
Orders
Events
Employees
Customers
Payments
```

For example:

```text
/users
/products
/orders
/events
```

Here:

```text
/users       → User resource
/products    → Product resource
/events      → Event resource
```

---

# 3. What is a URL?

**URL** stands for:

> **Uniform Resource Locator**

A URL identifies the location of a resource on a network.

Example:

```text
https://api.example.com/users/101
```

Let's break it down.

```text
https://api.example.com/users/101
│       │               │      │
│       │               │      └── Path Parameter
│       │               └───────── Path
│       └───────────────────────── Domain/Host
└───────────────────────────────── Protocol
```

---

# 4. Components of an API URL

Consider:

```text
https://api.example.com/v1/users/101?active=true
```

| Component       | Value             |
| --------------- | ----------------- |
| Protocol        | `https`           |
| Domain/Host     | `api.example.com` |
| Version         | `v1`              |
| Path            | `/users/101`      |
| Path Parameter  | `101`             |
| Query Parameter | `active=true`     |

Let's understand each one.

---

# 5. Protocol

The beginning:

```text
https://
```

is the **protocol/scheme**.

Commonly you'll see:

```text
http://
https://
```

For APIs, HTTPS is generally preferred because it protects data in transit using encryption.

---

# 6. Domain

Example:

```text
https://api.example.com/users
       └──────────────┘
          Domain
```

The domain identifies the host where the API is available.

For your EventHub API, the host is:

```text
api.eventhub.rahulshettyacademy.com
```

---

# 7. Base URL

The **base URL** is the common starting portion used by multiple API endpoints.

For example:

```text
https://api.example.com
```

Then different endpoints may be:

```text
/users
/events
/products
/orders
```

So:

```text
Base URL + Endpoint Path
```

gives the complete API URL.

Postman similarly describes a base URL as the base location and the endpoint as the path used for a particular API operation. ([Postman Docs][2])

---

# 8. Endpoint

An **API endpoint** is a specific URL through which an API accepts requests for a particular operation/resource.

For example:

```text
GET /users
```

and:

```text
GET /users/101
```

are endpoints.

An endpoint is commonly understood using:

```text
HTTP Method + URL/Path
```

For example:

```text
GET https://api.example.com/users/101
```

means:

> Retrieve user 101.

([Postman Blog][3])

---

# 9. Path

The path identifies the resource location within the API.

Example:

```text
https://api.example.com/users/101
                      └─────────┘
                          Path
```

The path is:

```text
/users/101
```

Another example:

```text
/products
```

---

# 10. Path Parameter

A **path parameter** is a value included directly in the URL path to identify a specific resource.

Example:

```text
GET /users/101
```

Here:

```text
101
```

is the path parameter.

It identifies a specific user.

### Another example

```text
GET /events/500
```

Here:

```text
500
```

is the event ID.

Conceptually:

```text
/events/{eventId}
```

Actual request:

```text
/events/500
```

Path parameters are commonly used when you need to identify a specific resource. ([Postman Docs][4])

### Easy way to remember

> **Path parameter = Which specific resource?**

Example:

```text
/users/101
```

Means:

> User number 101.

---

# 11. Query Parameter

A **query parameter** is additional information added to the URL after `?`.

Example:

```text
GET /events?city=Hyderabad
```

Here:

```text
city=Hyderabad
```

is a query parameter.

Multiple query parameters are separated using `&`.

Example:

```text
GET /events?city=Hyderabad&type=technical
```

Here we have:

```text
city=Hyderabad
type=technical
```

Query parameters are commonly used for filtering, sorting, searching and pagination. ([Postman Docs][4])

### Easy way to remember

> **Path parameter = identify the resource.**

> **Query parameter = filter/customize the result.**

### Example

```text
/events/101
```

→ Give me **event 101**.

```text
/events?city=Hyderabad
```

→ Give me **events in Hyderabad**.

---

# 12. Path Parameter vs Query Parameter

| Path Parameter                         | Query Parameter                    |
| -------------------------------------- | ---------------------------------- |
| Part of URL path                       | Comes after `?`                    |
| Usually identifies a specific resource | Usually filters/customizes results |
| Example `/users/101`                   | Example `/users?city=Hyderabad`    |
| Often required                         | Often optional                     |
| Uses `/`                               | Uses `?` and `&`                   |

### Interview answer

> A path parameter is used to identify a specific resource and forms part of the URL path, while a query parameter is generally used to filter, search, sort, paginate or customize the response.

---

# 13. Headers

**Headers** contain additional information/metadata about an HTTP request or response.

Examples:

```text
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
```

HTTP headers allow clients and servers to exchange additional information about the message. ([MDN Web Docs][5])

### Common headers

#### Content-Type

Tells the server what format the request body uses.

Example:

```text
Content-Type: application/json
```

Means:

> The request body is JSON.

#### Accept

Tells the server what response format the client can accept.

```text
Accept: application/json
```

#### Authorization

Used to send authentication credentials/token.

```text
Authorization: Bearer <token>
```

---

# 14. Request Body

The **request body** contains data sent from the client to the server.

It is commonly used with:

```text
POST
PUT
PATCH
```

Example:

```http
POST /users
Content-Type: application/json
```

Body:

```json
{
  "name": "Ankitha",
  "email": "ankitha@example.com"
}
```

Postman supports sending body data in formats such as raw, form-data and URL-encoded data. ([Postman Docs][4])

---

# 15. Response Body

The response body contains the data returned by the server.

Example:

```json
{
  "id": 101,
  "name": "Ankitha",
  "email": "ankitha@example.com"
}
```

As a QA, you may validate:

* Required fields
* Field values
* Data types
* JSON structure
* Business rules
* Error messages

---

# 16. Complete API Request Structure

A REST API request can look like this:

```text
GET https://api.example.com/users/101?active=true
Authorization: Bearer token
Accept: application/json
```

Let's identify everything:

```text
GET
 ↓
HTTP Method

https://
 ↓
Protocol

api.example.com
 ↓
Domain

/users/101
 ↓
Path

101
 ↓
Path Parameter

?active=true
 ↓
Query Parameter

Authorization
 ↓
Header
```

---

# 17. HTTP vs HTTPS

### HTTP

**HTTP = HyperText Transfer Protocol**

It is used for communication between clients and servers.

Example:

```text
http://example.com
```

### HTTPS

**HTTPS = HTTP Secure**

HTTPS uses encryption through TLS to protect communication between client and server.

Example:

```text
https://example.com
```

### Difference

| HTTP                           | HTTPS                  |
| ------------------------------ | ---------------------- |
| Not encrypted by TLS           | Encrypted by TLS       |
| Less secure for sensitive data | More secure            |
| Uses `http://`                 | Uses `https://`        |
| Port 80 commonly used          | Port 443 commonly used |

### Interview answer

> HTTP is a protocol used for communication between clients and servers, while HTTPS is HTTP secured using TLS encryption to protect data transmitted between them.

---

# 18. HTTP Methods

HTTP methods tell the server **what operation the client wants to perform**. They are also called HTTP verbs. ([MDN Web Docs][5])

The main methods you need for API testing are:

```text
GET
POST
PUT
PATCH
DELETE
```

We'll also briefly cover:

```text
HEAD
OPTIONS
```

---

# 19. GET Method

### Purpose

**GET** is used to retrieve data.

Example:

```text
GET /users
```

Means:

> Get users.

Specific user:

```text
GET /users/101
```

Means:

> Get user 101.

GET is intended to retrieve a representation of a resource and is considered safe and idempotent. ([MDN Web Docs][6])

### Example response

```json
{
  "id": 101,
  "name": "Ankitha"
}
```

### QA validations

Check:

* Status code
* Response body
* Response fields
* Data
* Headers
* Response time

---

# 20. POST Method

### Purpose

**POST** is commonly used to create a new resource or submit data for processing.

Example:

```text
POST /users
```

Request body:

```json
{
  "name": "Ankitha",
  "email": "ankitha@example.com"
}
```

Possible response:

```text
201 Created
```

POST can cause a change in server state and is generally not idempotent. ([MDN Web Docs][1])

### QA validations

Check:

* Correct status code
* Resource created
* Generated ID
* Response body
* Database/data consistency
* Validation errors
* Duplicate handling

---

# 21. PUT Method

### Purpose

**PUT** is generally used to replace the current representation of a resource with the supplied representation.

Example:

```text
PUT /users/101
```

Body:

```json
{
  "name": "Ankitha",
  "email": "new@example.com",
  "city": "Hyderabad"
}
```

PUT is defined as idempotent. ([MDN Web Docs][1])

### Important

Think:

> **PUT = Replace/update the resource representation**

---

# 22. PATCH Method

### Purpose

**PATCH** is used for a **partial modification** of a resource.

Suppose the existing user is:

```json
{
  "name": "Ankitha",
  "email": "old@example.com",
  "city": "Hyderabad"
}
```

You only want to change the email.

```text
PATCH /users/101
```

Body:

```json
{
  "email": "new@example.com"
}
```

Only the specified field is modified.

PATCH is specifically defined for partial modifications. ([MDN Web Docs][1])

### Easy memory

```text
PUT   → Full replacement
PATCH → Partial modification
```

---

# 23. DELETE Method

### Purpose

DELETE is used to delete a specified resource.

Example:

```text
DELETE /users/101
```

Means:

> Delete user 101.

DELETE is defined as idempotent, although the response to repeated requests can vary depending on the API implementation. ([MDN Web Docs][1])

Possible response:

```text
204 No Content
```

---

# 24. HEAD Method

HEAD is similar to GET, but the server returns the response headers without the response body.

Example:

```text
HEAD /users/101
```

It can be useful when you want to check whether a resource exists or inspect metadata without downloading the representation.

([MDN Web Docs][1])

---

# 25. OPTIONS Method

OPTIONS is used to discover the communication options supported by a target resource/server.

For example, a server may indicate:

```text
Allow: GET, POST, OPTIONS
```

This tells the client which methods are supported in that context. ([MDN Web Docs][7])

---

# 26. HTTP Methods — Quick Table

| Method  | Main Purpose          | Example             |
| ------- | --------------------- | ------------------- |
| GET     | Retrieve              | `GET /users/101`    |
| POST    | Create/submit         | `POST /users`       |
| PUT     | Replace               | `PUT /users/101`    |
| PATCH   | Partial update        | `PATCH /users/101`  |
| DELETE  | Delete                | `DELETE /users/101` |
| HEAD    | Headers only          | `HEAD /users/101`   |
| OPTIONS | Communication options | `OPTIONS /users`    |

---

# 27. CRUD and HTTP Methods

A very important interview concept is **CRUD**.

CRUD means:

```text
C → Create
R → Read
U → Update
D → Delete
```

Mapping:

| CRUD           | HTTP Method |
| -------------- | ----------- |
| Create         | POST        |
| Read           | GET         |
| Update/Replace | PUT         |
| Partial Update | PATCH       |
| Delete         | DELETE      |

### Easy memory

```text
POST   → Create
GET    → Read
PUT    → Update/Replace
PATCH  → Partial Update
DELETE → Delete
```

---

# 28. What is an HTTP Status Code?

An **HTTP status code** tells the client the outcome of the request.

For example:

```text
200 OK
```

means the request was successfully processed.

HTTP status codes are grouped into five classes. ([MDN Web Docs][5])

```text
1xx → Informational
2xx → Success
3xx → Redirection
4xx → Client Error
5xx → Server Error
```

---

# 29. 1xx — Informational

These indicate that the request has been received/understood and processing is continuing.

Examples:

```text
100 Continue
101 Switching Protocols
```

For normal API testing, these are less commonly the focus.

---

# 30. 2xx — Success

These indicate that the request was successfully handled.

### 200 OK

Request succeeded.

Example:

```text
GET /users/101
```

Response:

```text
200 OK
```

---

### 201 Created

A new resource was successfully created.

Commonly associated with successful POST operations.

Example:

```text
POST /users
```

Response:

```text
201 Created
```

---

### 202 Accepted

The request has been accepted for processing, but processing may not yet be complete.

---

### 204 No Content

The request succeeded, but there is no response body.

A common example is a successful DELETE.

---

# 31. 3xx — Redirection

These indicate that further action may be needed or the resource/request has been redirected.

Important examples:

```text
301 Moved Permanently
302 Found
304 Not Modified
```

---

# 32. 4xx — Client Errors

These indicate a problem with the request from the client side.

### 400 Bad Request

The server cannot process the request because the request is invalid.

Example:

```json
{
  "email": 
}
```

Invalid JSON/request format could result in 400.

---

### 401 Unauthorized

Usually means the request lacks valid authentication credentials.

Example:

```text
Authorization token missing/invalid
```

### Important interview point

**401 does not normally mean "you don't have permission."**

It is primarily associated with **authentication**.

---

### 403 Forbidden

The server understood the request, but the authenticated client is not allowed to perform the operation.

Think:

```text
401 → Who are you?
403 → I know who you are, but you can't do this.
```

---

### 404 Not Found

The requested resource/endpoint could not be found.

Example:

```text
GET /users/999999
```

if that user does not exist.

---

### 405 Method Not Allowed

The resource exists, but the HTTP method isn't allowed for that endpoint.

Example:

```text
DELETE /users
```

when the endpoint doesn't support DELETE.

---

### 409 Conflict

The request conflicts with the current state of the resource.

For example, an API may use 409 when attempting to create a duplicate resource.

---

### 422 Unprocessable Content

The request format can be understood, but the supplied data fails semantic/business validation.

Example:

```text
Event date is invalid
```

The exact status code chosen depends on the API contract.

---

### 429 Too Many Requests

The client has sent too many requests within a specified period/rate limit.

---

# 33. 5xx — Server Errors

These indicate that the server encountered an error while processing a valid-looking request.

### 500 Internal Server Error

Generic server-side error.

### 502 Bad Gateway

A gateway/proxy received an invalid response from an upstream server.

### 503 Service Unavailable

The server/service is temporarily unavailable.

### 504 Gateway Timeout

A gateway/proxy did not receive a timely response from an upstream server.

---

# 34. Important Status Codes for QA

You should memorize these first:

```text
200 → OK
201 → Created
202 → Accepted
204 → No Content

400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found
405 → Method Not Allowed
409 → Conflict
422 → Validation/Semantic error
429 → Too Many Requests

500 → Internal Server Error
502 → Bad Gateway
503 → Service Unavailable
504 → Gateway Timeout
```

The exact status code expected should always be judged against the API's documented contract; different APIs can legitimately choose different codes for some situations. ([Postman Blog][8])

---

# 35. Very Important: Status Code Alone Is Not Enough

This is a **QA interview point**.

Suppose you send:

```text
GET /users/101
```

and receive:

```text
200 OK
```

Can you immediately say the test passed?

### No.

You should also verify:

```text
Status Code
     ↓
Response Body
     ↓
Response Data
     ↓
Headers
     ↓
Business Rules
     ↓
Response Time
```

Example:

Expected:

```json
{
  "id": 101,
  "name": "Ankitha"
}
```

Actual:

```json
{
  "id": 101,
  "name": "Rahul"
}
```

Status:

```text
200 OK
```

The HTTP request technically succeeded, but **your API test should fail if the business/data expectation was Ankitha**.

---

# 36. Complete API Flow

Now combine everything we learned.

Suppose we have:

```text
GET https://api.example.com/users/101?active=true
```

### Step 1 — Client

Postman sends the request.

### Step 2 — Method

```text
GET
```

Means:

> Retrieve data.

### Step 3 — Protocol

```text
HTTPS
```

### Step 4 — Domain

```text
api.example.com
```

### Step 5 — Path

```text
/users/101
```

### Step 6 — Path Parameter

```text
101
```

Identifies the specific user.

### Step 7 — Query Parameter

```text
active=true
```

Adds filtering/customization.

### Step 8 — Server processes request

Server may check:

* Authentication
* Authorization
* User existence
* Business rules
* Database

### Step 9 — Server response

```text
200 OK
```

### Step 10 — Response body

```json
{
  "id": 101,
  "name": "Ankitha",
  "active": true
}
```

### QA validates

```text
✓ Status code
✓ Response body
✓ User ID
✓ User name
✓ Active status
✓ Headers
✓ Response time
```

---

# 37. Interview Questions — Part 2

### Q1. What is REST?

> REST stands for Representational State Transfer. It is an architectural style for designing networked APIs, commonly using HTTP methods to operate on resources.

### Q2. What is an endpoint?

> An endpoint is a specific API location/URL through which a client can access a particular resource or operation.

### Q3. What is a path parameter?

> A path parameter is a value included in the URL path to identify a specific resource, such as `/users/101`.

### Q4. What is a query parameter?

> A query parameter is additional information appended after `?` in a URL, commonly used for filtering, searching, sorting or pagination.

### Q5. Difference between path and query parameter?

> Path parameters identify a specific resource, whereas query parameters generally filter, search, sort, paginate or customize the returned data.

### Q6. Difference between PUT and PATCH?

> PUT is generally used to replace the resource representation, whereas PATCH is used for partial modification.

### Q7. What is the difference between 401 and 403?

> 401 generally indicates that valid authentication credentials are missing or invalid, while 403 indicates that the server understands the client but refuses to authorize the requested operation.

### Q8. What is the difference between 200 and 201?

> 200 indicates a successful request, while 201 indicates that a new resource was successfully created.

### Q9. What is 404?

> 404 Not Found indicates that the requested resource or endpoint could not be found.

### Q10. If an API returns 200, does that mean the test passed?

> No. We must also validate the response body, data, headers, business rules, and other expected conditions.

---

# ⭐ Part 2 — Quick Revision Sheet

Memorize this:

```text
URL
 ↓
Protocol + Domain + Path + Parameters
```

```text
Path Parameter
 ↓
Identifies a specific resource

Query Parameter
 ↓
Filters/customizes the result
```

```text
POST   → Create
GET    → Read
PUT    → Replace
PATCH  → Partial Update
DELETE → Delete
```

```text
1xx → Information
2xx → Success
3xx → Redirection
4xx → Client Error
5xx → Server Error
```

And the most important API testing flow:

```text
Request
   ↓
Method
   ↓
URL
   ↓
Headers
   ↓
Parameters
   ↓
Body
   ↓
Server
   ↓
Status Code
   ↓
Response Headers
   ↓
Response Body
   ↓
Validate Everything
```
# Part 3 — API Testing Process, Types, Tools & Test Case Design

Part 1 covered **API fundamentals and web services**.

Part 2 covered **REST, URLs, parameters, HTTP methods and status codes**.

Now we move into the most important question for a QA:

> **How do I actually test an API?**

---

# 1. What is API Testing?

**API testing** is the process of testing an API directly to verify that it works correctly according to its requirements and specifications.

In API testing, instead of interacting with the application through the UI, we send requests directly to the API and validate the responses.

### Simple flow

```text
Client / Postman
       ↓
   API Request
       ↓
      API
       ↓
    Server
       ↓
   API Response
       ↓
      QA
       ↓
   Validation
```

### Interview definition

> **API testing is a type of software testing in which we directly test APIs by sending requests and validating responses such as status codes, response body, headers, data, business rules and response time.**

---

# 2. Why Do We Perform API Testing?

Suppose an application has a login page:

```text
Username
Password
   ↓
Login
```

When you click Login, the UI may call:

```text
POST /login
```

Instead of testing only through the UI, we can directly test:

```text
POST /login
```

This helps us identify backend problems earlier.

### Major reasons

### 1. Validate business logic

Example:

> An event date should not be in the past.

We can test this directly through the API.

### 2. Validate data

Check whether the correct data is returned or stored.

### 3. Validate error handling

Example:

```text
Invalid username
Missing password
Invalid event ID
```

### 4. Validate security

Test:

* Authentication
* Authorization
* Invalid tokens
* Expired tokens
* Access control

### 5. Faster than UI testing

API requests generally execute much faster than navigating through a UI.

### 6. Test backend independently

Even if the UI is not ready, APIs may already be available for testing.

---

# 3. API Testing vs UI Testing

| API Testing                     | UI Testing                        |
| ------------------------------- | --------------------------------- |
| Tests API/backend               | Tests user interface              |
| No UI required                  | UI required                       |
| Usually faster                  | Usually slower                    |
| Validates request/response      | Validates visual/user interaction |
| Tests business logic directly   | Tests business logic through UI   |
| Easier to automate at API level | UI automation can be more fragile |
| Postman, REST Assured           | Selenium, Playwright              |

### Example

UI:

```text
Open Login Page
↓
Enter Username
↓
Enter Password
↓
Click Login
↓
Verify Dashboard
```

API:

```text
POST /login
↓
Send username/password
↓
Validate response
↓
Validate token
```

---

# 4. What Should We Validate in API Testing?

A common beginner mistake is:

> "I only need to check the status code."

No.

A good API test validates multiple things.

```text
API Response
     │
     ├── Status Code
     ├── Response Body
     ├── Response Headers
     ├── Data
     ├── Schema
     ├── Business Rules
     ├── Authentication
     ├── Authorization
     └── Response Time
```

---

# 5. Status Code Validation

Suppose:

```text
POST /events
```

creates an event.

Expected:

```text
201 Created
```

If the API returns:

```text
500 Internal Server Error
```

the test should fail.

But remember:

> **Correct status code does not automatically mean the API is correct.**

---

# 6. Response Body Validation

Suppose we expect:

```json
{
  "id": 101,
  "name": "Tech Summit"
}
```

But actual response is:

```json
{
  "id": 101,
  "name": "Music Festival"
}
```

Status code could still be:

```text
200 OK
```

But the test should fail because the response data is incorrect.

---

# 7. Header Validation

Example:

```text
Content-Type: application/json
```

We may verify:

* Content-Type
* Authorization-related headers
* Cache headers
* Custom headers
* Security headers where applicable

---

# 8. Response Time Validation

Suppose the requirement says:

> API should respond within 2 seconds.

Actual:

```text
Response time = 5 seconds
```

The API may return correct data, but the performance requirement has failed.

---

# 9. Schema Validation

Schema validation checks whether the response follows the expected structure.

Expected:

```json
{
  "id": 101,
  "name": "Ankitha",
  "age": 23
}
```

Suppose the API returns:

```json
{
  "id": "101",
  "name": "Ankitha",
  "age": "twenty-three"
}
```

The data types are different from the expected schema.

Schema validation can detect this type of issue.

---

# 10. Business Rule Validation

This is very important for a QA.

Suppose the requirement says:

> Event date must be in the future.

You send:

```json
{
  "eventDate": "2020-01-01"
}
```

The API should reject it.

If it accepts the event, that may be a **business logic defect** even if the API returns a technically successful HTTP response.

---

# 11. API Testing Types

There are several types of API testing.

---

## 11.1 Functional Testing

Checks whether the API performs its intended functionality correctly.

Example:

```text
POST /events
```

Expected:

> New event should be created.

Test:

```text
Valid event data
↓
POST API
↓
201 Created
↓
Verify event
```

---

# 12. Positive Testing

Positive testing uses **valid input**.

Example:

```json
{
  "name": "Tech Summit",
  "city": "Hyderabad"
}
```

Expected:

```text
201 Created
```

Question:

> Does the API work correctly with valid data?

---

# 13. Negative Testing

Negative testing uses **invalid or unexpected input**.

Examples:

```text
Missing required field
Invalid data type
Invalid ID
Empty value
Null value
Invalid token
Expired token
Invalid date
Invalid HTTP method
```

Example:

```json
{
  "name": "",
  "city": "Hyderabad"
}
```

Expected:

```text
4xx error
```

The exact status depends on the API contract.

---

# 14. Smoke Testing

**Smoke testing** checks whether the critical functionality is working after a new build/deployment.

The purpose is:

> **Is the API build stable enough for further testing?**

For an event application, smoke tests might include:

```text
Create event
Get event
Update event
Delete event
```

Only the most critical flows are tested.

---

# 15. Sanity Testing

**Sanity testing** is focused testing performed after a specific change or fix to verify that the affected functionality works.

Example:

Developer fixes:

> Event update API bug.

QA may perform:

```text
PUT /events/{id}
```

and test:

* Valid update
* Invalid update
* Required fields
* Response
* Status code

The goal is not necessarily to execute the entire regression suite.

---

# 16. Regression Testing

Regression testing verifies that existing functionality continues to work after changes.

Suppose developers change:

```text
Update Event API
```

We should also verify related functionality:

```text
Create Event
Get Event
Update Event
Delete Event
Search Event
```

The purpose is:

> **Make sure the new change didn't break existing functionality.**

---

# 17. Integration Testing

Integration testing verifies communication between different systems/components.

Example:

```text
Event API
   ↓
Database
```

or:

```text
Order API
   ↓
Payment API
   ↓
Payment Gateway
```

We verify that the systems work correctly together.

---

# 18. Security Testing

Security testing checks whether APIs are properly protected.

Examples:

### Authentication

Can an unauthenticated user access protected APIs?

### Authorization

Can a normal user access admin functionality?

### Token testing

What happens when:

```text
Valid token
Invalid token
Expired token
Missing token
```

is used?

### Input security

Test malicious/unexpected input according to the application's security requirements.

---

# 19. Performance Testing

Performance testing checks API behavior under expected or high loads.

We may measure:

```text
Response time
Throughput
Requests per second
Error rate
Resource utilization
```

Tools such as JMeter can be used for API performance testing.

---

# 20. Load Testing

Load testing checks how the API behaves under expected/concurrent user load.

Example:

```text
1 user
↓
10 users
↓
100 users
↓
1000 users
```

We observe:

* Response time
* Errors
* Throughput
* Stability

---

# 21. Stress Testing

Stress testing pushes the system beyond expected limits to find its breaking point.

Example:

```text
Expected load = 1,000 requests/minute

Test:
2,000
5,000
10,000
...
```

We want to understand:

> At what point does the system become unstable?

---

# 22. Contract Testing

Contract testing verifies that an API's request/response behavior conforms to an agreed contract between consumers and providers.

For example:

Expected response:

```json
{
  "id": 101,
  "name": "Ankitha"
}
```

If the provider suddenly changes:

```json
{
  "eventId": 101,
  "eventName": "Ankitha"
}
```

an existing consumer may break.

Contract testing helps detect incompatible changes.

---

# 23. Reliability Testing

Reliability testing checks whether the API continues to behave correctly over time and under repeated usage.

Example:

```text
Send 10,000 valid requests
↓
Check failures
↓
Check response time
↓
Check data consistency
```

---

# 24. API Testing Process

Now the most important process.

A typical API testing process is:

```text
Requirement Analysis
        ↓
API Documentation Analysis
        ↓
Test Planning
        ↓
Test Data Preparation
        ↓
Test Case Design
        ↓
Environment Setup
        ↓
Test Execution
        ↓
Response Validation
        ↓
Defect Reporting
        ↓
Retesting
        ↓
Regression Testing
        ↓
Test Closure
```

Let's understand each step.

---

# 25. Step 1 — Requirement Analysis

First understand:

* What does the API do?
* What inputs are required?
* What output is expected?
* What are the business rules?
* What authentication is required?
* What validations exist?

Example requirement:

> Event date must be in the future.

This becomes a test condition.

---

# 26. Step 2 — Analyze API Documentation

Read the API documentation.

Check:

```text
Endpoint
HTTP Method
Parameters
Headers
Authentication
Request Body
Response
Status Codes
```

For your EventHub project, the API documentation is available here:

[EventHub API Documentation](https://api.eventhub.rahulshettyacademy.com/api/docs?utm_source=chatgpt.com)

We'll use this documentation in **Part 4**.

---

# 27. Step 3 — Test Planning

Decide:

* What APIs will be tested?
* What types of testing are required?
* What environment will be used?
* What tools are required?
* What test data is required?
* What are the entry/exit criteria?
* What risks exist?

---

# 28. Step 4 — Test Data Preparation

Prepare:

### Valid data

```text
Valid username
Valid email
Valid event date
Valid event ID
```

### Invalid data

```text
Invalid email
Blank name
Past event date
Invalid event ID
Missing required field
```

### Boundary data

```text
Minimum length
Maximum length
Maximum numeric value
Empty value
Null value
```

---

# 29. Step 5 — Test Case Design

Create test cases based on requirements.

Example:

```text
TC_API_001

Scenario:
Create event with valid data

Method:
POST

Expected:
201 Created
```

Another:

```text
TC_API_002

Scenario:
Create event without event name

Method:
POST

Expected:
Validation error
```

---

# 30. Step 6 — Environment Setup

Set up:

* API URL
* Authentication
* Postman
* Test data
* Environment variables
* Required tools

Example:

```text
Environment:
QA

Base URL:
https://api.example.com
```

---

# 31. Step 7 — Test Execution

Send the request.

Example:

```text
POST /events
```

Provide request body.

Then observe:

```text
Status
Response
Headers
Response time
```

---

# 32. Step 8 — Validate Response

Compare actual vs expected.

Example:

### Expected

```text
Status: 201
```

### Actual

```text
Status: 201
```

Pass.

Then check response:

```json
{
  "id": 101,
  "name": "Tech Summit"
}
```

Verify that the data is also correct.

---

# 33. Step 9 — Defect Reporting

Suppose expected:

```text
201 Created
```

Actual:

```text
400 Bad Request
```

You investigate and confirm the API is incorrect.

Then create a bug report containing:

```text
Bug ID
Summary
Environment
API endpoint
Method
Steps
Request
Expected result
Actual result
Severity
Priority
Evidence
```

---

# 34. Step 10 — Retesting

After the developer fixes the defect:

```text
Developer fixes bug
       ↓
QA retests same scenario
       ↓
Pass?
```

If it works:

> Defect can be marked fixed/closed according to the team's workflow.

If it still fails:

> Reopen/report the issue as appropriate.

---

# 35. Step 11 — Regression Testing

After the fix, test related existing functionality to make sure the change didn't introduce new issues.

Example:

```text
Update Event API fixed
        ↓
Run update tests
        ↓
Run related event tests
        ↓
Verify existing functionality
```

---

# 36. API Testing Tools

Now let's understand the main tools.

---

## 36.1 Postman

**Postman** is one of the most popular tools for manually testing APIs.

You can use it to:

* Send requests
* Add headers
* Add parameters
* Send request bodies
* Handle authentication
* Inspect responses
* Write tests
* Organize collections
* Use environments
* Run collections

For beginners:

> **Postman is the first tool you should become comfortable with.**

---

# 37. Swagger / Swagger UI

Swagger is commonly associated with tools and documentation around APIs.

**Swagger UI** provides an interactive interface where you can view API documentation and often execute requests directly from the documentation page.

For example:

```text
API Documentation
       ↓
Endpoint
       ↓
Try it out
       ↓
Enter parameters
       ↓
Execute
       ↓
Response
```

Your EventHub documentation is an example of this style of API documentation.

---

# 38. OpenAPI

**OpenAPI Specification** is a standard, machine-readable way of describing HTTP APIs.

It can describe:

* Endpoints
* Methods
* Parameters
* Request bodies
* Responses
* Authentication
* Schemas

This allows tools to generate interactive documentation and other API-related artifacts.

### Important distinction

> **OpenAPI = specification/standard**

> **Swagger = tooling/ecosystem commonly used around OpenAPI**

---

# 39. SoapUI

SoapUI is a tool used for testing APIs, particularly SOAP services, and it can also be used with REST APIs.

It supports:

* Functional testing
* Assertions
* Data-driven testing
* Automation
* API testing

---

# 40. REST Assured

**REST Assured** is a Java library used to automate REST API testing.

Since you're already learning:

```text
Java
+
TestNG
+
Selenium
```

REST Assured is especially relevant for you.

Example:

```java
given()
    .when()
    .get("/users/101")
    .then()
    .statusCode(200);
```

This is something we'll learn in detail after you understand manual API testing.

---

# 41. Newman

**Newman** is a command-line collection runner for Postman.

The basic flow is:

```text
Postman Collection
        ↓
      Newman
        ↓
Command-line execution
        ↓
CI/CD
```

It is useful for running Postman collections in automated pipelines.

---

# 42. JMeter

Apache JMeter is widely used for performance/load testing.

For APIs, it can simulate multiple users/requests and measure performance characteristics.

Example:

```text
100 users
   ↓
API
   ↓
Response time
Throughput
Errors
```

---

# 43. Tool Selection

| Requirement                      | Common Tool  |
| -------------------------------- | ------------ |
| Manual API testing               | Postman      |
| API documentation                | Swagger UI   |
| API specification                | OpenAPI      |
| SOAP testing                     | SoapUI       |
| REST API automation with Java    | REST Assured |
| Run Postman collections from CLI | Newman       |
| API performance/load testing     | JMeter       |

---

# 44. API Test Case Design

Now let's learn how a QA thinks while creating API test cases.

Suppose we have:

```text
POST /events
```

We shouldn't create only one test:

> Create event with valid data.

We need multiple scenarios.

---

## 44.1 Valid Request

```json
{
  "name": "Tech Summit",
  "city": "Hyderabad"
}
```

Expected:

```text
201 Created
```

---

## 44.2 Missing Required Field

```json
{
  "city": "Hyderabad"
}
```

Expected:

> Validation error.

---

## 44.3 Empty Value

```json
{
  "name": "",
  "city": "Hyderabad"
}
```

Expected:

> Validation error if name is required.

---

## 44.4 Invalid Data Type

Suppose name should be a string:

```json
{
  "name": 12345
}
```

Expected:

> Request should be rejected according to the API contract.

---

## 44.5 Null Value

```json
{
  "name": null
}
```

Verify the API's expected behavior.

---

## 44.6 Boundary Testing

Suppose:

> Event name allows 1–100 characters.

Test:

```text
1 character
100 characters
0 characters
101 characters
```

---

## 44.7 Duplicate Data

Try creating the same resource twice.

Check whether the API:

* Allows duplicates
* Rejects duplicates
* Returns an appropriate error

depending on requirements.

---

# 45. API Test Case Categories

A good test suite should cover:

```text
Functional
Positive
Negative
Boundary
Validation
Authentication
Authorization
Security
Performance
Integration
Regression
```

---

# 46. API Test Case Template

Here's a practical template you can use:

| Field             | Example                          |
| ----------------- | -------------------------------- |
| Test Case ID      | API_TC_001                       |
| Module            | Events                           |
| Test Scenario     | Create event                     |
| Test Type         | Positive                         |
| Method            | POST                             |
| Endpoint          | `/events`                        |
| Preconditions     | API available                    |
| Headers           | `Content-Type: application/json` |
| Request Body      | Valid event JSON                 |
| Test Data         | Valid event data                 |
| Expected Status   | 201                              |
| Expected Response | Event created                    |
| Actual Result     | —                                |
| Status            | Pass/Fail                        |
| Priority          | High                             |
| Severity          | —                                |
| Comments          | —                                |

---

# 47. Example Test Cases

### TC_API_001

**Scenario:** Create event with valid data

```text
Method: POST
Endpoint: /events
Input: Valid event data
Expected: 201 Created
```

---

### TC_API_002

**Scenario:** Create event without required name

```text
Method: POST
Endpoint: /events
Input: Name missing
Expected: Validation error
```

---

### TC_API_003

**Scenario:** Get existing event

```text
Method: GET
Endpoint: /events/{validId}
Expected: 200 OK
```

---

### TC_API_004

**Scenario:** Get non-existing event

```text
Method: GET
Endpoint: /events/{invalidId}
Expected: Appropriate 4xx response
```

---

### TC_API_005

**Scenario:** Update existing event

```text
Method: PUT/PATCH
Endpoint: /events/{validId}
Input: Valid update data
Expected: Successful update response
```

---

### TC_API_006

**Scenario:** Delete existing event

```text
Method: DELETE
Endpoint: /events/{validId}
Expected: Successful deletion response
```

---

# 48. What Makes a Good API Test Case?

A good API test case should be:

### Clear

Anyone should understand what you're testing.

### Independent

Where practical, tests should avoid unnecessary dependencies.

### Repeatable

The test should produce consistent results under the same conditions.

### Traceable

It should map back to a requirement or API contract.

### Specific

Clearly define:

```text
Input
Expected status
Expected response
Expected business behavior
```

---

# 49. Common API Testing Mistakes

### Mistake 1

Checking only status code.

❌

```text
200 = Pass
```

Not enough.

### Mistake 2

Testing only positive scenarios.

You must test:

```text
Positive
Negative
Boundary
Security
Validation
```

### Mistake 3

Ignoring response body.

### Mistake 4

Ignoring headers.

### Mistake 5

Not checking business rules.

### Mistake 6

Using hard-coded dynamic data everywhere.

For example:

```text
eventId = 123
```

may become invalid after the test data changes.

### Mistake 7

Not cleaning up test data.

If your test creates 100 events every time, your environment can become polluted.

---

# 50. API Testing Challenges

You asked specifically about challenges, so let's understand the important ones.

### 1. Authentication

APIs may require:

```text
API key
Bearer token
OAuth
Basic authentication
```

### 2. Dynamic Data

IDs may change every time.

Example:

```text
POST → creates ID 101
```

Next run:

```text
POST → creates ID 102
```

Your next request needs the newly generated ID.

---

### 3. Token Expiration

A token may expire.

Test automation needs to handle:

```text
Get token
↓
Use token
↓
Token expires
↓
Generate/refresh token
```

---

### 4. API Dependency

Example:

```text
Create Event
     ↓
Get Event
     ↓
Update Event
     ↓
Delete Event
```

If Create fails, the dependent tests may also fail.

---

### 5. Test Data Management

You need valid and invalid data.

Examples:

```text
Valid event
Invalid event
Duplicate event
Expired event
Future event
Missing fields
```

---

### 6. Environment Dependency

Different environments may have different:

```text
Base URLs
Databases
Credentials
Test data
Configurations
```

Example:

```text
DEV
QA
UAT
PROD
```

---

### 7. Third-Party APIs

Your application may depend on external services.

Example:

```text
Application
    ↓
Payment API
    ↓
Third-party payment provider
```

If the third-party system is unavailable, testing becomes difficult.

---

### 8. Complex JSON

Large nested JSON can be difficult to validate.

Example:

```json
{
  "user": {
    "address": {
      "city": "Hyderabad"
    }
  }
}
```

---

### 9. Asynchronous APIs

Some APIs don't return the final result immediately.

Example:

```text
POST /generate-report
        ↓
202 Accepted
        ↓
Processing...
        ↓
Report ready later
```

Testing requires handling asynchronous behavior.

---

### 10. Rate Limiting

APIs may restrict the number of requests.

Example:

```text
100 requests/minute
```

If you exceed the limit:

```text
429 Too Many Requests
```

---

# 51. ⭐ API Testing Mindset

When you receive an API requirement, think like this:

```text
1. What does this API do?
          ↓
2. What is the endpoint?
          ↓
3. Which HTTP method?
          ↓
4. What input is required?
          ↓
5. What headers are required?
          ↓
6. Is authentication required?
          ↓
7. What is the expected response?
          ↓
8. What status code should be returned?
          ↓
9. What happens with invalid data?
          ↓
10. What are the boundary conditions?
          ↓
11. What business rules exist?
          ↓
12. What security checks are needed?
          ↓
13. What happens under repeated/high load?
```

That is the **QA mindset** interviewers want to see.

---

# 52. ⭐ Part 3 Interview Questions

### Q1. What is API testing?

> API testing is testing an API directly by sending requests and validating responses, including status codes, response data, headers, business rules and other expected behavior.

### Q2. What do you validate in API testing?

> I validate status code, response body, headers, data, schema, business rules, authentication, authorization and response time depending on the requirement.

### Q3. What is positive testing?

> Testing an API with valid input and verifying that it produces the expected successful result.

### Q4. What is negative testing?

> Testing an API with invalid, missing, unexpected or boundary input and verifying that it handles the error correctly.

### Q5. What is smoke testing?

> Smoke testing is a small set of critical tests used to verify that the main API functionality is working and the build is stable enough for further testing.

### Q6. What is sanity testing?

> Sanity testing is focused testing of specific functionality after a change or fix to verify that the affected functionality works correctly.

### Q7. What is regression testing?

> Regression testing verifies that existing functionality continues to work after changes or fixes.

### Q8. What is Swagger?

> Swagger is an ecosystem of tools used for working with API descriptions and documentation, commonly around the OpenAPI specification. Swagger UI provides an interactive way to explore API documentation.

### Q9. What is OpenAPI?

> OpenAPI is a standard specification for describing HTTP APIs in a machine-readable format.

### Q10. What is Postman?

> Postman is a tool used to develop, explore and test APIs by sending requests, inspecting responses, organizing collections and writing automated checks.

### Q11. What is REST Assured?

> REST Assured is a Java library used to automate testing of REST APIs.

### Q12. What is Newman?

> Newman is a command-line runner for executing Postman collections, commonly used in automated or CI/CD workflows.

---

# ⭐ Part 3 — Quick Revision

Remember this API testing flow:

```text
Requirement
    ↓
API Documentation
    ↓
Test Plan
    ↓
Test Data
    ↓
Test Cases
    ↓
Send Request
    ↓
Validate Response
    ↓
Pass / Fail
    ↓
Defect
    ↓
Retest
    ↓
Regression
```

Remember the major testing types:

```text
Functional
Positive
Negative
Smoke
Sanity
Regression
Integration
Security
Performance
Load
Stress
Contract
```

Remember the major tools:

```text
Postman       → Manual API Testing
Swagger UI    → API Documentation/Exploration
OpenAPI       → API Specification
SoapUI        → SOAP/REST Testing
REST Assured  → Java API Automation
Newman        → Postman CLI Execution
JMeter        → Performance Testing
```

And remember the **three most important API testing validations**:

> **Status Code + Response Body + Business Logic**

---




