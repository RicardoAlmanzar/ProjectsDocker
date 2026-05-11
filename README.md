<div align="center">

# 🐳 Docker Learning Portfolio

**A structured journey from writing a first Dockerfile to production-ready multi-stage builds.**  
Built project by project, concept by concept — not a course, a commitment.

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=flat&logo=nginx&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=flat&logo=docker&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)

| 10 projects | ~10 weeks | 80% image size reduction | 1-command deployments |
|:-----------:|:---------:|:------------------------:|:---------------------:|

</div>

---

> **Honest note:** These are deliberate learning projects, not production applications.  
> Each one was built to understand a specific Docker concept deeply before moving to the next.  
> The progression reflects how I approach new technology: structured, incremental, and documented.

---

## Progression map

```
Dockerfile basics  →  App containerization  →  State & persistence  →  Multi-container  →  Production patterns
    (01 – 02)               (03 – 04)                (05 – 06)              (07 – 08)           (09 – 10)
```

No Compose until I understood why volumes exist. No multi-stage builds until I had a real image bloat problem to solve.

---

## Projects

### Phase 1 — Dockerfile basics

#### [`01 · BuildContext`](./BuildContext)
**Core concept:** Build context & `.dockerignore`

How Docker sends files to the daemon, why context size matters, and how to exclude secrets and `node_modules` before they leak into an image. The `.dockerignore` file is not optional — it's a security and performance decision.

`Dockerfile` `.dockerignore` `Build context`

---

#### [`02 · DockerfileNGINX`](./DockerfileNGINX)
**Core concept:** Writing Dockerfiles from scratch

Layer ordering for cache efficiency. Serving static content with NGINX. Why instruction order is a performance decision, not a style choice — and how a badly ordered Dockerfile punishes every rebuild.

`NGINX` `Layer caching` `Static serving`

---

### Phase 2 — App containerization

#### [`03 · ContainerizeExpressAPP`](./ContainerizeExpressAPP)
**Core concept:** Containerizing a Node.js API

Copying and running a real Express app inside a container. Port mapping, environment variable injection, and the critical distinction between build-time configuration and runtime configuration.

`Node.js` `Port mapping` `Environment variables`

---

#### [`04 · containerize-react-app`](./containerize-react-app)
**Core concept:** Frontend containerization

The difference between build-time and runtime env vars in React — a common source of production bugs. How to serve a SPA build correctly using NGINX instead of `npm start`.

`React` `NGINX` `Env variable strategy`

---

### Phase 3 — State & persistence

#### [`05 · KeyValueApp`](./KeyValueApp)
**Core concept:** Container ephemerality

Why containers lose data on restart. The fundamental problem this creates for any stateful application — and why solving it requires a different architectural approach, not a Docker flag.

`Stateful apps` `Ephemerality` `Architecture`

---

#### [`06 · Volumes`](./Volumes)
**Core concept:** Docker Volumes & bind mounts

Named vs anonymous volumes. Bind mounts for dev workflows. Persisting data across container restarts — the direct architectural answer to the problem surfaced in project 05.

`Volumes` `Bind mounts` `Data persistence`

---

### Phase 4 — Multi-container

#### [`07 · DockerCompose`](./DockerCompose)
**Core concept:** Multi-container orchestration

Writing `docker-compose.yml` from scratch. Service dependencies, shared networks, environment management. The shift from `docker run` commands to infrastructure-as-code that a whole team can use.

`Docker Compose` `Networking` `Service dependencies`

---

#### [`08 · NotesApp`](./NotesApp)
**Core concept:** Full-stack app with Compose

Connecting a Node.js API + database + React frontend as a single Compose stack. Health checks, service startup order, and one-command environment spin-up for any machine.

`Full-stack` `Compose` `Health checks` `Startup order`

---

### Phase 5 — Production patterns

#### [`09 · MultistageBuild`](./MultistageBuild)
**Core concept:** Multi-stage builds

Separating build and runtime stages so dev dependencies never ship to production. The pattern that makes images lean, fast to pull, and smaller attack surface — standard in any serious CI/CD pipeline.

`Multi-stage` `Security` `Lean images`

---

#### [`10 · OptimizingImages`](./OptimizingImages)
**Core concept:** Image size & layer cache optimization

Layer caching strategies that cut rebuild times from 3 minutes to 30 seconds. Alpine base images. Reducing final image size by 60–80% — meaningful at scale for pull times, storage cost, and security surface.

`Alpine` `Optimization` `CI/CD ready` `Cache strategy`

---

## Key takeaways

**Layer caching is a performance decision, not a style choice.**  
Copying `package.json` before source code means a dependency cache hit on every non-dependency change. The difference: 30-second rebuilds vs 3-minute ones. This transfers directly to CI/CD pipeline optimization.

**Containers are stateless compute units — design accordingly.**  
The `KeyValueApp` → `Volumes` sequence was the most important conceptual shift. Treating containers as ephemeral and externalizing state is foundational to how I now think about deployment architecture.

**Multi-stage builds cut image size 60–80%.**  
Before `MultistageBuild`, my images were shipping dev dependencies, build tooling, and cached package managers into production. The reduction affects pull times, security surface, and infrastructure cost — not just disk space.

**Compose enforces reproducibility across a team.**  
Long `docker run` commands with flags are unmanageable at team scale. After `DockerCompose` and `NotesApp`, spinning up a full multi-service environment became a one-command operation that anyone can run on any machine.

---

## How this connects to real work

I build commercial SaaS products targeting the Dominican Republic and LATAM markets. Current projects:

**GeoPlanner Pro** — Route optimization SaaS for sales and logistics teams (Next.js + Python + Supabase).  
Docker applies directly: containerized deployments, reproducible dev environments, and CI/CD pipelines that don't break between machines.

**WhatsApp CRM** — Quotation generation and client management for freelancers (Next.js + Supabase).  
Running a Compose-based local development stack that mirrors the production environment.

These learning projects were the foundation for that.

---

## What's next

- [ ] Kubernetes fundamentals — moving from Compose to k8s for orchestration at scale  
- [ ] CI/CD integration — GitHub Actions building and pushing images on every merge  
- [ ] Production deployment — applying containerization to GeoPlanner Pro's deployment pipeline  

---

<div align="center">

Full-stack developer · Student at [INTEC](https://www.intec.edu.do/) · Santo Domingo, Dominican Republic  
*Next.js · Python · Supabase · Docker*

</div>
