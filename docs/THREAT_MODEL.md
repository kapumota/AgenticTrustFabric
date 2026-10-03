### Threat model

Este documento define amenazas relevantes para la evolución de AgenticTrustFabric.

No representa una taxonomia exhaustiva.

#### Activos

Los principales activos son:

- integridad del código
- integridad de artifacts
- evidencia de seguridad
- credenciales
- configuración de policy
- capabilities de tools
- identidad de actores
- cadena de delegación
- resultados de evaluación

#### Superficies actuales

La implementación actual expone superficies relacionadas con:

- skills
- tools MCP
- resources MCP
- prompts MCP
- Makefile targets
- artifacts
- evidence packs
- CI
- Docker
- Kubernetes

#### Amenazas actuales

##### Prompt injection

Una entrada intenta modificar el comportamiento esperado del agente o de una tool.

##### Tool poisoning

Una tool o su metadata induce al agente a ejecutar una acción diferente de la esperada.

##### Path traversal

Una entrada intenta acceder a rutas fuera del espacio autorizado.

##### Evidence tampering

Un actor modifica evidencia, manifests o hashes para aparentar un estado de seguridad distinto.

##### Privilege escalation

Una llamada intenta obtener permisos superiores a los asociados con el rol efectivo.

##### Sandbox escape

Una operación intenta superar los límites establecidos por el entorno de ejecución.

#### Amenazas futuras con A2A

##### Delegation confusion

Un agente receptor interpreta una tarea delegada como si incluyera autoridad que no fue concedida.

##### Confused deputy

Un agente con privilegios ejecuta una acción para otro agente que no posee esos privilegios.

##### Capability escalation across agents

Una cadena de agentes acumula o transfiere capabilities de forma no autorizada.

##### Provenance laundering

Una respuesta atraviesa varios agentes y pierde información sobre su origen real.

##### Cross protocol injection

Contenido recibido mediante A2A induce posteriormente una llamada MCP peligrosa.

##### Delegation loop

Una tarea se delega repetidamente y produce consumo no controlado de recursos o pérdida de trazabilidad.

#### Amenazas de supply chain

Se consideran relevantes:

- dependencia comprometida
- imagen vulnerable
- paquete sustituido
- action de CI comprometida
- SBOM incompleto
- artifact manipulado

#### Fuera de alcance actual

Todavia no existe evidencia para afirmar protección completa frente a:

- agentes remotos hostiles
- A2A real
- identity federation
- ataques distribuidos multiagente
- aislamiento fuerte de nivel kernel
- compromise de la plataforma de CI

Estas áreas pertenecen a fases futuras.
