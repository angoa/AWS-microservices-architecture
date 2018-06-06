
# User Interface
Modern web applications often use JavaScript frameworks to implement a
single-page application that communicates with a RESTful API. Static web
content can be served using Amazon Simple Storage Service (Amazon S3) and
Amazon CloudFront.
```
CloudFront is a global content delivery network (CDN) service that
accelerates delivery of your websites, APIs, video content, and other web
assets.
```
Since clients of a microservice are served from the closest edge location and get
responses either from a cache or a proxy server with optimized connections to
the origin, latencies can be significantly reduced. However, microservices
running close to each other don’t benefit from a CDN. This
approach might even add more latency. It is a best practice to implement other
caching mechanisms to reduce chattiness and minimize latencies.

# Microservices
The API of a microservice is the central entry point for all client requests. The
application logic hides behind a set of programmatic interfaces, typically a
RESTful web services API. This API accepts and processes calls from clients
and might implement functionality such as traffic management, request
filtering, routing, caching, and authentication and authorization.
Many AWS customers use the Elastic Load Balancing (ELB) Application Load
Balancer together with Amazon EC2 Container Service (Amazon ECS) and Auto
Scaling to implement a microservices application. The Application Load
Balancer routes traffic based on advanced application-level information that
includes the content of the request.
```
ELB automatically distributes incoming application traffic across
multiple Amazon EC2 instances.
```
The Application Load Balancer distributes incoming requests to Amazon ECS
container instances running the API and the business logic.
```
Amazon EC2 is a web service that provides secure, resizable compute
capacity in the cloud. It is designed to make web-scale cloud computing
easier for developers.

Amazon EC2 Container Service (Amazon ECS) is a highly scalable, high
performance container management service that supports Docker
containers and allows you to easily run applications on a managed cluster
of Amazon EC2 instances.
```
Amazon ECS container instances are scaled out and scaled in, depending on the
load or the number of incoming requests. Elastic scaling allows the system to be
run in a cost-efficient way and also helps protect against denial of service
attacks.
```
Auto Scaling helps you maintain application availability and allows you
to scale your Amazon EC2 capacity up or down automatically according
to conditions you define.
```
# Data Store
The data store is used to persist data needed by the microservices. Popular
stores for session data are in-memory caches such as Memcached or Redis.
AWS offers both technologies as part of the managed Amazon ElastiCache
service.
```
Amazon ElastiCache is a web service that makes it easy to deploy,
operate, and scale an in-memory data store or cache in the cloud.21 The
service improves the performance of web applications by allowing you to
retrieve information from fast, managed, in-memory caches, instead of
relying entirely on slower disk-based databases.
```
Putting a cache between application servers and a database is a common
mechanism to alleviate read load from the database, which, in turn, may allow
resources to be used to support more writes. Caches can also improve latency.
Relational databases are still very popular for storing structured data and
business objects. AWS offers six database engines (Microsoft SQL Server,
Oracle, MySQL, MariaDB, PostgreSQL, and Amazon Aurora) as managed
services via Amazon Relational Database Service (Amazon RDS).
```
Amazon RDS makes it easy to set up, operate, and scale a relational
database in the cloud.22 It provides cost-efficient and resizable capacity
while managing time-consuming database administration tasks, freeing
you to focus on applications and business.
```

Since individual microservices are designed to do one thing well, they typically
have a simplified data model that might be well suited to NoSQL persistence. It
is important to understand that NoSQL-databases have different access patterns
than relational databases. If this is necessary, the logic has to be implemented in the application.
```
Amazon DynamoDB is a fast and flexible NoSQL database service for all
applications that need consistent, single-digit millisecond latency at any
scale.
```

# API Implementation
The architecture we have described is already using managed services, but you
still have to operate EC2 instances. We can further reduce the operational
efforts needed to run, maintain, and monitor microservices by using a fully
serverless architecture.

Architecting, continuously improving, deploying, monitoring, and maintaining
an API can be a time-consuming task. Sometimes different versions of APIs
need to be run to assure backward compatibility of all APIs for clients. The
different stages of the development cycle (development, testing, and
production) further multiply operational efforts.
Access authorization is a critical feature for all APIs, but it is usually complex to
build and involves repetitive work. When an API is published and becomes
successful, the next challenge is to manage, monitor, and monetize the
ecosystem of third-party developers utilizing the API.
Other important features and challenges include throttling requests to protect
the backend, caching API responses, request and response transformation, and
generating API definitions and documentation with tools such as Swagger.
Amazon API Gateway addresses those challenges and reduces the operational
complexity of creating and maintaining RESTful APIs.
```
API Gateway is a fully managed service that makes it easy for developers
to create, publish, maintain, monitor, and secure APIs at any scale.
```

# Serverless Microservices
Getting rid of servers is the
ultimate way to eliminate operational complexity.
```
AWS Lambda lets you run code without provisioning or managing
servers. You pay only for the compute time you consume – there is no
charge when your code is not running. With Lambda, you can run code 
for virtually any type of application or backend service – all with zero
administration.
```
You simply upload your code and let Lambda take care of everything required to
run and scale the execution to meet your actual demand curve with high
availability. Lambda supports several programming languages and can be
triggered from other AWS services or be called directly from any web or mobile
application.
Lambda is highly integrated with API Gateway. The possibility of making
synchronous calls from API Gateway to AWS Lambda enables the creation of
fully serverless applications and is described in detail in our documentation.
