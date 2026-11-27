# Registro de seguridad · Sistema Alumnos

Estudiante: ANTONIA FAUNDES   Repositorio: https://github.com/Atto9752/Parcial_3_Ciberseguridad   Fecha: 27-11-26

Completa este registro a medida que avanzas. Cada fila debe poder seguirse hasta un **build de Jenkins**
y un **commit** (usa el identificador `VULN-xx` en el mensaje del commit).

## 1. Revisiones de seguridad realizadas

| # | Etapa del SDLC | Herramienta / técnica | Build | Resultado (resumen) |
|---|---|---|---|---|
| R1 | Código (SAST) | Bandit en el pipeline | #__ | __ hallazgos High / __ Medium / __ Low |
| R2 | Dependencias (SCA) | pip-audit en el pipeline | #__ | __ vulnerabilidades en __ paquetes |
| R3 | Pruebas dinámicas (DAST) | OWASP ZAP sobre staging | #__ | __ High / __ Medium / __ Low |
| R4 | Revisión manual | Lectura de `app.py` | — | |
| R5 | Producción | Grafana + Prometheus | — | |

## 2. Vulnerabilidades identificadas y corregidas

| ID | Vulnerabilidad (CWE) | Detectada por | Ubicación | Riesgo | Corrección aplicada | Commit | Build que lo verifica |
|---|---|---|---|---|---|---|---|
| VULN-01 | | | `app.py:__` | | | | #__ |
| VULN-02 | | | | | | | |
| VULN-03 | | | | | | | |

(Agrega las filas que necesites.)

## 3. Resultados de OWASP ZAP

| Alerta de ZAP | Riesgo | URL de ejemplo | VULN relacionada | Cómo se mitiga | ¿Mitigada? Build |
|---|---|---|---|---|---|
| | | | | | |

## 4. Monitoreo e incidentes

| Hora | Panel / métrica de Grafana | Qué se observó | Entorno | Clasificación | Acción de respuesta | Verificación |
|---|---|---|---|---|---|---|
| | | | | | | |

## 5. Gestión de dependencias

| Paquete | Versión inicial | Vulnerabilidades (IDs) | Versión final | Origen del cambio (PR de Dependabot / manual) | ¿Pruebas, pip-audit y ZAP siguen OK? Build |
|---|---|---|---|---|---|
| Flask | 2.2.2 | | | | |
| Werkzeug | 2.2.2 | | | | |
| Jinja2 | 3.1.2 | | | | |
| gunicorn | 21.2.0 | | | | |
| prometheus-client | 0.17.1 | | | | |

## 6. Trazabilidad


| Build | Fecha (UTC) | Versión | Commit | Mensaje del commit | Pruebas | Bandit H/M/L | pip-audit | ZAP H/M/L | Resultado | Producción |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2026-11-27 21:08 | 1.0.1+980b626 | `980b626` | Add files via upload | 9/9 OK | n/a | n/a | n/a | SUCCESS | 1.0.1+980b626 |
| 2 | 2026-11-27 21:19 | 1.0.2+63f48ce | `63f48ce` | integraciones | 9/9 OK | 2/2/0 | 19 vuln. | 3/3/1 | UNSTABLE | no desplegado |
| 3 | 2026-11-27 21:19 | 1.0.3+63f48ce | `63f48ce` | integraciones | 9/9 OK | 2/2/0 | 19 vuln. | 3/3/1 | UNSTABLE | no desplegado |
| 4 | 2026-11-27 22:30 | 1.0.4+45a6984 | `45a6984` | Vuln6 | 9/9 OK | 0/1/0 | 19 vuln. | 0/0/0 | UNSTABLE | no desplegado |
| 5 | 2026-11-27 22:37 | 1.0.5+45a6984 | `45a6984` | Vuln6 | 9/9 OK | 0/1/0 | 19 vuln. | 0/0/0 | UNSTABLE | no desplegado |
| 6 | 2026-11-27 22:39 | 1.0.6+45a6984 | `45a6984` | Vuln6 | 9/9 OK | 0/1/0 | 19 vuln. | 0/0/0 | UNSTABLE | no desplegado |
| 7 | 2026-11-27 22:48 | 1.0.7+681b037 | `681b037` | Pequeña correccion Vuln2 | 9/9 OK | 0/0/0 | 19 vuln. | 0/0/0 | UNSTABLE | no desplegado |
| 8 | 2026-11-27 23:42 | 1.0.8+e5308a7 | `e5308a7` | Actualizacion dependencias | 9/9 OK | 0/0/0 | 0 vuln. | 0/0/0 | SUCCESS | 1.0.8+e5308a7 |


| Actividad | Hallazgo | Build que lo detectó | Commit / PR que lo resolvió | Build que lo verificó | Versión en producción |
|---|---|---|---|---|---|
| Revisión de seguridad (Bandit) | SQL Injection (CWE-89) / MD5 (CWE-327) / debug=True | #1 | | Vuln2, Vuln3 y Vuln6 | #8|
| Prueba automatizada (OWASP ZAP) | XSS en /hello, SQLi, falta de Anti-CSRF y cabeceras CSP | #1 | | Vuln1,Vuln2, Vuln4 y Vuln5   | #8|
| Gestión de dependencias (Dependabot) | Vulnerabilidades en Flask, Werkzeug, Jinja2 y gunicorn | #1| PR de dependabot| #__ | #8|

