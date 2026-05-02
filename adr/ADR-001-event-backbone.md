# ADR-001: Introduce Event Backbone using Amazon EventBridge

Status: Accepted  
Date: 2026-05-02  
Owner: Sebastian Celejewski 

# Context

The current architecture of ChoCoop is a single integrated serverless application.

New capabilities are planned:

- notifications
- Kimbalontek mood engine
- time-based processing

These capabilities should be implemented as independent components.

The system currently lacks a mechanism for decoupled communication between components.

Direct integration (e.g. calling services or extending the existing backend) would lead to tighter coupling and reduced flexibility.

# Decision

Introduce an event-driven integration layer based on Amazon EventBridge.

The core application will publish domain events, and other components will consume them independently.

# Alternatives Considered

## Option A — Extend Existing Backend (Monolithic Approach)

Add notifications and other logic directly into the current backend.

### Pros

- simplest implementation
- no new infrastructure required

### Cons

- tight coupling
- reduced modularity
- harder to evolve architecture
- violates architecture principles (loose coupling, incremental evolution)

## Option B — Direct Service-to-Service Calls

Introduce separate services, but connect them via synchronous API calls.

### Pros

- clear control flow
- familiar model

### Cons

- runtime coupling between services
- harder to scale independently
- less resilient
- requires service discovery and API management

## Option C — Event-Driven Integration (Chosen)

Use an event bus to decouple producers and consumers.

### Pros

- loose coupling
- independent deployment of components
- natural fit for notifications and asynchronous workflows
- enables future extensibility (analytics, additional services)

### Cons

- increased architectural complexity
- requires event design and governance
- eventual consistency

# Rationale

The event-driven approach aligns with the architecture principles:

- Loose Coupling  
- Incremental Evolution  
- Event-Driven Where Valuable  

It enables adding new capabilities (notifications, Kimbalontek) without modifying the core application.

It also provides a strong foundation for learning event-driven architecture in practice.

# Consequences

## Positive

- decoupled architecture
- easier addition of new services
- independent deployments
- improved extensibility

## Negative

- need to define and maintain event contracts
- increased complexity compared to monolith
- need for observability and debugging of async flows

# Implementation Notes

Initial scope:

- create EventBridge bus
- publish first domain events from core application
- no mandatory consumers in the first iteration

# Follow-Up Decisions

Future ADRs may define:

- event naming conventions
- event schema versioning
- notification delivery strategy
- Kimbalontek mood model