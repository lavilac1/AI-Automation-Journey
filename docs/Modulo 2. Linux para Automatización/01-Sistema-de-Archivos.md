---
proyecto: AI Automation Journey
capitulo: 2.1
titulo: Linux para Automatización – Sistema de Archivos
tecnologia: Ubuntu Linux
nivel: Principiante
version: 1.0
---

# Capítulo 02.1 · Linux para Automatización – Sistema de Archivos

> Proyecto: **AI Automation Journey**

---

# Introducción

Cuando trabajamos con **Docker**, **Docker Compose** o **n8n**, realmente estamos interactuando con un sistema operativo Linux, incluso si nuestro equipo utiliza Windows como sistema anfitrión.

Por esta razón, comprender cómo Linux organiza sus archivos y directorios es un conocimiento fundamental antes de comenzar a desplegar aplicaciones contenedorizadas.

En este capítulo se estudiará la estructura del sistema de archivos de Linux, aprendiendo a navegar entre directorios y a organizar proyectos mediante los comandos básicos de la terminal.

---

# Objetivo

## Objetivo general

Comprender la estructura del sistema de archivos de Linux mediante laboratorios prácticos, aprendiendo a navegar entre directorios y organizar proyectos de forma correcta, como base para trabajar posteriormente con Docker Compose, n8n y aplicaciones desplegadas en contenedores.

## Objetivos específicos

- Comprender cómo organiza Linux la información.
- Diferenciar el sistema de archivos de Linux respecto a Windows.
- Identificar el concepto de directorio raíz (`/`).
- Aprender a navegar por el árbol de directorios.
- Crear una estructura organizada para un proyecto.
- Comprender por qué una buena organización facilita el mantenimiento de aplicaciones.

---

# Conceptos principales

## Sistema de archivos

Es la estructura utilizada por Linux para organizar, almacenar y acceder a toda la información del sistema.

## Directorio

Un directorio es un contenedor lógico utilizado para agrupar archivos y otros directorios relacionados.

## Directorio raíz (`/`)

Es el punto de inicio del sistema de archivos de Linux. Todos los directorios dependen de esta ubicación.

## Ruta absoluta

Ruta que comienza desde la raíz (`/`) e indica la ubicación completa de un archivo o directorio.

## Ruta relativa

Ruta calculada a partir del directorio actual donde se encuentra el usuario.

---

# Desarrollo

## Arquitectura del sistema de archivos Linux

```text
                     /

               (Root Directory)

         ├── home
         ├── etc
         ├── tmp
         ├── usr
         ├── var
         └── opt
```

A diferencia de Windows, Linux no organiza la información mediante unidades como **C:**, **D:** o **E:**.

Todo el sistema parte de una única raíz (`/`) y cada directorio forma parte del mismo árbol.

---

## Estructura del proyecto creada durante el laboratorio

```text
proyecto

├── documentos
├── scripts
└── evidencias
```

El objetivo fue comprender cómo agrupar información relacionada dentro de un mismo contexto, principio que posteriormente será aplicado en proyectos con Docker, Docker Compose, n8n y desarrollo de software.

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

### Objetivo del laboratorio

Realizar todas las prácticas directamente dentro del contenedor Ubuntu para familiarizarse con el sistema de archivos Linux.

---

# Comandos utilizados

## Consultar el directorio actual

### `pwd`

**Descripción**

Muestra el directorio donde se encuentra ubicada actualmente la terminal.

El nombre del comando significa **Print Working Directory**.

```bash
pwd
```

**Resultado esperado**

```text
/
```

o

```text
/home
```

dependiendo del directorio donde se encuentre la sesión.

**Buenas prácticas**

- Utilizarlo antes de ejecutar comandos como `rm`, `cp` o `mv`.
- Verificar siempre la ubicación actual antes de modificar archivos o directorios.

---

## Listar el contenido de un directorio

### `ls`

**Descripción**

Muestra los archivos y directorios contenidos en la ubicación actual.

También puede utilizarse indicando una ruta específica.

```bash
ls
```

```bash
ls /
```

**Resultado esperado**

```text
home
etc
tmp
usr
var
```

**Buenas prácticas**

- Utilizar `ls` antes de acceder o modificar un directorio.
- Verificar la estructura del sistema antes de crear nuevos recursos.

---

## Cambiar de directorio

### `cd`

**Descripción**

Cambia el directorio de trabajo actual.

El nombre del comando significa **Change Directory**.

Durante el laboratorio se utilizó para comprender la estructura jerárquica del sistema de archivos de Linux.

```bash
cd /home
```

```bash
cd /
```

```bash
cd /tmp
```

### Ejemplo práctico

```bash
cd /tmp
pwd
```

**Resultado**

```text
/tmp
```

**Buenas prácticas**

- Confirmar siempre la nueva ubicación utilizando `pwd`.
- Recordar que `cd` únicamente cambia el directorio actual; no mueve ni copia archivos.

---

## Crear directorios

### `mkdir`

**Descripción**

Crea nuevos directorios.

El nombre del comando significa **Make Directory**.

Durante el laboratorio se utilizó para construir una estructura organizada de proyecto.

```bash
mkdir proyecto
```

Posteriormente:

```bash
mkdir documentos
mkdir scripts
mkdir evidencias
```

**Resultado esperado**

```text
proyecto

├── documentos
├── scripts
└── evidencias
```

**Buenas prácticas**

- Organizar la información mediante directorios principales y subdirectorios.
- Utilizar nombres descriptivos.
- Este mismo principio será utilizado posteriormente con Docker Compose y n8n.

> **Relación con el proyecto**
>
> Más adelante esta organización permitirá estructurar proyectos Docker, almacenar configuraciones de n8n, gestionar volúmenes y mantener una distribución clara de archivos y recursos.

---

# Laboratorio paso a paso

Durante el laboratorio se realizaron las siguientes actividades.

## Paso 1 · Consultar el directorio actual

```bash
pwd
```

---

## Paso 2 · Visualizar el contenido

```bash
ls
```

---

## Paso 3 · Consultar el contenido del directorio raíz

```bash
ls /
```

---

## Paso 4 · Navegar entre directorios

```bash
cd /home

pwd

cd /

pwd

cd /tmp

pwd
```

---

## Paso 5 · Crear el directorio del proyecto

```bash
mkdir proyecto

cd proyecto
```

---

## Paso 6 · Crear la estructura del proyecto

```bash
mkdir documentos

mkdir scripts

mkdir evidencias
```

---

## Paso 7 · Validar la estructura

```bash
ls
```

**Resultado esperado**

```text
documentos
scripts
evidencias
```

---

# Validaciones

Durante el laboratorio se verificó correctamente:

- La ubicación actual mediante `pwd`.
- El contenido del sistema de archivos utilizando `ls` y `ls /`.
- La navegación entre directorios mediante `cd`.
- La creación del directorio `proyecto`.
- La creación de las carpetas `documentos`, `scripts` y `evidencias`.
- La correcta organización jerárquica del sistema de archivos.

---

# Evidencias

Durante esta práctica se obtuvieron evidencias relacionadas con:

- Resultado del comando `pwd`.
- Visualización del contenido mediante `ls`.
- Navegación entre directorios utilizando `cd`.
- Creación del directorio `proyecto`.
- Creación de las carpetas `documentos`, `scripts` y `evidencias`.
- Validación de la estructura creada mediante `ls`.

> **Nota:** Se recomienda incorporar capturas de pantalla de cada uno de estos pasos dentro del repositorio para facilitar el seguimiento del laboratorio.

---

# Problemas encontrados

Durante este laboratorio no se presentaron errores técnicos.

La principal dificultad consistió en comprender la diferencia entre la organización del sistema de archivos de Windows y Linux, especialmente el concepto de una única raíz (`/`) desde la cual se organizan todos los directorios.

---

# Soluciones y conceptos aprendidos

Durante este capítulo se consolidaron los siguientes conceptos:

- Linux organiza toda la información mediante un único árbol de directorios.
- El directorio raíz (`/`) representa el punto de inicio del sistema de archivos.
- Los directorios permiten agrupar información relacionada.
- `pwd` indica la ubicación actual dentro del sistema.
- `ls` permite visualizar el contenido de un directorio.
- `cd` cambia la ubicación actual del usuario.
- `mkdir` permite crear nuevas carpetas para organizar proyectos.
- Una buena estructura de directorios facilita el mantenimiento y la administración de aplicaciones.

---

# Buenas prácticas

- Verificar siempre la ubicación actual utilizando `pwd`.
- Utilizar `ls` antes de modificar el contenido de un directorio.
- Organizar los proyectos mediante directorios principales y subdirectorios.
- Evitar crear recursos directamente sobre la raíz (`/`) cuando no sea necesario.
- Mantener una estructura clara y consistente para facilitar el mantenimiento.
- Utilizar nombres descriptivos para los directorios.

---

# Resumen del capítulo

En este capítulo se estudió la estructura del sistema de archivos de Linux y se aprendió a navegar por ella utilizando los comandos fundamentales de la terminal.

Se comprendió la diferencia entre la organización de archivos en Windows y Linux, identificando el directorio raíz (`/`) como el punto de partida de todo el sistema. Además, se practicó la creación de una estructura organizada de directorios, estableciendo las bases necesarias para administrar proyectos y comprender cómo herramientas como Docker, Docker Compose y n8n organizan su información.

---

# Próximo capítulo

## Capítulo 02.2 · Linux para Automatización – Administración de Archivos

En el siguiente capítulo se abordarán los siguientes temas:

- Creación de archivos (`touch`).
- Lectura de archivos (`cat`).
- Escritura de contenido (`echo`).
- Copia de archivos (`cp`).
- Movimiento y renombrado (`mv`).
- Eliminación de archivos (`rm`).
- Diferencias entre copiar, mover y eliminar información.

El objetivo será comprender cómo administrar archivos dentro de Linux antes de trabajar con configuraciones reales de Docker, Docker Compose y n8n.

> Continúa en el siguiente capítulo.