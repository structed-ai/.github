# Structed AI - Engineering README

This README contains implementation-facing details that were removed from the public profile.

## Tech stack

### Frontend
- Angular 20
- TypeScript
- PrimeNG

### Backend
- NestJS 11
- Node.js
- PostgreSQL
- TypeORM
- JWT

### AI / ML
- Python 3.12
- FastAPI
- LangGraph
- OpenAI / OpenRouter

### Infrastructure
- Docker
- GitHub Actions
- AWS

## Architecture

```text
Client Browser (Angular + PrimeNG SPA)
  -> REST / SSE
NestJS Backend (Auth, Projects, Interviews, Briefs, Webhooks)
  -> PostgreSQL
  -> HTTP
Python FastAPI AI Service
  -> LangGraph state machine
  -> Stage-based prompts
  -> OpenAI / OpenRouter
  -> PostgreSQL
```

## Repositories

| Repository | Description | Stack |
|---|---|---|
| `structed-ai` | Main application monorepo | Angular, NestJS, FastAPI, LangGraph |
| `infrastructure` | Deployment configs and environments | Docker, GitHub Actions |

## Project structure

```text
structed-ai/
├── frontend/          # Angular 20 SPA
├── backend/           # NestJS 11 REST API
├── ai/                # Python FastAPI + LangGraph pipeline
├── docker/            # Service configs
├── .github/workflows/ # CI/CD pipelines
├── docker-compose.yml
└── Makefile
```

## Local setup

```bash
git clone https://github.com/structed-ai/structed-ai
cd structed-ai
cp .env.example .env
docker compose up --build
```

## Roadmap checklist

- [x] Core AI interview engine (LangGraph state machine)
- [x] Multi-stage requirement extraction
- [x] Structured brief generation
- [x] User auth + Google SSO
- [x] Client interview link (no login required)
- [ ] Billing and subscription (Stripe)
- [ ] Regeneration flow
- [ ] API documentation (OpenAPI / Swagger)
- [ ] Security hardening and GDPR compliance
- [ ] Production observability (Sentry, OpenTelemetry)
- [ ] Team workspace features
