# 99 Problemas en Racket

## Trabajando con listas

### P01 (1)  Encuentre el último de la lista

```lisp
=> (último '(a b c d))
(d)
```

### P02 (1) Encuentre los últimos dos de la lista

```lisp
=> (últimos-dos '(a b c d))
(c d)
```

### P03 (1) Encuentre el k-ésimo de la lista

```lisp
=> (elemento-en '(a b c d e) 3)
c
```

### P04 (1) Encuentre el número de elementos en la lista

### P05 (1) Invierta la lista

### P06 (1) Determine si la lista es un palíndrome

Un palíndrome se lee igual de izquierda a derecha que de derecha a izquierda. Ejemplo `(x a m a x)`.

### P07 (2) Aplane una estructura anidada de listas

Transforme una lista, que posible contenga otras listas, en una lista "plana" al reemplazar cada sublista por sus elementos (recursivamente).

```lisp
=> (aplanar '(a (b (c d) e)))
(a b c d e)
```

*Pista*: Puede utilizar las funciones predefinidas `list` y `append`.

### P08 (2) Elimine elementos consecutivos duplicados de la lista

Si una lista contiene elementos que se repiten consecutivamente, estos deben ser reemplazados por una única copia del elemento. El orden de los elementos no debe variar.

```lisp
=> (comprimir '(a a a a b c c a a d e e e e))
(a b c a d e)
```

### P09 (2) Empacar elementos consecutivos duplicados de una lista en sublistas.

Si una lista contiene elementos consecutivos duplicados, estos deben ser colocados en sublistas.

```lisp
=> (empacar '(a a a a b c c a a d e e e e))
((a a a a) (b) (c c) (a a) (d) (e e e e))
```

### P10 (1) Codificación de longitud de repetición de una lista.

Utilice el resultado del problema P09 para implementar el método de compresión llamado *longitud de repetición* (run-length encoding en inglés). Los duplicados consecutivos de un elemento se codifican como listas `(n e)` donde `n` es el número de duplicados del elemento `e`.

```lisp
=> (codificar '(a a a a b c c a a d e e e e))
((4 a) (1 b) (2 c) (2 a) (1 d) (4 e))
```

### P11 (1) Codificación de longitud de repetición modificado.

Modifique el resultado del problema P10 tal que si un elemento no tiene duplicados simplemente se copia en la lista resultante. Sólo los elementos duplicados se transfieren como listas `(n e)`.

```lisp
=> (codificar-mod '(a a a a b c c a a d e e e e))
((4 a) b (2 c) (2 a) d (4 e))
```

### P12 (2) Decodificación de una lista codificada con longitud de repetición.

Dada una lista codificada con el algoritmo de longitud de repetición como la especificada en el problema P11, construya su versión decodificada.

```lisp
=> (decodificar '((4 a) b (2 c) (2 a) d (4 e)))
(a a a a b c c a a d e e e e)
```

### P13 (2) Solución directa para la codificación de longitud de ejecución.

Implemente la codificación de longitud de ejecución directamente, es decir no utilice el resultado de P09, sino más bien cuente las repeticiones conforme vaya creando las listas `(n e)`. Al igual que en P11, simplifique el resultado reemplazando las listas de la forma `(1 x)` por `x`.

```lisp
=> (codificar-directo '(a a a a b c c a a d e e e e))
((4 a) b (2 c) (2 a) d (4 e))
```

### P14 (1) Duplicar los elementos de una lista.

```lisp
=> (dup '(a b c c d))
(a a b b c c c c d d)
```

### P15 (2) Replicar los elementos de una lista un número dado de veces.

```lisp
=> (replicar '(a b c) 3)
(a a a b b b c c c)
```

### P16 (2) Elimine cada k-ésimo elemento de una lista.

El índice inicia en `1`, no en `0`.

```lisp
=> (eliminar '(a b c d e f g h i k) 3)
(a b d e g h k)
```

### P17 (1) Parta una lista en dos partes, la longitud de la primera parte es dada.

No utilice ninguna función predefinida.

```lisp
=> (partir '(a b c d e f g h i k) 3)
((a b c) (d e f g h i k))
```

### P18 (2) Extraiga una porción de una lista.

Dados dos índices `i` y `k`, la porción es la lista que contiene los elementos entre el i-ésimo y el k-ésimo elemento de la lista original (incluyendo ambos límites). Empiece a contar los elementos de `1`.

```lisp
=> (porción '(a b c d e f g h i k) 3 7)
(c d e f g)
```

### P19 (2) Rote la lista `n` lugares a la izquierda.

```lisp
=> (rotar '(a b c d e f g h) 3)
(d e f g h a b c)
```

```lisp
=> (rotar '(a b c d e f g h) -2)
(g h a b c d e f)
```

*Pista*: Utilice las funciones predefinidas `length` y `append`, así como el resultado del problema P17.

### P20 (1) Elimine el k-ésimo elemento de la lista.

```lisp
=> (eliminar-el '(a b c d) 2)
(a c d)
```

### P21 (1) Inserte un elemento en una posición dada en una lista.

```lisp
=> (insertar-en 'alfa '(a b c d) 2)
(a alfa b c d)
```

### P22 (1) Crear una lista que contiene todos los enteros en un rango dado.

Si el primer argumento es mayor que el segundo, produzca una lista en orden descendente.

```lisp
=> (rango 4 9)
(4 5 6 7 8 9)
```

```lisp
=> (rango 6 2)
(6 5 4 3 2)
```

### P23 (2) Extraiga un número dado de elementos seleccionados al azar de una lista.

Los elementos seleccionados deben ser retornados en una lista.

```lisp
=> (seleccionar-al-azar '(a b c d e f g h) 3)
(e d a)
```

*Pista*: Utilice el generador de números pseudo-aleatorios de racket y el resultado del problema P20.

### P24 (1) Lotería: elija `n` números diferentes aleatoriamente del conjunto `1..M`.

Los números elegidos deben ser retornados en una lista.

Si `n` es `6` y `m` es `49`:

```lisp
=> (lotería 6 49)
(23 1 17 33 21 37)
```

*Pista*: combine las soluciones a los problemas P22 y P23.

### P25 (1) Generar una permutación aleatoria de elementos de una lista.

```lisp
=> (permutación-azar '(a b c d e f))
(b a d c e f)
```

*Pista*: Utilice la solución al problema P23.

### P26 (2) Genere las combinaciones de `k` objetos distintos elegidos de `n` elementos de una lista.

¿De cuántas maneras diferentes puede elegirse un comité de 3 personas de un grupo de 12? Sabemos que hay `C(12, 3) = 220` posibilidades (`C(n, k)` denota el conocido coeficiente binomial). Para los matemáticos puros este resultado podría ser suficiente. Pero nosotros queremos generar realmente todas las posibilidades en una lista.

```lisp
=> (combinaciones 3 '(a b c d e f))
((a b c) (a b d) (a b e) ...)
```

### P27  (2) Agrupar los elementos de un conjunto en subconjuntos disjuntos.

* ¿De cuántas maneras diferentes puede un grupo de 9 personas trabajar en 3 subgrupos disjuntos de 2, 3 y 4 personas? Escriba una función que genere todas las posibilidades y las retorne en una lista.

```lisp
=> (agrupar3 '(abel beatriz carla david eva felipe gabriela hugo ignacio))
(((abel beatriz) (carla david eva) (felipe gabriela hugo ignacio)) ...)
```

* Generalice el predicado anterior tal que podamos especificar en una lista los tamaños de los grupos, y el predicado retornará las listas correspondientes.

```lisp
=> (agrupar '(abel beatriz carla david eva felipe gabriela hugo ignacio) '(2 2 5))
(((abel beatriz) (carla david) (eva felipe gabriela hugo ignacio)) ...)
```

Note que no queremos las permutaciones de los miembros de los grupos; por ejemplo `'((abel beatriz) ...)` es la misma solución que `((beatriz abel) ...)`

Ud podría encontrar más información acerca de este problema combinatorio en algún buen libro de matemática discreta bajo el término "coeficientes multinomiales".

### P28 (2) Ordenar una lista de listas de acuerdo con la longitud de las sublistas.

* Supongamos que una lista contiene elementos que son a su vez listas. El objetivo es ordenar los elementos de esta lista de acuerdo con sus longitudes. Es decir, las listas más cortas de primero, las más largas después.

```lisp
=> (ordenar-long '((a b c) (d e) (f g h) (d e) (i j k l) (m n) (o))
((o) (d e) (d e) (m n) (a b c) (f g h) (i j k l))
```

* Nuevamente, supongamos que una lista contiene elementos que son a su vez listas. Esta vez, el objetivo es ordenar los elementos de acuerdo con su frecuencia de longitud. Es decir, las listas con longitudes poco frecuentes aparecerán de primero, las listas con longitudes más frecuentes aparecerán después.

```lisp
=> (ordenar-frec-long '((a b c) (d e) (f g h) (d e) (i j k l) (m n) (o))
((i j k l) (o) (a b c) (f g h) (d e) (d e) (m n))
```

Note que en el ejemplo anterior, las primeras dos listas en el resultado tienen longitud 4 y 1, ambas longitudes aparecen sólo una vez. El tercer y cuarto elementos tienen largo 3 el cual aparece dos veces (hay dos listas con esta longitud). Y finalmente, las últimas tres listas tienen largo 2, esta es la longitud más frecuente.

## Árboles binarios

Un árbol binario o es vacío o está compuesto de un elemento raíz y dos sucesores los cuales son a su vez árboles binarios.
En Racket representamos el árbol vacío con `null` o `'()` y el árbol no vacío con la lista `(X I D)`, donde `X` denota el elemento raíz y tanto `I` como `D` representan los subárboles izquierdo y derecho respectivamente. El árbol de la figura se representa con la siguiente lista:

![árbol binario](https://f93da235-a-62cb3a1a-s-sites.googlegroups.com/site/prologsite/prolog-problems/4/p67.gif?attachauth=ANoY7cobxmZ4rrWGye8FlDJ_qEusWCh18ytBTUdILLMwn1h7rNgYEmK1CcXwUK3cZT5tQhdZIGGQxcTiFN_RMEaTDqPeT92dOUB6-B9dcmpQuZ4nDMYh3EXahUJPgXze6cOaYf7oIGKfrtZsxINtL3ANHVPwKL6cOskPNM4_5Z7edUfwHAjb8P5RcOzNjctPHokwooHZSKWdUqlDhSmOqiiiKpXBS577j3wr8K69Dd6iXT6WFZ_7ohI%3D&attredirects=0)

```lisp
(a (b (d () ()) (e () ())) (c () (f (g () ()) ())))
```

Un árbol binario que sólo contiene su nodo raíz:

```lisp
(a () ())
```

El árbol binario vacío:

```lisp
()
```

Puede probar sus funciones utilizando estos árboles de ejemplo.

### P54A (1) Verifique que un término dado representa un árbol

Escriba un predicado `árbol-bin?` que retorna `#t` si y solo si su argumento es una lista que representa un árbol binario.

```lisp
=> (árbol-bin? (a (b () ()) ()))
#t

=> (árbol-bin? (a (b () ())))
#f
```

### P55 (2) Construya árboles binarios completamente balanceados

En un árbol binario completamente balanceado se cumple la siguiente propiedad para cualquier nodo: el número de nodos en su subárbol izquierdo y el número de nodos en su subárbol derecho son casi iguales, es decir la diferencia no puede ser mayor que 1.

Escriba una función `árbol-bin-cbal` para construir árboles binarios completamente balanceados para un número dado de nodos. La función debería generar todas las posibles soluciones utilizando backtracking. Utilice el símbolo `'x` como información en todos los nodos del árbol.

```lisp
=> (árbol-bin-cbal 4)
(x (x (x () ()) ()) (x () ()))
```

### P56 (2) Árboles binarios simétricos

Un árbol binario es simétrico si se puede dibujar una línea vertical a través de la raíz del árbol y el subárbol derecho es una imagen espejo del subárbol izquierdo. Escriba una función `simétrico?` para verificar si un árbol es simétrico. Pista: escriba primero una función `espejo?` para determinar si un árbol es la imagen espejo de otro. Sólo nos interesa la estructura del árbol, no el contenido de los nodos.

```lisp
=> (simétrico? '(3 (2 (1 () ()) ()) (5 () (7 () ()))))
#t
```

### P57 (2) Árboles de búsqueda binarios (diccionarios)

Escriba una función para construir un árbol de búsqueda binario a partir de una lista de números.

```lisp
=> (árbol-búsqueda-bin '(3 2 5 7 1))
(3 (2 (1 () ()) ()) (5 () (7 () ())))
```

### P58 (2) Paradigma generar-y-probar

Aplique el paradigma de generación y prueba para construir todos los árboles binarios completamente balanceados y simétricos dado un número de nodos.

```lisp
((x (x () (x () ())) (x (x () ()) ()))
 (x (x (x () ()) ()) (x () (x () ()))))
```

¿Cuántos de estos árboles existen con 57 nodos? Investigue cuántas soluciones hay para un número dado de nodos. ¿Qué pasa si el número de nodos es par?

### P59 (2) Construya árboles binarios balanceados por altura

En un árbol binario balanceado por altura se cumplen las siguientes propiedades para cada nodo: la altura de su subárbol izquierdo y la altura de su subárbol derecho son casi iguales, es decir difieren en no más de 1.

Escriba una función `árbol-bin-abal` para construir árboles binarios balanceados por altura para una altura dada. La función debería generar todos los árboles utilizando backtracking. Utilice el símbolo `'x` como valor para todos los vértices.

```lisp
=> (árbol-bin-abal 3)
((x (x (x () ()) (x () ())) (x (x () ()) (x () ())))
 (x (x (x () ()) (x () ())) (x (x () ()) ()))
 ...)
```

### P60 (2) Construya árboles binarios balanceados por altura con un número dado de nodos

Considere un árbol binario balanceado por altura de altura `H`. ¿Cuál es el número máximo de nodos que puede contener? Claramente, $max_n = 2^{H} - 1$. Sin embargo, cuál es número mínimo $min_n$. Esta pregunta es más difícil. Intente encontrar una expresión recursiva e impleméntela como una función `(num-min-nodos altura)`.

Por otro lado, podríamos preguntar ¿cuál es la altura máxima que puede tener un árbol binario balanceado por altura de $n$ nodos? `(altura-max num-nodos)`.

Ahora podemos atacar el problema principal: contruir todos los árboles binarios balanceados por altura con un número dado de nodos.

```lisp
=> (árbol-bin-abal-nodos 15)
...
```
 ¿Cuántos árboles hay para $N = 15$.

### P61 (1) Cuente las hojas de un árbol binario

Una hoja es un árbol que no tiene hijos. Escriba una función `(contar-hojas árbol-bin)` que las cuente.

### P61A (1) Agregue las hojas de un árbol binario en una lista

Una hoja es un árbol que no tiene hijos. Escriba una función `(hojas árbol-bin)` para agregarlas todas en una lista.

### P62 (1) Agregue los nodos internos de un árbol binario en una lista

Un nodo interno de un árbol binario tiene ya sea uno o dos hijos no vacíos. Escriba una función `(internos árbol-bin)` para agregarlos todos en una lista.

### P62B (1) Agregue los nodos de un nivel dado en una lista

Un nodo de árbol binario está en el nivel $n$ si el camino desde la raíz hasta el nodo tiene longitud $n - 1$. La raíz del nodo está en el nivel 1. Escriba una función `(nodos-en-nivel n)` para agregar todos los nodos que se encuentran de un nivel dado en una lista.

La función `nodos-en-nivel` se puede utilizar para construir una función `orden-por-nivel` para crear la secuencia ordenada por nivel de los nodos de un árbol binario. Sin embargo hay formas más eficientes de hacer esto.

### P63 (2) Construya un árbol binario completo

Un árbol binario completo con altura $H$ se define de la siguiente manera: los niveles $1, 2, 3, ..., H-1$ contienen el número máximo de nodos (es decir $2^{i-1}$ en el nivel $i$, note que empezamos a contar los niveles desde 1 en la raíz). En el nivel $H$, el cual podría contener menos que el máximo número de nodos posibles, todos los nodos están "ajustados a la izquierda". Esto quiere decir que en un recorrido ordenado por nivel todos los nodos internos aparecen primero, las hojas de segundo, y los sucesores vacíos (los `'()` que en realidad no son nodos) aparecen de último.

Particularmente, los árboles binarios completos se utilizan como estructuras de datos (o esquemas de direccionamiento) para heaps.

En un árbol binario completo podemos asignarle un número de dirección a cada nodo al enumerarlos en orden por nivel, empezando por la raíz con el número 1. Al hacer esto, nos damos cuenta que para cada nodo $X$ con dirección $D$ se sostiene la siguiente propiedad: la dirección de los sucesores izquierdo y derecho de $X$ son $2A$ y $2A+1$ respectivamente, suponiendo que dichos sucesores existen. Este hecho se puede utilizar para construir elegantemente un árbol binario completo `(árbol-bin-completo num-nodos)`.

### P64 (2) Disposición de un árbol binario (1)

Como preparación para dibujar un árbol binario, se necesita de un algoritmo de disposición (layout) para determinar la posición de cada no en una malla rectangular. Es posible pensar en varios métodos de disposición, uno de los cuáles se muestra en la siguiente figura.

![disposición1](https://f93da235-a-62cb3a1a-s-sites.googlegroups.com/site/prologsite/prolog-problems/4/p64.gif?attachauth=ANoY7cp2vnM7GXNAGN1drzdn8IlgqLRLS1fyWPwqrAHJSCGJM6yc-e_GsncdDL6epiU3xCJt-23ZtD3ZNVHgGLAXZmpc2KqUV7gAWkUR1vdQUdjMcyb5KnXGPL4ziSsLFOGZOR8dQc_nCBvw4ZvglyaWNfOwpbcbJrz1tpl4pCDuLLig6IU2NaqQFVNDh8W0CaGebdpNh2RhwIJsXpg8RQRXAf4xcQHmjv4poIvqMLJs9SGaNUtucfQ%3D&attredirects=0)

En esta estrategia, la posición de un nodo $v$ se obtiene a través de las siguientes reglas:
+ $x(v)$ es igual a la posición del nodo $v$ en la secuencia en-orden.
+ $y(v)$ es igual a la profundidad del nodo $v$ en el árbol.

Esriba una función `(disposición-1 árbol-bin)` que retorne una lista nodos con sus correspondientes coordenadas $x$ y $y$.

### P65 (2) Disposición de un árbol binario (2)

Un método alternativo de disposición se muestra en la siguiente figura.

![disposición2](https://f93da235-a-62cb3a1a-s-sites.googlegroups.com/site/prologsite/prolog-problems/4/p65.gif?attachauth=ANoY7cqa2VEK5NFC6eC9zkwxoWDNN8ivmOzdJk3qx3K_R5k6QkHQeoAE170MZ-mznViqsPuQCfWj_yZePw47Myrn6adr2yaxGNIIvKZuBq9qjmMAtFGcpk5tKUCFquLkJBJSiHERN38EVPVgHWMK0jHddQSaux1K426GI9mobj9ht8mQcP_pjVt62BeS4Sb18hGp2mk5kGGLX_Wwb4CBg2M2DaFoEqCYDANwfALgUVOUuPcTxxcBRNk%3D&attredirects=0)

Encuentre las reglas y escriba la función correspondiente `(disposición-2 árbol-bin)`. Pista: en un nivel dado, la distancia horizontal entre nodos vecinos es constante.

### P66 (3) Disposición de un árbol binario (3)

Una estrategia más se muestra en la siguiente figura.

![disposición3](https://f93da235-a-62cb3a1a-s-sites.googlegroups.com/site/prologsite/prolog-problems/4/p66.gif?attachauth=ANoY7cq5g9hd7iV_h5hOQSyQoYrQaqvI8Wc60DqdzSLXQi_uVhGxNEKf3nFpMAQ9ZSaHONnlI3GQMrMO22-fzqxndvmRZ0s7MMqHTlUo5vaI-BRa1-xnHnxXdNuA0h14c2kKAIq3O1-KVrX-Q_Ds4_iWa6z4HeqBbwfwlFI3ZxbtAaNcJMVTKtQOhf9lufiUdlhEc4NC0XTsXcBBXujxBoHelDiC_2DroAsGy6CCCqKyDSqFxFJbOnw%3D&attredirects=0)

El método produce una disposición muy compacta mientras que mantiene cierta simetría en cada nodo. Encuentre las reglas y escriba la función correspondiente `(disposición-3 árbol-bin)`. Pista: considere la distancia horizontal entre un nodo y sus sucesores. ¿Qué tan ajustadamente puede compactar juntos dos subárboles para construir el árbol binario combinado?

Nota: este es un problema difícil ¡No se dé por vencida/vencido muy pronto!

¿Cuál disposición prefiere?

### P67 (2) Representación en hilera de un árbol binario

Considere el siguiente árbol binario.

![árbol-hilera](https://f93da235-a-62cb3a1a-s-sites.googlegroups.com/site/prologsite/prolog-problems/4/p67.gif?attachauth=ANoY7cpfHR6B-eOJycVX0NbGXRB3O3SlQd9eyVuwGMXxB2_EU7zwFTk6VtFLs8S5afnpt2YSDH4R8KJOlzGOLfVnq26J-MYRoOsawrI-LxivFtAao-nbZB8yAlpPP6gplbY4xeGI0VB-kZSYjFi7BtKa5P0teoEayiH2yiiWzUAI2QSXaMFQgHq9jMtcRS-tp98EHW3Xju9UCy9VO6y0cyOoVZXf3KhR6B3yttR_x3m02HoFyq-V-28%3D&attredirects=0)

Dicho árbol se puede representar como una hilera de la siguiente manera:

`"a(b(d,e),c(,f(g,)))"`

Escriba una función `(árbol-bin->hilera árbol-bin)` que genere esta representación. Y luego escriba otra función que haga el proceso inverso, es decir dada la representación en hilera produzca la estructura de listas del árbol binario `(hilera->árbol-bin hilera)`.

Por siimplicidad suponga que la información de los dos es un símbolo y que no hay espacios en la hilera.
Pista: considere las funciones `string->symbol` y `symbol->string`.

### P68 (2) Secuencias pre-orden y en-orden

1. Escriba funciones `(pre-orden árbol-bin)` y `(en-orden árbol-bin)` para construir las correspondientes secuencias de un árbol binario dado. Los resultados deberían ser listas de símbolos que representen dichas secuencias.

2. ¿Es posible escribir una función `(árbol-bin-pre-orden secuencia)` que reciba una lista de nodos en secuencia pre-orden y construya el árbol binario correspondiente? Si no es el caso, ¿qué ajustes serían necesarios?

3. Dadas ambas secuencias `pre-orden` y `en-orden` es posible determinar el árbol binario sin ambigüedades. Escriba entonces una función para construir el árbol binario `(árbol-bin-pre-en-orden secuencia-pre-orden secuencia-en-orden)`.

### P69 (2) Representación del árbol binario con hileras de puntos

El árbol del problema 67 se puede representar con la secuencia pre-orden de sus nodos en la cual se utilizan puntos `.` en representación de los árboles vacíos `'()` que se encuentren durante el recorrido. La representación con hileras de puntos sería: `"abd..e..c.fg..."`. Escriba funciones que hagan las conversiones en ambas direcciones (de árbol a hilera y de hilera a árbol).
