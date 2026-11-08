# Problema de la mochila 0/1 — backtracking con visualización

Aplicación de escritorio que resuelve el problema de la mochila 0/1 mediante **backtracking** y dibuja el árbol de decisión completo, incluyendo las ramas podadas y el camino de la solución óptima.

![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/Interfaz-Swing-5B8C5A)
![Algoritmos](https://img.shields.io/badge/Algoritmos-backtracking-7C3AED)

---

## El problema

Dada una mochila con capacidad limitada y un conjunto de elementos, cada uno con peso y valor, hay que elegir un subconjunto que **maximice el valor total sin superar el peso máximo**. Cada elemento se toma o se deja: no se puede fraccionar (por eso es 0/1).

Resolverlo por fuerza bruta implica explorar `2^n` combinaciones. Este proyecto lo hace con backtracking y **poda**: cuando agregar un elemento ya supera la capacidad, la rama se descarta y se marca como podada.

## Funcionalidades

- Entrada de la **capacidad** de la mochila.
- Entrada de elementos con el formato `peso,valor`, uno por línea.
- Resolución con backtracking y poda por capacidad.
- **Visualización del árbol de decisión**:
  - nodos normales, nodos de la solución y nodos podados con colores distintos;
  - zoom (0.3× a 3×) y desplazamiento;
  - panel de resultados con el valor óptimo, la combinación elegida y el conteo de nodos explorados y podados.

## Cómo está construido

```
MochilaBacktracking/
└── src/
    ├── module-info.java
    ├── main/Main.java
    ├── modelo/
    │   ├── MochilaModelo.java   # backtracking, poda y métricas
    │   └── NodoArbol.java       # nodo del árbol de decisión
    ├── controlador/
    │   └── MochilaControlador.java
    └── vista/
        ├── MochilaVista.java    # formulario y panel de resultados
        └── PanelArbol.java      # dibujo del árbol con Graphics2D
```

`MochilaModelo` guarda la mejor solución encontrada y el camino que la produjo; la vista solo dibuja lo que el modelo expone. La separación modelo–vista–controlador permite cambiar la interfaz sin tocar el algoritmo.

## Cómo ejecutarlo

### Opción 1 — IDE

Abre la carpeta `MochilaBacktracking` en NetBeans, IntelliJ IDEA o Eclipse y ejecuta `main.Main`.

### Opción 2 — línea de comandos (PowerShell)

```powershell
cd MochilaBacktracking
javac -d bin (Get-ChildItem -Recurse src -Filter *.java).FullName
java --module-path bin -m MochilaBacktracking/main.Main
```

En Bash/macOS/Linux:

```bash
cd MochilaBacktracking
javac -d bin $(find src -name "*.java")
java --module-path bin -m MochilaBacktracking/main.Main
```

### Ejemplo de entrada

```
Capacidad: 10

Elementos (peso,valor):
5,10
4,40
6,30
3,50
```

## Documentación

[`U3InfoGrup1.pdf`](U3InfoGrup1.pdf) — informe del proyecto con el análisis del algoritmo y las capturas de la interfaz.

## Autora

**Corina Acosta** — [@Corinaast](https://github.com/Corinaast)

Proyecto de la asignatura de **Estructuras de Datos** (ESPE).
