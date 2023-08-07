Here is the README converted to markdown format:

# Event Driven Architecture in Rust

This project shows an implementation of an event-driven architecture in Rust using some common crates.

## Overview

- **Domain** - Contains domain models, events, and handlers
- **Infrastructure** - Implements interfaces to external services
    - Database - Uses SQLx to persist models
    - MessageBus - Kafka implementation for events
- **Interfaces** - Exposes APIs and async workers
    - API - Actix web API with endpoints
    - Workers - Async tasks that process events
- **Configuration** - Loading config from file and environment
- **Telemetry** - Metrics with Prometheus and distributed tracing
- **Main** - Wires up components and starts app

Key principles followed:

- Separation of domain and infrastructure
- Domain events to propagate state changes
- Async message-driven work processing
- Declarative API endpoints using Actix web

## Running

**Requirements**

- Rust
- Docker

**Steps**

1. Start dependencies
   ```
   docker-compose up -d
   ```
2. Build and run
   ```
   cargo build
   cargo run
   ```

This will start the app on localhost:8080.

Kafka and Postgres run in containers defined in docker-compose.yml.

## Usage

- Web API exposes endpoints like:
    - POST /users
    - POST /orders
- Creating models publishes domain events
- Workers process events asynchronously
- Metrics exposed on /metrics endpoint
- Configuration loaded from config.yaml and .env file

## Extending

Some ideas:

- Add more API endpoints
- Introduce new bounded contexts/domains
- Add RPC capabilities using gRPC
- Use Kafka Streams for inter-service communication
- Try a different datastore like Cassandra

The core domain/infrastructure separation and asynchronous event-driven approach aims to support flexibility and maintainability.

Let me know if you have any other questions!