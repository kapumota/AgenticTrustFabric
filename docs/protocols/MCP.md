### Adaptador MCP

MCP es el protocolo actualmente integrado en AgenticTrustFabric.

#### Estado

La implementación existente incluye:

- servidor MCP
- resources
- tools
- prompt de triage
- auditor MCP
- RBAC
- ejecución controlada
- sandbox

#### Responsabilidad futura del adaptador

El adaptador MCP debe encargarse de:

1. recibir una operación MCP
2. extraer identidad y contexto disponibles
3. construir un evento canónico
4. solicitar una decisión al núcleo de policy
5. ejecutar solo cuando la decisión lo permita
6. registrar evidencia

#### Restricción

El cliente no debe poder seleccionar directamente su rol efectivo.

Esta regla ya forma parte del comportamiento actual y debe conservarse durante la migración.

#### Separación

El código específico de MCP debe quedar fuera del núcleo neutral.

La migración debe evitar que modelos internos dependan de tipos concretos del SDK MCP.
