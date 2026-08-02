---
proyecto: AI Automation Journey
capitulo: 02
titulo: Docker Fundamentals – Imágenes, Contenedores y Ciclo de Vida
tecnologia: Docker
nivel: Principiante
version: 1.0
---

# Capítulo 02 · Docker Fundamentals – Imágenes, Contenedores y Ciclo de Vida

> Proyecto: **AI Automation Journey**

---

# Introducción

Antes de desplegar aplicaciones reales como **n8n**, es fundamental comprender cómo funciona Docker y cuáles son los conceptos que sustentan su funcionamiento.

En este capítulo se estudian los pilares de Docker mediante laboratorios prácticos, abordando la diferencia entre imágenes y contenedores, el funcionamiento del comando `docker run`, el ciclo de vida de un contenedor, la persistencia de datos y el uso de herramientas de inspección como `docker ps`, `docker logs` y `docker exec`.

Estos conocimientos servirán como base para desplegar aplicaciones contenedorizadas en los siguientes capítulos.

---

# Objetivo

## Objetivo general

Comprender los conceptos fundamentales de Docker mediante laboratorios prácticos, diferenciando imágenes, contenedores y su ciclo de vida, para construir una base sólida antes de desplegar aplicaciones reales como **n8n**.

## Objetivos específicos

- Comprender qué es una imagen Docker.
- Comprender qué es un contenedor.
- Diferenciar imagen y contenedor.
- Comprender cómo funciona `docker run`.
- Analizar el ciclo de vida de un contenedor.
- Comprender el concepto de persistencia.
- Introducir el uso de logs y el acceso interactivo a contenedores.

---

# Conceptos principales

## Imagen Docker

Una imagen es una plantilla inmutable que contiene todo lo necesario para crear uno o varios contenedores.

## Contenedor

Un contenedor es una instancia en ejecución creada a partir de una imagen Docker.

## Docker Hub

Repositorio oficial desde donde Docker descarga imágenes cuando no se encuentran disponibles localmente.

## Docker Engine

Motor encargado de crear, ejecutar y administrar contenedores.

## Persistencia

Los datos almacenados dentro de un contenedor permanecen mientras este exista. Si el contenedor es eliminado, dicha información también se pierde, salvo que se utilicen volúmenes.

## Ciclo de vida del contenedor

Un contenedor puede pasar por distintos estados, como **Created**, **Running**, **Paused** y **Exited**, dependiendo del estado de ejecución de su proceso principal.

---

# Desarrollo

## Flujo de ejecución de Docker

```text
                 Docker Hub
                      │
          docker run ubuntu
                      │
                      ▼
            Descarga de Imagen
                      │
                      ▼
              Docker Engine (WSL2)
                      │
                      ▼
            Creación del Contenedor
                      │
                      ▼
         Ejecución del proceso principal
                      │
          ┌───────────┴────────────┐
          ▼                        ▼
   Proceso activo             Proceso finaliza
          │                        │
          ▼                        ▼
      Running                  Exited
```

---

## Relación entre imagen y contenedor

```text
Imagen Ubuntu

        │

        ├──────────────► Contenedor A

        ├──────────────► Contenedor B

        ├──────────────► Contenedor C

        └──────────────► Contenedor D
```

Una única imagen puede generar múltiples contenedores independientes, cada uno con su propio sistema de archivos y ciclo de vida.

---

## Configuración del laboratorio

| Elemento | Configuración |
|----------|---------------|
| Sistema operativo | Windows 11 |
| Plataforma | Docker Desktop |
| Backend | WSL2 |
| Distribución Linux | Ubuntu |
| Consola | PowerShell |
| Imagen utilizada | `ubuntu` |
| Contenedor creado | `laboratorio` |
| Proceso principal | `sleep infinity` |

El proceso `sleep infinity` mantiene el contenedor en estado **Running**, permitiendo interactuar con él de forma continua.

---

## Comandos utilizados

### Descargar y ejecutar una imagen

```bash
docker run hello-world
```

**Aprendizaje**

- Descarga la imagen desde Docker Hub si no existe localmente.
- Crea un nuevo contenedor.
- Ejecuta el proceso principal.
- Finaliza el contenedor cuando dicho proceso termina.

---

### Crear un contenedor persistente

```bash
docker run -dit --name laboratorio ubuntu sleep infinity
```

#### Parámetros utilizados

| Parámetro | Descripción |
|-----------|-------------|
| `-d` | Ejecuta el contenedor en segundo plano (Detached Mode). |
| `-i` | Mantiene abierta la entrada estándar (Interactive). |
| `-t` | Asigna una terminal (TTY). |
| `--name` | Asigna un nombre al contenedor. |

---

### Listar imágenes

```bash
docker images
```

**Objetivo**

Visualizar las imágenes almacenadas localmente.

---

### Ver contenedores activos

```bash
docker ps
```

**Objetivo**

Mostrar únicamente los contenedores que se encuentran en estado **Running**.

---

### Ver todos los contenedores

```bash
docker ps -a
```

**Objetivo**

Mostrar contenedores en cualquier estado:

- Running
- Exited
- Created
- Paused

---

### Detener un contenedor

```bash
docker stop laboratorio
```

**Objetivo**

Finalizar el proceso principal del contenedor.

---

### Iniciar un contenedor existente

```bash
docker start laboratorio
```

**Objetivo**

Reutilizar el mismo contenedor conservando su sistema de archivos.

---

### Consultar logs

```bash
docker logs laboratorio
```

**Objetivo**

Mostrar la salida generada por el proceso principal del contenedor.

> **Nota:** En este laboratorio no se obtuvieron logs porque el proceso `sleep infinity` no genera salida estándar.

---

### Acceder al contenedor

```bash
docker exec -it laboratorio bash
```

**Objetivo**

Abrir una terminal interactiva dentro del contenedor para ejecutar comandos manualmente.

---

# Validaciones

Durante el laboratorio se realizaron las siguientes comprobaciones.

## Validación 1

**La imagen Ubuntu fue descargada correctamente.**

**Resultado esperado**

La imagen quedó disponible mediante:

```bash
docker images
```

---

## Validación 2

**El contenedor fue creado correctamente.**

**Resultado esperado**

```bash
docker ps
```

Estado esperado:

```text
Up
```

---

## Validación 3

**El contenedor cambió correctamente de estado tras ejecutar:**

```bash
docker stop laboratorio
```

Estado esperado:

```text
Exited
```

---

## Validación 4

**El contenedor fue iniciado nuevamente utilizando:**

```bash
docker start laboratorio
```

Estado esperado:

```text
Up
```

---

## Validación 5

Se creó el archivo:

```text
prueba.txt
```

dentro del contenedor.

Después de detenerlo e iniciarlo nuevamente, el archivo continuó existiendo, demostrando que el sistema de archivos del contenedor permanece mientras este no sea eliminado.

---

# Evidencias

Durante este laboratorio se obtuvieron evidencias relacionadas con:

- Descarga automática de la imagen Ubuntu.
- Ejecución del contenedor **laboratorio**.
- Consulta mediante `docker ps`.
- Consulta mediante `docker ps -a`.
- Cambio de estado de **Running** a **Exited**.
- Acceso interactivo mediante `docker exec`.
- Creación del archivo `prueba.txt`.
- Persistencia del archivo después de reiniciar el contenedor.

> **Nota:** Para la documentación pública del repositorio se recomienda incorporar capturas de pantalla de cada uno de estos pasos con el fin de facilitar la comprensión del laboratorio.

---

# Problemas encontrados

## Problema 1

El comando inicial:

```bash
docker run -dit --name laboratorio ubuntu
```

no mantenía el contenedor en ejecución.

### Diagnóstico

La imagen Ubuntu no ejecuta un proceso persistente por defecto. Al finalizar el proceso principal, Docker detiene automáticamente el contenedor.

### Solución

Se añadió un proceso principal permanente:

```text
sleep infinity
```

Comando utilizado:

```bash
docker run -dit --name laboratorio ubuntu sleep infinity
```

---

## Problema 2

El comando:

```bash
docker logs laboratorio
```

no mostró información.

### Diagnóstico

No existía ningún error.

El proceso principal (`sleep infinity`) no genera salida estándar, por lo que no había registros disponibles para mostrar.

---

# Soluciones aplicadas

Durante este capítulo se consolidaron los siguientes conceptos:

- Una imagen es una plantilla inmutable.
- Un contenedor es una instancia creada a partir de una imagen.
- Una imagen puede generar múltiples contenedores independientes.
- El estado **Exited** no implica que el contenedor haya sido eliminado.
- `docker start` reutiliza un contenedor existente.
- `docker run` crea un contenedor nuevo.
- Los archivos creados dentro del contenedor permanecen mientras este exista.
- Eliminar un contenedor implica perder los datos almacenados en él, salvo que se utilicen volúmenes.
- Los logs dependen exclusivamente de la salida generada por el proceso principal.

---

# Buenas prácticas

## Durante el trabajo con contenedores

- Asignar nombres descriptivos utilizando `--name`.
- Utilizar `docker ps` para verificar el estado de ejecución.
- Ejecutar `docker ps -a` antes de asumir que un contenedor fue eliminado.
- Consultar los logs antes de reiniciar o eliminar un contenedor.
- Comprender el ciclo de vida del contenedor antes de trabajar con aplicaciones más complejas.
- Evitar almacenar información crítica dentro del contenedor sin utilizar volúmenes.
- Validar siempre el estado del proceso principal cuando un contenedor finaliza inesperadamente.

---

# Resumen del capítulo

En este capítulo se estudiaron los fundamentos de Docker mediante laboratorios prácticos orientados a comprender el funcionamiento interno de imágenes y contenedores.

Se analizó el comportamiento del comando `docker run`, el ciclo de vida de un contenedor, el uso de `docker ps`, `docker stop`, `docker start`, `docker logs` y `docker exec`, además de comprobar cómo la información almacenada dentro de un contenedor permanece disponible mientras este no sea eliminado.

También se identificaron problemas comunes relacionados con el proceso principal de un contenedor y se documentaron las soluciones aplicadas, consolidando las bases necesarias para desplegar aplicaciones contenedorizadas.

---

# Próximo capítulo

## Capítulo 03 · Despliegue de n8n utilizando Docker

En el siguiente capítulo se abordarán los siguientes temas:

- ¿Qué es una aplicación contenedorizada?
- Descarga de la imagen oficial de n8n.
- Publicación de puertos (`-p`).
- Variables de entorno (`-e`).
- Persistencia mediante volúmenes (`-v`).
- Primer acceso a la interfaz web de n8n.
- Creación del primer workflow.

> Continúa en el siguiente capítulo.