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

