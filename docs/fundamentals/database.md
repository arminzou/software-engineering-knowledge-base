---
title: Database & Storage
description: This document covers fundamental concepts of Database & Storage
---

# Database & Storage

## Database Types

### SQL Database

Relational database that uses structured query language for defining and
manipulating data.

!!! example "Popular Implementations"

    - PostgreSQL
    - MySQL
    - SQL Server
    - Oracle

!!! tip "Best For"

    Complex queries, transactions, and data with well-defined relationships

### NoSQL Database

Non-relational database designed for distributed data stores with diverse data
models.

!!! info "Common Types"

    - **Document stores**: MongoDB, Couchbase
    - **Key-value stores**: Redis, DynamoDB
    - **Column-family stores**: Cassandra, HBase
    - **Graph databases**: Neo4j, Amazon Neptune

!!! tip "Best For"

    Scalability, flexibility with unstructured data, high write throughput

### TSDB (Time Series Database)

Database optimized for time-stamped or time series data.

!!! example "Popular Implementations"

    - InfluxDB
    - TimescaleDB (PostgreSQL extension)
    - Prometheus

!!! tip "Best For"

    Metrics, monitoring data, IoT sensor data, financial market data

## Data Partition

### Partitioning (Vertical Partitioning)

Division of a database table into multiple tables by columns, with each table
having fewer columns.

!!! example "Use Case"

    - Splitting a wide table with customer profile data, purchase history, and preferences into separate tables by data category

### Sharding (Horizontal Partitioning)

Database architecture pattern where rows of a database table are held separately
in different database nodes.

!!! info "Common Sharding Strategies"

    - **Range-based**: Partition by ranges of a key (e.g., customer_id 1-1000, 1001-2000)
    - **Hash-based**: Use a hash function on the key
    - **Directory-based**: Maintain a lookup table mapping keys to shards

## Database Optimization

### Database Indexing

Data structure technique to improve the speed of data retrieval operations.

!!! warning "Tradeoffs"

    - Indexes speed up reads but slow down writes and require additional storage

!!! tip "Best Practices"

    - Index columns used in WHERE clauses and joins
    - Avoid over-indexing
    - Consider composite indexes for multi-column queries

### Denormalization

Strategy to improve read performance by adding redundant data or grouping data.

!!! example "Techniques"

    - Materialized views
    - Precomputed aggregates
    - Redundant fields

## Storage Solutions

### Blob Storage

System for storing large binary objects, such as images, videos, or documents.

!!! example "Services"

    - AWS S3
    - Azure Blob Storage
    - Google Cloud Storage

!!! tip "Best For"

    - Unstructured data like media files, backups, and static website content
