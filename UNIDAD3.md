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

### Ejemplo 1: Pase por Valor (Área del Círculo)
En este programa, se envía la variable del radio por valor para calcular el área de un círculo. La función recibe una copia exacta del dato en un espacio de memoria nuevo, realiza la operación matemática y devuelve el resultado con un return. De esta manera, el radio original en la función principal permanece intacto, seguro y sin alteraciones.

```cpp
#include <stdio.h>

// Módulo que recibe el radio por valor y calcula el área
float calcularAreaCirculo(float radio) {
    float pi = 3.14159;
    radio = pi * (radio * radio); // Modifica solo la copia local del radio
    return radio; // Devuelve el área calculada
}

int main() {
    float miRadio = 5.0;
    float miArea;

    printf("=== EJERCICIO: PASE POR VALOR ===\n");
    printf("Radio original en el main: %.2f\n", miRadio);

    // Se pasa 'miRadio' por valor a la función
    miArea = calcularAreaCirculo(miRadio);

    printf("Area calculada: %.2f\n", miArea);
    
    // Comprobamos que el radio original NO fue alterado por la función
    printf("Radio fuera de la funcion (sigue intacto): %.2f\n", miRadio);

    return 0;
}


```

SALIDA DEL TERMINAL
<img width="1194" height="180" alt="image" src="https://github.com/user-attachments/assets/2d8cc639-0d92-46b5-bca5-11dbfae8a0c8" />


---

### Ejemplo 2: Pase por Referencia (Sistema de Salud en Videojuegos)
En este programa, se simula el uso de una poción curativa enviando la salud actual de un personaje mediante un puntero (int *). La función accede directamente a la dirección de memoria real del personaje usando el operador &. De esta manera, los puntos de vida aumentan de forma inmediata y permanente en el programa principal, reflejando el cambio de estado en tiempo real sin usar copias.

```cpp
#include <stdio.h>

// Módulo que aplica una cura modificando la salud original por referencia
void aplicarPocionCura(int *saludPersonaje, int puntosCura) {
    // Se modifica directamente el valor en la dirección de memoria apuntada
    *saludPersonaje = *saludPersonaje + puntosCura; 
    
    // Limita la salud máxima a 100 puntos
    if (*saludPersonaje > 100) {
        *saludPersonaje = 100;
    }
}

int main() {
    int vidaJugador = 45; // Variable que será modificada por la función
    int pocionGrande = 30;

    printf("=== PRUEBA PASE POR REFERENCIA ===\n");
    printf("Salud inicial del jugador: %d HP\n", vidaJugador); // Imprime 45 HP

    // Se envía la variable 'vidaJugador' por referencia usando el operador &
    aplicarPocionCura(&vidaJugador, pocionGrande);

    // La variable original fue modificada directamente por la función
    printf("Salud final despues de la pocion: %d HP\n", vidaJugador); // Ahora es 75 HP

    return 0;
}


```

SALIDA DEL TERMINAL
<img width="1192" height="208" alt="image" src="https://github.com/user-attachments/assets/d91cedf0-11e7-46c9-ad67-14bfa469933c" />


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
En este programa, se utilizan arreglos unidimensionales para emparejar de forma lineal los nombres y las cantidades del inventario de un personaje. El sistema almacena de forma consecutiva cadenas de texto (char *) y enteros (int), permitiendo recorrer ambos vectores simultáneamente con un único índice dentro de un ciclo iterativo para mostrar la información estructurada en pantalla.

```cpp
#include <stdio.h>

int main() {
    // Un arreglo de cadenas de texto para los nombres de los ítems
    char *nombresItems[5] = {"Pociones", "Espadas", "Escudos", "Monedas", "Flechas"};
    
    // El arreglo con las cantidades de cada ítem
    int cantidades[5] = {12, 3, 0, 50, 15}; 

    printf("=== INVENTARIO DEL JUGADOR ===\n");

    // El ciclo FOR recorre ambos arreglos usando el mismo índice
    for (int i = 0; i < 5; i++) {
        printf("Espacio [%d] -> %s: %d unidades\n", i, nombresItems[i], cantidades[i]);
    }

    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1188" height="214" alt="image" src="https://github.com/user-attachments/assets/fc8600a7-c020-45b4-902c-74daef3c9c61" />


---

### 2.3 Arreglos Bidimensionales (Matrices - Laberinto de Pac-Man)
En este programa, se utiliza una matriz de caracteres para renderizar de forma visual un fragmento del mapa clásico de Pac-Man en dos dimensiones. La estructura organiza el laberinto mediante filas y columnas que representan coordenadas espaciales, requiriendo ciclos anidados para recorrer cada casilla e imprimir muros, pasillos con puntos o la posición actual del personaje en la pantalla.

```cpp
#include <stdio.h>

int main() {
    // Matriz de 4 filas y 5 columnas que dibuja una esquina del laberinto
    // '#' = Muro, '.' = Pildora/Comida, 'C' = Pac-Man
    char laberinto[4][5] = {
        {'#', '#', '#', '#', '#'}, // Fila 0: Muro superior
        {'#', '.', '.', 'C', '#'}, // Fila 1: Pasillo con Pac-Man
        {'#', '.', '#', '.', '#'}, // Fila 2: Pasillo con un muro interno
        {'#', '#', '#', '#', '#'}  // Fila 3: Muro inferior
    };

    printf("=== ARREGLO BIDIMENSIONAL (LABERINTO PAC-MAN) ===\n");

    // Recorrido usando ciclos anidados (f para fila, c para columna)
    for(int f = 0; f < 4; f++) {
        for(int c = 0; c < 5; c++) {
            // Imprime el caracter de la celda seguido de un espacio para darle forma cuadrada
            printf("%c ", laberinto[f][c]); 
        }
        printf("\n"); // Salto de línea al terminar cada fila del laberinto
    }

    return 0;
}

```

SALIDA DEL TERMINAL
<img width="1184" height="204" alt="image" src="https://github.com/user-attachments/assets/d5018ff7-c181-4368-9299-bb15e837eaba" />

#### Explicación del Código (Simulación Teórica)
##### Este programa no constituye un videojuego jugable ni interactivo de Pac-Man, ya que carece de mecánicas de movimiento, lógica de colisiones o bucles de juego en tiempo real. Su propósito es puramente educativo y demostrativo, sirviendo como una maqueta estática para ilustrar de forma gráfica cómo las estructuras de datos bidimensionales organizan y representan mundos virtuales basados en cuadrículas dentro de la memoria del computador.
---

### 2.4 Arreglos Multidimensionales (Torre de Mazmorras 3D)
En este programa, se utiliza un arreglo tridimensional (3D) para gestionar las recompensas de oro en una torre de mazmorras de múltiples pisos. La estructura añade una tercera dimensión llamada "capa" (el piso del mapa), organizando los datos en un cubo virtual en memoria que requiere tres índices independientes manejados con ciclos anidados de tres niveles para leer la información posicional completa. 

```cpp
#include <stdio.h>

int main() {
    // Arreglo tridimensional [2 pisos][2 filas][2 columnas] 
    // Almacena la cantidad de monedas de oro en los cofres de cada zona
    int mazmorra[2][2][2] = {
        { // Capa 0: Piso Subterráneo
            {10, 20}, // Fila 0: Cofres del pasillo izquierdo
            {30, 40}  // Fila 1: Cofres del pasillo derecho
        },
        { // Capa 1: Piso Principal
            {50, 60}, // Fila 0: Cofres de la sala de armas
            {70, 80}  // Fila 1: Cofres del trono
        }
    };

    printf("=== ARREGLO MULTIDIMENSIONAL (TORRE MAZMORRA 3D) ===\n");

    // Recorrido usando tres ciclos anidados (índices: piso, fila, columna)
    for(int piso = 0; piso < 2; piso++) {
        printf("--- Piso %d ---\n", piso);
        for(int f = 0; f < 2; f++) {
            for(int c = 0; c < 2; c++) {
                printf("Cofre [%d][%d][%d] = %d monedas\n", piso, f, c, mazmorra[piso][f][c]);
            }
        }
    }

    return 0;
}


```

SALIDA DEL TERMINAL 

<img width="1190" height="258" alt="image" src="https://github.com/user-attachments/assets/e537fe6b-37f8-41b8-b51f-795415979a23" />

---
## 4. Principales dificultades en la aplicación de los contenidos.
Aplicar la programación modular y las estructuras de datos estáticas me generó ciertas dificultades porque exige un nivel de abstracción y orden mucho más estricto. Con la modularidad, el principal tropiezo fue aprender a fragmentar el problema correctamente y decidir cuándo enviar datos por valor (protegiendo la variable original) o por referencia (modificándola directamente), lo que al principio provocaba confusiones sobre dónde se alteraban realmente los datos. Con los arreglos (unidimensionales, matrices y multidimensionales), el verdadero dolor de cabeza fue controlar los índices de lectura y escritura; es muy fácil cometer errores de desbordamiento de memoria al intentar acceder a una posición que está fuera del tamaño fijo establecido, o confundirse al anidar ciclos para recorrer las diferentes capas y dimensiones de una matriz.

## 5. Reflexión crítica
La reflexión crítica que me deja esta unidad es que el software eficiente nace de la organización y la optimización de los recursos. La modularidad nos enseña que el código limpio y reutilizable es fundamental para el mantenimiento a largo plazo, obligándonos a pensar en componentes independientes en lugar de un bloque de texto monolítico. Por otro lado, trabajar con estructuras estáticas como los arreglos nos aterriza a la realidad del uso de la memoria en la computadora, recordándonos que los recursos son finitos y que debemos dimensionar nuestros datos con precisión desde el inicio. El verdadero aprendizaje está en entender que programar no es solo resolver un problema, sino estructurar la solución de forma tan ordenada y lógica que sea fácil de escalar, leer y mantener por cualquier desarrollador.

> ### 🤖 Declaración de Uso de IA - Unidad 3
> * **Herramienta utilizada:** Gemini
> * **Uso específico:** Debido a la complejidad de la gestión de memoria y el flujo de variables, se utilizó la IA para clarificar el comportamiento de los punteros/referencias en la transferencia de parámetros. También sirvió como apoyo para visualizar la lógica de ciclos anidados necesarios en el recorrido de arreglos bidimensionales y multidimensionales. El código final fue razonado, implementado y probado por el autor.

[Siguiente: Conclusiones ➡️](./conclusiones.md)



