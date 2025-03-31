Ejercicio 1. ¿Qué es una MT universal? 

Una  máquina  de  Turing  universal  (MT  U)  es  una  máquina  de  Turing  capaz  de  ejecutar  cualquier  otra MT. La MT U recibe como entrada una MT M (codificada mediante 
una cadena <M>) y una cadena w, y ejecuta M a partir de w.

Ejercicio  2.  Explicar  cómo enumeraría  los  números naturales pares, los números enteros, los números racionales (o fraccionarios), y las cadenas de Ʃ* siendo Ʃ = {0, 1}. 

Para enumerar los números naturales pares son aquellos que son divisibles entre 2, es decir, tienen la forma 
0,2,4,6,8,…. Para enumerar los números naturales pares, simplemente comenzamos desde 0 y vamos incrementando de 2 en 2

Para enumerar los números enteros, se tendría que primero escribir el 0 seguido de un separador, continuar con el 1 y un separador y luego su negativo -1 seguido de un separador, escribir después el 2 con separador y después su negativo -2, y así infinitamente.

Una forma común de enumerar los números racionales es usando una tabla de fracciones 𝑝/𝑞, donde 𝑝 y 𝑞 son enteros. Para evitar repeticiones (por ejemplo, 2/4 y 1/2 son el mismo número), se pueden considerar las fracciones de la forma irreducible.
Podemos usar un esquema de "recorrido en espiral" o diagonalización de Cantor para enumerar todos los números racionales. En este esquema, comenzamos desde la fracción 1/0 , luego 1/1, -1/1,1/2,-1/2 , y así sucesivamente. 

Para enumerar todas las cadenas de Ʃ* siendo Ʃ = {0, 1}, se tienen que escribir todos las cadenas de forma creciente en cuanto a su largo. Es decir, primero se escriben todas las cadenas con largo 0 (que sería el vacío), luego todas las cadenas con largo 1 (0, 1), las cadenas con largo 2 (00, 01, 01, 10), y así infitamente. Luego de escribir cualquier cadena se tendría que escribir un separador, por ejemplo una coma “,”.


Ejercicio 3. Dar la idea general de cómo sería una MT que, teniendo como cadena de entrada 
un número natural i, genera la i-ésima fórmula booleana satisfactible según el orden canónico. 
Comentario:  asumir  que  existen  una  MT  M1  que  determina  si  una  cadena  es  una  fórmula 
booleana, y una MT M2 que determina si una fórmula booleana es satisfactible.    
 
Ejercicio 4. Sea M1 una MT que genera en su cinta de salida todas las cadenas de un lenguaje 
L. Dar la idea general de cómo sería una MT M2 que, usando M1, acepte una cadena w sii w ∈ L.  
 
Ejercicio  5.  El  lenguaje  LU  =  {(<M>,  w)  |  M  acepta  w}  se  conoce  como  lenguaje  universal,  y 
representa el problema general de aceptación. Probar que LU ∈ RE. Ayuda: construir una MT que 
acepte LU. 
 
Ejercicio 6. Una función f : A ⟶ B es total computable sii existe una MT Mf que la computa para 
todo elemento a  A. Sea la función f01 : Ʃ* ⟶ {0, 1} tal que: 
f01(v) = 1, si v = (<M>, w) y M para a partir de w. 
f01(v) = 0, si v = (<M>, w) y M no para a partir de w o bien v ≠ (<M>, w). 
Probar que f01 no es total computable. Ayuda: ¿con qué problema se relaciona dicha función?  
 
Ejercicio  7.  Responder  breve  y  claramente  cada  uno  de  los  siguientes  incisos  (en  todos  los 
casos, las MT mencionadas tienen una sola cinta):  
a. Probar que se puede decidir si una MT M, a partir de la cadena vacía λ, escribe alguna vez 
un símbolo no blanco. Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en un loop?  
b. Probar que se puede decidir si una MT M que sólo se mueve a la derecha,  a partir de una 
cadena w, para, Ayuda: ¿Cuántos pasos puede hacer M antes de entrar en un loop?  
c. Probar que se puede decidir si dada una MT M, existe una cadena w a partir de la cual M 
para en a lo sumo 10 pasos. Ayuda: ¿Hasta qué tamaño de cadenas hay que chequear? 
d. ¿Se puede decidir si dada una MT M, existe una cadena w de a lo sumo 10 símbolos a partir 
de la cual M para? Justificar la respuesta.  