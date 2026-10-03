### Política de seguridad

AgenticTrustFabric documenta su modelo de seguridad y sus límites de confianza de forma explícita.

#### Reporte responsable

No se deben publicar vulnerabilidades sensibles mediante issues públicos.

Un reporte privado debe incluir, cuando corresponda:

- versión o commit afectado
- pasos mínimos de reproducción
- impacto esperado
- precondiciones necesarias
- evidencia no sensible
- propuesta de mitigación si existe

#### Alcance actual

La implementación actual cubre:

- Skill Scanner
- MCP Auditor
- Policy Engine
- Evidence Pack
- benchmark adversarial
- RBAC
- sandbox
- ejecución controlada de tools MCP
- validación de evidencia DevSecOps

#### Alcance futuro

La arquitectura contempla incorporar controles para:

- identidad de agentes
- delegación entre agentes
- A2A
- provenance entre protocolos
- cadenas de confianza
- trazabilidad distribuida
- policy enforcement neutral respecto al protocolo

Estas capacidades no deben considerarse implementadas hasta disponer de código, pruebas y evidencia reproducible.

#### Límites

El modo `demo-local` no certifica seguridad real.

Los modos `ci` y `strict` requieren scanners reales y evidencia verificable. Un workflow diagnóstico que finaliza correctamente no equivale a un release gate superado.

#### Documentos relacionados

- `docs/SEGURIDAD.md`
- `docs/TRUST_MODEL.md`
- `docs/THREAT_MODEL.md`
- `docs/PROTOCOL_MODEL.md`
