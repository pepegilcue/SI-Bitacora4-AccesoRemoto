# Bitácora Técnica 4 - Administración Remota Segura con SSH y RDP

## 1. Objetivo de la práctica

En esta práctica se ha trabajado la administración remota de sistemas utilizando distintos métodos de acceso seguro a servidores Linux mediante contenedores Docker.

El propósito principal ha sido aprender a conectarnos a servidores sin necesidad de acceso físico, aplicando medidas básicas de seguridad y comprendiendo cómo funcionan los servicios de red asociados a cada protocolo.

### Resultado de aprendizaje
**RA6 - Operar sistemas en red gestionando recursos e identificando restricciones de seguridad.**

### Criterios evaluados
- Acceso remoto a servidores mediante SSH y RDP.
- Protección básica del sistema y control de accesos.
- Uso de herramientas y utilidades de seguridad.


# 2. Entorno utilizado

Para realizar la práctica se ha utilizado una infraestructura basada en Docker Compose en lugar de máquinas virtuales tradicionales.

## ¿Por qué Docker?

Después de probar diferentes métodos, Docker ha resultado mucho más práctico porque:

- Los servicios arrancan en pocos segundos.
- El consumo de recursos es mucho menor.
- Todos los equipos de clase trabajan exactamente con la misma configuración.
- Facilita el aislamiento de red y la gestión de puertos.
- Evita errores frecuentes de virtualización y compatibilidad.


# 3. Despliegue del laboratorio

## Creación del entorno

Primero se creó una carpeta para almacenar el proyecto y dentro de ella se guardó el archivo `docker-compose.yml`.

Posteriormente se ejecutó el siguiente comando:

```bash
docker-compose up -d
