# Generador y Analizador Estadístico de Datos en C

[![C Language](https://img.shields.io/badge/Language-C99-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Build System](https://img.shields.io/badge/Build-Makefile-orange.svg)](https://www.gnu.org/software/make/)
[![Documentation](https://img.shields.io/badge/Docs-Doxygen-brightgreen.svg)](https://www.doxygen.nl/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Este proyecto es un programa modular desarrollado en **C** que permite obtener automáticamente el análisis estadístico de conjuntos de datos numéricos de hasta **100,000 muestras**. Fue diseñado para generar escenarios de simulación y comparar la eficiencia de múltiples algoritmos de ordenamiento frente a diferentes distribuciones probabilísticas.

El programa está estructurado bajo los más altos estándares de ingeniería de software, contando con modularidad estricta, rutinas de evaluación de rendimiento temporal y documentación autogenerada mediante **Doxygen**.

---

## Tabla de Contenidos

- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Características Principales](#-características-principales)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Algoritmos y Funcionalidades](#-algoritmos-y-funcionalidades)
  - [Generador Aleatorio de Distribuciones](#1-generador-aleatorio)
  - [Motor de Ordenamiento](#2-motor-de-ordenamiento)
  - [Análisis Estadístico](#3-análisis-estadístico)
- [Modos de Interfaz](#-modos-de-interfaz)
- [Instrucciones de Compilación y Ejecución](#-instrucciones-de-compilación-y-ejecución)
- [Documentación Técnica](#-documentación-técnica)
- [Licencia](#-licencia)

---

## Descripción del Proyecto

El **Generador y Analizador Estadístico** provee un entorno para la simulación numérica y benchmarking de algoritmos en C. Permite a investigadores, estudiantes y desarrolladores:
1. Generar conjuntos de datos aleatorios basados en distribuciones matemáticas específicas.
2. Evaluar el impacto de la distribución inicial de datos en el rendimiento de **8 algoritmos de ordenamiento**.
3. Obtenener un diagnóstico descriptivo profundo compuesto por **15 métricas estadísticas clave**.

---

## Características Principales

* **Generación Probabilística Avanzada:** Soporte para distribuciones Uniforme, Normal (Gaussiana) y Laplace.
* **Flexibilidad de Parametrización:** Selección entre configuración por rangos $[Min, Max]$ o por parámetros estadísticos (Media, Varianza/Escala).
* **Evaluación de Rendimiento Numérico:** Medición precisa del tiempo de ejecución en algoritmos de ordenamiento para arreglos masivos (hasta $100,000$ elementos).
* **Análisis Estadístico Completo:** Cálculo de 15 métricas descriptivas, de tendencia central, dispersión, posición y forma.
* **Soporte Dual de Interfaz:** Ejecución interactiva por menú en consola o automatizable mediante argumentos por línea de comandos.

---

## Estructura del Proyecto

```text
generador-analizador-estadistico/
├── .gitignore   
├── .gitattributes        
├── Makefile                 # Script de compilación automatizada.
├── README.md                # Documentación principal del proyecto.
├── bin/                     # Directorio de salida para los binarios ejecutables.
├── build/                   # Directorio de objetos compilados (.o).
├── docs/                    # Documentación generada y reportes.
│   ├── html/                # Documentación interactiva en HTML generada por Doxygen.
│   ├── Reporte_Proyecto2.pdf # Reporte académico/técnico del proyecto.
│   └── Doxyfile             # Archivo de configuración de Doxygen.
├── include/                 # Archivos de cabecera (.h) con prototipos y estructuras.
│   ├── estadistica.h        # Prototipos para el módulo de análisis estadístico.
│   ├── generacion.h         # Prototipos para el módulo de generación aleatoria.
│   └── ordenamiento.h       # Prototipos para el módulo de algoritmos de ordenamiento.
└── src/                     # Código fuente (.c).
|   ├── estadistica.c        # Cálculo de las 15 medidas estadísticas.
|   ├── generacion.c         # Algoritmos de generación de distribuciones.
|   ├── main.c               # Flujo principal e interfaz (CLI / Menú).
|   └── ordenamiento.c       # Implementación de los 8 algoritmos de ordenamiento.
|
|__ Reporte/
    |__ Reporte.pdf 
```

### Descripción de Módulos:
* **`src/`**: Contiene el código fuente (`.c`), dividido en los módulos principales (`main.c`, `generacion.c`, `ordenamiento.c` y `estadistica.c`).
* **`include/`**: Contiene los archivos de cabecera (`.h`) con los prototipos de las funciones y definiciones de cada módulo.
* **`bin/`**: Directorio de salida donde se aloja el ejecutable final tras la compilación.
* **`docs/`**: Documentación del proyecto, incluyendo el reporte final en PDF y la documentación interactiva en HTML generada por Doxygen.

---

##  Algoritmos y Funcionalidades

### 1. Generador Aleatorio
Soporta tres distribuciones probabilísticas configurables:
* **Distribución Uniforme:** Generación en rangos contiguos.
* **Distribución Normal (Gaussiana):** Implementación del método de Box-Muller o aproximaciones estándar.
* **Distribución Laplace (Doble Exponencial):** Simulación basada en la transformación de la variable uniforme.

**Modos de parametrización:**
- **Modo por Rango:** Definición mediante límites inferiores y superiores ($[Min, Max]$).
- **Modo por Parámetros:** Definición mediante propiedades teóricas (Media $\mu$, Varianza $\sigma^2$ o parámetro de escala $b$).

---

### 2. Motor de Ordenamiento
Implementación modular de **8 algoritmos de ordenamiento** para la evaluación empírica de su complejidad temporal y espacial:

1. **Burbuja (Bubble Sort)** — $\mathcal{O}(n^2)$
2. **Pares y Nones (Odd-Even Sort)** — $\mathcal{O}(n^2)$
3. **Selección (Selection Sort)** — $\mathcal{O}(n^2)$
4. **Inserción (Insertion Sort)** — $\mathcal{O}(n^2)$
5. **Casilleros (Bucket Sort)** — $\mathcal{O}(n + k)$
6. **Burbuja Bidireccional (Cocktail Sort)** — $\mathcal{O}(n^2)$
7. **Shell (Shell Sort)** — $\mathcal{O}(n \log^2 n)$ / $\mathcal{O}(n^{3/2})$
8. **Conteo (Counting Sort)** — $\mathcal{O}(n + k)$

---

### 3. Análisis Estadístico
Cálculo automatizado de **15 medidas estadísticas independientes**:

* **Tendencia Central:** Media aritmética, Mediana, Moda.
* **Dispersión:** Varianza, Desviación estándar, Rango, Rango intercuartílico.
* **Posición:** Cuartiles ($Q_1, Q_2, Q_3$), Percentiles arbitrarios.
* **Forma y Momentos:** Momentos centrados, Momentos no centrados, Asimetría (Skewness), Curtosis.

---

## Modos de Interfaz

El programa ofrece una **doble interfaz de usuario** adaptada a diferentes flujos de trabajo:

1. **Modo Interactivo (Consola):**
   Navegación guiada paso a paso mediante menús interactivos (`printf` / `scanf`) para la configuración de muestras, generación de datos y análisis visual.
   
2. **Modo Automatizado (Línea de Comandos - CLI):**
   Soporte para recepción de parámetros desde terminal (`argc` / `argv`), lo que permite integrar el programa en scripts de automatización (Bash, Python) para pruebas masivas de benchmarking.

---

## Instrucciones de Compilación y Ejecución

### Requisitos Previos

* Compilador de C (GCC, Clang o MinGW).
* Utilidad `make`.
* Doxygen *(Opcional, para regenerar la documentación HTML)*.

### Compilación usando `make`

Desde la raíz del proyecto:

```bash
# Compilar todo el proyecto y generar el binario ejecutable
make

# Limpiar los archivos objetos y binarios generados
make clean

# Recompilar desde cero
make re
```

### Ejecución

* **Modo Interactivo:**
  ```bash
  ./bin/analizador_estadistico
  ```

* **Modo Automatizado (Ejemplo CLI):**
  ```bash
  ./bin/analizador_estadistico --dist normal --samples 50000 --sort shell
  ```

---

## Documentación Técnica

La documentación del código está completamente estandarizada con formato **Doxygen**:
* **Documentación Web (HTML):** Abrir el archivo `docs/html/index.html` en cualquier navegador web.
* **Reporte del Proyecto:** Archivo en formato PDF ubicado en `docs/Reporte_Proyecto2.pdf`.

Para regenerar la documentación web:
```bash
doxygen docs/Doxyfile
```

---
