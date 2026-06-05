# Current State Architecture

Project: Chores Cooperative (ChoCoop)  
Version: 0.5.0  
Status: Production  
Last Updated: 2026-05-02  
Owner: Sebastian Celejewski

# Executive Summary

ChoCoop is a production-ready household collaboration application designed to motivate users to perform shared tasks through gamification.

Version 0.5.0 is deployed to production and has already received positive user feedback.

The platform currently operates as a single integrated serverless application combining frontend, backend, authentication, and data storage in one main deployment stack.

# Business Capabilities Available Today

## Task Recording

Users can register completed chores as Activities.

## Future Task Planning

Users can create Work Requests representing chores that should be completed later.

## Recognition & Motivation

Users receive XP points and reactions for completed work.

## Visibility & Fairness

Shared task history provides transparency of contributions.

# Functional Scope

## Activities

Completed work items containing:

- type
- experience points
- date
- optional comment
- reactions

## Work Requests

Pending work items containing:

- type
- experience points
- priority
- optional instructions

Can be promoted into Activities after completion.

## Users

Authenticated participants with nicknames and XP progression.

# Technology Landscape

## Frontend

- React
- TypeScript
- Progressive Web App model
- Virtualized lists using react-virtualized

## Backend

- AWS Amplify
- GraphQL API
- Serverless architecture

## Authentication

- AWS Cognito
- Amplify Authenticator

## Data Storage

- DynamoDB (via Amplify models)

## Quality Engineering

- Playwright end-to-end tests

# Deployment Model

Current solution is deployed primarily as one integrated stack.

Characteristics:

- simple operational model
- fast iteration speed
- low operational overhead
- tightly grouped infrastructure lifecycle

# Strengths

## Working Production Product

The system is already usable and validated by real users.

## Fast Delivery Model

Single-stack architecture enables quick feature delivery.

## Low Operations Burden

Managed cloud services minimize maintenance effort.

## Good Product Direction

Gamification and household collaboration have clear user value.

# Constraints / Pain Points

## Limited Separation of Concerns

Notifications, scheduler logic, and future engagement services are not separated yet.

## Single Deployment Boundary

Changes to unrelated areas may still belong to the same infrastructure lifecycle.

## No Event Backbone

There is currently no formal event-driven integration layer.

## No Native Notification Capability

No push, scheduled, or engagement notifications yet.

## No Emotional UX Layer

Kimbalontek mood engine does not exist yet.

# Architecture Risks

## Growth Inside Main Stack

Future capabilities may accumulate inside the current stack if boundaries are not introduced.

## Tight Runtime Coupling Risk

New modules added directly into the current backend may reduce maintainability.

# Strategic Opportunity

Chocoop is at a strong transition point:

- validated product exists
- users already engage with the system
- architecture can evolve before scale creates friction

This creates an ideal opportunity for structured architecture transformation.

# Current Architecture Summary

Current state can be summarized as:

A successful lightweight serverless product with clear business value, ready to evolve into a more modular event-driven platform.