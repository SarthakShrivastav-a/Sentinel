# Sentinel

Sentinel is a multi-service uptime monitoring platform with a Next.js dashboard, Spring Boot API, Go probe worker, PostgreSQL persistence, Kafka events, public status pages, incidents, maintenance windows, reports, and a Pydantic AI copilot.

## Repositories

This repository is an umbrella repo. Each service lives in its own repository and is referenced here as a Git submodule:

- `frontend` -> https://github.com/SarthakShrivastav-a/Sentinel-Frontend
- `backend-springboot` -> https://github.com/SarthakShrivastav-a/Uptime-Monitoring
- `monitor-worker-go` -> https://github.com/SarthakShrivastav-a/UptimeServer
- `ai-service` -> https://github.com/SarthakShrivastav-a/Sentinel-AI

## Clone

```bash
git clone --recurse-submodules https://github.com/SarthakShrivastav-a/Sentinel.git
cd Sentinel
```

If the repo was cloned without submodules:

```bash
git submodule update --init --recursive
```

## Run

```bash
cp .env.example .env
docker compose up --build
```

Frontend: http://localhost:3000
Backend: http://localhost:8080
AI service: http://localhost:8090
MailHog: http://localhost:8025
