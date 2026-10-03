### AgenticTrustFabric

AgenticTrustFabric es una plataforma de seguridad y confianza para sistemas agénticos. El proyecto busca aplicar políticas, control de privilegios, aislamiento, trazabilidad y evidencia verificable sobre interacciones entre agentes, herramientas y servicios.

La implementación actual se concentra en MCP, auditoría de skills, policy gates, RBAC, sandbox, evaluación adversarial y evidencia DevSecOps. La arquitectura futura separa el núcleo de confianza de los protocolos concretos para permitir adaptadores MCP, A2A y otros protocolos sin acoplar las políticas de seguridad a una sola tecnología.

#### Estado actual

Actualmente están implementadas las siguientes capacidades:

- auditoría de archivos `skills/*/SKILL.md`
- auditoría de tools, resources y prompts MCP
- policy gate con modos `demo`, `ci` y `strict`
- benchmark adversarial controlado
- evidence pack verificable
- RBAC para operaciones expuestas mediante MCP
- sandbox local y Docker
- dashboard de estado
- integración con scanners DevSecOps
- hardening inicial para Docker Compose y Kubernetes

A2A y otros adaptadores aún no forman parte del código funcional. Se documentan como evolución planificada.

#### Principio arquitectónico

AgenticTrustFabric se organiza alrededor de un núcleo neutral respecto al protocolo.

```text
Agentic system
     |
Protocol adapter
     |
Canonical security event
     |
Policy and trust core
     |
Policy decision and evidence
     |
Controlled execution
```

MCP se considera un adaptador para interacciones entre agentes, herramientas y recursos. A2A se considera un adaptador futuro para interacciones entre agentes.

La política de seguridad, la evidencia, la identidad y la trazabilidad no deben depender directamente del protocolo de transporte.

#### Compatibilidad heredada

El repositorio fue renombrado a `AgenticTrustFabric`, pero algunos identificadores internos conservan temporalmente la identidad anterior.

Entre ellos se encuentran:

- paquete Python `skillchain-mcp-guard`
- comando `skillchain`
- módulo `devsecops_agent`
- variables de entorno con prefijo `SKILLCHAIN_`
- nombre interno del servidor MCP `skillchain-mcp-guard`

Estos identificadores no se modifican en la fase documental para evitar mezclar cambios de arquitectura con cambios funcionales. Su migración se realizará después de estabilizar contratos, pruebas y compatibilidad.

#### Perfiles de ejecución

| Perfil | Comando | Función |
|---|---|---|
| Demo | `make demo-local` | Demostración reproducible, puede terminar en `WARN` |
| Diagnóstico CI | Workflow `ci-devsecops.yml` | Ejecuta controles informativos y no debe interpretarse como release gate |
| Security CI | `make security-ci` | Ejecuta scanners reales, policy gate y evidencia |
| Release | `make release-verify` | Exige evidencia válida y no acepta fallback |

#### Separación de estados

Un resultado exitoso del workflow diagnóstico no significa que el repositorio haya superado un release gate.

Se mantienen cuatro niveles conceptuales:

```text
Level 0  demo
Level 1  diagnostic
Level 2  security-ci
Level 3  release
```

Solo los niveles de seguridad y release deben poder declarar evidencia operacional verificada.

#### Comandos actuales

```bash
python -m pytest -q
make demo-local
skillchain policy-check --mode demo --json
skillchain benchmark run --suite eval_cases --output artifacts/benchmark-report.json --json
skillchain evidence verify artifacts/evidence-pack-*.tar.gz --manifest artifacts/evidence-manifest.json
```

Estos comandos conservan nombres heredados hasta la fase de migración interna.

#### Modelo de seguridad

La ejecución controlada se apoya actualmente en:

1. allowlist de targets Makefile
2. RBAC definido en `config/rbac.json`
3. sandbox seleccionado por configuración
4. timeout de operaciones
5. logs limitados para clientes
6. policy gates
7. evidencia ligada a una ejecución concreta

El objetivo futuro es extender este modelo a identidad de agentes, delegación, provenance y cadenas de confianza entre protocolos.

#### Benchmark

El benchmark de `eval_cases/cases.yaml` sirve para detectar regresiones sobre un dataset controlado. Sus métricas no representan certificación de seguridad, pentest exhaustivo ni cobertura completa de ataques reales.

La evolución experimental se documenta en `docs/THREAT_MODEL.md` y `ROADMAP.md`.

#### Documentación principal

- `docs/ARCHITECTURE.md`
- `docs/TRUST_MODEL.md`
- `docs/THREAT_MODEL.md`
- `docs/PROTOCOL_MODEL.md`
- `docs/protocols/MCP.md`
- `docs/protocols/MCP_COMPATIBILITY.md`
- `docs/protocols/A2A.md`
- `docs/SEGURIDAD.md`
- `docs/BENCHMARK.md`
- `docs/RBAC_SANDBOX.md`
- `docs/KUBERNETES.md`
- `ROADMAP.md`
- `SECURITY.md`

#### Regla para la siguiente fase

No se debe introducir A2A, migrar el SDK MCP ni renombrar paquetes internos hasta que el modelo neutral de protocolo y los contratos de seguridad esten definidos y revisados.
