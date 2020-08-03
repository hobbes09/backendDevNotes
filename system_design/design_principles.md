## Design Principles

#### Design for self healing

In a distributed system, failures happen. Design your application to be self healing when failures occur.

- Detect failures.
- Respond to failures gracefully.
- Log and monitor failures, to give operational insight
- Alert metrics

#### Make all things redundant

Build resiliency infrastructure for every node and connections between the code of the architecture.

This includes :
- Databases
- Services
- Geo-replication
- Multiple region deployments
- Disaster recovery mechanism

#### Minimize coordination

Minimize coordination between application services to achieve scalability
