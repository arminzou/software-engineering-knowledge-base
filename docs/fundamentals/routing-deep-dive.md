---
title: How Internet Routing Works
description: A detailed explanation of how data travels across the internet through routing
---

# How Internet Routing Works

## Overview

Understanding how your data travels from your device to any website across the globe - through the complex web of interconnected networks that make up the internet.

When you click a link or type a URL, your data doesn't travel in a straight line. Instead, it hops through multiple networks, with routers at each step deciding the best path forward, like a sophisticated postal system that automatically finds the fastest route to deliver your package.

## The Big Picture: Network of Networks

The internet is essentially a "network of networks" - thousands of independent networks all connected together. When you visit a website, your data doesn't travel in a straight line but hops through multiple networks to reach its destination.

!!! example "Internet Routing Journey"

    **When you visit google.com from your home:**
    
    1. **Your device** → **Home router** (via WiFi)
    2. **Home router** → **ISP network** (Comcast, Verizon, etc.)
    3. **Your ISP** → **Internet backbone** (major fiber networks)
    4. **Internet backbone** → **Google's ISP** (Google's network provider)
    5. **Google's network** → **Google's servers**
    
    Each step involves routers making decisions about the best next hop.

## The Postal System Analogy

Internet routing works remarkably like the postal system:

- **Your letter (data packet)** has a destination address
- **Post offices (routers)** don't need to know the complete route to every address
- **Each post office** only needs to know which direction gets the letter closer to its destination
- **Multiple routes exist** - if one path is blocked, alternatives are automatically used
- **Regional sorting centers (backbone networks)** handle long-distance transport

## Autonomous Systems: Internet's Neighborhoods

The internet is organized into **Autonomous Systems (AS)** - think of them as internet neighborhoods:

!!! info "How AS Networks Work"

    - **Your ISP** (like Comcast) is one Autonomous System
    - **Google** operates its own Autonomous System  
    - **University networks** are often their own AS
    - **Each AS** decides how to route traffic within its network
    - **BGP protocol** lets these AS networks share routing information with each other

## Routing in Action

Here's what actually happens when you click on a link:

1. **DNS lookup**: Your computer finds the IP address for the website
2. **Local routing**: Your router sends the packet to your ISP
3. **ISP routing**: Your ISP's routers decide the best path toward the destination
4. **Backbone routing**: Major internet backbones carry traffic across continents
5. **Destination routing**: The destination network routes the packet to the specific server
6. **Response routing**: The web server's response follows a similar (but possibly different) path back

!!! tip "Why Routing is Resilient"

    - **Multiple paths exist** between any two points on the internet
    - **Automatic failover** - if one path fails, routers find alternatives
    - **Load balancing** - traffic spreads across available paths
    - **Self-healing** - network problems are automatically routed around

## Routing Tables and Protocols

**Routing tables** contain information about network destinations and how to reach them, while **routing protocols** are the methods by which routers share information to build these tables.

!!! example "Simplified Routing Table"

    | Destination Network | Subnet Mask     | Next Hop      | Interface | Metric |
    |---------------------|-----------------|---------------|-----------|--------|
    | 192.168.1.0         | 255.255.255.0   | 0.0.0.0       | eth0      | 0      |
    | 10.0.0.0            | 255.0.0.0       | 192.168.1.254 | eth0      | 10     |
    | 0.0.0.0             | 0.0.0.0         | 192.168.1.1   | eth0      | 1      |

!!! info "Routing Process"

    When a router receives a packet:

    1. Extract the destination IP address
    2. Look for the longest matching prefix in the routing table
    3. Forward the packet to the next hop or directly to the destination
    4. If no match is found, send to the default gateway (if configured)

### Default Gateways

A **default gateway** is the node (typically a router) that serves as an access point to other networks when no specific route matches the destination.

!!! note

    - Default route is represented as 0.0.0.0/0 in routing tables
    - It's used as a "last resort" when no more specific route exists
    - In home/office networks, the default gateway connects the local network to the internet
    - Without a default gateway, devices can only communicate within their local network

!!! example

    For a device with IP 192.168.1.100 and subnet mask 255.255.255.0:
    
    - Can directly reach addresses 192.168.1.1 through 192.168.1.254
    - Must use default gateway (typically 192.168.1.1) to reach any other address

### Routing Protocols: How Routers Learn Paths

Routing protocols enable routers to dynamically discover and share information about network topologies.

!!! note "Interior vs. Exterior Protocols"

    === "Interior Gateway Protocols (IGP)"
    
        Used within an autonomous system:
        
        - **OSPF (Open Shortest Path First)**: Link-state protocol that calculates shortest path first using Dijkstra's algorithm
        - **IS-IS (Intermediate System to Intermediate System)**: Similar to OSPF, used in large service provider networks
        - **RIP (Routing Information Protocol)**: Simple distance-vector protocol with hop count as metric (limited to 15 hops)
        - **EIGRP (Enhanced Interior Gateway Routing Protocol)**: Cisco's advanced distance-vector protocol
    
    === "Exterior Gateway Protocols (EGP)"
    
        Used between autonomous systems:
        
        - **BGP (Border Gateway Protocol)**: The routing protocol of the internet, makes decisions based on paths, policies, and rule-sets rather than just metrics

!!! info "Routing Protocol Selection Factors"

    - Network size and complexity
    - Convergence speed requirements
    - Administrative boundaries
    - Hardware capabilities
    - Scalability needs