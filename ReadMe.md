# 8-puzzle
## Juan Pablo de Jesus Figueroa Jaramillo ISC FIE Universidad de Colima

![Screen 5](puzzle-1.jpg)

## En que consiste el juego?

Un 8-Puzzle es un juego simple que consiste en una cuadrícula de 3 x 3 (que contiene 9
cuadrados). Una de las plazas está vacía. El objetivo del juego es mover a las casillas en torno
a diferentes posiciones y tener los números que aparecen en el &quot; estado final &quot; . Este documento se
orienta a dar una breve introducción, hacia lo que es la solución de este problema utilizando algoritmos
de búsqueda implementados a estructuras de datos como grafos y arboles.

## Que es una estructura de árbol?

En ciencias de la computación y en informática, un árbol es
una estructura de datos ampliamente usada que imita la forma
de un árbol (un conjunto de nodos conectados). Un nodo es la
unidad sobre la que se construye el árbol y puede tener cero o
más nodos hijos conectados a él. Se dice que un
nodo  es padre de un nodo  si existe un enlace
desde  hasta  (en ese caso, también decimos que  es hijo de ).
Sólo puede haber un único nodo sin padres, que llamaremos
raíz. Un nodo que no tiene hijos se conoce como hoja. Los
demás nodos (tienen padre y uno o varios hijos) se les conoce
como rama.

## Algoritmos de Búsqueda

Un algoritmo de búsqueda es aquel que está diseñado
para localizar un elemento con ciertas propiedades
dentro de una estructura de datos; por ejemplo, ubicar
el registro correspondiente a cierta persona en una base
de datos, o el mejor movimiento en una partida
de ajedrez.
Busqueda en Profundidad: Una Búsqueda en profundidad
(en inglés DFS o Depth First Search) es un algoritmo que
permite recorrer todos los nodos de un grafo o árbol (teoría de
grafos) de manera ordenada, pero no uniforme. Su
funcionamiento consiste en ir expandiendo todos y cada uno
de los nodos que va localizando, de forma recurrente, en un
camino concreto. Cuando ya no quedan más nodos que visitar
en dicho camino, regresa (Backtracking), de modo que repite
el mismo proceso con cada uno de los hermanos del nodo ya
procesado.

## Busqueda en Anchura

En Ciencias de la Computación,
Búsqueda en anchura (en inglés BFS - Breadth First Search)
es un algoritmo para recorrer o buscar elementos en un grafo
(usado frecuentemente sobre árboles). Intuitivamente, se
comienza en la raíz (eligiendo algún nodo como elemento raíz
en el caso de un grafo) y se exploran todos los vecinos de este
nodo. A continuación para cada uno de los vecinos se
exploran sus respectivos vecinos adyacentes, y así hasta que
se recorra todo el árbol.
Formalmente, BFS es un algoritmo de búsqueda sin
información, que expande y examina todos los nodos de un
árbol sistemáticamente para buscar una solución. El algoritmo
no usa ninguna estrategia heurística

### Pseudocodigo para Busqueda en Anchura

            BFS(grafo G, nodo_fuente s) 
                        { 
                            // recorremos todos los vértices del grafo inicializándolos a NO_VISITADO,
                            // distancia INFINITA y padre de cada nodo NULL
                            for u ∈ V[G] do
                            {
                                estado[u] = NO_VISITADO;
                                distancia[u] = INFINITO; /* distancia infinita si el nodo no es alcanzable */
                                padre[u] = NULL;
                            }
                            estado[s] = VISITADO;
                            distancia[s] = 0;
                            padre[s] = NULL;
                            CrearCola(Q); /* nos aseguramos que la cola está vacía */
                            Encolar(Q, s);
                            while !vacía(Q) do
                            {
                                // extraemos el nodo u de la cola Q y exploramos todos sus nodos adyacentes
                                u = extraer(Q);
                                for  v ∈ adyacencia[u]  do
                                {
                                if estado[v] == NO_VISITADO then
                                {
                                        estado[v] = VISITADO;
                                        distancia[v] = distancia[u] + 1;
                                        padre[v] = u;
                                        Encolar(Q, v);
                                }
                                }
                            }
                        }

## Solución del 8-puzle utilizando Arboles

Una de las soluciones que implementamos para la solución de
este problema fue apoyándonos en la implementación de
árboles, donde cada nodo del árbol es una matriz donde se
representa cada ficha en el tablero de 3x3, al mover una ficha
a un espacio vacio.
El algoritmo empieza con una matriz inicial que es a la que se
le está buscando solución, luego se le enseña al programa el
estado final al que se desea llegar, el algoritmo iniciara una
búsqueda visitando cada nodo y comparando la matriz que
hay en este nodo con la matriz a la que deseamos llegar. Como todo algoritmo de búsqueda en amplitud, A* es un
algoritmo completo: en caso de existir una solución, siempre
dará con ella.
Para garantizar la optimización del algoritmo, la función debe
ser heurística admisible, esto es, que no sobrestime el coste
real de alcanzar el nodo objetivo.
De no cumplirse dicha condición, el algoritmo pasa a
denominarse simplemente A, y a pesar de seguir siendo
completo, no se asegura que el resultado obtenido sea el
camino de coste mínimo. Asimismo, si garantizamos

## Pseudocodigo de este Algoritmo de Búsqueda

                    caso . = . perteneciente a ()
                    si g(.) &lt; g(.) entonces // (-----)
                    // nos quedamos con el camino de menor coste
                    .:= MEJORNODO
                    actualizar g(.) y f&#39;(.)
                    propagar g a . de .
                    eliminar .
                    añadir . a ._MEJORNODO
                    caso . = . perteneciente a )-----(
                    si g(.) &lt; g(.) entonces
                    // nos quedamos con el camino de menor coste
                    .:= MEJORNODO
                    actualizar g(.) y f&#39;(.)
                    eliminar .
                    añadir . a ._MEJORNODO
                    caso . no estaba en ).( ni (.)
                    añadir . a ).(
                    añadir . a ._MEJORNODO
                    f&#39;(.) := g(.) + h&#39;(.)