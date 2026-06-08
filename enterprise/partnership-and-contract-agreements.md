# Partnership and Contract Relationships

Project: Celejewski Family Enterprise
Scope: Preliminary Phase / External Dependencies and Relationships
Status: Draft
Last Updated: 2026-06-08
Owner: Sebastian Celejewski

# Overview

This document describes external relationships, service dependencies, operational partnerships, and supporting providers influencing the Celejewski family enterprise ecosystem.

The enterprise operates as a small household-oriented socio-technical ecosystem and therefore does not maintain formal enterprise-scale contractual structures. Nevertheless, several external relationships significantly influence:

* operational capabilities
* system architecture
* household coordination
* infrastructure management
* cost structure
* operational risk

Some relationships are technical, while others directly influence household operations and responsibility distribution.

# Cloud Infrastructure Providers

## Amazon Web Services (AWS)

AWS is the primary cloud infrastructure and platform provider for the enterprise ecosystem.

Core enterprise systems depend heavily on AWS managed services including:

* AWS Lambda
* Amplify
* Cognito
* EventBridge
* DynamoDB
* AWS Backup
* Route53

AWS services currently support:

* authentication
* application hosting
* event-driven integration
* data storage
* operational recoverability
* environment management

AWS therefore represents a critical external operational dependency.

The cloud-native operational model and serverless architecture principles of the ecosystem are strongly influenced by AWS capabilities and service design.

# DNS and Domain Providers

## home.pl

home.pl currently functions as a domain registration and DNS-related provider for enterprise internet presence and domain management.

The provider influences:

* domain ownership
* DNS configuration
* external routing
* production cutover operations

Recent production migration activities demonstrated the operational importance of DNS provider coordination and external routing management.

## AWS Route53

Route53 is used as part of the cloud-native DNS and infrastructure ecosystem.

The relationship between Route53 and external DNS providers forms part of the operational deployment and migration architecture.

# Open-Source and Development Ecosystem

The enterprise ecosystem depends heavily on external open-source software ecosystems and community-maintained tooling.

Examples include:

* Node.js
* TypeScript
* npm ecosystem
* AWS SDKs
* open-source libraries and frameworks

These ecosystems significantly influence:

* development practices
* architecture style
* operational tooling
* implementation approaches
* long-term maintainability

The enterprise intentionally leverages mature external ecosystems rather than building isolated proprietary solutions.

# External Household Support Services

## Cleaning Service

The enterprise partially relies on an external cleaning service provider responsible for periodic household cleaning activities.

The cleaning service significantly influences:

* household workload distribution
* recurring household operations
* responsibility allocation
* household coordination dynamics

This relationship effectively externalizes part of the household work execution capability.

The enterprise therefore operates using a hybrid operational model in which:

* some household responsibilities are performed internally by family members
* selected responsibilities are partially outsourced to external providers

This operational relationship influences both real-world household coordination and supporting software-system assumptions.

# Behavioral and Internal Agreements

## Experience-to-Pocket-Money Exchange Model

The enterprise uses an internal reward agreement in which experience points earned through household participation may be exchanged for additional pocket money.

The current exchange model is:

* 5 experience points = 1 PLN additional pocket money

Although informal, this agreement functions as an internal behavioral and motivational contract influencing:

* participation incentives
* gamification mechanisms
* household motivation dynamics
* reward expectations

This agreement forms an important part of the enterprise's encouragement-oriented participation model.

# Learning and Certification Ecosystem

The enterprise ecosystem is also influenced by external professional learning and certification ecosystems.

Examples include:

* AWS certification programs
* TOGAF learning materials
* cloud architecture educational resources
* software engineering knowledge ecosystems

These relationships significantly influence:

* architecture evolution
* operational maturity
* governance practices
* experimentation strategy
* technology selection

The enterprise intentionally combines practical household systems with professional development and architecture learning objectives.

# Dependency Characteristics

The enterprise intentionally prefers:

* managed services
* mature ecosystems
* low operational overhead
* incremental operational complexity
* reusable external platforms

At the same time, the enterprise recognizes risks associated with external dependencies including:

* cloud-provider dependency
* DNS-provider dependency
* operational pricing changes
* ecosystem evolution
* service availability risks

Operational governance practices such as:

* backups
* restore validation
* environment separation
* staged migrations

partially mitigate these dependency risks.

# Overall Assessment

The enterprise currently operates with:

* relatively low contractual complexity
* moderate external platform dependency
* strong reliance on cloud-native managed ecosystems
* limited formal legal relationships
* several important operational dependencies

The most critical external dependency is currently the AWS cloud ecosystem, which forms the foundation of the enterprise's technical architecture and operational model.
