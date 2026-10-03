### Roadmap de AgenticTrustFabric

El roadmap separa documentación, arquitectura, migración y nuevas capacidades para evitar cambios simultáneos difíciles de auditar.

#### Fase D0. Identidad

Estado esperado:

- repositorio renombrado a `AgenticTrustFabric`
- README alineado con la nueva identidad
- alcance actual y futuro diferenciados
- identificadores internos heredados documentados

No se modifica código funcional.

#### Fase D1. Arquitectura

Entregables:

- `docs/ARCHITECTURE.md`
- `docs/TRUST_MODEL.md`
- `docs/THREAT_MODEL.md`
- `docs/PROTOCOL_MODEL.md`

Resultado esperado:

El núcleo queda definido como neutral respecto al protocolo.

#### Fase D2. Contrato canónico

Objetivo:

Definir modelos versionados para representar eventos de seguridad.

Primeros contratos:

- actor
- peer
- operation
- capability
- delegation
- provenance
- evidence
- policy decisión

En está fase comienzan cambios de código.

#### Fase D3. Adaptador MCP

Objetivo:

Aislar la implementación MCP existente detras de una interfaz de adaptador.

Requisitos:

- conservar comportamiento observable
- conservar RBAC
- conservar sandbox
- agregar pruebas de contrato
- reducir dependencias MCP dentro del núcleo

#### Fase D4. Migración MCP

Objetivo:

Actualizar la versión del SDK MCP de forma controlada.

La migración debe realizarse después de estabilizar el adaptador.

#### Fase D5. Adaptador A2A

Objetivo:

Agregar comunicación agent to agent bajo el mismo policy core.

Primera versión:

- descubrimiento controlado
- tareas
- identidad de peer
- contexto de delegación
- policy enforcement
- evidence record

#### Fase D6. Delegation security

Objetivo:

Agregar controles específicos para cadenas de delegación.

Casos:

- delegation depth
- capability attenuation
- confused deputy
- replay
- loops
- provenance loss

#### Fase D7. Observabilidad

Objetivo:

Relacionar decisiones de policy, llamadas de protocolo y evidencia mediante trazas.

La integración debe ser compatible con OpenTelemetry cuando sea viable.

#### Fase D8. Workload identity

Objetivo:

Evaluar identidad verificable para agentes y servicios.

Posibles líneas experimentales:

- SPIFFE
- SPIRE
- identidad de agentes
- credenciales de workload

Ninguna tecnología se adopta sin evaluación previa.

#### Fase D9. Evaluación multiagente

Objetivo:

Extender el benchmark a ataques entre protocolos y entre agentes.

Familias iniciales:

- A2A to MCP injection
- capability escalation
- delegation confusion
- provenance laundering
- evidence tampering
- compromised peer

#### Condición para comenzar código nuevo

No se inicia la implementación A2A hasta cerrar D1 y definir el contrato de D2.
