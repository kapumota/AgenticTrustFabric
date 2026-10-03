### ADR 0003. A2A como adaptador

#### Estado

Propuesto.

#### Contexto

AgenticTrustFabric necesita modelar interacciones entre agentes sin convertir la seguridad en una dependencia de A2A.

#### Decisión

A2A se implementará como un adaptador sobre el mismo núcleo de policy.

La primera versión no permitira delegación transitiva sin una regla explícita.

#### Consecuencias

La implementación A2A requiere:

- identidad de peer
- modelo de tareas
- contexto de delegación
- provenance
- policy enforcement
- pruebas de integración
- threat cases propios
