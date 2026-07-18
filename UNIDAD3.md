div align="center" style="margin-bottom: 35px; border-top: 2px solid #58a6ff; border-bottom: 2px solid #58a6ff; padding: 20px 0;">
  <h1 style="color: #58a6ff; font-size: 28px; font-weight: 800; letter-spacing: 3px; margin: 0; text-transform: uppercase; font-family: 'Segoe UI', system-ui, sans-serif;">
    Unidad III: Programación modular y estructura de datos estáticas
  </h1>
  <div style="color: #8b949e; font-size: 14px; font-style: italic; margin-top: 8px; letter-spacing: 1px;">
    — Diseño Modular, Parámetros y Gestión de Arreglos en Memoria —
  </div>
</div>

---

# 1. Modularidad en Programación

La modularidad consiste en dividir un programa en partes independientes llamadas **módulos**. Cada módulo realiza una tarea específica y se comunica con los demás a través de interfaces claras.

## 1.1  Ventajas Principales
* **Reutilización**: Evita duplicar código.
* **Mantenimiento**: Facilita corregir errores aislados.
* **Legibilidad**: Simplifica la estructura del código.

---

## 1.2  Modos de Pase de Parámetros

Los módulos reciben datos del programa principal mediante parámetros utilizando dos mecanismos:

### 1.3 Pase por Valor
* Envía una **copia** de la variable.
* Los cambios dentro del módulo **no afectan** el valor original.

### 1.4 Pase por Referencia
* Envía la **dirección de memoria** de la variable.
* Los cambios dentro del módulo **sí modifican** el valor original.

---

## 1.5 Ejemplos Prácticos Independientes (C++)

A continuación, se presentan dos ejemplos separados para analizar cada comportamiento de forma aislada.

### Ejemplo 1: Pase por Valor
En este caso, la función recibe un duplicado. El valor original de la variable no se altera.

```cpp
#include <iostream>

// Módulo independiente para pase por valor
void duplicarPorValor(int numero) {
    numero = numero * 2; // Solo modifica la copia local
    std::cout << "Dentro de la funcion (copia): " << numero << std::endl;
}

int main() {
    int miNumero = 15;

    std::cout << "=== PRUEBA PASE POR VALOR ===" << std::endl;
    std::cout << "Valor inicial: " << miNumero << std::endl; // Imprime 15
    
    duplicarPorValor(miNumero);
    
    std::cout << "Valor final fuera de la funcion: " << miNumero << std::endl; // Sigue siendo 15
    return 0;
}
```

### Ejemplo 2: Pase por Referencia
En este caso, la función recibe la dirección real de la variable mediante el operador `&`. El valor original se modifica directamente.

```cpp
#include <iostream>

// Módulo independiente para pase por referencia
void duplicarPorReferencia(int &numero) {
    numero = numero * 2; // Modifica la variable original en memoria
    std::cout << "Dentro de la funcion (original): " << numero << std::endl;
}

int main() {
    int miNumero = 15;

    std::cout << "=== PRUEBA PASE POR REFERENCIA ===" << std::endl;
    std::cout << "Valor inicial: " << miNumero << std::endl; // Imprime 15
    
    duplicarPorReferencia(miNumero);
    
    std::cout << "Valor final fuera de la funcion: " << miNumero << std::endl; // Ahora es 30
    return 0;
}
```
---
# 2. Arreglos en Programación

Un arreglo (array o vector) es una estructura de datos que almacena una colección de elementos del **mismo tipo** bajo un único nombre. Los elementos se guardan en posiciones de memoria contiguas y se acceden mediante **índices**.

## Características Principales
* **Homogeneidad**: Todos sus datos deben ser del mismo tipo (ej. solo enteros).
* **Tamaño fijo**: Se define al crearlo y no cambia durante la ejecución.
* **Acceso directo**: Se accede a cualquier posición usando su número de índice.

---

## 2.1 Tipos de Arreglos y Ejemplos (C++)

Los arreglos se clasifican según el número de dimensiones o índices que requieren para acceder a sus elementos.

### 2.2 Arreglos Unidimensionales (Vectores)
Tienen una sola dimensión. Utilizan un único índice para acceder a los datos de forma lineal (como una lista de elementos).

```cpp
#include <iostream>

int main() {
    // Declaración e inicialización de un vector de 5 notas
    int notas[5] = {85, 92, 78, 90, 88};

    std::cout << "=== ARREGLO UNIDIMENSIONAL ===" << std::endl;
    
    // Acceso y lectura mediante un ciclo FOR (un solo índice)
    for(int i = 0; i < 5; i++) {
        std::cout << "Nota en posicion [" << i << "]: " << notas[i] << std::endl;
    }
    
    return 0;
}
```

### 2.3 Arreglos Bidimensionales (Matrices)
Tienen dos dimensiones. Organizan la información en una estructura de **filas y columnas** (como una tabla de Excel o un tablero de ajedrez). Requieren dos índices.

```cpp
#include <iostream>

int main() {
    // Declaración de una matriz de 2 filas y 3 columnas
    int matriz[2][3] = {
        {1, 2, 3},  // Fila 0
        {4, 5, 6}   // Fila 1
    };

    std::cout << "=== ARREGLO BIDIMENSIONAL ===" << std::endl;

    // Recorrido usando ciclos anidados (dos índices: f para fila, c para columna)
    for(int f = 0; f < 2; f++) {
        for(int c = 0; c < 3; c++) {
            std::cout << "Elemento [" << f << "][" << c << "]: " << matriz[f][c] << "  ";
        }
        std::cout << std::endl; // Salto de línea al terminar cada fila
    }

    return 0;
}
```

### 2.4 Arreglos Multidimensionales
Tienen tres o más dimensiones. El caso más común es el tridimensional (3D), que se puede imaginar como un **cubo de datos** o un libro con varias páginas, donde cada página contiene una matriz (filas y columnas). Requieren tres o más índices.

```cpp
#include <iostream>

int main() {
    // Arreglo 3D: 2 capas (páginas), 2 filas, 2 columnas
    int cubo[2][2][2] = {
        { // Capa 0
            {10, 20}, // Fila 0
            {30, 40}  // Fila 1
        },
        { // Capa 1
            {50, 60}, // Fila 0
            {70, 80}  // Fila 1
        }
    };

    std::cout << "=== ARREGLO MULTIDIMENSIONAL (3D) ===" << std::endl;

    // Recorrido usando tres ciclos anidados (índices: capa, fila, columna)
    for(int capa = 0; capa < 2; capa++) {
        std::cout << "--- Capa " << capa << " ---" << std::endl;
        for(int f = 0; f < 2; f++) {
            for(int c = 0; c < 2; c++) {
                std::cout << "Cubo[" << capa << "][" << f << "][" << c << "] = " << cubo[capa][f][c] << std::endl;
            }
        }
    }

    return 0;
}
```
---
## 4. Principales dificultades en la aplicación de los contenidos.
Aplicar la programación modular y las estructuras de datos estáticas me generó ciertas dificultades porque exige un nivel de abstracción y orden mucho más estricto. Con la modularidad, el principal tropiezo fue aprender a fragmentar el problema correctamente y decidir cuándo enviar datos por valor (protegiendo la variable original) o por referencia (modificándola directamente), lo que al principio provocaba confusiones sobre dónde se alteraban realmente los datos. Con los arreglos (unidimensionales, matrices y multidimensionales), el verdadero dolor de cabeza fue controlar los índices de lectura y escritura; es muy fácil cometer errores de desbordamiento de memoria al intentar acceder a una posición que está fuera del tamaño fijo establecido, o confundirse al anidar ciclos para recorrer las diferentes capas y dimensiones de una matriz.

## 5. Reflexion critica
La reflexión crítica que me deja esta unidad es que el software eficiente nace de la organización y la optimización de los recursos. La modularidad nos enseña que el código limpio y reutilizable es fundamental para el mantenimiento a largo plazo, obligándonos a pensar en componentes independientes en lugar de un bloque de texto monolítico. Por otro lado, trabajar con estructuras estáticas como los arreglos nos aterriza a la realidad del uso de la memoria en la computadora, recordándonos que los recursos son finitos y que debemos dimensionar nuestros datos con precisión desde el inicio. El verdadero aprendizaje está en entender que programar no es solo resolver un problema, sino estructurar la solución de forma tan ordenada y lógica que sea fácil de escalar, leer y mantener por cualquier desarrollador.

> ### 🤖 Declaración de Uso de IA - Unidad 3
> * **Herramienta utilizada:** Gemini
> * **Uso específico:** Debido a la complejidad de la gestión de memoria y el flujo de variables, se utilizó la IA para clarificar el comportamiento de los punteros/referencias en la transferencia de parámetros. También sirvió como apoyo para visualizar la lógica de ciclos anidados necesarios en el recorrido de arreglos bidimensionales y multidimensionales. El código final fue razonado, implementado y probado por el autor.

[Siguiente: Conclusiones ➡️](./conclusiones.md)



