<div align="center" style="margin-bottom: 35px; border-top: 2px solid #58a6ff; border-bottom: 2px solid #58a6ff; padding: 20px 0;">
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


EJERCICIO 
```cpp
#include <stdio.h>

// Módulos (Funciones)
void mostrarSaldo(int saldoCopia);
void depositar(int *saldoReal);

int main() {
    int miSaldo = 100; // Saldo inicial en la cuenta

    // 1. Paso por Valor
    mostrarSaldo(miSaldo);
    printf("Saldo en tu tarjeta despues de consultar: $%d\n\n", miSaldo);

    // 2. Paso por Referencia
    depositar(&miSaldo); // Enviamos la cuenta real con &
    printf("Saldo en tu tarjeta despues de depositar: $%d\n", miSaldo);

    return 0;
}

// Recibe una copia. No puede cambiar el saldo de la tarjeta.
void mostrarSaldo(int saldoCopia) {
    saldoCopia = 0; // Simulamos un error interno
    printf("[CAJERO] Tu saldo en pantalla es: $%d\n", saldoCopia);
}

// Recibe la dirección real. Modifica el saldo de la tarjeta.
void depositar(int *saldoReal) {
    *saldoReal = *saldoReal + 50; // Sumamos $50 directamente a la memoria
    printf("[CAJERO] Has depositado $50 con exito.\n");
}


```


SALIDA DEL TERMINAL 
<img width="1193" height="233" alt="image" src="https://github.com/user-attachments/assets/60585b07-4cec-425a-a74e-546ab405c62a" />

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

## 1.5 Ejemplos Prácticos Independientes (C)

A continuación, se presentan dos ejemplos separados para analizar cada comportamiento de forma aislada.

### Ejemplo 1: Pase por Valor
En este caso, la función recibe un duplicado. El valor original de la variable no se altera.

```cpp
#include <stdio.h>

// Módulo independiente para pase por valor
void duplicarPorValor(int numero) {
    numero = numero * 2; // Solo modifica la copia local
    printf("Dentro de la funcion (copia): %d\n", numero);
}

int main() {
    int miNumero = 15;
    
    printf("=== PRUEBA PASE POR VALOR ===\n");
    printf("Valor inicial: %d\n", miNumero); // Imprime 15
    
    duplicarPorValor(miNumero);
    
    printf("Valor final fuera de la funcion: %d\n", miNumero); // Sigue siendo 15
    
    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1181" height="172" alt="image" src="https://github.com/user-attachments/assets/5a706ea1-ae41-4ecb-b5bf-d744aec0621c" />

---

### Ejemplo 2: Pase por Referencia
En este caso, la función recibe la dirección real de la variable mediante el operador `&`. El valor original se modifica directamente.

```cpp
#include <stdio.h>

// Módulo independiente para pase por referencia usando punteros
void duplicarPorReferencia(int *numero) {
    *numero = *numero * 2; // Modifica el valor en la dirección de memoria original
    printf("Dentro de la funcion (original): %d\n", *numero);
}

int main() {
    int miNumero = 15;

    printf("=== PRUEBA PASE POR REFERENCIA ===\n");
    printf("Valor inicial: %d\n", miNumero); // Imprime 15
    
    // Se envía la dirección de memoria usando el operador &
    duplicarPorReferencia(&miNumero);
    
    printf("Valor final fuera de la funcion: %d\n", miNumero); // Ahora es 30
    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1180" height="191" alt="image" src="https://github.com/user-attachments/assets/789dbc91-e5ba-4276-a6eb-a293bc97eb6b" />

---
# 2. Arreglos en Programación

Un arreglo (array o vector) es una estructura de datos que almacena una colección de elementos del **mismo tipo** bajo un único nombre. Los elementos se guardan en posiciones de memoria contiguas y se acceden mediante **índices**.

## Características Principales
* **Homogeneidad**: Todos sus datos deben ser del mismo tipo (ej. solo enteros).
* **Tamaño fijo**: Se define al crearlo y no cambia durante la ejecución.
* **Acceso directo**: Se accede a cualquier posición usando su número de índice.

---

## 2.1 Tipos de Arreglos y Ejemplos (C)

Los arreglos se clasifican según el número de dimensiones o índices que requieren para acceder a sus elementos.

### 2.2 Arreglos Unidimensionales (Vectores)
Tienen una sola dimensión. Utilizan un único índice para acceder a los datos de forma lineal (como una lista de elementos).

```cpp
#include <stdio.h>

int main() {
    // Declaración e inicialización de un vector de 5 notas
    int notas[5] = {85, 92, 78, 90, 88};

    printf("=== ARREGLO UNIDIMENSIONAL ===\n");
    
    // Acceso y lectura mediante un ciclo FOR (un solo índice)
    for(int i = 0; i < 5; i++) {
        printf("Nota en posicion [%d]: %d\n", i, notas[i]);
    }
    
    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1189" height="228" alt="image" src="https://github.com/user-attachments/assets/0a65fc8d-575a-417d-9638-1d2f079abc59" />

---

### 2.3 Arreglos Bidimensionales (Matrices)
Tienen dos dimensiones. Organizan la información en una estructura de **filas y columnas** (como una tabla de Excel o un tablero de ajedrez). Requieren dos índices.

```cpp
#include <stdio.h>

int main() {
    // Declaración de una matriz de 2 filas y 3 columnas
    int matriz[2][3] = {
        {1, 2, 3},  // Fila 0
        {4, 5, 6}   // Fila 1
    };

    printf("=== ARREGLO BIDIMENSIONAL ===\n");

    // Recorrido usando ciclos anidados (dos índices: f para fila, c para columna)
    for(int f = 0; f < 2; f++) {
        for(int c = 0; c < 3; c++) {
            printf("Elemento [%d][%d]: %d  ", f, c, matriz[f][c]);
        }
        printf("\n"); // Salto de línea al terminar cada fila
    }

    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1181" height="219" alt="image" src="https://github.com/user-attachments/assets/d293f67c-8ae8-489f-819d-5c8cb731fd5e" />

---
### 2.4 Arreglos Multidimensionales
Tienen tres o más dimensiones. El caso más común es el tridimensional (3D), que se puede imaginar como un **cubo de datos** o un libro con varias páginas, donde cada página contiene una matriz (filas y columnas). Requieren tres o más índices.

```cpp
#include <stdio.h>

int main() {
    // CORRECCIÓN: Se agregaron los corchetes [2][2][2] al nombre de la variable
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

    printf("=== ARREGLO MULTIDIMENSIONAL (3D) ===\n");

    // Recorrido usando tres ciclos anidados (índices: capa, fila, columna)
    for(int capa = 0; capa < 2; capa++) {
        printf("--- Capa %d ---\n", capa);
        for(int f = 0; f < 2; f++) {
            for(int c = 0; c < 2; c++) {
                printf("Cubo[%d][%d][%d] = %d\n", capa, f, c, cubo[capa][f][c]);
            }
        }
    }

    return 0;
}

```

SALIDA DEL TERMINAL 
<img width="1181" height="296" alt="image" src="https://github.com/user-attachments/assets/9e2ed7d3-df17-4de9-92e2-aa041a6b8462" />

---
---
## 4. Principales dificultades en la aplicación de los contenidos.
Aplicar la programación modular y las estructuras de datos estáticas me generó ciertas dificultades porque exige un nivel de abstracción y orden mucho más estricto. Con la modularidad, el principal tropiezo fue aprender a fragmentar el problema correctamente y decidir cuándo enviar datos por valor (protegiendo la variable original) o por referencia (modificándola directamente), lo que al principio provocaba confusiones sobre dónde se alteraban realmente los datos. Con los arreglos (unidimensionales, matrices y multidimensionales), el verdadero dolor de cabeza fue controlar los índices de lectura y escritura; es muy fácil cometer errores de desbordamiento de memoria al intentar acceder a una posición que está fuera del tamaño fijo establecido, o confundirse al anidar ciclos para recorrer las diferentes capas y dimensiones de una matriz.

## 5. Reflexion critica
La reflexión crítica que me deja esta unidad es que el software eficiente nace de la organización y la optimización de los recursos. La modularidad nos enseña que el código limpio y reutilizable es fundamental para el mantenimiento a largo plazo, obligándonos a pensar en componentes independientes en lugar de un bloque de texto monolítico. Por otro lado, trabajar con estructuras estáticas como los arreglos nos aterriza a la realidad del uso de la memoria en la computadora, recordándonos que los recursos son finitos y que debemos dimensionar nuestros datos con precisión desde el inicio. El verdadero aprendizaje está en entender que programar no es solo resolver un problema, sino estructurar la solución de forma tan ordenada y lógica que sea fácil de escalar, leer y mantener por cualquier desarrollador.

> ### 🤖 Declaración de Uso de IA - Unidad 3
> * **Herramienta utilizada:** Gemini
> * **Uso específico:** Debido a la complejidad de la gestión de memoria y el flujo de variables, se utilizó la IA para clarificar el comportamiento de los punteros/referencias en la transferencia de parámetros. También sirvió como apoyo para visualizar la lógica de ciclos anidados necesarios en el recorrido de arreglos bidimensionales y multidimensionales. El código final fue razonado, implementado y probado por el autor.

[Siguiente: Conclusiones ➡️](./conclusiones.md)



