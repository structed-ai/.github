<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6366f1,100:8b5cf6&height=160&section=header&text=Structed%20AI&fontSize=52&fontColor=ffffff&fontAlignY=38&desc=Turn%20every%20client%20conversation%20into%20a%20perfect%20brief&descSize=16&descAlignY=60&descColor=e0e7ff" width="100%"/>

</div>

<div align="center">

[![Website](https://img.shields.io/badge/structed.ai-6366f1?style=for-the-badge&logo=safari&logoColor=white)](https://structed.ai)
[![Status](https://img.shields.io/badge/Beta-February%202026-22c55e?style=for-the-badge&logo=rocket&logoColor=white)](https://structed.ai)
[![Made in UK](https://img.shields.io/badge/Incorporated-UK%20%F0%9F%87%AC%F0%9F%87%A7-0ea5e9?style=for-the-badge)](https://structed.ai)

</div>

---

## What we build

> **Structed AI eliminates the hours spent extracting requirements from client calls.**
> Our AI agent runs structured interviews, captures everything that matters, and delivers a ready brief — automatically.

Agencies and freelancers spend **3–4 hours per project** on discovery: chasing answers, filling forms, decoding vague feedback. Structed replaces that with an AI-guided interview that runs itself and outputs a complete, actionable brief.

**97% extraction accuracy. Zero manual work.**

---

## The problem we solve

<table>
<tr>
<td width="50%" valign="top">

**Before Structed**

- Scattered notes from 3 different calls
- Client forgets half the requirements
- You spend hours writing the brief yourself
- Misunderstandings discovered mid-project
- 4 hours lost on discovery, every time

</td>
<td width="50%" valign="top">

**After Structed**

- AI conducts the client interview
- Every requirement captured in real time
- Structured brief generated automatically
- Clarity before work begins
- Discovery done in 20 minutes

</td>
</tr>
</table>

---

## Who it's for

<div align="center">

|  | Small agencies | Independent consultants | Freelancers |
|---|---|---|---|
| Team size | 3–10 people | Solo or small team | Solo |
| Pain | Client briefs always incomplete | Discovery calls eat the calendar | Can't afford back-and-forth |
| Value | Consistent briefs across all projects | Structured intake without the admin | Professional onboarding from day one |

</div>

---

## Tech stack

<div align="center">

### Frontend
![Angular](https://img.shields.io/badge/Angular%2020-DD0031?style=flat-square&logo=angular&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PrimeNG](https://img.shields.io/badge/PrimeNG-0EA5E9?style=flat-square&logo=primeng&logoColor=white)

### Backend
![NestJS](https://img.shields.io/badge/NestJS%2011-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![TypeORM](https://img.shields.io/badge/TypeORM-FE0803?style=flat-square&logo=typeorm&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)

### AI / ML
![Python](https://img.shields.io/badge/Python%203.12-3776AB?style=flat-square&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)

### Infrastructure
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logo=amazonaws&logoColor=white)

</div>

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Client Browser                        │
│                   Angular 20 + PrimeNG SPA                  │
└──────────────────────────┬──────────────────────────────────┘
                           │  REST / SSE
┌──────────────────────────▼──────────────────────────────────┐
│                    NestJS 11 Backend                         │
│   Auth · Projects · Interviews · Briefs · Webhooks          │
└──────────┬───────────────────────────────────┬──────────────┘
           │  PostgreSQL (TypeORM)              │  HTTP
           │                         ┌──────────▼──────────────┐
           │                         │   Python / FastAPI       │
           │                         │   AI Microservice        │
           │                         │                          │
           │                         │  LangGraph State Machine │
           │                         │  Stage-based Prompts     │
           │                         │  OpenAI / OpenRouter     │
           │                         └──────────┬──────────────┘
           │                                    │ PostgreSQL
┌──────────▼────────────────────────────────────▼─────────────┐
│                        PostgreSQL                            │
│    Users · Projects · Interviews · Messages · Briefs        │
└─────────────────────────────────────────────────────────────┘
```

The AI pipeline runs as a separate microservice — a multi-stage LangGraph state machine that processes client responses, extracts structured data at each stage, and returns a complete brief via webhook.

---

## Repositories

<details>
<summary><b>📦 Core repositories</b></summary>

<br/>

| Repository | Description | Stack |
|---|---|---|
| `structed-ai` | Main application monorepo | Angular · NestJS · FastAPI · LangGraph |
| `infrastructure` | Deployment configs and environments | Docker · GitHub Actions |

</details>

<details>
<summary><b>🗺 Project structure</b></summary>

<br/>

```
structed-ai/
├── frontend/          # Angular 20 SPA
├── backend/           # NestJS 11 REST API
├── ai/                # Python FastAPI + LangGraph pipeline
├── docker/            # Service configs
├── .github/workflows/ # CI/CD pipelines
├── docker-compose.yml
└── Makefile
```

</details>

<details>
<summary><b>🚀 Local setup</b></summary>

<br/>

```bash
git clone https://github.com/structed-ai/structed-ai
cd structed-ai
cp .env.example .env
docker compose up --build
```

App will be available at `http://localhost:4200`.

See [CLAUDE.md](./CLAUDE.md) for full developer documentation.

</details>

---

## Traction

<div align="center">

| Metric | Value |
|---|---|
| AI extraction accuracy | **97%** |
| Prototype rating (user feedback) | **8.5 / 10** |
| Organic visitors / month | **300–500** |
| Pipeline customers | **~16** |
| MVP completion | **~80%** |

</div>

---

## Pricing

<div align="center">

|  | Freelancers | Agencies |
|---|---|---|
| Price | $110 / year | $150 / month |
| Interviews | Unlimited | Unlimited |
| Projects | ✓ | ✓ |
| Auto-generated briefs | ✓ | ✓ |
| Team seats | — | ✓ |

</div>

---

## Roadmap

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

---

## Team

**Structed AI Ltd** — incorporated in the United Kingdom, August 2025.
Stage: Pre-seed. Raising SEIS round.

<div align="center">

| | Role | Contact |
|---|---|---|
| **Marina Shmayger** | CEO — product, GTM, fundraising | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/marina-shmayger/) [![Email](https://img.shields.io/badge/marina@structed.ai-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:marina@structed.ai) |
| **Denys Korolkov** | CTO — architecture, engineering, AI systems | [![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/denyskorolkov/) |

</div>

---

<div align="center">

[![Website](https://img.shields.io/badge/structed.ai-6366f1?style=for-the-badge&logo=safari&logoColor=white)](https://structed.ai)
[![Email](https://img.shields.io/badge/marina@structed.ai-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:marina@structed.ai)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:8b5cf6,100:6366f1&height=80&section=footer" width="100%"/>

</div>
