# TP04 — Redes y YAML

Este repositorio contiene los entregables correspondientes al Trabajo Práctico 04, enfocado en la gestión de configuraciones mediante YAML y el diagnóstico de conectividad de red.

## Entregables

### 1. YAML multi-entorno (`config/app-config.yml`)
Configuración completa para entornos de **development**, **staging** y **production**:
* **Parámetros:** Configuración de servidor, base de datos y caché por entorno.
* **Monitoreo y Logging:** Configuración compartida de Prometheus, Healthchecks y logs en formato JSON.
* **Schedules:** Registro de scripts con sus respectivos horarios cron.

**Validar con Python:**
`python3 -c "import yaml; yaml.safe_load(open('config/app-config.yml'))"`

---

### 2. Diagnóstico de red (`scripts/diagnostico-red.sh`)
Script de Bash que automatiza el diagnóstico de conectividad y genera un reporte en la carpeta `reports/`.

| Check | Comando usado |
| :--- | :--- |
| **Interfaces activas** | `ip addr show` |
| **Tabla de rutas** | `ip route show` |
| **DNS configurado** | `/etc/resolv.conf` |
| **Ping a hosts** | `ping -c 2 -W 3` |
| **Resolución DNS** | `dig +short` |
| **Servicios HTTP** | `curl -o /dev/null -s -w "%{http_code}"` |
| **Puertos locales** | `ss -tlnp` |

**Uso:**
`bash scripts/diagnostico-red.sh "google.com github.com 8.8.8.8"`

---

### 3. Verificación de Configuración (`scripts/verificar-config.sh`)
Script que procesa el YAML redactado y verifica que los datos de los entornos sean legibles y que los hosts sean alcanzables mediante la integración de Python en Bash.

## Conceptos Aprendidos
* **YAML:** Importancia de la indentación (2 espacios), tipos de datos y uso de variables de entorno `${VAR}`.
* **Redes:** Uso de herramientas clave para diagnosticar si un problema es de red, DNS, firewall o de la aplicación.