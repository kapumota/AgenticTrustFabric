### Compatibilidad MCP

Este documento separa el estado actual de la evolución planificada.

#### Dependencia actual

El repositorio utiliza actualmente:

```text
mcp[cli]>=1.10.1,<2.0
```

El servidor importa `FastMCP` desde el SDK actual del proyecto.

#### Objetivo

La migración a una generación moderna del SDK MCP debe realizarse después de estabilizar el modelo neutral de protocolo.

No se debe mezclar la migración del SDK con la incorporación inicial de A2A.

#### Requisitos para migrar

Antes de cambiar la dependencia MCP deben existir:

- pruebas de contrato del adaptador actual
- pruebas de autorización
- pruebas de resources y tools
- pruebas de rechazo
- pruebas de policy gate
- compatibilidad documentada
- estrategia de rollback

#### Regla de versionado

La versión de protocolo soportada y la versión del SDK deben declararse de forma separada.

El repositorio no debe afirmar compatibilidad con una revisión que no haya sido ejecutada en CI.
