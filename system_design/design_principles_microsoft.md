## Source
https://docs.microsoft.com/en-us/azure/architecture/guide/

## Architecture Styles

#### N-Tier
N-tier is a traditional architecture for enterprise applications. Dependencies are managed by dividing the application into layers that perform logical functions, such as presentation, business logic, and data access. A layer can only call into layers that sit below it. However, this horizontal layering can be a liability.

#### Web-Queue-Worker
For a purely PaaS solution, consider a Web-Queue-Worker architecture. In this style, the application has a web front end that handles HTTP requests and a back-end worker that performs CPU-intensive tasks or long-running operations. The front end communicates to the worker through an asynchronous message queue.


#### Event-driven architecture
Event-Driven Architectures use a publish-subscribe (pub-sub) model, where producers publish events, and consumers subscribe to them. The producers are independent from the consumers, and consumers are independent from each other.

#### MicroService
A microservices application is composed of many small, independent services. Each service implements a single business capability. Services are loosely coupled, communicating through API contracts.

Benefits :

  - Independent development
  - Independent deployments
  - Fault isolation
  - Granular scaling
  - Independent tech


#### Best practices

- Model services around the business domain.
- Decentralize everything. Avoid sharing code or data schemas.
- Data storage should be private to the service that owns the data.
- Services communicate through well-designed APIs. APIs should model the domain.
- Avoid coupling between services. Causes of coupling include shared database schemas and rigid communication protocols.
- Services should have loose coupling and high functional cohesion.
- Isolate failures. Use resiliency strategies to prevent failures within a service from cascading.
