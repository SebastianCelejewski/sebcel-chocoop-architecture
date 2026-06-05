# Stakeholders and Concerns

Project: Celejewski Family Enterprise
Scope: Preliminary Phase / Business Architecture
Status: Draft
Last Updated: 2026-06-05
Owner: Sebastian Celejewski

# Overview

This document describes key stakeholders of the Celejewski family enterprise ecosystem and their major concerns, motivations, expectations, and tensions related to household coordination and supporting software systems such as ChoCoop.

The purpose of this document is to better understand stakeholder perspectives before defining architecture principles, capabilities, and solution architectures.

# Enterprise Context

The enterprise is defined as the Celejewski family as a cooperative household unit.

ChoCoop is not treated as the enterprise itself, but as one of the systems supporting selected enterprise capabilities such as household coordination, motivation, visibility of contributions, and family cooperation.

# Stakeholders

## Sebastian Celejewski

### Roles

* father
* architect
* software developer
* system operator
* product owner

### Concerns

* increasing children's participation in household work
* maintaining household order
* preserving real-world family interaction
* avoiding excessive digitization of family life
* supporting cooperation instead of punishment
* meaningful motivation mechanisms
* low-friction household coordination
* emotional appreciation of invisible work
* maintainability and flexibility of systems
* operational simplicity
* low operational cost

### Additional Personal Motivations

The enterprise ecosystem is also used by Sebastian as:

* a software engineering laboratory
* a cloud architecture practice environment
* a TOGAF learning platform
* an AWS learning platform
* a professional development vehicle
* a creative and recreational hobby activity

### Observations

ChoCoop successfully became a regularly used family system, but it did not fully achieve its original goal of significantly increasing children's participation in household work.

This creates tension between:

* practical household effectiveness
* enjoyment of the platform
* experimentation and software evolution

## Wife

### Roles

* mother
* primary household work contributor
* most active ChoCoop user

### Concerns

* fair distribution of household work
* visibility of invisible work
* motivating children
* accountability and fairness
* reducing frustration related to unequal participation

### Observations

Statistics and visibility mechanisms are frequently used as evidence in family discussions about fairness and participation.

Positive feedback is often given regarding new platform features, although direct feature requests are rare.

## Son

### Roles

* household participant
* active feature idea contributor

### Concerns

* insufficient visibility of available work
* lack of proactive notifications
* incomplete representation of real household work
* desire for richer coordination support
* desire for more system-driven organization

### Observations

The son frequently proposes feature extensions and broader system coordination mechanisms.

A recurring tension exists between:

* system-driven coordination
* real-world/offline coordination preferred by Sebastian

Another recurring issue is uncertainty regarding what work currently needs to be done.

## Daughter

### Roles

* household participant

### Concerns

* low interaction overhead
* simple and lightweight usage patterns

### Observations

The daughter uses the system regularly but with lower engagement regarding:

* feature discussions
* AI-generated summaries
* experimental platform capabilities

Activities are often entered with significant delay, suggesting asynchronous or low-priority interaction patterns.

# Cross-Stakeholder Tensions

Several architectural and organizational tensions have emerged:

* gamification vs real motivation
* digital coordination vs offline communication
* visibility vs feeling monitored
* experimentation vs simplicity
* detailed tracking vs low interaction overhead

These tensions are considered important architectural drivers for future evolution of the enterprise ecosystem.
