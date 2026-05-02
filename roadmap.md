# Architecture Roadmap

Project: Chores Cooperative (ChoCoop)  
Status: Active  
Planning Horizon: 2026 Q2–Q3  
Last Updated: 2026-05-02  
Owner: Sebastian Celejewski 

# Overview

This roadmap describes the incremental transformation from the current single-stack architecture to a modular, event-driven system.

The transformation is divided into controlled phases. Each phase delivers standalone value while preparing the foundation for the next step.

---

# Phase 0 — Baseline (Completed)

## State

- Single Amplify-based application
- Activities and Work Requests implemented
- Activity list implemented using virtualization (react-virtualized) to ensure performance with growing datasets
- Production deployment (v0.5.0)

## Outcome

- Stable product baseline
- Validated user value
- Starting point for architecture evolution

---

# Phase 1 — Event Backbone Introduction

## Goal

Introduce an event-driven integration layer without changing core behavior.

## Scope

- Create event infrastructure (EventBridge)
- Define initial event schema
- Publish first domain events from core application

## Key Events

- WorkRequestCreated
- WorkRequestCompleted
- ActivityCreated

## Outcome

- Core application becomes an event producer
- Foundation for decoupled services established

## Notes

No consumers required yet — focus on safe introduction.

---

# Phase 2 — Notifications Service (MVP)

## Goal

Deliver first user-facing value from the event-driven architecture.

## Scope

- Create notifications service (separate deployment unit)
- Subscribe to selected domain events
- Implement basic notification handling (log / simple push)

## Example Behaviors

- Notify on new work request
- Notify on overdue tasks (if available)

## Outcome

- First independent consumer of events
- Proof of event-driven architecture viability
- First externalized capability outside core app

---

# Phase 3 — Time-Based Processing

## Goal

Enable scheduled logic independent of user actions.

## Scope

- Introduce scheduler (EventBridge Scheduler)
- Implement periodic checks (e.g. daily evaluation)

## Example Behaviors

- Detect inactivity (no activities in a day)
- Detect overdue tasks

## Outcome

- System gains time-awareness
- Enables next phase (Kimbalontek)

---

# Phase 4 — Kimbalontek Engine (MVP)

## Goal

Introduce emotional engagement layer.

## Scope

- Create Kimbalontek service
- Consume domain events and scheduled triggers
- Implement initial mood calculation model

## Mood States (initial)

- happy
- neutral
- sad

## Output

- Emit KimbalontekMoodChanged events

## Outcome

- First domain intelligence outside core app
- New engagement mechanism

---

# Phase 5 — Notification Expansion

## Goal

Enhance user engagement and delivery mechanisms.

## Scope

- Extend notification types
- Add delivery channels (push, email if needed)
- Subscribe to Kimbalontek events

## Example Behaviors

- Notify when Kimbalontek becomes sad
- Send daily summaries

## Outcome

- Rich notification experience
- Strong user engagement loop

---

# Phase 6 — Architecture Stabilization

## Goal

Consolidate and refine the architecture.

## Scope

- Review event taxonomy
- Improve observability
- Clean up boundaries between services
- Optimize costs and performance

## Outcome

- Stable modular architecture
- Clear service responsibilities
- Production-ready structure

---

# Dependency Flow

The phases must follow this order:

    Event Backbone
        → Notifications
            → Scheduler
                → Kimbalontek
                    → Advanced Notifications

---

# Guiding Principles for Execution

- deliver working software at each phase  
- avoid breaking existing functionality  
- introduce new components incrementally  
- validate each step before proceeding  

---

# Success Criteria

The roadmap is successful when:

- core application is no longer the only place for logic  
- new capabilities are implemented as independent services  
- communication happens via events, not direct calls  
- system remains simple and maintainable  

---

# Summary

This roadmap transforms Chores Cooperative step by step into an event-driven platform while continuously delivering value and maintaining production stability.