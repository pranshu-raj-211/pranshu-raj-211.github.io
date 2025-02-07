## Understanding REST: A Practical Perspective  

For a long time I've been confused by what REST really means, partly due to the inconsistent ways it is explained on many well known resources. This blog post is documentation of what I learnt about the REST specification, what it really is, what it's not and how to make the most out of it.

In a standard client-server architecture, a client makes a request, and the server responds—often in JSON format. REST (Representational State Transfer) provides a set of guidelines on how these interactions should happen, but it is not a strict protocol. It’s a specification that focuses on how clients request information and how servers respond, independent of how data is stored internally.  

### Resources in REST  

Everything in REST is a resource—an entity in your system. For example:  
- **E-commerce system**: Users, Products, Orders, Sellers  
- **Library management system**: Students, Books  

REST does not concern itself with how these resources are stored. Instead, it focuses on how they are exposed and manipulated by clients.  

#### Representation in REST  

The key idea behind REST is representation. A client requests data in a specific format, and the server responds accordingly. This is controlled via the **Content-Type** header in HTTP requests. A well-implemented REST API should support multiple representations of the same data, such as JSON, XML, or CSV.  

Internally, data might be stored in a relational database with rows and columns, but externally, it is represented in a format suitable for clients (e.g., JSON).  

#### HTTP and REST  

While REST doesn’t enforce a specific protocol, it is most commonly implemented using HTTP. However, just because we use HTTP doesn’t mean we are following REST principles.  

REST utilizes HTTP verbs to define operations on resources:  
- **GET** `/users/155` → Fetch the user with ID 155  
- **DELETE** `/users/155` → Delete the user with ID 155  
- **POST** `/users` → Create a new user  

A key principle of REST is that the **URL identifies the resource, not the action**. For example:  
- ✅ **RESTful**: `GET /students/1`  
- ❌ **Not RESTful**: `POST /getstudent/` (where the ID is in the request body)  

By using HTTP verbs, we can operate on the same URL (`/students/1`) in different ways.  

#### Why HTTP Works Well for REST  

HTTP comes with robust tooling and infrastructure, making it easy to implement REST APIs without reinventing the wheel. However, there are some downsides:  

1. **Serialization Overhead**  
   - REST is not as efficient as RPC-style communication. Data needs to be serialized and deserialized, adding latency.  
   - Every client has to manually convert JSON/XML into native objects.  

2. **Repetitive Consumption**  
   - Every API consumer has to handle serialization, retries, failures, and timeouts.  

3. **Limited HTTP Verb Support**  
   - Some web servers don’t support all HTTP verbs, reducing flexibility in designing APIs.  

4. **Large HTTP Payloads**  
   - JSON payloads are heavy, making REST less suitable for high-performance, low-latency systems.  

5. **Protocol Lock-in**  
   - Switching from HTTP to another transport protocol is difficult in RESTful systems.  

Despite these drawbacks, REST remains widely used due to its simplicity and compatibility with existing web technologies. However, for performance-critical applications, alternatives like gRPC or GraphQL might be worth considering.
