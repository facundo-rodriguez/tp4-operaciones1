TP04 Redes y YAML

Entregables

1. YAML multi-entorno (config/app-config.yml)

Configuración completa para dev / staging / producción con:

Parámetros de servidor, base de datos y caché por entorno

Configuración de monitoreo y logging compartida

Registro de scripts con sus schedules cron

Validar:
Ejecutar en bash:
python3 -c "import yaml; yaml.safe_load(open('config/app-config.yml'))"

2. Diagnóstico de red (scripts/diagnostico-red.sh)

Script que genera un reporte completo de conectividad:

Check

Comando usado

Interfaces activas

ip addr show

Tabla de rutas

ip route show

DNS configurado

/etc/resolv.conf

Ping a hosts

ping -c 2 -W 3

Resolución DNS

dig +short

Servicios HTTP

curl -o /dev/null -s -w "%{http_code}"

Puertos locales

ss -tlnp

Uso:
bash scripts/diagnostico-red.sh "google.com github.com 8.8.8.8"

Los reportes se guardan en reports/red_FECHA.txt.

Conceptos aprendidos

YAML: Indentación con 2 espacios, tipos de datos (string, int, bool, lista, mapa), strings con caracteres especiales entre comillas, variables de entorno con ${VAR}.

Redes: ping mide alcanzabilidad y latencia, traceroute muestra la ruta, dig/nslookup resuelven DNS, curl verifica servicios HTTP, ss lista puertos abiertos.