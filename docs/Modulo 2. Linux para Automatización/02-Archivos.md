---
proyecto: AI Automation Journey
capitulo: 2.2
titulo: Linux para Automatización – Administración de Archivos
tecnologia: Ubuntu Linux
nivel: Principiante
version: 1.0
---

# Capítulo 02.2 · Linux para Automatización – Administración de Archivos

> Proyecto: **AI Automation Journey**

---

# Introducción

Una vez comprendida la organización del sistema de archivos de Linux, el siguiente paso consiste en aprender a administrar la información almacenada en él.

En este capítulo se estudiarán los comandos fundamentales para crear, visualizar, modificar, copiar, mover y eliminar archivos desde la terminal. Estas operaciones forman parte del trabajo diario de cualquier administrador de sistemas y serán utilizadas posteriormente para gestionar configuraciones, respaldos y archivos de aplicaciones como Docker, Docker Compose y n8n.

---

# Objetivo

## Objetivo general

Aprender a crear, visualizar, copiar, mover y eliminar archivos en Linux mediante comandos fundamentales, comprendiendo cómo administrar la información dentro de un sistema operativo Linux y un contenedor Docker.

## Objetivos específicos

- Comprender la diferencia entre archivos y directorios.
- Crear archivos desde la terminal.
- Leer el contenido de un archivo.
- Escribir información dentro de un archivo.
- Copiar archivos.
- Mover y renombrar archivos.
- Eliminar archivos de forma segura.

---

# Conceptos principales

## Archivo

Unidad básica donde Linux almacena información.

## Directorio

Contenedor utilizado para organizar archivos y otros directorios relacionados.

## Copia

Proceso mediante el cual se crea un nuevo archivo independiente conservando el original.

## Movimiento

Acción que permite cambiar un archivo de ubicación o modificar su nombre sin crear una copia.

## Eliminación

Proceso mediante el cual un archivo deja de existir dentro del sistema de archivos.

---

# Desarrollo

## Flujo del laboratorio

```text
touch informe.txt
        │
        ▼
Archivo vacío
        │
        ▼
echo "Hola AI Automation Journey" > informe.txt
        │
        ▼
Archivo con contenido
        │
        ▼
cp informe.txt copia.txt
        │
        ▼
Dos archivos independientes
        │
        ▼
mv copia.txt backup.txt
        │
        ▼
Cambio de nombre
        │
        ▼
rm backup.txt
        │
        ▼
Archivo eliminado
```

---

## Estructura utilizada durante el laboratorio

```text
Directorio

├── informe.txt
├── copia.txt
└── backup.txt
```

Durante el laboratorio se trabajó sobre un mismo directorio para comprender cómo cambian los archivos a medida que se crean, copian, renombran y eliminan.

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

## Crear un archivo

### `touch`

**Descripción**

Crea un archivo vacío si este no existe. Si el archivo ya existe, actualiza su fecha de modificación.

```bash
touch informe.txt
```

**Resultado esperado**

```text
informe.txt
```

visible al ejecutar:

```bash
ls
```

**Buenas prácticas**

- Utilizar `touch` para crear archivos de prueba rápidamente.
- Verificar su creación mediante `ls`.

---

## Leer el contenido de un archivo

### `cat`

**Descripción**

Muestra el contenido completo de un archivo sin modificarlo.

```bash
cat informe.txt
```

**Resultado esperado**

Inicialmente:

```text
(archivo vacío)
```

Después de escribir información:

```text
Hola AI Automation Journey
```

**Buenas prácticas**

- Utilizar `cat` para validar el contenido de un archivo antes de modificarlo.
- Es especialmente útil para revisar archivos de configuración.

---

## Escribir información en un archivo

### `echo`

**Descripción**

Escribe texto dentro de un archivo.

```bash
echo "Hola AI Automation Journey" > informe.txt
```

El operador `>` reemplaza el contenido existente del archivo.

**Resultado esperado**

```text
Hola AI Automation Journey
```

**Buenas prácticas**

- Utilizar `echo` para generar archivos de prueba o configuraciones simples.
- Recordar que `>` sobrescribe el contenido existente.

---

## Copiar un archivo

### `cp`

**Descripción**

Crea una copia independiente del archivo original.

```bash
cp informe.txt copia.txt
```

**Resultado esperado**

```text
informe.txt
copia.txt
```

Ambos archivos existen de forma independiente.

**Buenas prácticas**

- Crear copias de respaldo antes de modificar archivos importantes.
- Recordar que modificar la copia no afecta al archivo original.

---

## Mover o renombrar un archivo

### `mv`

**Descripción**

Permite mover un archivo entre directorios o cambiar su nombre.

```bash
mv copia.txt backup.txt
```

**Resultado esperado**

```text
backup.txt
```

El archivo `copia.txt` deja de existir con ese nombre.

**Buenas prácticas**

- Utilizar `mv` para reorganizar archivos sin crear duplicados.
- Recordar que este comando no genera una copia del archivo.

---

## Eliminar un archivo

### `rm`

**Descripción**

Elimina permanentemente el archivo indicado.

```bash
rm backup.txt
```

**Resultado esperado**

El archivo deja de aparecer al ejecutar:

```bash
ls
```

> ⚠️ **Advertencia**
>
> Linux no envía los archivos eliminados a una papelera de reciclaje.
>
> El comando:
>
> ```bash
> rm -rf
> ```
>
> elimina directorios completos junto con todo su contenido y debe utilizarse únicamente cuando se comprende exactamente qué se va a eliminar.

---

# Laboratorio paso a paso

Durante el laboratorio se realizaron las siguientes actividades.

## Paso 1 · Crear un archivo

```bash
touch informe.txt
```

---

## Paso 2 · Verificar su existencia

```bash
ls
```

---

## Paso 3 · Consultar el contenido

```bash
cat informe.txt
```

---

## Paso 4 · Escribir información

```bash
echo "Hola AI Automation Journey" > informe.txt
```

---

## Paso 5 · Confirmar el contenido

```bash
cat informe.txt
```

---

## Paso 6 · Crear una copia

```bash
cp informe.txt copia.txt
```

---

## Paso 7 · Renombrar el archivo

```bash
mv copia.txt backup.txt
```

---

## Paso 8 · Eliminar el archivo

```bash
rm backup.txt
```

---

## Paso 9 · Validar el resultado

```bash
ls
```

---

# Validaciones

Durante el laboratorio se verificó correctamente:

- La creación del archivo `informe.txt`.
- La lectura del contenido mediante `cat`.
- La escritura de información utilizando `echo`.
- La creación de una copia mediante `cp`.
- El cambio de nombre utilizando `mv`.
- La eliminación del archivo mediante `rm`.
- La validación final utilizando `ls`.

---

# Evidencias

Durante esta práctica se obtuvieron evidencias relacionadas con:

- Creación del archivo `informe.txt`.
- Visualización mediante `ls`.
- Lectura utilizando `cat`.
- Escritura mediante `echo`.
- Copia del archivo utilizando `cp`.
- Renombrado mediante `mv`.
- Eliminación mediante `rm`.

> **Nota:** Se recomienda incorporar capturas de pantalla de cada uno de estos pasos dentro del repositorio para facilitar el seguimiento del laboratorio.

---

# Problemas encontrados

Durante este laboratorio no se presentaron errores técnicos.

Sin embargo, se identificó como principal riesgo el uso del comando `rm`, ya que elimina archivos de forma permanente.

También se explicó el funcionamiento del comando:

```bash
rm -rf
```

el cual puede eliminar directorios completos junto con todo su contenido si se utiliza incorrectamente.

---

# Soluciones y conceptos aprendidos

Durante este capítulo se consolidaron los siguientes conceptos:

- Un archivo es la unidad básica donde se almacena información.
- `touch` permite crear archivos rápidamente.
- `cat` muestra el contenido de un archivo.
- `echo` permite escribir información dentro de un archivo.
- `cp` crea una copia independiente.
- `mv` permite mover o renombrar archivos.
- `rm` elimina archivos de forma permanente.
- Antes de eliminar información es recomendable verificar la ubicación actual mediante `pwd`.

---

# Buenas prácticas

- Verificar el contenido del directorio antes de eliminar archivos.
- Crear copias de respaldo utilizando `cp` antes de modificar archivos importantes.
- Utilizar nombres descriptivos para los archivos.
- Evitar ejecutar `rm -rf` sin conocer exactamente el contenido que será eliminado.
- Confirmar siempre la ubicación actual utilizando `pwd` antes de eliminar información.

---

# Resumen del capítulo

En este capítulo se aprendió a administrar archivos desde la terminal de Linux utilizando los comandos fundamentales para crear, visualizar, modificar, copiar, mover y eliminar información.

A través de un laboratorio práctico se comprendió la diferencia entre copiar y mover archivos, la importancia de validar el contenido antes de realizar modificaciones y los riesgos asociados a la eliminación permanente mediante `rm`.

Estos conocimientos constituyen la base para trabajar posteriormente con archivos de configuración, respaldos y recursos utilizados por Docker, Docker Compose y n8n.

---

# Próximo capítulo

## Capítulo 02.3 · Linux para Automatización – Procesos y Red

En el siguiente capítulo se abordarán los siguientes temas:

- Administración de procesos mediante `ps`.
- Consulta detallada de procesos con `ps -ef`.
- Monitoreo del sistema utilizando `top`.
- Administración de paquetes con `apt`.
- Instalación de herramientas.
- Consumo de APIs mediante `curl`.
- Diagnóstico de errores comunes en contenedores Linux.

El objetivo será comprender cómo monitorear procesos y consumir servicios HTTP directamente desde un entorno Linux, conocimientos fundamentales para administrar aplicaciones Docker y n8n.

> Continúa en el siguiente capítulo.