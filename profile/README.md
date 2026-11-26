<h1 align="center">FBR.Dev Technology</h1>

<p align="center">
  Sites, sistemas e produtos digitais sob medida. Do primeiro contato ao site no ar.
  <br>
  <a href="https://fbrdev.com.br"><strong>fbrdev.com.br</strong></a>
</p>

---

## O que fazemos

| Frente | Entrega |
|---|---|
| Sites institucionais | Next.js com SSG/SSR, Lighthouse 95+, WCAG 2.2 AA |
| Plataformas SaaS | Area do cliente, painel do gestor, planos e assinaturas |
| Hospedagem gerenciada | Sites de clientes em subdominios `*.fbrdev.com.br` com TLS |
| Privacidade | Consentimento, retencao e descarte conforme a LGPD |

## Stack

| Camada | Tecnologia |
|---|---|
| Frontend | Next.js 16 (App Router), React 19, TypeScript, CSS Modules |
| API | Node.js 24, Fastify 5, Better Auth, Kysely, Zod, WebSockets |
| Dados | PostgreSQL 17, migrations SQL-first |
| Infra | Docker, Caddy (TLS automatico), Hostinger, VPS |
| Qualidade | GitHub Actions, typecheck, smoke tests, auditoria de seguranca |

## Fluxo da plataforma

```mermaid
flowchart LR
    V([Visitante]) --> S[Site<br>fbrdev.com.br]
    S -->|contato| L[Lead]
    S -->|agendamento| A[Reuniao]
    L --> P[Proposta e plano]
    A --> P
    P -->|assinatura| C[Area do cliente]
    C --> D[Site do cliente<br>*.fbrdev.com.br]
    G[Painel do gestor] -.gerencia.-> L
    G -.gerencia.-> A
    G -.cobrancas e analytics.-> C
```

## Arquitetura

```mermaid
flowchart TB
    U([Navegador]) -->|HTTPS| W[Frontend<br>Next.js 16 - Hostinger]
    U -->|HTTPS + WS| E[Caddy<br>core.fbrdev.com.br]
    W -->|REST| E
    E --> API[API Fastify 5<br>Docker]
    API --> DB[(PostgreSQL 17)]
    API --> AUTH[Better Auth<br>e-mail + Google]
    API --> PAY[Pagamentos<br>Stripe e PIX]
    API --> MAIL[E-mail transacional]
```

## Como trabalhamos

```mermaid
flowchart LR
    I[Issue] --> B[Branch]
    B --> CM[Commit<br>Conventional Commits]
    CM --> SA[Auditoria de seguranca]
    SA --> PR[Pull request]
    PR --> CI{CI<br>typecheck, build, smoke}
    CI -->|falhou| B
    CI -->|ok| M[main]
    M --> DA[Deploy API<br>VPS via SSH]
    M --> DW[Deploy Web<br>Hostinger]
    DA --> H[Health check]
```

---

<p align="center">FBR.Dev Technology - Brasil</p>
