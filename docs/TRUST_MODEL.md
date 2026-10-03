### Modelo de confianza

AgenticTrustFabric no debe asumir que un agente, cliente, tool, servidor o artifact es confiable por el simple hecho de participar en el sistema.

#### Principios

##### Deny by default

Una operación sin autorización explícita debe ser rechazada.

##### Least privilege

Cada actor debe recibir solo las capabilities necesarias para su función.

##### Evidence before trust

La confianza operacional debe basarse en evidencia verificable y no solo en declaraciones del agente o del cliente.

##### Protocol independence

La confianza no debe derivarse del protocolo utilizado.

Un mensaje MCP o A2A puede transportar una operación legitima o maliciosa.

##### Delegation is not authority

Un agente que recibe una tarea delegada no hereda automaticamente todos los privilegios del agente que origino la solicitud.

#### Actores

El modelo considera inicialmente:

- usuario
- agente
- agente remoto
- cliente MCP
- servidor MCP
- tool
- runtime
- pipeline CI
- scanner de seguridad
- mantenedor

#### Objetos protegidos

Los objetos protegidos incluyen:

- código
- artifacts
- evidence packs
- credenciales
- configuración
- tools
- recursos MCP
- tareas A2A futuras
- resultados de agentes
- decisiones de política

#### Niveles de evidencia

##### Evidence observed

Existe un resultado, pero su procedencia o integridad no ha sido verificada completamente.

##### Evidence verified

La evidencia tiene procedencia conocida, identificador de ejecución, integridad consistente y corresponde al contexto evaluado.

##### Evidence rejected

La evidencia es fallback no permitido, está obsoleta, tiene hashes inconsistentes o no puede vincularse con la ejecución evaluada.

#### Límite de confianza

El sistema no debe confiar en datos enviados por un cliente para seleccionar su propio rol efectivo.

Este principio ya se aplica al rol MCP actual y debe extenderse a futuros protocolos.
