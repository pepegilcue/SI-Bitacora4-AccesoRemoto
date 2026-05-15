# Memoria Técnica SI
## Infraestructura de Acceso Remoto Centralizado mediante Docker y Apache Guacamole

**Autor:** Pepe Gil Cué
**Ciclo:** DAW — Sistemas Informáticos
**Fecha:** 15 de mayo de 2026

## Índice

1. Análisis de Necesidades
- 1.1. Contexto y Problemática Actual
- 1.2. Solución Propuesta: Infraestructura Híbrida Docker-Guacamole
- 1.3. Justificación Técnica y Beneficios (TCO)
2. Identificación de Licencias
3. Arquitectura del Sistema
4. Proceso de Despliegue
5. Conclusiones

## 1. Análisis de Necesidades

### 1.1. Contexto y Problemática Actual

La empresa objeto de este proyecto, dedicada al desarrollo de software, requería que su equipo técnico pudiese acceder de forma remota a los servidores de desarrollo y bases de datos ubicados en el centro de datos privado. El acceso como antes he explicado se realiza de manera directa mediante los protocolos RDP y SSH, lo cual obligaba a mantener abiertos múltiples.

Esto presenta una serie de problemas de naturaleza técnica y de seguridad que comprometían la viabilidad del entorno a largo plazo. En primer lugar, la superficie de ataque del sistema era excesivamente grande, cada puerto abierto representa una entrada accesible.

### 1.2. Solución Propuesta: Infraestructura Híbrida Docker-Guacamole

Tras analizar los requerimientos de accesibilidad y seguridad se opta por implementar una infraestructura basada en Apache Guacamole desplegada mediante Docker Compose.

Apache Guacamole es una pasarela de escritorio remoto sin cliente que actúa como punto de acceso único para los protocolos SSH, RDP y VNC. El usuario accede exclusivamente a través de un navegador web, sin necesidad de instalar ningún software adicional en su máquina.

La arquitectura desplegada mediante Docker Compose está compuesta por los varios servicios:

Guacamole: contenedor que ejecuta la aplicación web Java desplegada sobre Apache. Es la interfaz que ve el usuario final.

Guacd: el demonio de Guacamole, responsable de establecer las conexiones con los sistemas remotos. Actúa como intermediario entre la aplicación web y los servidores 

### 1.3. Justificación Técnica y Beneficios (TCO)

La elección de esta solución responde a la necesidad de optimizar el Coste Total. Al emplear exclusivamente software distribuido bajo licencias permisivas de código abierto.

Estos costes evitados pueden reinvertirse en la mejora de la seguridad de la infraestructura o en la formación del equipo técnico, incrementando así el valor generado al principio.

En definitiva, la infraestructura Docker-Guacamole supone una solución técnicamente sólida, económicamente y eficiente

Referencias:

Drake, J. M. (2008). Análisis de requisitos y especificación de una aplicación [en línea]. Disponible en: https://www.ctr.unican.es/asignaturas/ingenieria_software_4_f/doc/m3_08_especificacion-2011.pdf

García Notario, D. (2015). Análisis de requisitos en el desarrollo del software [en línea]. Disponible en: https://e-archivo.uc3m.es/rest/api/core/bitstreams/a66b0a2d-fa7c-483f-ac5e-1476ff2da8eb/content


## 2. Identificación de Licencias

El archivo LICENSES.md en la raíz del repositorio, donde se recoge la clasificación completa del software utilizado según su licencia y propósito, en cumplimiento del criterio de evaluación CE a.

**Nota:** Los apartados 3, 4 y 5 de esta memoria no forman parte de los requisitos del Sprint 1. Se han añadido de forma voluntaria y fuera de plazo debido a que la actividad no me quedó completamente clara en un primer momento, por lo que decidí profundizar en el trabajo para comprender con mayor precision el funcionamiento completo del sistema desplegado. Al tratarse de un contenido extra, no solicito que sea tenido en cuenta para la calificación de la entrega.

## 3. Arquitectura del Sistema 
 
Los tres contenedores (guacamole, guacd y postgres) se comunican entre ellos por una red interna que crea Docker Compose automáticamente. Desde fuera solo se puede acceder al puerto de Guacamole, los demás están cerrados.
 
Guacamole habla con guacd para abrir las sesiones remotas y con PostgreSQL para comprobar el usuario y la contraseña. Guacd es el que se conecta de verdad a los servidores por SSH o RDP.
 
## 4. Proceso de Despliegue
 
El despliegue se hizo en un servidor Linux con Docker y Docker Compose. Los pasos que se siguieron fueron:
 
1. Instalar Docker y Docker Compose en el servidor.
2. Crear el docker-compose.yml con los tres servicios.
3. Poner las credenciales de la base de datos en las variables de entorno.
4. Ejecutar el script SQL de Guacamole para crear las tablas.
5. Levantar los contenedores con `docker compose up -d`.
6. Entrar al puerto 8080 desde el navegador y comprobar que el login funcionaba.
 
## 5. Conclusiones
 
Con este proyecto se ha montado un sistema de acceso remoto real usando solo software gratuito. Se ha visto cómo Docker hace mucho más fácil desplegar servicios y cómo Guacamole soluciona el problema de acceder a servidores sin tener que instalar nada en el ordenador.
 
También se ha entendido por qué es importante documentar bien: si no explicas lo que has hecho y por qué, el siguiente que llegue no va a entender nada.

