# Maxlona

> Feature management built for every team that ships software.

[Website](https://maxlona.com) | [Documentation](https://maxlona.com/wiki) | [SDK Examples](https://maxlona.com/wiki/sdk) | [API Reference](https://maxlona.com/wiki/http-rest)

---

## Welcome to Maxlona

Welcome to the official GitHub home of **Maxlona**.

Maxlona is a feature management platform for controlling how software features are released.

Deploy code separately from feature activation, target specific users, run gradual rollouts, manage experiments, and disable features without another deployment.

Maxlona brings engineering, product, QA, operations, and business teams into one feature management workflow.

---

## Core Capabilities

- Feature flags
- Boolean and multi-variant flags
- Release, experiment, and operational flags
- Percentage-based rollouts
- Deterministic user assignment
- User and attribute targeting
- Segments
- Environment-specific configuration
- A/B testing and conversion tracking
- Kill switches
- Approval workflows
- Audit history
- Flag dependencies
- Realtime updates
- Signed webhooks
- HTTP evaluation
- Local and remote evaluation
- Role-based access control
- Management API
- SDK integrations

---

## SDKs

Maxlona provides SDK and integration options for multiple application stacks.

Current documentation includes examples for:

- Node.js
- React
- Angular
- .NET / C#
- Python
- Java
- PHP
- Android / Kotlin
- iOS / Swift
- Go
- cURL / REST

### Node.js

Install the Maxlona Node.js SDK:

    npm install @maxlona/feature-flags

The package supports Node.js 18.17+, TypeScript declarations, ESM, and CommonJS.

### .NET

Install the Maxlona .NET SDK:

    dotnet add package Maxlona.FeatureFlags

The .NET SDK supports .NET 8+ with dependency injection, typed variants, resilient HTTP, and evaluation and management clients.

---

## Evaluation API

Applications can evaluate feature flags through the Maxlona Evaluation API.

Endpoint:

    POST /flags/{key}

Example:

    POST https://maxlona.com/flags/checkout-redesign

Headers:

    Content-Type: application/json
    x-api-key: YOUR_API_KEY

Request:

    {
      "userId": "user-42",
      "stage": "production"
    }

Example response:

    {
      "variant": true,
      "key": "on"
    }

The returned variant tells your application which feature behavior to use.

---

## Targeting

Pass application-specific attributes during evaluation.

Example:

    {
      "userId": "user-123",
      "stage": "production",
      "context": {
        "plan": "pro",
        "region": "us-west"
      }
    }

Targeting rules can use these attributes to determine which variant the user receives.

---

## Gradual Rollouts

Maxlona supports percentage-based feature releases.

For example:

    Development     100%
    Test            100%
    Stage            25%
    Production        0%

You can increase production exposure without deploying new application code.

Maxlona uses deterministic bucketing so the same user remains assigned consistently during percentage rollouts.

---

## Feature Flag Types

### Release Flags

Use release flags when introducing new functionality.

Deploy the code first, then control when the feature becomes available.

### Experiment Flags

Use experiment flags for A/B and multi-variant testing.

Track exposures and conversion events to compare variant performance.

### Ops Flags

Use operational flags as long-lived kill switches.

Disable integrations or expensive functionality during incidents without redeploying your application.

---

## Realtime Updates

Maxlona supports multiple ways to receive feature configuration changes.

### HTTP Evaluation

Evaluate the current flag state when your application needs it.

### Webhooks

Receive server-to-server notifications when feature configuration changes.

Webhook payloads can use HMAC-SHA256 signatures for verification.

### Realtime Streaming

Applications can subscribe to flag-change notifications through the Maxlona streaming endpoint.

    /hubs/flags

Applications can refresh their current configuration after receiving a change notification.

---

## How Evaluation Works

A feature evaluation follows a deterministic pipeline.

1. Validate the evaluation key.
2. Identify the organization, application, and environment.
3. Check organization and kill-switch state.
4. Load the requested feature flag.
5. Evaluate targeting rules by priority.
6. Apply percentage allocation.
7. Select the appropriate variant.
8. Record exposure data when applicable.

Maxlona uses layered caching to keep feature evaluation fast.

---

## Management API

Maxlona also provides an API for managing feature flags programmatically.

Common endpoints include:

    GET    /api/flags
    GET    /api/flags/{name}
    POST   /api/flags
    PUT    /api/flags/{name}
    DELETE /api/flags/{name}

Environment configuration:

    POST /api/flags/{name}/configs

Management requests authenticate using:

    x-management-key: YOUR_MANAGEMENT_KEY

This separates management operations from application feature evaluation.

---

## Example Release Workflow

    Create Feature Flag
            |
            v
    Deploy Application
            |
            v
    Enable in Development
            |
            v
    Validate in Test
            |
            v
    Release to 10% of Production
            |
            v
    Monitor
            |
            v
    Increase Rollout
            |
            v
    100% Production

If a release needs attention, disable the flag without redeploying the application.

---

## Built for Production

Maxlona includes infrastructure and controls for production feature management.

- Environment isolation
- Organization isolation
- Secure API authentication
- Role-based access control
- Layered caching
- Redis-backed distributed caching
- Realtime notifications
- Audit history
- Approval workflows
- Rate limiting
- Webhook delivery tracking
- HMAC-SHA256 webhook signing
- Cryptographically generated API keys
- Encrypted application secrets
- Automated rollout controls

---

## Quick Start

1. Create your Maxlona organization.

2. Create a feature flag.

3. Configure your environments.

4. Generate an evaluation API key.

5. Install an SDK or use the REST API.

6. Evaluate the flag from your application.

7. Control the release from Maxlona.

---

## Documentation

Main Website

    https://maxlona.com

Documentation

    https://maxlona.com/wiki

SDK Examples

    https://maxlona.com/wiki/sdk

REST API Reference

    https://maxlona.com/wiki/http-rest

Feature Flags

    https://maxlona.com/wiki/feature-flags

Realtime Updates

    https://maxlona.com/wiki/realtime-updates

---

## Feature Freedom for What's Next

Build your feature.

Deploy when ready.

Release when you decide.

Control it with Maxlona.
