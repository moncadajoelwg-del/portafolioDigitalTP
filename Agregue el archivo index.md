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
