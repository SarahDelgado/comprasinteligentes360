# Decisiones técnicas
## IA generativa: entorno real vs. mock

La integración con IA generativa se diseñó y validó en el entorno guiado de SAP AI Launchpad (Generative AI Hub Basic Trial), que no expone credenciales hacia aplicaciones externas (no hay opción de Deploy ni de exportar service key). El código incluye la implementación real de la llamada a la Orchestration API y un modo `mock` para que el proyecto sea ejecutable sin depender de un tenant personal.
