name: default
layout: true
class: center, middle
---
name: inverse
layout: true
class: center, middle, inverse
---
template: default
![](docker.png)
# Introduction to Docker Containers and Microservices
---
## Monolithic Architecture
---
layout: false
.left-column[
  ## What is it?
]
.right-column[
- Application is deployed as a single monolithic application

- Multiple instances of the application are deployed behind a load balancer in order to scale and improve availability

- Application uses a single database

- Netflix, Amazon.com and eBay initially had a monolithic architecture
]
---
layout: false
.left-column[
  ## What is it?
  ## Benefits
]
.right-column[
- Simple development process

- Deployments are straightforward

- Simple scaling strategy
]
---
layout: false
.left-column[
  ## What is it?
  ## Benefits
  ## Drawbacks
]
.right-column[
Once the application becomes large and the team grows in size, this approach has a number of drawbacks

- Large monolithic code base intimidates developers

- Modularity breaks down over time

- The larger the application the longer it takes to start up

- Continuous deployment is difficult

- Scaling can get tricky

- Obstacle to scaling development

- Requires a long-term commitment to a technology stack
]
---
background-image: url(monolithic-architecture.png)
---
template: inverse
## Microservices Architecture
---
layout: false
.left-column[
  ## What is it?
]
.right-column[
- An architecture that structures the application as a set of loosely coupled, collaborating services

- Each service implements a set of narrowly, related functions (e.g. Order Management Service, Customer Management Service)
]
---
layout: false
.left-column[
  ## What is it?
  ## Benefits
]
.right-column[
- Each microservice is relatively small, easier to understand and starts up faster

- Each service can be deployed independently of other services

- Easier to scale development (2 pizza teams)

- Improved fault isolation

- Eliminates any long-term commitment to a technology stack
]
---
layout: false
.left-column[
  ## What is it?
  ## Benefits
  ## Drawbacks
]
.right-column[
- Developers must deal with the additional complexity of creating a distributed system

- Developers must implement the inter-service communication mechanism (gRPC, Apache Thrift, REST)

- Implementing use cases that span multiple services without using distributed transactions is difficult

- Implementing use cases that span multiple services requires careful coordination between the teams

- In production, there is also the operational complexity of deploying and managing a system comprised of many different service types
]
---
background-image: url(microservices-architecture.png)
---
layout: false
.left-column[
  ## When to use?
]
.right-column[
One challenge with using this approach is deciding when it makes sense to use it.

- When developing the first version of an application, you often do not have the problems that this approach solves.

- Using an elaborate, distributed architecture will slow down development.

- As the application grows and you need to scale, performing functional decomposition on the tangled dependencies might make it difficult to decompose the monolithic application into a set of services.
]
---
layout: false
.left-column[
  ## When to use?
  ## How to decompose?
]
.right-column[
Each service should have only a small set of responsibilities. Apply the  the Single Responsibility Principle (SRP).

- By business capability/department (Banking, Insurance, etc.)

- By verb or use case (Shipping, Invoicing, etc.)

- By nouns or resources (Account, Order, etc.)
]
---
layout: false
.left-column[
  ## When to use?
  ## How to decompose?
  ## Data consistency?
]
.right-column[
In order to ensure loose coupling, each service has its own database.

- 2 phase-commit/distributed transactions is not an option for many applications.

- Use an event-driven archirecture (Event Sourcing, Transaction Log Tailing).
]
---
template: inverse
## Docker
---
background-image: url(what-is-docker.png)
---
layout: false
.left-column[
  ## What is Docker?
]
.right-column[
- An open platform for developers and sysadmins to build, ship, and run distributed applications.

- Enables apps to be quickly assembled from components and eliminates the friction between development, QA, and production environments.

- Eliminates *“works on my machine”* problems.

- DevOps run and manage apps side-by-side in isolated containers to get better compute density.

- Works on both Microsoft Windows and all major Linux distributions.
]
---
layout: false
.left-column[
  ## What is Docker?
  ## What is a Container?
]
.right-column[
Everything required to make a piece of software run is packaged into isolated containers.

- Unlike VMs, containers do not bundle a full operating system.

- Efficient, lightweight, self-contained systems.

- Guarantee that software will always run the same, regardless of where it’s deployed.

- Isolate applications from one another and from the underlying infrastructure.
]
---
layout: false
.left-column[
  ## What is Docker?
  ## What is a Container?
  ## Container vs VMs
]
.right-column[
  .full-width[![](vm.png)]
]
---
layout: false
.left-column[
  ## What is Docker?
  ## What is a Container?
  ## Container vs VMs
]
.right-column[
  .full-width[![](container.png)]
]
---
background-image: url(grumpy-cat-demo-time.jpg)
