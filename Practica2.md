Ejercicio 1. Responder breve y claramente los siguientes incisos:
 
1. ¿En qué se diferencian los lenguajes recursivos, los lenguajes recursivamente numerables 
no recursivos y los lenguajes no recursivamente numerables? 


recursivos: Lenguajes aceptados por MT que siempre paran.
recursivamente numerables: Lenguajes aceptados por MT que a partir de algunas instancias negativas no paran.
no recursivamente numerables: Lenguajes sin MT que los acepten (a partir de algunas instancias positivas no paran).

---

2. Probar que R ⊆ RE ⊆ L  .  Ayuda: usar las definiciones. 

Demostración de R ⊆ RE

Definición de R: Un lenguaje L es recursivo si existe una MT M que lo decide, es decir, para toda cadena w ∈ Σ∗:
Si w ∈ L, M para en qA(acepta).
Si w ∉ L M para en qR(rechaza).

Definición de R: Un lenguaje L es recursivamente enumerable si existe una MT M que lo acepta, es decir
Si w ∈ L, M para en qA(acepta).
Si w ∉ L M puede no parar o parar en qR(rechaza).

Toda MT que decide L (pertenece a R) también acepta L, ya que cumple con las condiciones de RE. Por lo tanto, R⊆RE.

Demostración de RE ⊆ L:

Definición de L: Es el conjunto de todos los lenguajes posibles sobre Σ∗ , es decir, todos los subconjuntos de Σ∗.

Inclusión: Todo lenguaje recursivamente enumerable es un subconjunto de Σ∗, por definición. Por lo tanto, RE⊆L.

Conclusión: R ⊆ RE ⊆ L, ya que:

Toda MT que decide un lenguaje también lo acepta y porque los lenguajes RE son subconjuntos de Σ∗.

---

3. Dijimos en clase que el hecho de que si L es recursivo entonces LC también lo es, significa 
en  términos  de  problemas  que  si  un  problema  es  decidible  entonces  también  lo  es  el 
problema  contrario.  ¿Qué  significa  en  términos  de  problemas  que  la  intersección  de  dos 
lenguajes recursivos es también un lenguaje recursivo? 



Definiciones clave
1. **Lenguaje recursivo (decidible):** Un lenguaje \( L \) es recursivo si existe una Máquina de Turing (MT) que **siempre se detiene** y decide si una cadena \( w \) pertenece a \( L \) o no.

2. **Intersección de lenguajes:** Dados dos lenguajes \( P1 \) y \( P2 \), su intersección \( P = P1 ∩ P2 \) contiene todas las cadenas que pertenecen **simultáneamente** a \( P1 \) y \( P2 \).


**Demostración formal**

Sean \( P1 \) y \( P2 \) lenguajes recursivos. Entonces, existen MTs \( M1 \) y \( M2 \) que deciden \( P1 \) y \( P2 \), respectivamente, y **siempre paran**. Construimos una MT \( M \) para decidir \( P = P1 ∩ P2 \):

**Algoritmo de \( M \):**
1. **Ejecutar \( M1 \) sobre la entrada \( w \):**
   - Si \( M1 \) **rechaza** \( w \), \( M \) rechaza \( w \).
   - Si \( M1 \) **acepta** \( w \), continuar al paso 2.
2. **Ejecutar \( M2 \) sobre \( w \):**
   - Si \( M2 \) **acepta** \( w \), \( M \) acepta \( w \).
   - Si \( M2 \) **rechaza** \( w \), \( M \) rechaza \( w \).



**Conclusión**
La construcción de \( M \) demuestra que:
- La **intersección de lenguajes recursivos** es recursiva.
- Esto significa que si dos problemas son decidibles, su combinación mediante una condición lógica **"Y"** también es decidible.

---

4. Explicar por qué no es correcta la siguiente prueba de que si L ∈ RE, también LC ∈ RE: dada 
una  MT  M  que  acepta  L,  entonces  la  MT  M’,  igual  que  M  pero  con  los  estados  finales 
permutados, acepta LC.  

La prueba es incorrecta porque permutar los estados finales de la máquina M no altera el comportamiento fundamental de la máquina en cuanto a su proceso de cómputo. En una máquina de Turing que reconoce un lenguaje L (es decir, que pertenece a 𝑅𝐸), se garantiza que para cada entrada 𝑥 ∈ 𝐿
la máquina se detendrá en un estado de aceptación; sin embargo, para 𝑥 ∉ 𝐿 la máquina puede rechazar o, más problemáticamente, entrar en un bucle infinito.

Al construir la máquina 𝑀′ igual que 𝑀 pero con los estados finales permutados", lo único que se logra es cambiar la forma en que se etiquetan ciertos estados, sin modificar el hecho de que la máquina original podría no detenerse en entradas que no pertenecen a 𝐿. Por ello, 𝑀′ no necesariamente acepta todo lo que está en 𝐿𝐶(el complemento de 𝐿), ya que en los casos en los que 𝑀 no se detiene, 𝑀′ tampoco lo hará. En otras palabras, el hecho de "permutar" los estados de aceptación no implica que la máquina se comporte como una máquina que reconoce el complemento, ya que la propiedad clave de aceptación (detenerse y entrar en un estado de aceptación) no se garantiza para las entradas en 𝐿𝐶.


---

5. ¿Qué lenguajes de la clase CO-RE tienen MT que los aceptan? ¿También los deciden?  

El conjunto CO-RE tiene los complementos de los lenguajes del conjunto RE (L ∈ RE si LC ∈ CO-RE)

--- 

6. Probar que el lenguaje Ʃ* de todas las cadenas y el lenguaje vacío ∅ son recursivos. Alcanza 
con plantear la idea general. Ayuda: encontrar MT que los decidan.  
1. Demostración de que Σ∗ es recursivo
El lenguaje contiene todas las posibles cadenas sobre el alfabeto Σ. 

Una máquina de Turing que decida este lenguaje puede funcionar de la siguiente manera:

- Leer la entrada.
- Aceptar inmediatamente, sin importar cuál sea la cadena, ya que toda cadena pertenece a Σ∗.

Esta máquina de Turing siempre acepta, lo que significa que decide Σ∗, y por lo tanto, Σ∗ es un lenguaje recursivo.

2. Demostración de que ∅ es recursivo

El lenguaje ∅ no contiene ninguna cadena. Para decidirlo, podemos construir una MT que funcione así:

- Leer la entrada.
- Rechazar inmediatamente, sin importar cuál sea la cadena, ya que ninguna cadena pertenece a ∅.

Esta MT siempre rechaza, lo que implica que decide ∅ y, por lo tanto, ∅ es un lenguaje recursivo.

Conclusión
Ambos lenguajes son decididos por máquinas de Turing que aceptan o rechazan en tiempo finito para cualquier entrada. Esto prueba que Σ∗ y ∅ son lenguajes recursivos.
---

7. Probar que todo lenguaje finito es recursivo.  Alcanza con  plantear la idea general.  Ayuda: 
encontrar una MT que lo decida (pensar cómo definir sus transiciones para cada una de las 
cadenas del lenguaje). 

Un lenguaje 𝐿 es recursivo si existe una MT que lo decide, es decir, que acepta todas las cadenas en 𝐿 y rechaza todas las que no están en L, siempre en tiempo finito.

Si 𝐿 es finito, esto significa que contiene un número limitado de cadenas 𝑤1,𝑤2,𝑤𝑛​. Podemos construir una MT que compare la entrada con cada una de estas cadenas y decida si aceptarla o rechazarla.

La MT para un lenguaje finito 𝐿={𝑤1,𝑤2,...,𝑤𝑛} funciona así:

- Leer la entrada.
- Compararla con cada una de las cadenas 𝑤𝑖 w en 𝐿:
   - Si la entrada coincide con alguna 𝑤𝑖, aceptar.
   - Si la entrada no coincide con ninguna 𝑤𝑖, rechazar.
- Detenerse siempre en tiempo finito.

Dado que la MT siempre se detiene después de comparar la entrada con las cadenas en 𝐿, esto demuestra que todo lenguaje finito es recursivo, ya que puede ser decidido por una MT.
---

Ejercicio 2. Considerando la Propiedad 2 estudiada en clase: 

1. ¿Cómo implementaría la copia de la entrada w en la cinta 2 de la MT M? 
Se tendría que recorrer toda la entrada w de la cinta 1, cada vez que se lee un carácter diferente a Blanco se copia en la cinta 2. Una vez que se encuentre con Blanco en la cinta 1 (se terminó w), se tendría que mover hacia la izquierda hasta encontrar Blanco para volver al inicio de la cadena. Cuando se encuentre Blanco, se debe mover una posición hacia la derecha y el cabezal habrá vuelto al inicio de w en cinta 1. Lo mismo tendría que hacerse en cinta 2.
2. ¿Cómo implementaría el borrado del contenido de la cinta 2 de la MT M? 
Para borra rel contenido de la cinta 2, cada vez que se encuentre un carácter diferente a Blanco en la cinta 2 se reemplaza por Blanco, vaciando la cinta.
 

Ejercicio 3. Probar: 
1. La clase R es cerrada con respecto a la operación de unión. Ayuda: la prueba es similar a la desarrollada para la intersección. 

Para probar que R es cerrada creariamos una MT decisora para L1 U L2 apartir de las decisoras de L1 y L2.

Construcción de M3:

Para esto decimos que dado w hacemos lo siguiente

1 - Ejecutamos la  M1:
   - Si M1 acepta entonces w pertence a L1 y M3 acepta
   - Si M1 rechaza entonces w no pertence a L1 vamos al siguiente
2 - Ejecutamos la M2:
   - Si M1 acepta entonces w pertence a L2 y M3 acepta
   - Si M2 rechaza entonces w no pertence ni a L1 ni a L2 M3 rechaza, por lo que 𝑤 ∉ 𝐿1 y 𝑤 ∉ 𝐿2.

Como M1 y M2 siempre terminan entonces M siempre termina y como acepta L1 U L2 se prueba que L1 U L2 es recursivo

2. La clase RE es cerrada con respecto a la operación de intersección. 
Ayuda: la prueba es similar a la desarrollada para la clase R. 

Yo no creo que sea cerrada a la intersección.
Si tuvieramos dos lenguajes que fueran recursivamente enumerables L1 y L2 no siempre la L1 ∩ L2 sera será también un lenguaje de la clase RE.

1 - Máquinas de Turing no deterministas: Si realizamos la intersección de dos lenguajes podría dar lugar a un lenguaje en el que, para una cadena 
𝑤 la maquina tendria que realizar una verificacion para saber si pertence a L1 y L2 no podemos garantizar que ambas máquinas terminen en tiempo finito.

2 - Comportamiento no siempre terminante: No siempre se puede garantizar la terminación de ambas máquinas, lo que puede resultar en un bucle infinito sin una respuesta definitiva.

Si 𝑤 pertenece a la intersección entonces ambas máquinas deben aceptar 𝑤 Pero si una de las máquinas no acepta, lo que puede ocurrir es que se quede en un bucle infinito(ya que las máquinas de Turing para lenguajes RE).

Entonces si M1 acepta w, pero M2 no termina no sabremos si w pertenece porque no podemos deducir si 𝑀2 eventualmente aceptará o no 𝑤.

Caso contrario si fuera factible verificar si una cadena w pertence a L1 y L2 garantizando que las dos terminaran entonces RE seria cerrada con respecto a la operación de intersección.


Ejercicio  4.  Sean  L1  y  L2  dos  lenguajes  recursivamente  numerables  de  números  naturales 
codificados en unario (por ejemplo, el número 5 se representa con 11111). Probar que también 
es recursivamente numerable el lenguaje L = {x | x es un número natural codificado en unario, y 
existen y, z, tales que y + z = x, con y ∈ L1, z ∈ L2}.  
Ayuda: la prueba es similar a la vista en clase, de la clausura de la clase RE con respecto a la 
operación de concatenación.  

Para probar este caso se podrian utilizar una MT M la cual tendria M1 la cual acepta L1 y M2 la cual acepta L2 esto para poder verificar que la cadena unaria recibida de entrada se encuentra en L1 o en L2 probando que existe una suma la cual da x. 
Por ultimo nos quedaria una M3 que genere todas las posibles cadenas de entrada para M1 y M2 nuestro flujo quedaria:


               M
               
--w--> M3 -------------(y,z)-----------y---> M1
                                    |
                                    └─z────> M2

Por ejemplo si se quiere sumar 5(11111) la maquina M3 recibiria 11111 y generaria {(vacio,11111),(1,1111),(11,111),(111,11),(1111,1),(11111,vacio)}.

Para que M3 genere las posibles cadenas 

Dado un número natural x codificado en unario M3 debe generar z e y

- Cinta 1: Almacena y, la primera parte de la partición de x.
- Cinta 2: Almacena z, la segunda parte de la partición de x.

Funcionamiento: 
El cabezal de la Cinta 1 comienza al inicio de la secuencia de '1's.
El cabezal de la Cinta 2 comienza en la primera celda vacía de esa cinta.
Cada iteración mueve un 1 de la Cinta 1 a la Cinta 2, creando una nueva partición (𝑦,𝑧)

Entonces teniendo x = 5 en la primera iteración tendriamos 

primera iteración: 
   - cinta 1 = 11111
   - cinta 2 = vacio
segunda iteración:
   - cinta 1 = 1111
   - cinta 2 = 1   
...
ultima iteración :
   - cinta 1 = vacio 
   - cinta 2 = 11111

Cada vez que se itera se envia a la M1 y M2 (y,z)

- si M1 sobre y acepta entonces y ∈ L1 
- si M2 sobre z acepta entonces z ∈ L2 
- Si ambas máquinas aceptan, entonces aceptamos x y M
- Si no, se prueba con la siguiente partición generada por 𝑀3.

Si se prueban todas las particiones sin éxito, M no se detiene comprobando que L es RE



Ejercicio 5. Dada una MT M1 con alfabeto Γ = {0, 1}: 
1. Construir una MT M2, utilizando la MT M1, que acepte, cualquiera sea su cadena de entrada, 
sii la MT M1 acepta al menos una cadena.

Basicamente MT M2 debera ir generando cadenas con el alfabeto de 0 y 1, estas cadenas debera ir pasandolas a M1 para saber si acepta o no.

- si M1 acepta la entrada pasa al estado qA y M2 también

ahora que pasa si no acepta nunca?
Existe la posibilidad de que nunca termine M1 de chequear. Para esto usamos un indice el cual generara i entradas las cuales se le pasara a M1 

Para cada cadena generada (por ejemplo, primero la cadena vacía, luego "0", luego "1", "00", "01", "10", "11", y así), 𝑀2 le da exactamente i pasos a 𝑀1 para ver si acepta esa cadena.

- Si M1 acepta alguna cadena en su simulación con i pasos, entonces M 2 pasa al estado de aceptación qA y acepta la entrada.
- Si después de probar todas las cadenas de longitud ≤ i M1 no acepta el contador i se incrementa en 1, haciendo que M2 genere cadenas de longitud i + 1
- Este proceso se sigue repitiendo, y con cada ciclo M2 genera cadenas más largas y le da más tiempo a M1 para aceptar.


2. ¿Se puede construir además una MT M3, utilizando la MT M1, que acepte, cualquiera sea su 
cadena de entrada, sii la MT M1 acepta a lo sumo una cadena? Justificar.  
Ayuda para la parte (1): si M1 acepta al menos una cadena, entonces existe al menos una cadena 
de símbolos 0 y 1, de tamaño n, tal que M1 la acepta en k pasos. Teniendo en cuenta esto, pensar 
cómo M2 podría simular M1 considerando todas las cadenas de símbolos 0 y 1 hasta encontrar 
eventualmente una que M1 acepte (¡cuidándose de los casos en que M1 entre en loop!).

Dado que el alfabeto de M1 es infinito, no es posible construir una máquina de Turing M3 que acepte cualquier cadena de entrada si y solo si M1 acepta a lo sumo una cadena, ya que necesitaríamos probar infinitas cadenas y no podríamos asegurar la aceptación de solo una de ellas sin generar todas las posibles cadenas, lo cual es inviable.