### ADR 0002. MCP como adaptador

#### Estado

Propuesto.

#### Contexto

La implementación actual contiene servidor, auditor y controles MCP integrados con componentes generales de seguridad.

#### Decisión

MCP se conservará como primer adaptador operativo de AgenticTrustFabric.

El comportamiento actual se usará como baseline durante el refactor.

#### Consecuencias

Antes de migrar el SDK MCP se deben crear pruebas de contrato que cubran tools, resources, autorización, errores y evidencia.
