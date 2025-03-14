# Ejercicio 1

Responder breve y claramente los siguientes incisos:

1. **¿En qué se diferencia un problema de búsqueda de un problema de decisión?**

Un problema de búsqueda y un problema de decisión son dos tipos de problemas con diferencias clave:

Problema de búsqueda:

Se trata de encontrar una solución válida dentro de un espacio de búsqueda.
La respuesta no es simplemente "sí" o "no", sino que se debe proporcionar un resultado concreto.
Ejemplo: "¿Cuál es el camino más corto entre A y B en un grafo?"

Problema de decisión:

Se trata de determinar si existe una solución que cumpla con ciertos criterios.
La respuesta es "sí" o "no".
Ejemplo: "¿Existe un camino entre A y B en un grafo con peso total menor que 10?"


2. **¿Por qué en el caso de los problemas de decisión, podemos referirnos indistintamente a problemas y lenguajes?**

3. **El problema de satisfactibilidad de las fórmulas booleanas, en su forma de decisión, es:**
   - “Dada una fórmula φ, ¿existe una asignación A de valores de verdad que la hace verdadera?”
   - **Enunciar el problema de búsqueda asociado.**

Si tenemos la fórmula: φ=(A∨¬B)∧(¬A∨B)

- El problema de decisión pregunta: ¿Existe una asignación de 𝐴 y 𝐵 que satisfaga φ?
- El problema de búsqueda requiere encontrar una asignación válida, por ejemplo: A = true y B = true es una asignación satisfactoria.


4. **Otra visión de MT es la que genera un lenguaje (visión generadora). En el caso del problema del inciso anterior, ¿qué lenguaje generaría la MT de visión generadora que resuelve el problema?**



5. **¿Qué postula la Tesis de Church-Turing?**



6. **¿Cuándo dos MT son equivalentes? ¿Y cuándo dos modelos de MT son equivalentes?**




# Ejercicio 2

Dado el alfabeto Ʃ = {0, 1}:

1. **Obtener el conjunto Ʃ* y el lenguaje incluido en Ʃ* con cadenas de a lo sumo 2 símbolos.**


Ʃ* = (0^n 1^m | n ≥ 0 m ≥ 0)
L = {'',0,1,00,01,11,10}


2. **Sea el lenguaje L = {0^n1^n | n ≥ 0}. Obtener los lenguajes Ʃ* ⋂ L, Ʃ* ⋃ L y L^C respecto de Ʃ*.**

L = {0^n1^n | n ≥ 0}

Ʃ* ⋂ L = L

Ʃ* ⋃ L = Ʃ*

L^C = Σ∗−L

# Ejercicio 3

En clase se mostró una MT no determinística (MTN) que acepta las cadenas de la forma ha^n o hb^n, con n ≥ 0. **Construir (describir la función de transición) una MT determinística (MTD) equivalente.**

MTN: no devuelve siempre el mismo resultado 
MTD: devuelve siempre el mismo resultado



| Estado | h         | a         | b         | B         |
|--------|----------|----------|----------|----------|
| q0     | qh, h, R | x        | x        | x        |
| qh     | x        | qa, a, R | qb, b, R | x        |
| qa     | x        | qa, a, R | x        | qA, B, S |
| qb     | x        | x        | qb, b, R | qA, B, S |

---




# Ejercicio 4

**Describir la idea general de una MT con varias cintas que acepte, de la manera más eficiente posible (menor cantidad de pasos), el lenguaje L = {a^n b^n c^n | n ≥ 0}.**


|----|---------|---------|----------|--------|
|    |   a     |    b            |        c                |    B   | 
| q0 | q1,a,R  |    q2,b,R     |     q3,c,R                |    x   |
| q1 |   x     |  qa,a,R |  qb,b,R  |    x   |
| q2 |   x     |  qa,a,R |     x    | qA,B,S |
| q3 |   x     |   x     |  qb,b,R  | qA,B,S |



# Ejercicio 5

**Explicar cómo una MT sin el movimiento S (el no movimiento) puede simular (ejecutar) otra que sí lo tiene.**

Se mueve de forma intermitente de derecha a izquiera hasta que se tope con un simbolo X que represente ejecutar pasando la maquina al estado siguiente.

# Ejercicio 6

En clase se construyó una MT con 2 cintas que acepta L = {w | w ∈ {a, b}* y w es un palíndromo}. **Construir una MT equivalente con 1 cinta. Ayuda: la solución que vimos para aceptar el lenguaje de las cadenas a^nb^n, con n ≥ 1, puede ser un buen punto de partida.**

# Ejercicio 7

**Construir una MT que calcule la resta de dos números. Ayuda: se puede considerar la idea de solución propuesta en clase.**

# Ejercicio 8

**Construir una MT que genere todas las cadenas de la forma a^nb^n, con n ≥ 1. Ayuda: se puede considerar la idea de solución propuesta en clase.**



### **Ejercicio 3 - MT Determinística (MTD)**



### **Ejercicio 4 - MT con Múltiples Cintas**

#### **Idea general:**
La MT utilizará tres cintas para mejorar la eficiencia en la aceptación del lenguaje \( L = \{ a^n b^n c^n | n \geq 0 \} \):
1. **Cinta 1:** Contendrá la cadena de entrada.
2. **Cinta 2:** Contará las ‘a’, copiándolas mientras avanza.
3. **Cinta 3:** Verificará que el número de ‘b’ y ‘c’ sea igual al número de ‘a’ copiado en la cinta 2.

#### **Función de transición**

| Estado | a         | b         | c         | B         |
|--------|----------|----------|----------|----------|
| q0     | q1, a, R | q2, b, R | q3, c, R | x        |
| q1     | qa, a, R | qb, b, R | x        | x        |
| q2     | x        | qa, a, R | x        | qA, B, S |
| q3     | x        | x        | qb, b, R | qA, B, S |

---

### **Ejercicio 5 - Simulación de una MT sin el movimiento 'S'**
Una MT sin el movimiento 'S' puede simular una que sí lo tiene moviéndose de manera intermitente a la derecha e izquierda hasta alcanzar un símbolo especial que indique detenerse.
- En lugar de quedarse en el mismo lugar (S), la máquina puede moverse a la derecha, marcar la celda y luego regresar a la izquierda para continuar con la ejecución.

---

### **Ejercicio 6 - MT de Palíndromos con 1 Cinta**
**Idea general:**
- Reemplazar el primer y último símbolo con una marca especial.
- Moverse hacia la derecha y luego hacia la izquierda, verificando la coincidencia.
- Repetir hasta que se procesen todos los caracteres o haya una discrepancia.

---

### **Ejercicio 7 - MT para la Resta de Dos Números**
**Idea general:**
- Los números se representan en forma unaria (ej. 3 sería "111").
- La MT eliminará simultáneamente un "1" de cada número hasta que solo quede el resultado o se alcance 0.

---

### **Ejercicio 8 - MT Generadora de Cadenas de la Forma \( a^n b^n \)**
**Idea general:**
- Inicia con una única ‘a’.
- Duplica la cantidad de ‘a’ y genera un ‘b’ correspondiente.
- Repite el proceso para todas las combinaciones posibles.

