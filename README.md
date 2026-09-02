# ComprasInteligentes360

Plataforma end-to-end de gestión de solicitudes de compra sobre SAP BTP: ABAP Cloud (RAP), CAP, SAP Integration Suite e IA generativa (AI Core / Orchestration).

> 🚧 Proyecto en construcción — este README se actualiza a medida que avanza cada fase.

## Enunciado del proyecto

Plataforma de gestión inteligente de solicitudes de compra ("Purchase Requisition") para una empresa ficticia, que:

1. Gestiona el maestro de proveedores en un backend **ABAP Cloud** (SAP BTP ABAP Environment), expuesto vía **RAP** como servicio OData V4.
2. Expone la aplicación de negocio (creación, aprobación y seguimiento de solicitudes) como un servicio **CAP** (Node.js) que consume el backend ABAP como servicio remoto.
3. Enriquece los datos (tipo de cambio, notificaciones de aprobación) mediante un flujo de integración (**iFlow**) en SAP Integration Suite.
4. Incorpora **IA generativa** (SAP AI Launchpad / Orchestration) para resumir la justificación de cada solicitud y clasificar su nivel de riesgo.
5. Está administrada siguiendo buenas prácticas de **administración de BTP** (entitlements, roles, destinos, conectividad).

## Arquitectura

```
[API pública tipo de cambio]
        │
        ▼
 SAP Integration Suite (iFlow)
        │
        ▼
 App CAP (Node.js) ──consume remoto──► SAP ABAP Environment (RAP)
        │                                  (Maestro de Proveedores)
        │  (Solicitudes de Compra)
        │
        ├──► Módulo de IA (real / mock)
        │     diseñado y validado en SAP AI Launchpad
        │
        ▼
       UI (Fiori Elements / SAPUI5)
```

## Estructura del repositorio

```
comprasinteligentes360/
├── docs/                   # arquitectura, capturas, decisiones técnicas
├── abap/                   # objetos RAP: CDS, BDEF, metadata
├── cap-app/                # proyecto CAP: db, srv, app
├── integration-suite/      # iFlows exportados + capturas
└── ai-genai/               # prompts, capturas de AI Launchpad, módulo IA
```

## Roadmap / progreso

- [ ] **Fase 0 — Administración BTP**: subcuenta, entitlements, boosters, role collections, destinos
- [ ] **Fase 1 — Backend RAP en ABAP Cloud**: CDS, Behavior Definition, servicio OData V4
- [ ] **Fase 2 — Aplicación CAP**: modelo de datos, servicio remoto, UI
- [ ] **Fase 3 — Integración**: iFlows de tipo de cambio y notificación
- [ ] **Fase 4 — IA Generativa**: prompts en AI Launchpad, módulo real/mock en CAP
- [ ] **Fase 5 — Documentación final**: vídeo demo, diagrama definitivo

## Cómo ejecutar el proyecto

*(se completa en la Fase 2)*

## Notas técnicas relevantes

- La integración con IA generativa se diseñó y validó en el entorno guiado de SAP AI Launchpad (Generative AI Hub Basic Trial), que no expone credenciales hacia aplicaciones externas. El código incluye la implementación real de la llamada a la Orchestration API y un modo `mock` para que el proyecto sea ejecutable sin depender de un tenant personal. Más detalle en `docs/decisiones-tecnicas.md`.

## Licencia

MIT — ver [LICENSE](LICENSE).
