---
title: Security Fundamentals
description: This document covers fundamental concepts of Security in System Design
---

# Security Fundamentals

## Authentication & Authorization

### Authentication

Process of verifying the identity of a user or system.

!!! info "Common Methods"

    - **Password-based**: Username/password combinations
    - **Multi-factor (MFA)**: Multiple verification methods
    - **OAuth/OpenID Connect**: Third-party authentication
    - **JWT**: JSON Web Tokens for stateless authentication

### Authorization

Process of determining what resources a user can access and what actions they can perform.

!!! example "Models"

    - **RBAC**: Role-Based Access Control
    - **ABAC**: Attribute-Based Access Control
    - **ACL**: Access Control Lists

## Encryption

### Symmetric Encryption

Uses the same key for both encryption and decryption.

!!! info "Common Algorithms"

    - AES (Advanced Encryption Standard)
    - DES (Data Encryption Standard)
    - 3DES (Triple DES)

### Asymmetric Encryption

Uses a pair of keys: public key for encryption and private key for decryption.

!!! example "Use Cases"

    - SSL/TLS for secure web communication
    - Digital signatures
    - Key exchange

## Security Protocols

### TLS/SSL

Cryptographic protocols that provide secure communication over a computer network.

!!! warning "Best Practices"

    - Use TLS 1.2 or higher
    - Implement perfect forward secrecy
    - Regular certificate rotation

### OAuth 2.0

Authorization framework that enables applications to obtain limited access to user accounts.

!!! info "Grant Types"

    - Authorization Code
    - Implicit
    - Client Credentials
    - Resource Owner Password Credentials

### SSH



## Security Headers

### HTTP Security Headers

Headers that help protect against common web vulnerabilities.

!!! example "Important Headers"

    - **Content-Security-Policy**: Controls resources browser can load
    - **X-Frame-Options**: Prevents clickjacking
    - **X-Content-Type-Options**: Prevents MIME type sniffing
    - **Strict-Transport-Security**: Enforces HTTPS

## Common Vulnerabilities

### OWASP Top 10

Most critical web application security risks.

!!! warning "Key Risks"

    - Injection attacks (SQL, NoSQL, OS)
    - Broken Authentication
    - Sensitive Data Exposure
    - XML External Entities (XXE)
    - Broken Access Control
    - Security Misconfiguration
    - Cross-Site Scripting (XSS)
    - Insecure Deserialization
    - Using Components with Known Vulnerabilities
    - Insufficient Logging & Monitoring

## Security Best Practices

### Data Protection

Strategies for protecting sensitive data.

!!! tip "Recommendations"

    - Encrypt data at rest and in transit
    - Implement proper key management
    - Regular security audits
    - Data minimization principles

### API Security

Measures to secure API endpoints.

!!! info "Essential Practices"

    - Rate limiting
    - Input validation
    - Proper error handling
    - API versioning
    - Regular security testing
