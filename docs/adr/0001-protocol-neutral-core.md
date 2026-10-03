### ADR 0001. Núcleo neutral respecto al protocolo

#### Estado

Propuesto.

#### Contexto

El proyecto nacio alrededor de MCP, pero su policy engine, evidencia, RBAC y sandbox representan conceptos que pueden aplicarse a otros protocolos.

Acoplar estas funciones directamente a MCP impediria extender el sistema de forma limpia.

#### Decisión

El núcleo de AgenticTrustFabric será neutral respecto al protocolo.

MCP, A2A y futuros protocolos se implementarán como adaptadores.

#### Consecuencias

El refactor futuro debe:

- introducir contratos propios
- aislar tipos del SDK MCP
- evitar decisiones duplicadas en adaptadores
- mantener pruebas de compatibilidad
- conservar comportamiento existente durante la migración
