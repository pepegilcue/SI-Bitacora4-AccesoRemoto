# Memoria Técnica SI
## Infraestructura de Acceso Remoto Centralizado mediante Docker y Apache Guacamole

**Autor:** [Pepe Gil Cué]
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

La empresa objeto de este proyecto, dedicada al desarrollo de software multiplataforma, requería que su equipo técnico pudiese acceder de forma remota a los servidores de desarrollo y bases de datos ubicados en el centro de datos privado. El acceso como antes he explicado se realiza de manera directa mediante los protocolos RDP y SSH, lo cual obligaba a mantener abiertos múltiples.

Esto presenta una serie de problemas de naturaleza técnica, operativa y de seguridad que comprometían la viabilidad del entorno a largo plazo. En primer lugar, la superficie de ataque del sistema era excesivamente grande, cada puerto abierto representa una entrada accesible.

### 1.2. Solución Propuesta: Infraestructura Híbrida Docker-Guacamole

Tras analizar los requerimientos de accesibilidad, seguridad y escalabilidad, se ha optado por implementar una infraestructura basada en Apache Guacamole desplegada mediante Docker Compose.

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

Véase el archivo LICENSES.md en la raíz del repositorio, donde se recoge la clasificación completa del software utilizado según su licencia y propósito, en cumplimiento del criterio de evaluación CE a.


## 3. Arquitectura del Sistema



## 4. Proceso de Despliegue



## 5. Conclusiones

