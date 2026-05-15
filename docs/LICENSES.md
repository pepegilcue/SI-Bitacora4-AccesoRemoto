# LICENSES.md
## Identificación de Licencias del Software de Infraestructura

Este documento recoge las licencias de cada componente de software utilizado en la infraestructura desplegada en el proyecto. Su elaboración responde al criterio de evaluación CE a, que exige clasificar el software en función de su licencia y propósito.

## 1. Apache Guacamole

**Propósito:** Puerta de enlace de escritorio remoto ACCEDE a sesiones RDP/SSH/ VNC.

**Licencia:** Apache License 2.0

**Tipo:** Software libre y de código abierto (FOSS). Licencia permisiva que permite el uso, modificación y distribución del software, incluso en entornos comerciales, siempre que se incluya el aviso de copyright original.

**Fuente oficial:** https://guacamole.apache.org/doc/gug/introduction.html

## 2. OpenSSH

**Propósito:** Servidor SSH para acceso remoto seguro por terminal.

**Licencia:** Licencia BSD modificada (OpenBSD License)

**Tipo:** Software libre y de código abierto (FOSS). Licencia permisiva similar a la MIT. Permite el uso, copia, modificación y distribución con o sin modificaciones, tanto en proyectos libres como propietarios.

**Fuente oficial:** https://www.openssh.com/portable.html

## 3. Docker / Docker Engine

**Propósito:** Plataforma de contenedores que permite empaquetar aplicaciones en contenedores aislados. En este proyecto se usa mediante Docker Compose para orquestar los servicios de Guacamole.

**Licencia:** Apache License 2.0 (Docker Engine y Docker CLI son de código abierto bajo esta licencia)

**Tipo:** Software libre en su componente Engine/CLI. Licencia permisiva que permite uso comercial y redistribución.

**Fuente oficial:** https://docs.docker.com/engine/

## 4. PostgreSQL

**Propósito:** Sistema gestor de bases de datos relacional. Apache Guacamole lo utiliza como backend para almacenar usuarios y conexiones.

**Licencia:** PostgreSQL License

**Tipo:** Software libre y de código abierto. No impone restricciones sobre el uso comercial ni sobre la redistribución del software modificado o copiado.

**Fuente oficial:** https://www.postgresql.org/about/licence/

## 5. Clasificación resumen

| Software | Licencia | Tipo | Uso comercial permitido |
|-------------------|-----------------------|---------------|------------------------|
| Apache Guacamole | Apache 2.0 | FOSS permisiva | Sí |
| OpenSSH | BSD modificada | FOSS permisiva | Sí |
| Docker Engine | Apache 2.0 | FOSS permisiva | Sí |
| PostgreSQL | PostgreSQL License | FOSS permisiva | Sí |