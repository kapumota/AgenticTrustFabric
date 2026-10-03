### Modelo de protocolos

AgenticTrustFabric debe tratar los protocolos como mecanismos de interoperabilidad y no como fronteras de confianza.

#### Objetivo

El mismo núcleo de policy debe poder evaluar operaciones originadas en protocolos diferentes.

#### Adaptador MCP

MCP se utiliza actualmente para exponer tools, resources y prompts.

El adaptador MCP futuro debe convertir cada operación relevante en un evento canónico antes de autorizar su ejecución.

#### Adaptador A2A

A2A se incorpora al diseño para representar colaboración y delegación entre agentes.

Su primera implementación debe limitarse a:

- descubrimiento controlado
- recepción de tareas
- envio de tareas
- identificación del agente remoto
- propagación de contexto de seguridad
- trazabilidad de delegación

No se debe permitir delegación transitiva sin policy explícita.

#### Contrato común

Cada adaptador debe producir un objeto equivalente a:

```text
protocol
actor
peer
operation
resource
capability
delegation
provenance
evidence
```

#### Reglas

##### Ningún protocolo implica confianza

El uso de MCP o A2A no autentica por sí solo a un actor.

##### La autorización pertenece al núcleo

Los adaptadores no deben contener decisiones de negocio que puedan expresarse mediante policy común.

##### La evidencia debe conservar procedencia

Una operación traducida entre protocolos no debe perder información de origen.

##### La delegación debe ser explícita

Cada salto entre agentes debe poder representarse y auditarse.

#### Protocolos futuros

Un protocolo nuevo puede incorporarse cuando pueda traducirse al contrato canónico sin modificar las reglas centrales.

No se debe agregar soporte por tendencia o popularidad. Cada adaptador necesita un caso de uso, threat model, pruebas y evidencia.
