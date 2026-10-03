### Arquitectura de AgenticTrustFabric

AgenticTrustFabric se define como una capa de confianza y seguridad para sistemas agénticos.

El objetivo arquitectónico es evitar que el núcleo de seguridad dependa directamente de MCP, A2A o cualquier protocolo futuro.

#### Capas principales

##### Protocol adapters

Los adaptadores convierten operaciones específicas de cada protocolo en eventos de seguridad con una representación común.

Los primeros adaptadores considerados son:

- MCP
- A2A

MCP es el adaptador actualmente implementado de forma parcial mediante el servidor y auditor existentes.

A2A es una extensión planificada y aún no debe considerarse implementada.

##### Canonical security event

El núcleo debe recibir una representación normalizada de cada operación relevante.

El contrato conceptual inicial contiene:

```text
event_id
timestamp
protocol
actor
peer
operation
resource
capability
delegation
provenance
evidence
context
```

Este contrato se convertira posteriormente en un schema versionado.

##### Policy and trust core

El núcleo evalua:

- autorización
- identidad
- capability
- procedencia
- integridad de evidencia
- contexto de delegación
- restricciones de runtime
- modo operativo

La salida conceptual es una decisión controlada.

```text
ALLOW
DENY
REVIEW
QUARANTINE
```

La implementación actual usa principalmente resultados equivalentes a `PASS`, `WARN` y `FAIL`. La normalización de decisiones pertenece a una fase posterior.

##### Evidence plane

La evidencia debe poder relacionarse con:

- commit
- ejecución
- herramienta
- decisión
- artifact
- identidad
- protocolo

El evidence pack existente se conserva como base para este plano.

##### Runtime enforcement

La ejecución autorizada debe pasar por controles como:

- RBAC
- allowlist
- sandbox
- timeout
- límites de recursos
- restricciones de red cuando correspondan

#### Flujo conceptual

```text
Agent or service
Protocol adapter
Canonical security event
Policy and trust core
Decisión
Runtime enforcement
Evidence
```

#### Regla de dependencia

El núcleo no debe importar implementaciones específicas de MCP o A2A.

Los adaptadores pueden depender del núcleo.

El núcleo debe operar sobre modelos propios y contratos versionados.

#### Compatibilidad

Durante la migración se mantienen temporalmente:

- `devsecops_agent`
- `skillchain`
- variables `SKILLCHAIN_*`
- servidor MCP actual

La eliminación de estos nombres debe realizarse en una fase funcional separada y cubierta por pruebas.

#### Documentos relacionados

- `docs/TRUST_MODEL.md`
- `docs/THREAT_MODEL.md`
- `docs/PROTOCOL_MODEL.md`
- `ROADMAP.md`
