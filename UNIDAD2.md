# Estructuras Condicionales

Las estructuras condicionales controlan el flujo de un programa ejecutando diferentes acciones según se cumpla o no una condición lógica.

---

## 1. Condicional Simple (Si-Entonces)

Evalúa una condición. Si es verdadera, ejecuta una acción. Si es falsa, no hace nada.

### Pseudocódigo
```text
Si condición Entonces
    Instrucciones_si_verdadero
FinSi
```

### Diagrama de Flujo
*   Un rombo contiene la **Condición**.
*   Una flecha etiquetada como **Sí / Verdadero** sale del rombo hacia el bloque de instrucciones.
*   Una flecha etiquetada como **No / Falso** sale del rombo y esquiva el bloque de instrucciones, continuando el flujo normal.

---

## 2. Condicional Compuesto (Si-Entonces-Sino)

Evalúa una condición. Permite elegir entre dos caminos exclusivos dependiendo de si el resultado es verdadero o falso.

### Pseudocódigo
```text
Si condición Entonces
    Instrucciones_si_verdadero
Sino
    Instrucciones_si_falso
FinSi
```

### Diagrama de Flujo
*   Un rombo contiene la **Condición**.
*   La flecha de **Sí / Verdadero** va hacia un bloque de acciones específicas.
*   La flecha de **No / Falso** va hacia un bloque de acciones alternativas diferente.
*   Ambos caminos se unen más abajo para continuar con el programa.

---

## 3. Condicional Múltiple (Según / Caso)

Compara una variable con múltiples valores posibles o evalúa varias condiciones en cascada. Es útil para evitar demasiados "Si" seguidos.

### Pseudocódigo
```text
Según variable Hacer
    valor1:
        Instrucciones_1
    valor2:
        Instrucciones_2
    De Otro Modo:
        Instrucciones_por_defecto
FinSegún
```

### Diagrama de Flujo
*   Un rombo o un selector especial contiene la **Variable** o **Condición principal**.
*   Salen múltiples flechas (tantas como casos existan), cada una con el **Valor esperado**.
*   Cada flecha lleva a su propio bloque de instrucciones.
*   Existe una flecha final opcional para el caso **De Otro Modo** (si ningún valor coincide).
*   Todas las líneas se unifican al terminar los bloques de código.
