# ADR-002: Define Event Naming and Structure Conventions

Status: Accepted  
Date: 2026-05-02  
Owner: Sebastian Celejewski  

# Context

The system introduces an event-driven architecture using an event backbone.

Multiple components will publish and consume events:

- core application
- notifications service
- Kimbalontek engine
- future services

Without clear conventions, events may become inconsistent, hard to understand, and difficult to evolve.

A shared approach to event naming and structure is required.

# Decision

Adopt a consistent convention for event naming and payload structure based on domain events.

## Event Naming

Events follow the pattern:

    <Entity><PastTenseAction>

Examples:

    WorkRequestCreated
    WorkRequestCompleted
    ActivityCreated
    KimbalontekMoodChanged

## Event Semantics

- events represent facts that already happened  
- events are immutable  
- events are not commands  

## Event Payload Structure

Each event should contain:

- eventName  
- occurredAt (timestamp)  
- source (producer system)  
- entityId (e.g. workRequestId, activityId)  
- relevant business data  

Example structure (conceptual):

    eventName: WorkRequestCreated
    occurredAt: 2026-05-02T12:00:00Z
    source: sebcel-chocoop-app
    workRequestId: 550e8400-e29b-41d4-a716-446655440000
    user: 93546812-f081-70ba-5275-53f301512139
    priority: HIGH

## Versioning and Compatibility

Events are expected to be backward compatible by default.

### Compatibility Rules

The following rules apply to event evolution:

- existing fields must not be removed  
- existing field semantics must not change  
- new fields must be optional  
- consumers must ignore unknown fields  

### Breaking Changes

A change is considered breaking if it:

- removes an existing field  
- changes the meaning of a field  
- changes the data type or structure in a non-compatible way  

### Handling Breaking Changes

Breaking changes require one of the following:

- introducing a new event type, or  
- introducing explicit event versioning  

### Non-Breaking Changes

Backward-compatible changes (e.g. adding optional fields) are allowed without version changes.

# Alternatives Considered

## Option A — No Formal Convention

Allow each component to define events freely.

### Pros

- no upfront design effort

### Cons

- inconsistent naming  
- harder integration  
- increased maintenance cost  

## Option B — Technical/EventBus-Oriented Naming

Use infrastructure-based naming such as:

    event.workrequest.created

### Pros

- familiar for some systems  
- easy to group in infrastructure  

### Cons

- less readable from business perspective  
- leaks technical concerns into domain  

## Option C — Domain Event Naming (Chosen)

Use domain-driven naming based on business events.

### Pros

- readable and meaningful  
- aligns with domain model  
- easier collaboration and reasoning  

### Cons

- requires discipline  
- requires shared understanding of domain  

# Rationale

Domain-based event naming improves clarity and long-term maintainability.

It ensures that events represent meaningful business facts rather than technical signals.

This aligns with the architecture principles:

- Business Value First  
- Loose Coupling  
- Event-Driven Where Valuable  

# Consequences

## Positive

- consistent event ecosystem  
- easier onboarding and understanding  
- clear communication between services  

## Negative

- need for discipline in event design  
- need to maintain event documentation  

# Implementation Notes

- initial events should be defined alongside Phase 1 (Event Backbone)  
- event definitions can be documented in a shared file if needed (events.md)
- validation can be lightweight (no strict schema registry required at this stage)  

# Follow-Up Decisions

Future ADRs may define:

- event schema validation strategy  
- event versioning policy  
- naming of event sources  