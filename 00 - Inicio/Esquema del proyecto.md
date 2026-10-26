# 🗺️ Esquema del proyecto — Kampus

Volver a [[Inicio]] · Detalle técnico en [[Arquitectura y stack]]

## 1. Cuentas y herramientas por PC

Los 4 PCs (PC 1, PC 2, PC 3 y PC 4) se montan igual.

```mermaid
flowchart TB
  PC1[PC 1] & PC2[PC 2] & PC3[PC 3] & PC4[PC 4] --> CADA
  subgraph CADA[En cada PC]
    GH[GitHub<br/>cuenta propia]:::login
    OB[Obsidian + Obsidian Git<br/>sin cuenta]:::inst
    VS[VS Code + Node 22<br/>sin cuenta]:::inst
    EX[Expo Go en el móvil<br/>sin cuenta]:::inst
  end
  subgraph EQUIPO[Compartido por el equipo]
    FI[Figma<br/>proyecto compartido]:::login
    SB[Supabase<br/>por confirmar]:::pend
    VE[Vercel<br/>más adelante]:::pend
  end
  classDef login fill:#E1F5EE,stroke:#0F6E56,color:#085041
  classDef inst fill:#F1EFE8,stroke:#5F5E5A,color:#444441
  classDef pend fill:#FAECE7,stroke:#993C1D,color:#712B13
```

🟢 Iniciar sesión ya · ⚪ Solo instalar · 🟠 Pendiente

### Checklist de cada PC
| Paso | PC 1 | PC 2 | PC 3 | PC 4 |
|---|---|---|---|---|
| Cuenta de GitHub, colaborador en **SBIT_BIRM** y **Vault-sbit** | [ ] | [ ] | [ ] | [ ] |
| Token *classic* con permisos `repo` + `workflow` | [ ] | [ ] | [ ] | [ ] |
| Obsidian + plugin Obsidian Git, vault clonado | [ ] | [ ] | [ ] | [ ] |
| Node 22 + VS Code, `SBIT_BIRM` clonado y `npm install` | [ ] | [ ] | [ ] | [ ] |
| Expo Go en el móvil, la app abre con `npm start` | [ ] | [ ] | [ ] | [ ] |
| Acceso al proyecto de Figma | [ ] | [ ] | [ ] | [ ] |

## 2. Lo construido

```mermaid
flowchart LR
  subgraph V[Vault-sbit · Obsidian]
    P[Plan de trabajo]
    T[Tablero de tareas]
    D[Decisiones y stack]
  end
  subgraph S[SBIT_BIRM · código]
    A[App Expo<br/>web y Android]:::ok
    N[Núcleo hexagonal<br/>casos de uso]:::ok
    M[Backend memoria<br/>datos de prueba]:::ok
    SU[Adaptador Supabase<br/>sin activar]:::pend
    L[ESLint + Prettier]:::ok
    C[GitHub Actions<br/>CI en verde]:::ok
  end
  classDef ok fill:#E1F5EE,stroke:#0F6E56,color:#085041
  classDef pend fill:#FAECE7,stroke:#993C1D,color:#712B13
```

## 3. Hacia dónde vamos

```mermaid
flowchart LR
  F0[Arranque<br/>hecho]:::ok --> F1[Análisis<br/>ahora]:::now --> F2[Diseño<br/>Figma, BD] --> F3[Desarrollo<br/>sprints] --> F4[Entrega<br/>demo]
  F4 --> DEST
  subgraph DEST[Destino: Kampus terminado]
    APP[App móvil<br/>por perfiles]
    WEB[Panel web<br/>secretaría · Vercel]
    BE[Backend<br/>Supabase u otro]
  end
  classDef ok fill:#E1F5EE,stroke:#0F6E56,color:#085041
  classDef now fill:#EEEDFE,stroke:#534AB7,color:#3C3489
```
