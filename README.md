# TP04 — Redes y YAML

[cite_start]Este repositorio contiene los entregables correspondientes al Trabajo Práctico 04, enfocado en la gestión de configuraciones mediante YAML y el diagnóstico de conectividad de red[cite: 1, 2].

## Entregables

### 1. YAML multi-entorno (`config/app-config.yml`)
[cite_start]Configuración completa para entornos de **development**, **staging** y **production**[cite: 5, 12]:
* [cite_start]**Parámetros:** Configuración de servidor, base de datos y caché por entorno[cite: 37, 43, 75].
* [cite_start]**Monitoreo y Logging:** Configuración compartida de Prometheus, Healthchecks y logs en formato JSON[cite: 96, 101, 104].
* [cite_start]**Schedules:** Registro de scripts con sus respectivos horarios cron[cite: 122, 130].

**Validar con Python:**
[cite_start]`python3 -c "import yaml; yaml.safe_load(open('config/app-config.yml'))"` [cite: 375]

---

### 2. Diagnóstico de red (`scripts/diagnostico-red.sh`)
[cite_start]Script de Bash que automatiza el diagnóstico de conectividad y genera un reporte en la carpeta `reports/`[cite: 6, 202].

| Check | Comando usado |
| :--- | :--- |
| **Interfaces activas** | [cite_start]`ip addr show` [cite: 380] |
| **Tabla de rutas** | [cite_start]`ip route show` [cite: 382] |
| **DNS configurado** | [cite_start]`/etc/resolv.conf` [cite: 383] |
| **Ping a hosts** | [cite_start]`ping -c 2 -W 3` [cite: 385] |
| **Resolución DNS** | [cite_start]`dig +short` [cite: 387] |
| **Servicios HTTP** | [cite_start]`curl -o /dev/null -s -w "%{http_code}"` [cite: 389] |
| **Puertos locales** | [cite_start]`ss -tlnp` [cite: 390] |

**Uso:**
[cite_start]`bash scripts/diagnostico-red.sh "google.com github.com 8.8.8.8"` [cite: 392]

---

### 3. Verificación de Configuración (`scripts/verificar-config.sh`)
[cite_start]Script que procesa el YAML redactado y verifica que los datos de los entornos sean legibles y que los hosts sean alcanzables[cite: 333, 335].

## Conceptos Aprendidos
* [cite_start]**YAML:** Importancia de la indentación (2 espacios), tipos de datos y uso de variables de entorno `${VAR}`[cite: 395].
* [cite_start]**Redes:** Uso de herramientas clave para diagnosticar si un problema es de red, DNS, firewall o de la aplicación[cite: 396].