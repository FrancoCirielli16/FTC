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

Podemos usar 2 cintas una cinta se utiliza para copiar la letra leida y otra va iterando por las letras.

Cinta 1: Contiene la cadena de entrada.
Cinta 2: Se utiliza como una pila para contar y verificar el número de 'a's, 'b's y 'c's.

Pasos de la MT

Posicionar el cabezal de la Cinta 1 al inicio de la cadena.

Fase de conteo de 'a':

Movemos el cabezal de la Cinta 1 hacia la derecha, leyendo cada símbolo.
Por cada 'a' leída en la Cinta 1, escribis 'a' en la Cinta 2 y mover el cabezal de la Cinta 2 a la derecha.

Fase de conteo de 'b':

Continuar moviendo el cabezal de la Cinta 1 hacia la derecha.
Por cada 'b' leída en la Cinta 1, mover el cabezal de la Cinta 2 a la izquierda (para "descontar" una 'a').


Fase de conteo de 'c':

Continuar moviendo el cabezal de la Cinta 1 hacia la derecha.
Por cada 'c' leída en la Cinta 1, mover el cabezal de la Cinta 2 a la izquierda (para "descontar" una 'b').


Finalización:

Si la Cinta 2 está vacía y el cabezal de la Cinta 1 ha llegado al final de la cadena, aceptar la cadena.
De lo contrario, rechazar la cadena.

- El unico problema a esto es que cualquier lectura de una letra que no corresponda por ejemplo aabcc no se va a poder disparar el rechazo antes teniendo que esperar al resultado de haber leido la cadena completa.
otra forma quizas de poder solucionar esto es tener 3 cintas

Opcion con varias cintas:

Cinta 1: Contiene la cadena de entrada.
Cinta 2: Se utiliza como guardado de conteo
Cinta 3: Se utiliza como descuento de letras

Pasos de la MT

Posicionar el cabezal de la Cinta 1 al inicio de la cadena.

Fase de conteo de a:

Movemos el cabezal de la Cinta 1 hacia la derecha, leyendo cada símbolo.
Por cada 'a' leída en la Cinta 1, escribis 'x' en la Cinta 2 y mover el cabezal de la Cinta 2 a la derecha.
Si nos encontramos un simbolo que no es 'a' movemos cinta 3 n lugares como la cinta 2 tenga

Fase de conteo de 'b':

Continuar moviendo el cabezal de la Cinta 1 hacia la derecha
Por cada 'b' leída mover el cabezal de la Cinta 3 a la izquierda (para "descontar" una 'b').
Si nos encontramos un simbolo que no es 'b' y la cinta 3 no es B(blanco) entonces rechazamos
Si nos encontramos un simbolo que no es 'b' y  la cinta 3 es B(blanco) movemos cinta 3 n lugares como la cinta 2 tenga

Fase de conteo de 'c':

Continuar moviendo el cabezal de la Cinta 1 hacia la derecha
Por cada 'c' leída mover el cabezal de la Cinta 3 a la izquierda (para "descontar" una 'b').
Si nos encontramos un simbolo que no es 'c' y la cinta 3 no esta en B(blanco) entonces rechazamos

Finalización:

Si la Cinta 3 está vacía y el cabezal de la Cinta 1 ha llegado al final de la cadena, aceptar la cadena.
De lo contrario, rechazar la cadena.


- En esta caso podemos rechazar al momento de encontrarnos un simbolo antes y si el lenguaje cambia y acepta N letras con esta opcion podemos evitar recorrer toda la cadena para obtener el resutlado.


# Ejercicio 5

**Explicar cómo una MT sin el movimiento S (el no movimiento) puede simular (ejecutar) otra que sí lo tiene.**

Se mueve de forma intermitente de derecha a izquiera hasta que se tope con un simbolo X que represente ejecutar pasando la maquina al estado siguiente.

# Ejercicio 6

En clase se construyó una MT con 2 cintas que acepta L = {w | w ∈ {a, b}* y w es un palíndromo}. **Construir una MT equivalente con 1 cinta. Ayuda: la solución que vimos para aceptar el lenguaje de las cadenas a^nb^n, con n ≥ 1, puede ser un buen punto de partida.**

idea General:

- Marcar pares de símbolos desde los extremos hacia el centro.
- Comparar el primer símbolo no marcado con el último símbolo no marcado.
- Si coinciden, marcarlos y repetir. Si no, rechazar.
- Aceptar cuando todos los símbolos están marcados o queda uno en el centro.

Estados:
q₀ (Inicio):

Marca el primer símbolo (a/b) con # y dirige a q_a o q_b.
Si la cinta está vacía (B), acepta (q_A).

q_a y q_b:

Avanzan hacia la derecha hasta encontrar B (fin de cadena).
Al llegar al final, retroceden (q_izquierda_a/q_izquierda_b).

q_izquierda_a y q_izquierda_b:

Buscan el último símbolo sin marcar (a/b).
Si coincide, lo marcan (#) y reinician (q_reset).
Si no coincide, rechazan (q_R).

q_reset: retrocede al inicio de la cinta (B) para reiniciar el proceso en q₀.
q_A (Aceptación):
q_R (Rechazo):



Símbolos: a, b, #, B.

###

Transiciones:

- q₀:
   - (q₀,a) = {q_a,#,R}
   - (q₀,b) = {q_b,#,R}
   - (q₀,#) = {q_b,#,R}
   - (q₀,B) = {q_A,S}

- q_a:
   - (q_a,a) = {q_a,R}
   - (q_a,b) = {q_a,R}
   - (q_a,#) = {q_a,R}
   - (q_a,B) = {q_izquierda_a, B, L}


- q_izquierda_a:

   - (q_izquierda_a, a) → (q_reset, #, L)  
   - (q_izquierda_a, #) → (q_izquierda_a, #, L)  
   - (q_izquierda_a, b) → (q_R, b, S)       
   - (q_izquierda_a, B) → (q_R, B, S)       

- q_b:
   (q_b, a) → (q_b, a, R)    
   (q_b, b) → (q_b, b, R)    
   (q_b, #) → (q_b, #, R)    
   (q_b, B) → (q_izquierda_b, B, L)  

- q_izquierda_b:
   (q_izquierda_b, b) → (q_reset, #, L)  
   (q_izquierda_b, #) → (q_izquierda_b, #, L)  
   (q_izquierda_b, a) → (q_R, a, S)      
   (q_izquierda_b, B) → (q_R, B, S)       

- q_reset:
   (q_reset, a) → (q_reset, a, L)  
   (q_reset, b) → (q_reset, b, L)   
   (q_reset, #) → (q_reset, #, L) 
   (q_reset, B) → (q₀, B, R)       




# Ejercicio 7

**Construir una MT que calcule la resta de dos números. Ayuda: se puede considerar la idea de solución propuesta en clase.**

![Diagrama de la máquina de estados](Practicas/P1/image%20(1).png)


| Estado | 1         | -         | #         | B         |
|--------|-----------|-----------|-----------|-----------|
| q0     | q0.1.R    | q1.-,R    | q0.#,R    | q1.1.R    |
| q1     | q2.#,L    |           | q1.#,R    | q5.B,L    |
| q2     | q0.#,R    | q2.-,L    | q2.#,L    | q3.B,R    |
| q3     | q4.1,L    | q3.-,R    | q3.#,R    |           |
| q4     |           |           | q4.1,S    |           |
| q5     |           | q4.#,S    | q5.#,L    |           |

El separador es el -
Los estados en blancos representan los rechazados 


# Ejercicio 8

**Construir una MT que genere todas las cadenas de la forma a^nb^n, con n ≥ 1. Ayuda: se puede considerar la idea de solución propuesta en clase.**


