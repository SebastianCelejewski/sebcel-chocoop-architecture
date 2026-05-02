# Target State Architecture

Project: Chores Cooperative (ChoCoop)  
Status: Planned  
Planning Horizon: 2026 Q2–Q3  
Last Updated: 2026-05-02
Owner: Sebastian Celejewski

# Executive Summary

The target architecture evolves ChoCoop from a single-stack serverless application into a modular, event-driven platform.

The goal is to improve scalability, separation of concerns, and extensibility, while enabling new engagement features such as notifications and the Kimbalontek mood engine.

The transformation is incremental and preserves the existing production system while introducing new capabilities alongside it.

# Target Capabilities
## Event-Driven Integration

The system supports asynchronous communication between components using domain events.

## Notifications

Users receive timely notifications about:
- new work requests
- overdue tasks
- lack of activity
- system-generated engagement messages

## Emotional Engagement (Kimbalontek)

A virtual household spirit reflects the state of chores and motivates users through emotional feedback.

## Time-Based Processing

The system can trigger logic based on time (e.g. daily checks, reminders).

# Target Architecture Overview

The system is composed of independent components connected through an event-driven backbone.

```
sebcel-chocoop-app
    publishes domain events

sebcel-chocoop-events
    event bus / integration layer

sebcel-chocoop-notifications
    consumes events → sends notifications

sebcel-chocoop-kimbalontek
    consumes events + scheduler → calculates mood
    publishes KimbalontekMoodChanged events
```

# Architecture Building Blocks (Logical)
## Household Management System

Core application managing users, activities, and work requests.

## Event Messaging Backbone

Shared integration capability enabling asynchronous communication.

## Notification Service

Responsible for delivering messages to users.

## Mood Engine (Kimbalontek)

Calculates emotional state based on system data and time.

## Time Engine

Provides scheduled triggers for periodic evaluation.

# Solution Building Blocks (AWS)
## Core Application
- AWS Amplify (frontend + backend)
- GraphQL API
- DynamoDB
- Cognito

## Event Backbone
- Amazon EventBridge (custom event bus)

## Notifications
- AWS Lambda (event consumers)
- SNS / push mechanism (future)
- optional email integration

## Kimbalontek Engine
- AWS Lambda
- DynamoDB (mood state storage)
- EventBridge Scheduler (time-based triggers)

## Observability
- CloudWatch logs and metrics

# Integration Model
## Communication Style
- asynchronous
- event-driven
- loosely coupled

## Event Examples
```
WorkRequestCreated
WorkRequestCompleted
WorkRequestOverdue
ActivityCreated
KimbalontekMoodChanged
```

## Principles
- producers do not know consumers
- consumers are independently deployable
- events are stable contracts

# Deployment Model

Each major capability is deployed independently:

```
sebcel-chocoop-app
sebcel-chocoop-events
sebcel-chocoop-notifications
sebcel-chocoop-kimbalontek
```

Characteristics:
- independent lifecycle
- isolated changes
- reduced risk of cross-impact
- easier experimentation

# Data Ownership

Each component owns its data:
- app → activities, users, work requests
- Kimbalontek → mood state
- notifications → delivery metadata (optional)

No shared database across services.

# Evolution Strategy

The transformation is incremental:

- introduce event bus
- publish first domain events
- implement notifications service
- implement Kimbalontek engine
- extend event catalog and capabilities

The existing system remains operational throughout.

# Success Criteria

The target architecture is achieved when:

- notifications are delivered via event-driven flow
- Kimbalontek mood reacts to system state and time
- new capabilities can be added without modifying the core app
- components are independently deployable

# Constraints
- system scale remains small (household-level)
- operational simplicity is preferred over complexity
- cost should remain low (serverless-first approach)

# Summary

The target architecture transforms Chores Cooperative into a modular, event-driven system that supports both functional features (notifications) and emotional engagement (Kimbalontek), while serving as a practical learning platform for architecture design.