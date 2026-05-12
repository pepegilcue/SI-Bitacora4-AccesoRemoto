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

Primero se creó una carpeta para almacenar el proyecto y dentro de ella se guardó el archivo `docker-compose.yml`. Ejectute el comando y su instalacion autamtica de los paquetes e imagenes.

## Descripcion del primer problema

Al intentar conectarme por SSH a la maquina virtual con el comando:

```
ssh pepegil@localhost -p 2222
```
El sistema mostro el siguiente error:

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Host key verification failed.
```
Cuando nos conectamos por SSH a una maquina por primera vez, nuestro ordenador guarda una "firma digital" de esa maquina en un fichero llamado `known_hosts`, que se encuentra en:

```
C:\Users\DAW1\.ssh\known_hosts
```

Esta firma sirve para que la proxima vez que nos conectemos, el sistema pueda verificar que la maquina a la que nos conectamos es la misma de siempre y no hay nadie interceptando la conexion.

El problema ocurrio porque la firma que tenia guardada en `known_hosts` ya no coincide con la firma actual de la maquina virtual. Esto puede pasar por varias razones:

- La maquina virtual fue reinstalada o recreada desde cero
- Se reconfiguro el servicio SSH de la maquina virtual
- Se cambio algun parametro de red o de la maquina virtual

## Solucion aplicada

Para solucionar el problema ejecute el siguiente comando en PowerShell, que elimina la entrada antigua del fichero `known_hosts`:

``` en powershell
ssh-keygen -R "[localhost]:2222"
```

Este comando borra especificamente la firma guardada para `localhost` en el puerto `2222`, sin tocar el resto de entradas del fichero.

Despues volvi a conectarme con normalidad:

```powershell
ssh pepegil@localhost -p 2222
```

El sistema pregunto si confiaba en la nueva firma de la maquina:

```
Are you sure you want to continue connecting (yes/no)? yes
```

Tras responder `yes`, la conexion se establecio correctamente y el sistema guardo la nueva firma en `known_hosts` para futuras conexiones. 

Posteriormente se ejecutó el siguiente comando:

```bash
docker-compose up -d
