### Modelo de seguridad

AgenticTrustFabric aplica controles de seguridad sobre operaciones agenticas y sobre la evidencia utilizada para decidir si una operación puede considerarse confiable.

La implementación actual protege principalmente el flujo MCP y el pipeline DevSecOps. La arquitectura futura debe permitir aplicar las mismas decisiones a otros protocolos sin duplicar la lógica de seguridad.

#### Controles actuales

Los controles implementados incluyen:

1. auditoría de skills `SKILL.md`
2. auditoría de tools, resources y prompts MCP
3. policy gate con modos `demo`, `ci` y `strict`
4. evidence pack verificable con hashes SHA-256
5. RBAC para herramientas expuestas
6. sandbox para ejecución controlada
7. trazabilidad mediante identificador de ejecución

#### Principio deny by default

Las operaciones que no puedan asociarse con una política válida, identidad aceptada o evidencia suficiente deben ser rechazadas o enviadas a revisión.

El comportamiento exacto depende del modo operativo, pero el modo `strict` no debe convertir ausencia de evidencia en autorización.

#### Evidencia

La existencia de un archivo no implica que la evidencia sea confiable.

La evaluación debe considerar como mínimo:

- origen
- herramienta productora
- identificador de ejecución
- integridad
- vigencia
- modo de política
- presencia de fallback
- correspondencia con el commit evaluado

#### Separación entre demo y release

El modo `demo` puede aceptar evidencia fallback y terminar en `WARN`.

Los modos `ci` y `strict` no deben aceptar fallback, artifacts obsoletos ni hashes inconsistentes.

Después de `make demo-local`, un `policy-check --mode strict` debe fallar cuando la evidencia provenga del mecanismo fallback. La completitud de archivos no sustituye la procedencia real de la evidencia.

#### Seguridad neutral respecto al protocolo

El núcleo futuro debe evaluar un evento canónico antes de autorizar una operación.

Ese evento debe contener, cuando sea posible:

- identidad del actor
- protocolo
- operación solicitada
- recurso
- capability requerida
- contexto de delegación
- provenance
- evidencia asociada
- decisión de política

MCP y A2A deben traducirse a este modelo sin introducir reglas de negocio duplicadas.

#### Condiciones para release

Un release candidate debe demostrar:

- mismo `run_id` para evidencia relacionada
- hashes consistentes
- scanners reales cuando el perfil lo exige
- policy gate correspondiente al nivel de release
- autorización RBAC válida
- sandbox activo cuando corresponda
- configuración endurecida de contenedores
- limitaciones experimentales documentadas
