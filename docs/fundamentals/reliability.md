---
title: Reliability & Consistency
description: This document covers fundamental concepts of Reliability & Consistency in System Design
---

# Reliability & Consistency

## Consistency Models

### ACID Properties

Set of database transaction properties (Atomicity, Consistency, Isolation,
Durability) that guarantee valid transactions.

!!! info "Components"

    - **Atomicity**: Transactions are all-or-nothing
    - **Consistency**: Transactions bring the database from one valid state to another
    - **Isolation**: Concurrent transactions don't interfere with each other
    - **Durability**: Committed transactions persist even after system failures

### BASE Properties

Alternative to ACID for distributed systems: Basically Available, Soft state,
Eventually consistent.

!!! info "Components"

    - **Basically Available**: System guarantees availability
    - **Soft state**: State may change over time without input
    - **Eventually consistent**: System will become consistent over time

### CAP Theorem

States that distributed systems can provide at most two of three guarantees:
Consistency, Availability, and Partition tolerance.

!!! example "System Classifications"

    - **CP (Consistent, Partition-tolerant)**: MongoDB, HBase
    - **AP (Available, Partition-tolerant)**: Cassandra, DynamoDB
    - **CA (Consistent, Available)**: Traditional RDBMS (not partition-tolerant)

## Reliability Patterns

### Failover

Backup operational mode where functions are automatically transferred to standby
system components.

!!! example "Types"

    - **Active-passive**: Standby server only activates when primary fails
    - **Active-active**: Multiple servers handle traffic, survivors take over on failure

### Redundancy

Duplication of critical components to increase reliability.

!!! info "Types"

    - **Hardware redundancy**: Multiple physical components
    - **Software redundancy**: Multiple instances of software
    - **Data redundancy**: Multiple copies of data

### Circuit Breaker

Pattern that prevents cascading failures by stopping requests to failing
services.

!!! info "States"

    - **Closed**: Normal operation
    - **Open**: Stops all requests
    - **Half-Open**: Allows limited requests to test recovery

## Fault Tolerance

### Error Handling

Strategies for managing and recovering from errors.

!!! tip "Best Practices"

    - Graceful degradation
    - Automatic retries
    - Fallback mechanisms
    - Comprehensive logging

### Recovery Strategies

Methods for restoring system functionality after failures.

!!! info "Approaches"

    - **Rollback**: Revert to previous stable state
    - **Rollforward**: Apply changes to reach desired state
    - **Checkpointing**: Save system state at regular intervals

## High Availability

### Availability Metrics

Measurements of system reliability and uptime.

!!! example "Common Metrics"

    - **99.9% (Three nines)**: 8.76 hours downtime per year
    - **99.99% (Four nines)**: 52.56 minutes downtime per year
    - **99.999% (Five nines)**: 5.26 minutes downtime per year

### HA Patterns

Design patterns for achieving high availability.

!!! info "Common Patterns"

    - **Active-Active**: Multiple active instances
    - **Active-Passive**: One active, one or more standby
    - **Geographic redundancy**: Multiple data centers
    - **Load balancing**: Distribute traffic across instances

## Data Consistency

### Consistency Levels

Different guarantees about data consistency.

!!! info "Types"

    - **Strong consistency**: All reads see latest write
    - **Eventual consistency**: Reads eventually see latest write
    - **Causal consistency**: Preserves cause-effect relationships
    - **Read-your-writes**: User sees their own writes

### Consistency Patterns

Approaches to maintaining data consistency.

!!! tip "Common Patterns"

    - **Two-phase commit**: Distributed transaction protocol
    - **Quorum-based**: Majority of replicas must agree
    - **Version vectors**: Track updates across replicas
    - **Conflict resolution**: Handle concurrent updates
