# Lucas Mera — Portfolio de Productos con IA

🇪🇸 [Español](#español) | 🇺🇸 [English](#english)

---

## Español

Senior TPM (20+ años, Walmart / HP / Globant / DreamHost) e Independent Founder & AI Product Architect. Los proyectos de abajo comparten una misma arquitectura base (React/Vite + Node/Express + Supabase multi-tenant + motor de IA con fallback entre proveedores), reusada y extendida en cada producto — no son experimentos sueltos, son un mismo sistema de decisiones aplicado varias veces.

📎 Cada proyecto tiene su propio repo con case study. El código fuente real es privado donde hay cliente o datos de negocio de por medio — el patrón se explica acá, no se expone el código.

### Resumen

| Proyecto | Dolor que resuelve | Frontend | Backend | Infra / Datos | IA | Estado |
|---|---|---|---|---|---|---|
| **[Converta Seguros](https://github.com/luke7606/converta-seguros-ai)** | Los productores de seguros pierden ventas porque responden tarde en WhatsApp y no hay seguimiento sistemático del lead | React/Vite | Node/Express (Railway) | Supabase (Postgres multi-tenant) | Motor Lucía — Claude→Groq→Gemini fallback | **Producción — cliente real pagando** |
| **Sentinel Platform** | Empresas medianas no tienen forma de centralizar operación + IA sin depender de un equipo dev propio para cada cambio | React/Vite | Node/Express (Railway) | Supabase multi-tenant, adapters DB/IA/Storage intercambiables | Kai — shell de agente central, `useBrain` + prompts configurables | Desarrollo activo |
| **Doppia AI** | La info del día a día (tickets, pendientes, errores) queda dispersa en herramientas separadas y nadie la cruza de forma proactiva | React/Vite | Node/Express | Supabase propio, separado de Sentinel/Converta | AI router con fallback + Approval Gate (quien propone no aprueba) | Arquitectura definida, en construcción |
| **Architect / Finn** | Empresas no saben por dónde arrancar a aplicar IA en sus procesos; filtrar/responder candidatos a mano consume horas | — (agente, sin UI propia aún) | Node/Express | Supabase (`agent_registry`, multi-tenant) | Finn: clasificación de Gmail + generación de CV/respuesta con fit-score | Finn en desarrollo |
| **Nera Builder** | Armar una app nueva (CRUD + IA + analytics) implica repetir la misma arquitectura desde cero cada vez | React/Vite | Node/Express | Supabase multi-tenant | aiProvider.js compartido | Arquitectura definida |
| **Pedix** | Pequeños negocios de comida no tienen acceso a un sistema de pedidos tipo PedidosYa/Uber Eats sin pagar comisión | — (WhatsApp como interfaz) | Node/Express | Supabase (`pedix_*`) | — | Schema diseñado |
| **Headhunting System** | Procesos de selección manuales pierden trazabilidad entre etapas y nadie sabe en qué estado real está cada candidato | React (hook `useApplications`) | Express | Supabase (máquina de estados `VALID_TRANSITIONS`) | — | Construido |

### Por qué compartir arquitectura entre productos no es reutilizar código, es un principio de diseño

Todos parten de las mismas reglas, documentadas y aplicadas consistentemente:
- **Multi-tenant real**: cada cliente/empresa aislado por `company_id`, pensado para que un cliente nuevo sea solo configuración, no código nuevo
- **Cero hardcoding**: colores, textos, URLs, prompts — todo configurable, nunca escrito a mano en el código
- **"IA sugiere, humano aprueba"**: ninguna acción irreversible ocurre sin aprobación humana explícita, y quien propone la acción no es quien la aprueba
- **Motor de IA con fallback**: Claude como proveedor primario, con Groq y Gemini como respaldo automático si el primero falla

### Complemento: track enterprise (DreamHost)

En paralelo a construir estos productos, en DreamHost lidero coordinación de infraestructura y tooling operativo a nivel Senior TPM — inventario de 53.700+ servidores, agentes de IA internos para sync de tickets y reportes, migración de procesos manuales a flujos automatizados. Ese track muestra la otra mitad del perfil: ejecución enterprise a escala, no solo construcción de producto propio.

### Estructura sugerida de este repo

```
/portfolio-ai-products
├── README.md
├── /case-studies
│   ├── sentinel-platform.md
│   ├── doppia-ai.md
│   ├── architect-finn.md
│   ├── nera-builder.md
│   ├── pedix.md
│   └── headhunting-system.md
└── /diagrams
    └── shared-architecture.mmd
```

Converta Seguros queda como repo aparte porque tiene su propio README bilingüe y es el único con cliente en producción.

---

## English

Senior TPM (20+ years, Walmart / HP / Globant / DreamHost) and Independent Founder & AI Product Architect. The projects below share one underlying architecture (React/Vite + Node/Express + multi-tenant Supabase + an AI engine with provider fallback), reused and extended across each product — these aren't one-off experiments, they're the same set of design decisions applied repeatedly.

📎 Each project has its own repo with a case study. Actual source code is kept private wherever a client or business data is involved — the pattern is explained here, the code is not exposed.

### Summary

| Project | Pain point it solves | Frontend | Backend | Infra / Data | AI | Status |
|---|---|---|---|---|---|---|
| **[Converta Seguros](https://github.com/luke7606/converta-seguros-ai)** | Insurance agents lose sales because they respond too slowly on WhatsApp, with no systematic lead follow-up | React/Vite | Node/Express (Railway) | Supabase (multi-tenant Postgres) | Lucía engine — Claude→Groq→Gemini fallback | **Production — real paying client** |
| **Sentinel Platform** | Mid-size companies have no way to centralize operations + AI without depending on an in-house dev team for every change | React/Vite | Node/Express (Railway) | Multi-tenant Supabase, swappable DB/AI/Storage adapters | Kai — central agent shell, `useBrain` + configurable prompts | Active development |
| **Doppia AI** | Day-to-day information (tickets, pending items, errors) stays scattered across separate tools with nothing proactively connecting it | React/Vite | Node/Express | Own Supabase project, separate from Sentinel/Converta | AI router with fallback + Approval Gate (proposer can't approve) | Architecture defined, in progress |
| **Architect / Finn** | Companies don't know where to start applying AI to their processes; manually screening/replying to candidates eats hours | — (agent, no UI yet) | Node/Express | Supabase (`agent_registry`, multi-tenant) | Finn: Gmail classification + tailored CV/reply generation with a fit-score | Finn in development |
| **Nera Builder** | Building a new app (CRUD + AI + analytics) means rebuilding the same architecture from scratch every time | React/Vite | Node/Express | Multi-tenant Supabase | Shared aiProvider.js | Architecture defined |
| **Pedix** | Small food businesses have no access to a PedidosYa/Uber Eats-style ordering system without paying platform commissions | — (WhatsApp as the interface) | Node/Express | Supabase (`pedix_*`) | — | Schema designed |
| **Headhunting System** | Manual hiring pipelines lose traceability between stages, and nobody knows a candidate's real current status | React (`useApplications` hook) | Express | Supabase (state machine, `VALID_TRANSITIONS`) | — | Built |

### Why sharing architecture across products isn't code reuse — it's a design principle

Every product starts from the same rules, documented and consistently applied:
- **Real multi-tenancy**: every client/company isolated by `company_id`, designed so onboarding a new client is configuration only, never new code
- **Zero hardcoding**: colors, copy, URLs, prompts — all configurable, never written by hand into the code
- **"AI suggests, human approves"**: no irreversible action happens without explicit human approval, and whoever proposes an action is never the one who approves it
- **AI engine with fallback**: Claude as the primary provider, with Groq and Gemini as automatic backup if the first one fails

### Complementary track: enterprise (DreamHost)

Alongside building these products, at DreamHost I lead infrastructure coordination and operational tooling as a Senior TPM — an inventory of 53,700+ servers, internal AI agents for ticket/report syncing, and migrating manual processes into automated workflows. That track shows the other half of the profile: enterprise execution at scale, not just independent product building.

### Repository structure

```text
/portfolio-ai-products
├── README.md
└── /diagrams
    └── shared-architecture.mmd
```

Converta Seguros stays as a separate repo since it already has its own bilingual README and is the only one with a client in production.
