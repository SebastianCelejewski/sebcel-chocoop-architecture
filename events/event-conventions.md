# event-conventions.md

# Event Conventions

Project: Chores Cooperative (ChoCoop)
Status: Active
Last Updated: 2026-05-29
Owner: Sebastian Celejewski

---

# Purpose

This document defines naming conventions, structural rules, and compatibility requirements for events used in the ChoCoop platform.

The purpose of these conventions is to ensure:

* consistency
* readability
* compatibility between producers and consumers
* safe long-term evolution of event contracts

These conventions complement ADR-002.

---

# Event Philosophy

Events represent facts that already happened.

Events:

* describe completed actions or state transitions
* are immutable
* are append-only
* must not be modified after publication

Examples:

* `WorkRequestCreated`
* `ActivityCreated`
* `WorkRequestCompleted`

Non-examples:

* `CreateWorkRequest`
* `UpdateActivity`
* `HandleOverdueRequest`

---

# Naming Conventions

## Event Names

Event names:

* use PascalCase
* use past tense
* describe completed business facts

Examples:

* `ActivityCreated`
* `WorkRequestCompleted`
* `KimbalontekMoodChanged`

---

## Field Names

Field names:

* use camelCase
* should be descriptive and domain-oriented
* should avoid infrastructure terminology when possible

Examples:

* `workRequestId`
* `createdBy`
* `occurredAt`

---

# Event Structure

All events should contain:

* `eventName`
* `occurredAt`
* `source`

Optional metadata may include:

* correlation identifiers
* causation identifiers
* trace identifiers
* version information

---

# Identifier Rules

* identifiers are opaque
* identifiers must not encode business meaning
* GUIDs are preferred
* `userId` corresponds to Cognito `sub`

---

# Compatibility Rules

Event evolution must preserve backward compatibility whenever possible.

Allowed changes:

* adding optional fields
* adding new event types
* extending enumerations carefully

Forbidden changes:

* removing fields
* changing field semantics
* changing field types incompatibly
* renaming fields

Breaking changes require:

* explicit versioning, or
* introduction of a new event type

---

# Consumer Expectations

Consumers:

* must tolerate unknown fields
* should avoid strict schema assumptions
* should process events idempotently where possible

---

# Event Ownership

Each event should have:

* a clearly defined producer
* a well-understood business meaning
* stable semantic intent

The event catalog is the authoritative source of event definitions.

---

# Future Evolution

Future improvements may include:

* formal JSON schemas
* schema registry integration
* event version negotiation
* event metadata standardization
* tracing and observability integration
