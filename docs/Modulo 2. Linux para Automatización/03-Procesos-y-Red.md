---
proyecto: AI Automation Journey
capitulo: 2.3
titulo: Linux para Automatización – Procesos y Red
tecnologia: Ubuntu Linux
nivel: Principiante
version: 1.0
---

# Capítulo 02.3 · Linux para Automatización – Procesos y Red

> Proyecto: **AI Automation Journey**

---

# Introducción

Además de administrar archivos y directorios, un administrador de sistemas debe comprender cómo Linux ejecuta procesos y cómo interactuar con servicios externos desde la terminal.

En este capítulo se aprenderá a identificar procesos en ejecución, monitorear el consumo de recursos del sistema, instalar herramientas mediante el gestor de paquetes de Ubuntu y consumir APIs utilizando **curl**. Estas habilidades serán esenciales para diagnosticar aplicaciones Docker, validar servicios HTTP y probar posteriormente los Webhooks de **n8n**.

---

# Objetivo

## Objetivo general

Comprender cómo Linux administra los procesos del sistema y aprender a utilizar herramientas básicas de red para instalar software y consumir APIs desde la terminal, habilidades fundamentales para administrar aplicaciones ejecutándose en Docker y n8n.

## Objetivos específicos

- Comprender qué es un proceso en Linux.
- Consultar procesos en ejecución.
- Interpretar información básica de un proceso.
- Monitorear procesos en tiempo real.
- Instalar herramientas utilizando el gestor de paquetes de Ubuntu.
- Consumir una API utilizando `curl`.
- Diagnosticar y solucionar errores relacionados con herramientas no instaladas.

---

# Conceptos principales

## Proceso

Un proceso corresponde a un programa que se encuentra en ejecución dentro del sistema operativo.

## PID (Process ID)

Identificador único asignado a cada proceso que se ejecuta en Linux.

## Gestor de paquetes

Herramienta utilizada para instalar, actualizar y administrar software desde los repositorios oficiales de Ubuntu.

## API

Interfaz que permite la comunicación entre aplicaciones mediante protocolos como HTTP.

## curl

Herramienta de línea de comandos utilizada para realizar peticiones HTTP y consumir APIs directamente desde la terminal.

---

# Desarrollo

## Administración de procesos

```text
             Linux

               │

      Ejecuta Procesos

               │

      ┌────────┴────────┐

      ▼                 ▼

   Proceso 1        Proceso 2

      │                 │

     PID               PID
```

Cada aplicación que se ejecuta en Linux corresponde a un proceso identificado mediante un **PID (Process ID)**.

---

## Consumo de APIs

```text
Contenedor Ubuntu

        │

      curl

        │

        ▼

https://httpbin.org/get

        │

        ▼

Respuesta JSON
```

Durante el laboratorio se consumió una API pública para comprender cómo interactuar con servicios HTTP directamente desde Linux.

---

# Configuración del laboratorio

| Elemento | Configuración |
|----------|---------------|
| Sistema operativo | Windows 11 |
| Plataforma | Docker Desktop |
| Backend | WSL2 |
| Entorno Linux | Ubuntu (Contenedor Docker) |
| Terminal | Bash |
| Contenedor utilizado | `laboratorio` |

---

# Comandos utilizados

## Consultar procesos

### `ps`

**Descripción**

Muestra los procesos asociados a la sesión actual.

Cada proceso posee un identificador único denominado **PID (Process ID)**.

```bash
ps
```

**Resultado esperado**

```text
PID    TTY     TIME    CMD
```

**Buenas prácticas**

- Utilizar `ps` para verificar rápidamente qué procesos se encuentran en ejecución.
- Es útil para validar si una aplicación continúa activa.

---

## Consultar todos los procesos

### `ps -ef`

**Descripción**

Muestra una lista detallada de los procesos del sistema.

Incluye información como:

- Usuario propietario.
- PID.
- PPID (Proceso padre).
- Hora de inicio.
- Comando ejecutado.

```bash
ps -ef
```

**Buenas prácticas**

- Utilizar este comando cuando se requiera mayor información para diagnosticar problemas.
- Permite localizar procesos específicos dentro del sistema.

---

## Monitorear procesos en tiempo real

### `top`

**Descripción**

Muestra información dinámica del sistema en tiempo real.

Permite observar:

- Procesos activos.
- Consumo de CPU.
- Consumo de memoria.
- Tiempo de ejecución.

```bash
top
```

**Resultado esperado**

Una pantalla que se actualiza continuamente mostrando el estado del sistema.

> Para salir del comando presione la tecla:

```text
q
```

**Buenas prácticas**

- Utilizar `top` para identificar procesos que consumen excesivos recursos.
- Es una de las herramientas más utilizadas para diagnosticar problemas de rendimiento.

---

## Actualizar el catálogo de paquetes

### `apt update`

**Descripción**

Actualiza el índice de paquetes disponibles desde los repositorios oficiales de Ubuntu.

```bash
apt update
```

**Buenas prácticas**

- Ejecutar este comando antes de instalar nuevas herramientas.
- Recordar que no instala software; únicamente actualiza la información disponible.

---

## Instalar una herramienta

### `apt install`

**Descripción**

Instala software desde los repositorios oficiales.

Durante el laboratorio se utilizó para instalar **curl**.

```bash
apt install curl -y
```

El parámetro `-y` acepta automáticamente la confirmación de instalación.

**Buenas prácticas**

- Ejecutar previamente `apt update`.
- Instalar únicamente las herramientas necesarias dentro de un contenedor.

---

## Consumir una API

### `curl`

**Descripción**

Realiza una petición HTTP y muestra la respuesta directamente en la terminal.

```bash
curl https://httpbin.org/get
```

**Resultado esperado**

```json
{
  "url": "https://httpbin.org/get"
}
```

**Buenas prácticas**

- Utilizar `curl` para validar APIs antes de asumir problemas de conectividad.
- Será una herramienta fundamental para probar Webhooks de n8n durante los siguientes módulos.

> **Relación con el proyecto**
>
> En los módulos de APIs y n8n se utilizará `curl` para probar endpoints, validar respuestas HTTP y ejecutar pruebas rápidas sin depender de herramientas gráficas como Postman.

---

# Laboratorio paso a paso

Durante el laboratorio se realizaron las siguientes actividades.

## Paso 1 · Consultar los procesos de la sesión

```bash
ps
```

---

## Paso 2 · Consultar todos los procesos

```bash
ps -ef
```

---

## Paso 3 · Monitorear el sistema

```bash
top
```

Salir del monitor utilizando:

```text
q
```

---

## Paso 4 · Actualizar el catálogo de paquetes

```bash
apt update
```

---

## Paso 5 · Instalar la herramienta curl

```bash
apt install curl -y
```

---

## Paso 6 · Consumir una API

```bash
curl https://httpbin.org/get
```

---

# Validaciones

Durante el laboratorio se verificó correctamente:

- La consulta de procesos mediante `ps`.
- La obtención de información ampliada utilizando `ps -ef`.
- El monitoreo del sistema mediante `top`.
- La actualización del catálogo de paquetes con `apt update`.
- La instalación de `curl`.
- El consumo exitoso de la API `https://httpbin.org/get`, obteniendo una respuesta en formato JSON.

---

# Evidencias

Durante esta práctica se obtuvieron evidencias relacionadas con:

- Resultado del comando `ps`.
- Resultado del comando `ps -ef`.
- Monitoreo del sistema mediante `top`.
- Error inicial al ejecutar `curl`.
- Actualización del catálogo mediante `apt update`.
- Instalación de `curl`.
- Respuesta JSON obtenida desde `https://httpbin.org/get`.

> **Nota:** Se recomienda incorporar capturas de pantalla de cada uno de estos pasos dentro del repositorio para facilitar el seguimiento del laboratorio.

---

# Problemas encontrados

## Problema 1

Al ejecutar:

```bash
curl https://httpbin.org/get
```

se obtuvo el siguiente mensaje:

```text
bash: curl: command not found
```

### Diagnóstico

La imagen Ubuntu utilizada para el laboratorio no incluía la herramienta **curl** instalada por defecto.

---

# Soluciones y conceptos aprendidos

### Solución aplicada

Se ejecutaron los siguientes comandos:

```bash
apt update
apt install curl -y
```

Posteriormente se volvió a ejecutar:

```bash
curl https://httpbin.org/get
```

obteniendo correctamente la respuesta del servidor.

### Conceptos consolidados

- Todo programa ejecutándose en Linux corresponde a un proceso.
- Cada proceso posee un identificador único (**PID**).
- `ps` muestra una vista rápida de los procesos.
- `ps -ef` proporciona información más detallada.
- `top` permite monitorear el sistema en tiempo real.
- `apt update` actualiza el catálogo de paquetes disponibles.
- `apt install` permite instalar nuevas herramientas.
- `curl` permite consumir APIs directamente desde la terminal.
- Los errores del tipo **command not found** generalmente indican que la herramienta no está instalada.

---

# Buenas prácticas

- Utilizar `ps` antes de asumir que una aplicación dejó de ejecutarse.
- Utilizar `top` para identificar problemas de consumo de CPU o memoria.
- Ejecutar `apt update` antes de instalar software.
- Instalar únicamente las herramientas necesarias dentro de un contenedor.
- Validar APIs mediante `curl` antes de asumir que existe un problema de conectividad.
- Leer cuidadosamente los mensajes de error antes de intentar una solución.

---

# Resumen del capítulo

En este capítulo se aprendió cómo Linux administra los procesos del sistema y cómo utilizar herramientas básicas para monitorear el rendimiento e interactuar con servicios HTTP.

Se estudiaron los comandos `ps`, `ps -ef` y `top` para consultar y supervisar procesos, además del uso de `apt` para instalar software y `curl` para consumir APIs desde la terminal. También se resolvió un caso práctico relacionado con la ausencia de la herramienta `curl`, reforzando la importancia de interpretar correctamente los mensajes de error.

Estos conocimientos serán fundamentales para diagnosticar contenedores Docker, validar servicios y trabajar con Webhooks y APIs durante los siguientes módulos del proyecto.

---

# Próximo capítulo

## Módulo 3· Docker Compose – Despliegue de aplicaciones multicontenedor

En el siguiente módulo se abordarán los siguientes temas:

- ¿Qué es Docker Compose?
- Problemas de administrar múltiples contenedores con `docker run`.
- Estructura de un archivo `docker-compose.yml`.
- Definición de servicios.
- Redes entre contenedores.
- Volúmenes.
- Variables de entorno.
- Despliegue de una arquitectura completa con un único comando.

El objetivo será comprender cómo desplegar aplicaciones compuestas por múltiples servicios, preparando el entorno para instalar y configurar **n8n** de forma profesional.

> Continúa en el siguiente módulo.