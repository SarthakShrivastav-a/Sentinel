# Sentinel Upgrade Implementation Plan

Sentinel is being upgraded into a multi-service uptime, heartbeat, incident, status page, notification, reporting, and AI copilot platform.

## Target Architecture

- Frontend: Next.js dashboard and public status pages.
- Backend: Spring Boot API using PostgreSQL as the system of record.
- Monitor worker: Go probe engine coordinated by Kafka.
- AI service: FastAPI + Pydantic AI for incident summaries and postmortems.
- Runtime: Docker Compose with PostgreSQL, Kafka, MailHog, backend, frontend, Go worker, and AI service.

## Trackable Phases

1. Stabilize builds, config, and current API contracts.
2. Add Docker Compose and environment-driven runtime config.
3. Add Kafka monitor lifecycle and check-result events.
4. Add status pages, incidents, maintenance windows, notification channels, and reports.
5. Add Pydantic AI copilot service with deterministic fallback.
6. Expand frontend workflows around status, incidents, maintenance, reports, and AI.
7. Add observability, seed data, tests, CI, and final demo polish.

## Current Implementation Notes

- PostgreSQL replaces MongoDB for the Spring Boot database.
- Kafka is the primary service-to-service event path for monitor lifecycle and check results.
- REST monitor callbacks remain as a compatibility fallback while Kafka support is phased in.
- Pydantic AI uses OpenAI-compatible configuration by environment variables and falls back to deterministic summaries when no API key is configured.

## Run

```bash
docker compose up --build
```

Frontend: http://localhost:3000  
Backend: http://localhost:8080  
AI service: http://localhost:8090  
MailHog: http://localhost:8025
