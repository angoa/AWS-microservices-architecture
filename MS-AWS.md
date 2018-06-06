
# User Interface
Modern web applications often use JavaScript frameworks to implement a
single-page application that communicates with a RESTful API. Static web
content can be served using Amazon Simple Storage Service (Amazon S3) and
Amazon CloudFront.
CloudFront is a global content delivery network (CDN) service that
accelerates delivery of your websites, APIs, video content, and other web
assets.13
Since clients of a microservice are served from the closest edge location and get
responses either from a cache or a proxy server with optimized connections to
the origin, latencies can be significantly reduced. However, microservices
running close to each other don’t benefit from a CDN. In some cases, this
approach might even add more latency. It is a best practice to implement other
caching mechanisms to reduce chattiness and minimize latencies.

# Microservices
The API of a microservice is the central entry point for all client requests. The
application logic hides behind a set of programmatic interfaces, typically a
RESTful web services API.14 This API accepts and processes calls from clients
and might implement functionality such as traffic management, request
filtering, routing, caching, and authentication and authorization.
Many AWS customers use the Elastic Load Balancing (ELB) Application Load
Balancer together with Amazon EC2 Container Service (Amazon ECS) and Auto
Scaling to implement a microservices application. The Application Load
Balancer routes traffic based on advanced application-level information that
includes the content of the request.
ELB automatically distributes incoming application traffic across
multiple Amazon EC2 instances.15
The Application Load Balancer distributes incoming requests to Amazon ECS
container instances running the API and the business logic.
Amazon EC2 is a web service that provides secure, resizable compute
capacity in the cloud. It is designed to make web-scale cloud computing
easier for developers.16
Amazon EC2 Container Service (Amazon ECS) is a highly scalable, high
performance container management service that supports Docker
containers and allows you to easily run applications on a managed cluster
of Amazon EC2 instances.17
Amazon ECS container instances are scaled out and scaled in, depending on the
load or the number of incoming requests. Elastic scaling allows the system to be
run in a cost-efficient way and also helps protect against denial of service
attacks.
Auto Scaling helps you maintain application availability and allows you
to scale your Amazon EC2 capacity up or down automatically according
to conditions you define.18
