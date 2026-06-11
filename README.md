<div align="center">

# Vu Phan Gia Thinh

**Software Engineering Student** · *Ho Chi Minh City, Vietnam*

*Building production-grade systems — from Kubernetes GitOps pipelines and CI/CD automation to full-stack APIs and data engineering pipelines.*

<p>
  <a href="https://github.com/thinhvpg2410">GitHub</a> ·
  <a href="https://www.linkedin.com/in/thinhvpg/">LinkedIn</a> ·
  <a href="mailto:thinh.vpg@gmail.com">thinh.vpg@gmail.com</a> ·
  <strong>+84 919 475 444</strong>
</p>

</div>

---

## About

**Software Engineering** student at **Industrial University of Ho Chi Minh City** (Aug 2021 – present, expected graduation 2026), with hands-on production experience across **DevOps/infrastructure**, **full-stack development**, and **data engineering**. Delivered measurable outcomes across 4 projects: ~60% API latency reduction, ~80% CI/CD effort savings, 10–100x query throughput improvement, 99.7% production uptime.

---

## Open to

| Priority | Role |
|----------|------|
| 🥇 | **DevOps / Platform / SRE** |
| 🥈 | **Fullstack / Backend Engineer** |
| 🥉 | **Data Engineer** |

---

## Skills

| Area | Stack |
|------|-------|
| **Container & Orchestration** | Kubernetes (Kind), Helm 3, Docker, Docker Compose, multi-stage Dockerfile, Nginx |
| **CI/CD & GitOps** | GitLab CI (5-stage pipeline), GitHub Actions, ArgoCD, GitOps two-repo pattern, SSH deploy, Bash scripting |
| **Observability** | Prometheus, Grafana (kube-prometheus-stack), Loki, Promtail, structured logging, health checks |
| **Secrets & Security** | HashiCorp Vault (Agent Injector), Trivy image scanning, SSH key auth, UFW, Helmet, CORS, argon2 |
| **Cloud & Infrastructure** | AWS EC2, Linux (Ubuntu), IAM, EBS management |
| **Backend** | NestJS 11, TypeScript, Node.js, Prisma ORM, PostgreSQL 16, Redis 7, Socket.IO, REST, Swagger/OpenAPI |
| **Frontend** | Next.js, React Native (Expo), Redux Toolkit, Tailwind CSS |
| **Databases** | PostgreSQL, Redis, MongoDB |
| **Languages** | TypeScript, JavaScript, Python, SQL, Bash |
| **Integrations** | OpenAI API, Gemini 2.0 Flash, PayPal, Cloudinary, Firebase Admin SDK |
| **Practices** | GitOps, IaC, shift-left security, monorepo, Agile/Scrum |

---

## Projects

### [choco-k8s](https://github.com/thinhvpg2410/choco-k8s) — Kubernetes GitOps Infrastructure *(Jun 2026 – Present)*

> DevOps portfolio project covering the full Kubernetes + GitOps toolchain.

- Provisioned a **3-node Kind cluster** deploying NestJS API, PostgreSQL 16, and Redis 7 via **Helm 3** with `values-staging.yaml` overrides (3 replicas); achieved **ArgoCD Synced + Healthy** with a **sub-3-minute GitOps loop**
- Implemented **two-repo GitOps pattern**: GitLab CI pushes Docker Hub image and updates `image.tag` in `values-staging.yaml` via `sed` + `git commit --allow-empty [skip ci]`; ArgoCD auto-syncs within 3 minutes
- Deployed **full observability stack**: kube-prometheus-stack (Prometheus + Grafana) + Loki/Promtail in a dedicated namespace; Grafana dashboards expose NestJS HTTP request rate, error rate, and p95 latency
- Integrated **HashiCorp Vault Agent Injector** in dev mode — injects `DATABASE_URL` and `JWT_SECRET` as in-pod files, eliminating plaintext Kubernetes Secrets
- Authored Makefile automation targets and a **runbook** covering deploy, rollback, and observability access

*Stack: Kubernetes · Helm · ArgoCD · Prometheus · Grafana · Loki · Vault · GitLab CI · Docker Hub*

---

### [choco-ecomerce](https://github.com/thinhvpg2410/choco-ecomerce) — Production E-commerce Platform *(Jan 2026 – May 2026)*

> Full-stack monorepo: storefront, admin dashboard, and REST API — deployed on AWS EC2.

- Designed a **4-service Docker Compose** stack on AWS EC2: **99.7% uptime**, multiple deploys/week at **14–18 min end-to-end CI cycle**
- Built a **5-stage GitLab CI/CD** pipeline (install → lint → test → build → publish → deploy); cut release cycle **from ~25 min to under 6 min**
- Implemented **Redis 7 caching** on high-traffic catalog routes: **~78% cache-hit rate**, reducing PostgreSQL read load by ~60%; avg API response <80 ms (cached <15 ms)
- Authored **multi-stage Dockerfile** (builder + production stages) reducing image size by **~60–70%**, cold start under 3 seconds
- Configured **Nginx 1.27-alpine** with real-IP forwarding, WebSocket upgrade support, 20 MB upload limit, and 60s proxy timeouts
- Wrote **idempotent deploy script** (`set -euo pipefail`, `git reset --hard` before pull, `docker system prune` before build to prevent disk-full on 30 GB EBS)
- Dual payment gateways: **PayPal** + **Sepay QR bank transfer** via webhooks; Lighthouse 94/100 performance, 97/100 accessibility

*Stack: NestJS · Next.js · TypeScript · PostgreSQL · Prisma · Redis · Docker · GitLab CI/CD · AWS EC2 · Nginx*

---

### [daily-cook](https://github.com/thinhvpg2410/daily-cook) — AI Meal Planning & Nutrition *(Sep 2025 – Dec 2025, Graduation Thesis)*

> Full-stack TypeScript monorepo: mobile app, NestJS API, admin dashboard, and a data engineering layer.

- Engineered **OpenAI GPT-4o** AI suggestion engine with structured prompt templates — cut average meal-planning time by **~70%**
- Designed **16+ composite PostgreSQL indexes** targeting date-range joins and user-scoped lookups: **10–100x query throughput** improvement on production-scale datasets
- Built **GitHub Actions CI/CD** (lint → test → Docker build → SSH deploy): reduced release cycle **from ~20 min to 4 min** (~80% reduction)
- Containerized 3-service stack with Docker Compose; eliminated **100% of dev/prod environment parity bugs** across a 4-month production window
- Hardened production server (OWASP Top-10): SSH key-only auth, UFW firewall, IAM-scoped credentials, Helmet, CORS, argon2
- Implemented **ETL pipeline**: daily Puppeteer scraper → Vietnamese grocery prices → PostgreSQL upsert with unit normalization
- Designed **Star Schema** (nutrition analytics) and **Snowflake Schema** (recipe cost analytics) with PostgreSQL materialized views for daily macro and 7-day rolling aggregations

*Stack: NestJS · React Native (Expo) · PostgreSQL · Prisma · Docker · GitHub Actions · AWS EC2 · OpenAI · Puppeteer*

---

### [loza-chat](https://github.com/thinhvpg2410/loza-chat) — Real-time Messaging Platform *(Jan 2026 – May 2026)*

> Production-grade chat app: web + mobile clients, WebRTC calls, 22-model schema.

- **144 REST endpoints** + **14 WebSocket events** (Socket.IO): messaging, typing indicators, delivery/read receipts, reactions, sticker packs
- **WebRTC voice/video calls** with full signaling (offer/answer/ICE candidates), TURN server support; FCM push notifications for backgrounded callees
- **Auth**: phone OTP, JWT access/refresh with device session tracking, QR code web login approved from trusted mobile device
- **22 Prisma models**: users, conversations, messages, groups, attachments, sticker packs, audit logs
- Docker Compose + Nginx; GitHub Actions CI/CD with automated SSH deploy on push to `main`

*Stack: NestJS · Socket.IO · Next.js · Expo React Native · PostgreSQL · Prisma · WebRTC · Docker · GitHub Actions*

---

## Education

| | |
|--|--|
| **School** | Industrial University of Ho Chi Minh City |
| **Major** | Software Engineering |
| **Period** | Aug 2021 – Present · Expected Graduation: 2026 |
| **Coursework** | Operating Systems, Computer Networks, Database Systems, Software Architecture & Design |
| **Self-study** | AWS architecture, Kubernetes (CKA curriculum), Prometheus + Grafana, Linux SysAdmin, Terraform |

---

## Certifications

| | Status |
|--|--|
| **AWS Certified Cloud Practitioner (CLF-C02)** | In Progress · Expected Jul 2026 |
| **TOEIC Listening & Reading** | In Progress · Expected Aug 2026 |

---

## GitHub Stats

![Stats](https://github-readme-stats.vercel.app/api?username=thinhvpg2410&show_icons=true&theme=tokyonight&hide_title=true&hide=prs)
![Top languages](https://github-readme-stats.vercel.app/api/top-langs/?username=thinhvpg2410&layout=compact&theme=tokyonight)

---

<div align="center">

*Thanks for visiting — feel free to reach out.*

</div>
