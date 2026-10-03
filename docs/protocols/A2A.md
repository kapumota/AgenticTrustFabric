### Adaptador A2A

A2A se incorpora como protocolo planificado para comunicación y delegación entre agentes.

No existe todavia implementación funcional A2A en AgenticTrustFabric.

#### Objetivo inicial

La primera fase A2A debe demostrar una interacción mínima entre dos agentes con:

- identidad conocida
- tarea identificable
- policy antes de aceptar la tarea
- propagación de provenance
- evidence record
- límite de delegación

#### Operaciones de seguridad

Cada tarea A2A debe poder asociarse con:

```text
agent_id
peer_agent_id
task_id
operation
requested_capability
delegation_depth
parent_task
provenance
policy_decision
```

#### Riesgos prioritarios

Las primeras pruebas deben cubrir:

- agente desconocido
- capability no autorizada
- delegación transitiva
- tarea manipulada
- provenance incompleto
- replay
- cross protocol injection hacia MCP

#### Integración con MCP

Un flujo A2A puede terminar solicitando una tool MCP.

La decisión de autorizar la tool debe considerar el origen A2A y la cadena de delegación.

El contexto de seguridad no debe reiniciarse al cambiar de protocolo.

#### Criterio de terminado

A2A no se considera soportado hasta disponer de:

- adapter implementado
- pruebas unitarias
- pruebas de integración
- policy rules
- threat cases
- evidencia reproducible
- documentación de compatibilidad
