---
document_type: rfp
id: RFP-0002
title: Multitenant White-Label Platform Initial Architecture
status: draft
created_date: 2026-05-01
owners:
  - Architecture Team
reviewers:
  - Engineering Leads
  - Product Leadership
  - Security Team
release_refs:
  - none
related_adrs:
  - none
related_rfps:
  - RFP-0001
supersedes:
  - none
superseded_by:
  - none
tags:
  - architecture
  - multitenant
  - white-label
  - web
  - mobile
summary: Propose the initial architecture, technology stack, and infrastructure model for a long-lived multitenant white-label platform with web, admin, and mobile channels.
---

# RFP-0002: Multitenant White-Label Platform Initial Architecture

## Status

Draft

## Executive Summary

This RFP proposes the initial architecture for a new multitenant white-label platform that will
support a customer-facing web application, an administrative web console, and a mobile application.
The proposal is designed for long-term growth over many years, with strong modularity, high
testability, clear separation of responsibilities, and cloud-agnostic deployment.

The recommended approach is to adopt a modular microservice backend that is explicitly organized
by business domain and tenant-aware service boundaries, paired with Angular-based web applications
and a Flutter mobile application. Infrastructure should use open-source, portable building blocks
so the platform can scale operationally without locking the business into a single provider.

## Business Context

The system must support multiple tenants under a white-label strategy, which means the same core
platform must serve different brands, configurations, themes, and operational policies without
forking the product. The business needs a foundation that can evolve for years, allow incremental
feature growth, and maintain operational efficiency as the customer base expands.

Because the platform includes customer-facing and administrative capabilities across web and mobile
channels, the initial architecture must emphasize consistency, governance, operational visibility,
and strong control over tenant isolation.

## Scope

### In Scope

- Define the initial architecture style for the product platform.
- Select the recommended language and framework for each major tier.
- Define the infrastructure tools used to deploy, operate, observe, and scale the platform.
- Define the initial multitenancy and white-label strategy at the platform level.
- Define the criteria for human approval before detailed solution ADRs are created.

### Out Of Scope

- Detailed domain modeling for each business capability.
- Final UI design or branding definitions for specific tenants.
- Detailed cost modeling by cloud vendor.
- Low-level schema definitions or service-by-service API contracts.

## Problem Statement

The organization needs an initial architecture that supports long-term product evolution while
keeping complexity under control from day one. If the platform starts with fragmented technologies,
weak tenant boundaries, or provider-specific operational assumptions, it will become expensive to
change, difficult to validate, and harder to scale safely over time.

The architecture must therefore balance three needs:

- simplicity in the initial delivery model
- enough structural rigor to support multi-year growth
- clear technical standards so teams can build consistently across web, admin, and mobile channels

## Proposed Direction

Adopt a modular microservice backend with explicit domain service boundaries, tenant-aware data
access patterns, and well-defined APIs for web, admin, and mobile clients. Use a shared platform
model for authentication, authorization, tenant configuration, white-label theming, observability,
and deployment pipelines.

For the client layers, standardize on TypeScript with Angular for the web application and admin
console, and Flutter for the mobile application. For the backend, standardize on Java with Spring
Boot.

This combination keeps the number of primary platform languages small, supports strong static
typing, and provides a long-lived ecosystem suitable for enterprise-grade systems.

## Market Comparison Summary

The proposed stack is not the only viable approach in the market, but it is a defensible choice
for a long-lived multitenant white-label platform because it emphasizes maintainability,
operational control, and team scalability over short-term trend alignment.

### Frontend Comparison

#### Angular + TypeScript vs React + Next.js

- Angular is stronger when the organization wants a highly structured framework with consistent
  patterns, dependency injection, opinionated architecture, and strong alignment across multiple
  teams.
- React with Next.js often provides more flexibility and a larger ecosystem for content-heavy or
  public-facing applications, but that same flexibility can lead to wider architectural variation
  between teams.
- For this platform, Angular is preferable because the web and admin channels are likely to be
  business workflow applications with permissions, forms, configuration, and white-label rules
  rather than marketing-heavy websites.

#### Angular + TypeScript vs Vue

- Vue is often faster to onboard for smaller teams and can be very productive for lightweight web
  applications.
- Angular provides stronger built-in structure for larger organizations that expect the platform to
  evolve for many years with multiple contributors and strict architectural consistency.
- For this case, Angular is the better fit because it reduces framework-level ambiguity over time.

### Backend Comparison

#### Java + Spring Boot vs Node.js + NestJS

- Node.js with NestJS is productive for API development and has a good developer experience,
  especially for teams that want one primary language across frontend and backend.
- Java with Spring Boot is stronger for organizations that prioritize mature enterprise tooling,
  long-term maintainability, predictable JVM performance characteristics, and deep operational
  support across large systems.
- For this platform, Java with Spring Boot is preferable because the system is expected to grow for
  many years, support multitenancy, and maintain strong service boundaries under enterprise loads.

#### Java + Spring Boot vs .NET

- .NET is also a strong enterprise choice and competes closely with Java for large business systems.
- Java with Spring Boot is often preferred when the organization wants maximum cross-platform
  ecosystem flexibility, a very broad hiring market, and a large body of reference architectures for
  microservices, identity, and cloud-native systems.
- In this case, Java and Spring Boot remain a strong default because they align well with open-source,
  cloud-agnostic platform tooling and established microservice patterns.

#### Java + Spring Boot vs Go

- Go is strong for small, operationally efficient services and high-concurrency infrastructure-heavy
  workloads.
- Java with Spring Boot is better when business-domain complexity, framework maturity, validation,
  and developer productivity around enterprise concerns matter more than minimal runtime footprint.
- For this system, Java is preferable because domain modeling, security, and long-lived business
  workflows are central concerns.

### Mobile Comparison

#### Flutter vs Native Mobile Teams

- Native iOS and Android development can provide maximum platform-specific control but requires two
  delivery tracks and duplicated application logic.
- Flutter reduces duplication, accelerates multi-brand rollout, and keeps white-label customization
  more consistent across devices.
- For this platform, Flutter is the better tradeoff because product consistency and long-term delivery
  efficiency matter more than deep native specialization in the initial phase.

### Data And Multitenancy Comparison

#### PostgreSQL + RLS vs Separate Database Per Tenant

- A dedicated database per tenant gives strong isolation but introduces significant operational and
  cost overhead as the tenant count grows.
- PostgreSQL with Row-Level Security provides strong tenant protection at the database layer while
  preserving a more scalable operational model for a shared platform.
- For this platform, PostgreSQL RLS is the better starting point because it balances safety,
  simplicity, and long-term tenant scalability.

#### PostgreSQL vs NoSQL-First Approaches

- NoSQL platforms can be attractive for flexible schemas and horizontal distribution.
- PostgreSQL is preferable for this use case because white-label multitenant business systems usually
  depend on relational consistency, transactions, reporting, and strong data governance.

### Platform Tooling Comparison

#### Kong vs Cloud-Native Proprietary API Gateways

- Proprietary cloud gateways can reduce setup effort inside a single provider ecosystem.
- Kong is preferable because it keeps the gateway layer portable, open-source-friendly, and aligned
  with the repository's cloud-agnostic direction.

#### Podman vs Docker

- Docker remains the most widely recognized container workflow in the market.
- Podman is preferable here because it supports rootless, daemonless execution while still following
  OCI standards and fitting an open-source-first operational model.

#### Kubernetes vs Simpler Single-Host Orchestration

- Simpler runtime models may reduce short-term operational burden.
- Kubernetes is preferable because the platform is explicitly expected to grow over many years,
  support many tenants, and evolve across multiple services with controlled deployment patterns.

## Recommended Technology Stack

### Web Application

- **Language**: TypeScript
- **Framework**: Angular
- **Why**:
  - Angular provides a structured framework with clear conventions for large teams and long-lived systems.
  - TypeScript improves maintainability through strong typing and safer refactoring.
  - Angular's module and dependency injection patterns fit well with enterprise-grade admin and business applications.

### Admin Console

- **Language**: TypeScript
- **Framework**: Angular
- **Why**:
  - Using the same language and frontend platform as the web application reduces team fragmentation.
  - Shared design systems, validation logic, guards, and role-based interface components can be reused.
  - Angular is well suited to form-heavy, permission-sensitive administrative interfaces.

### Mobile Application

- **Language**: Dart
- **Framework**: Flutter
- **Why**:
  - Flutter provides a single cross-platform codebase for iOS and Android while keeping strong UI control.
  - White-label customization is easier to manage through shared widgets, theming, and configuration.
  - It reduces duplication across mobile platforms and helps maintain consistent behavior over time.

### Backend Platform

- **Language**: Java
- **Framework**: Spring Boot
- **Why**:
  - Java offers a large talent pool, broad ecosystem support, and strong long-term maintainability.
  - Spring Boot is proven for secure APIs, modular business services, transaction management, and enterprise workloads.
  - Java with Spring Boot is well suited for modular microservices with strong contracts, mature tooling, and operational consistency.

### Data Layer

- **Primary Database**: PostgreSQL
- **Cache**: Redis
- **Why**:
  - PostgreSQL is robust, open source, and suitable for tenant-aware transactional workloads.
  - Redis supports caching, short-lived session data, and performance optimization without becoming the source of truth.

## Multitenancy And White-Label Strategy

### Tenant Model

- Use a shared application platform with strict tenant-aware data access.
- Start with a shared database and shared schema model using a mandatory tenant identifier in all tenant-owned tables.
- Enforce PostgreSQL Row-Level Security policies so tenant isolation is protected at the database layer as well as the application layer.
- Enforce tenant context at the application, persistence, and SQL session layers so accidental cross-tenant access is blocked.

### Why This Approach

- It keeps the initial platform simpler than a per-tenant deployment model.
- It supports many tenants without multiplying operational overhead.
- PostgreSQL RLS adds a strong safety boundary for tenant data access without requiring separate databases for every tenant.
- It leaves room to isolate high-compliance or high-scale tenants later if business needs justify it.

### White-Label Model

- Store branding, feature flags, tenant configuration, and channel-specific customizations as tenant-managed configuration.
- Centralize theming and brand assets rather than hardcoding branding into client applications.
- Keep business logic shared wherever possible so white-label behavior stays configuration-driven.

## Infrastructure Tooling Recommendation

### Containerization

- **Tool**: Podman
- **Why**:
  - Supports OCI-compatible container workflows without requiring a central daemon.
  - Rootless execution improves the security posture for local development and operational environments.
  - Remains portable across cloud and on-premise platforms while fitting an open-source-first strategy.

### Orchestration

- **Tool**: Kubernetes
- **Why**:
  - Portable, cloud-agnostic runtime orchestration.
  - Supports long-term operational scale, workload isolation, and rolling deployment strategies.

### Infrastructure As Code

- **Tool**: Terraform
- **Why**:
  - Open-source-first workflow and strong multi-cloud support.
  - Declarative infrastructure definitions improve reproducibility and reviewability.

### Application Packaging And Deployment

- **Tools**: Helm and Argo CD
- **Why**:
  - Helm provides repeatable Kubernetes application packaging.
  - Argo CD supports GitOps-style deployment management, traceability, and safer promotion across environments.

### API Gateway And Edge Routing

- **Tool**: Kong
- **Why**:
  - Kong is mature, open-source-friendly, and well suited for routing, authentication, rate limiting, and policy enforcement.
  - It provides a clear control point for tenant-aware API behavior, traffic governance, and future API productization.
  - It integrates well with Kubernetes and identity providers such as Keycloak.

### Identity And Access Management

- **Tool**: Keycloak
- **Why**:
  - Open-source identity platform with support for federation, roles, realms, and modern token protocols.
  - Suitable for tenant-aware identity models and admin access control.

### Observability

- **Tools**: OpenTelemetry, Prometheus, Grafana, and Loki
- **Why**:
  - OpenTelemetry standardizes traces and metrics.
  - Prometheus and Grafana provide portable monitoring and dashboards.
  - Loki provides log aggregation without forcing a proprietary stack.

### Messaging

- **Tool**: Kafka only if asynchronous domain events become necessary
- **Why**:
  - Messaging should not be introduced on day one unless a clear need exists.
  - This keeps the initial architecture simpler while preserving a future integration path.

## Requirements

### Functional Requirements

- The platform must support multiple tenants on a shared core application.
- The platform must support white-label branding and configurable tenant behavior.
- The platform must provide a customer-facing web application.
- The platform must provide an administrative web console.
- The platform must provide a mobile application for end users.
- The platform must expose backend APIs that serve all client channels consistently.
- The platform must support role-based administration and tenant-aware access control.

### Non-Functional Requirements

- Simplicity expectations: keep the number of microservices disciplined and aligned to real business domains, avoiding unnecessary service proliferation.
- Modularity expectations: business domains must be separated clearly into service boundaries with explicit contracts.
- Testability expectations: tenant isolation, authorization, and configuration behavior must be testable independently.
- Decoupling expectations: clients, backend modules, and infrastructure concerns must remain separated by explicit interfaces.
- Code or document quality expectations: strong typing, coding standards, review gates, and architectural traceability are required.
- Performance expectations: the system must support responsive user experience across web, admin, and mobile channels.
- Scalability expectations: the architecture must support tenant growth, independent service scaling, and long-term operational expansion.
- Cloud-agnostic expectations: deployment and observability choices must stay portable across providers.

## Options Considered

### Option 1: Modular Microservices With Explicit Domain Boundaries

- Decision status: Selected
- Description: Build the backend as a controlled set of Java and Spring Boot microservices organized by business capability and supported by a shared platform layer.
- Advantages: Clear service ownership, strong boundary enforcement, independent scaling, and a better fit for long-term platform growth.
- Disadvantages: Higher operational complexity than a single deployable backend and stronger need for platform discipline.

### Option 2: Modular Monolith With Explicit Boundaries

- Decision status: Rejected for the initial target architecture
- Description: Build one deployable backend with strongly separated business modules and clear seams for later extraction.
- Advantages: Lower initial complexity, easier testing, simpler operations, and good long-term evolution path.
- Disadvantages: Service boundaries remain softer, and later extraction can become expensive if teams scale quickly.

### Option 3: Per-Tenant Isolated Deployments From Day One

- Decision status: Rejected for the initial target architecture
- Description: Deploy a separate stack per tenant.
- Advantages: Strong isolation.
- Disadvantages: High infrastructure cost and operational duplication for an initial platform.

## Evaluation Criteria

- Can the architecture support multi-year evolution without immediate re-platforming?
- Does the stack reduce unnecessary language and operational fragmentation?
- Can tenant isolation and white-label behavior be validated clearly?
- Is the infrastructure portable and based on open-source-friendly tooling?
- Can the platform scale without adopting premature complexity?

## Risks And Assumptions

### Risks

- Tenant isolation can fail if repository and service boundaries are not enforced rigorously.
- White-label customization can become excessive if branding evolves into tenant-specific forks.
- Kubernetes, GitOps, and microservice operations may be too heavy for a very small initial team if platform automation is weak.

### Assumptions

- The business intends to support many tenants over several years.
- A shared core platform is preferred over separate custom builds per tenant.
- The organization accepts a strong preference for open-source and cloud-agnostic tooling.

## Recommendation

Approve a modular microservice platform using Java with Spring Boot for backend services, TypeScript
with Angular for both web and admin applications, and Flutter for the mobile application. Approve
PostgreSQL with Row-Level Security and Redis for the initial data layer, and Podman, Kubernetes,
Terraform, Helm, Argo CD, Kong, Keycloak, OpenTelemetry, Prometheus, Grafana, and Loki for the
core infrastructure toolchain.

This RFP selects Option 1, Modular Microservices With Explicit Domain Boundaries, as the initial
target architecture.

This proposal best balances long-term maintainability, multitenant scalability, white-label
flexibility, operational clarity, and long-term service-level scalability for the target platform.

It is also competitive against common market alternatives because it favors stacks that are widely
proven in enterprise systems, supported by large talent pools, and aligned with cloud-agnostic,
open-source operational practices.

## Related Artifacts

- Related ADRs: None yet.
- Related RFPs: [RFP-0001](./rfp-0001-initial-architecture.md)
- Related diagrams: None yet.
- Related release manifests: None.

## Validation And Review Evidence

- Review file: [RFP-0002 Review](../../reviews/rfp/rfp-0002-multitenant-white-label-platform-review.md)
- Review status: Pending human approval
- Validation checks performed: Template-based drafting and repository-local editor validation.
- Open validation items: Human review of technology choices, cost implications, and security constraints.

## Follow-Up Actions

- Create ADRs for microservice boundaries, tenant isolation strategy, and client application structure.
- Create an infrastructure ADR covering Kubernetes, Terraform, deployment flow, and observability standards.
- Add diagrams for context, container boundaries, and tenant-aware request flow.