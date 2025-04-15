Ejercicio 1. Considerando la reducción de HP a LU descripta en clase, responder:

a. Explicar por qué la función identidad, es decir la función que a toda cadena le asigna la misma cadena, no es una reducción de HP a LU.

- HP implica que dada una MT M y una entrada w, MT se detiene. 
- LU implica que dada una MT M y una entrada w, MT acepta w.

La función identidad f(M,w)=(M,w) no satisface la equivalencia anterior en todos los casos. 

En particular:

Si M se detiene rechazando w, entonces: (M,w)∈HP (porque M se detiene).

Pero (M,w) ∈/ LU (porque M no acepta w).

Esto viola la condición de la reducción, ya que un "sí" en HP no se traduce en un "sí" en LU.

b. Explicar por qué las MT M2 generadas en los pares de salida (<M2>, w), o bien paran
aceptando, o bien loopean.


c. Explicar por qué la función utilizada para reducir HP a LU también sirve para reducir HP^C a LU^C

- El complemento de HP implica que dada una MT M y una entrada w, MT no se detiene. 
- El complemento de LU implica que dada una MT M y una entrada w, MT no acepta w.

Sabiendo esto podemos decir que dada una entrada (M,w) y dicha entrada pertence al complemento de HP entonces la M no se detiene, por lo que entonces M nunca acepta por lo que significa que (M,w) pertence al complemento de LU.
Caso contrario si (M,w) no pertence al complemento entonces M se detiene y M acepta, se cumple la equivalencia.

d. Explicar por qué la función utilizada para reducir HP a LU no sirve para reducir LU a HP.
La reducción de HP a LU funciona porque transforma detención en aceptación, ignorando si M acepta o rechaza. Sin embargo, para reducir LU a HP, necesitaríamos transformar aceptación en detención.
Esto implicaría que f(M, w) ∈ HP pero (M,w) ∉ LU, por lo que no se cumple el principio de correctitud.

e. Explicar por qué la siguiente MT Mf no computa una reducción de HP a LU: dada una cadena válida (<M>, w), Mf ejecuta M sobre w, si M acepta entonces genera la salida (<M>, w), y si M rechaza entonces genera la cadena 1.

Mf no computa una reducción de HP a LU ya que no cumple con la condición de que sea total computable. M no es total computable ya que puede loopear, por lo que no puede ser parte de una reducción. 
Puede loopear ya que ejecutar un código de máquina sin ningún tipo de restricción, entonces si puede loopear no puede ser parte de una función de reducción.

Ejercicio 2. Sabiendo que LU ∈ RE y LU^C ∈ CO-RE:

a. Probamos en clase que existe una reducción de LU a LƩ*. En base a esto, ¿qué se puede
afirmar con respecto a la ubicación de LƩ* en la jerarquía de la computabilidad?

Si existe una reducción de LU a LƩ* y LU ∈ RE, entonces significa que LƩ* ∈ RE.

b. Se prueba que existe una reducción de LUC a L∅ ¿qué se puede afirmar con respecto a la ubicación de L∅ en la jerarquía de la computabilidad?
Si existe una reducción de LUC a L∅ y LUC ∈ CO-RE, entonces significa que LƩ* ∈ CO-RE.

Ejercicio 3. Sea el lenguaje DHP = {wi | Mi para a partir de wi} (considerar el orden canónico}.
Encontrar una reducción de DHP a HP. Comentario: hay que definir la función de reducción y
probar su total computabilidad y correctitud.

Lo que se puede realizar es que la función de reducción ejecute la MT *Mi* a partir de la entrada *wi*. 
(Mi, wi) ∈ DHP ≤ f((Mi,wi)) ∈ HP.

Esto tiene 2 posibles soluciones:
Si Mi para con wi → *f(Mi, wi) ∈ HP* lo que nos permite comprobar que *Mi* para en la entrada *wi* → wi está en DHP (Mi, wi) ∈ DHP.*
Si Mi no para con wi → *f(Mi, wi) ∉ HP* lo que nos permite comprobar que *Mi* no va a parar en la entrada *wi → *wi no está en DHP *(Mi, wi) ∉ DHP.*

Ejercicio 4. Sean TAUT y NOSAT los lenguajes de las fórmulas booleanas sin cuantificadores
tautológicas (satisfactibles por todas las asignaciones de valores de verdad) e insatisfactibles
(insatisfactibles por todas las asignaciones de valores de verdad). Encontrar una reducción de
TAUT a NOSAT. Comentario: hay que definir la función de reducción y probar su total
computabilidad y correctitud.

siendo ϕ una fórmula booleana tautológica podemos decir que si ϕ ∈ TAUT entonces ϕ va a dar como resultado verdadera para toda asignación de valores, entonces podemos decir que ¬ϕ es falsa para toda asignación por lo que f(ϕ) ∈ NOSAT.
Si ϕ ∉ TAUT Existe al menos una asignación que hace ϕ falsa. Por lo tanto, ¬ϕ es verdadera bajo esa asignación, implicando que f(ϕ) ∉ NOSAT.

ϕ ∈ TAUT ≤ f(ϕ) ∈ NOSAT

Si tenemos (A v ¬A) 

| *A* | *¬A* | *(A v ¬A)* |   
| --- | --- | --- |
| V | F | V |
| F | V | V |

ϕ es una tautología (ϕ ∈ TAUT).

| *A* | *¬A* | *¬(A v ¬A)*
| --- | --- | --- |
| V | F | F | 
| F | V | F | 
f(ϕ) es una contradicción (f(ϕ) ∈ NOSAT).


Entonces podemos decir que f(ϕ) = ¬ϕ es una reduccion valida


Ejercicio 5. Se prueba que existe una reducción de LUC a LƩ* (y así, como LUC ∉ RE, entonces se cumple que LƩ* ∉ RE). 

La reducción es la siguiente. Para toda w: f((<M1>, w)) = <M2>, tal que M2,
a partir de su entrada v, ejecuta |v| pasos de M1 a partir de w, y acepta sii M1 no acepta. Probar
que la función definida es efectivamente una reducción de LUC a LƩ*. 
Comentario: hay que probar su total computabilidad y correctitud


