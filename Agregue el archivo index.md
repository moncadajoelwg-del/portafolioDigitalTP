# Portafolio Digital de Aprendizaje – Teoría de la Programación

## 📑 Datos Informativos
> **Institución:** Universidad Nacional de Loja  
> **Facultad:** Energía, las Industrias y los Recursos Naturales no Renovables  
> **Carrera:** [Nombre de tu Carrera]  
> **Asignatura:** Teoría de la Programación  
> **Ciclo:** [Tu Ciclo]  
> **Período Académico:** [Ej. 2024-2025]  
> **Docente:** [Nombre del Docente]  
> **Estudiante:** [Tu Nombre]

---

## 📂 Unidad 1

### 📘 Contenidos
En esta unidad exploramos los fundamentos de la lógica de programación. Los temas principales incluyeron:

* **Algoritmo y Pseudocódigo:** Estructuración lógica de procesos.
* **Diagrama de Flujo:** Representación visual de algoritmos.
* **Prueba de Escritorio:** Validación manual de la lógica.
* **Lenguajes de Programación:** Diferencias y propósitos.
* **Programación por Bloques:** Introducción visual a la lógica.

---
Algoritmos y Pseudocódigo
​1. ¿Qué es un Algoritmo?
​Un algoritmo es un conjunto de pasos lógicos, finitos y ordenados que permiten solucionar un problema o realizar una tarea específica. En programación, es el "mapa" antes de construir la casa.
​Características fundamentales:
​Preciso: Debe indicar el orden de realización de cada paso.
​Definido: Si se sigue dos veces, se debe obtener el mismo resultado.
​Finito: Debe tener un inicio y un final (un número determinado de pasos).
​2. Pseudocódigo: El lenguaje de transición
​El pseudocódigo es una forma de escribir algoritmos utilizando una mezcla de lenguaje natural (español) con algunas convenciones de lenguajes de programación. Su objetivo es que el programador se concentre en la lógica sin preocuparse por las reglas estrictas de sintaxis de un lenguaje como C++ o Java.
​Ventajas de usar pseudocódigo:
​Es fácil de entender para cualquier persona.
​Facilita el paso posterior a la codificación real.
​Permite detectar errores de lógica rápidamente.
​✍️ Ejemplo Práctico: Cálculo de Área de un Triángulo
​Para demostrar la aplicación de estos conceptos, aquí presento el desglose de un problema simple:
​A. Algoritmo (Pasos lógicos):
​Inicio.
​Obtener la medida de la base.
​Obtener la medida de la altura.
​Multiplicar la base por la altura.
​Dividir el resultado anterior para dos.
​Mostrar el resultado del área.
​Fin.
​B. Pseudocódigo (Representación estructurada):
Algoritmo CalcularAreaTriangulo
    Definir base, altura, area Como Real
    
    Escribir "Ingrese la base del triángulo:"
    Leer base
    
    Escribir "Ingrese la altura del triángulo:"
    Leer altura
    
    area <- (base * altura) / 2
    
    Escribir "El área resultante es: ", area
FinAlgoritmo
💡 Nota de Reflexión
​"El mayor reto no es aprender a escribir código, sino aprender a descomponer un problema complejo en pasos tan simples que una máquina pueda entenderlos."

### 💻 Ejercicio con Estructura Secuencial
// Ejemplo en C++ (ajústalo a tu lenguaje)
#include <iostream>
using namespace std;

int main() {
    int n1, n2, suma;
    cout << "Ingrese primer numero: ";
    cin >> n1;
    cout << "Ingrese segundo numero: ";
    cin >> n2;
    suma = n1 + n2;
    cout << "El resultado es: " << suma;
    return 0;
}
**Pseudocódigo:**
```text
Algoritmo EjercicioSecuencial
    Escribir "Ingrese primer número:"
    Leer num1
    Escribir "Ingrese segundo número:"
    Leer num2
    resultado <- num1 + num2
    Escribir "El resultado es: ", resultado
FinAlgoritmo
