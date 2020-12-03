PROYECTO
1.1)Explicación General del Código

1.2)Análisis de Complejidad

1.3)Casos de Prueba

GRAFO PONDERADO
2.1)¿Qué es?

2.2)Uso

2.3)Casos Reales 

2.4)Algoritmo 

2.5)Fuentes

-----------------------------------------
PROYECTO
-----------------------------------------
1.1)Explicación General del Código
El programa es un grafo ponderado para encontrar la distancia más corta entre dos estaciones. El usuario introduce dos estaciones, el origen y destino, y se despliegan los nombres de las estaciones que tienen la ruta más corta. 
Al iniciar el programa se cargan los datos del grafo por medio de dos archivos txt. El primero carga crea cada nodo y los enlaza a otros por medio de una lista de adyacencia. Una lista que guarda los costos de cada arco se va creando simultaneamente. El segundo archivo que ocupa el programa es utilizado para nombrar a cada nodo.
Después de cargar los datos del grafo se despliega un menú con tres opciones. La primera cumple la función principal del programa, dar rutas mínimas al usuario. La segunda ayuda al usuario a la interacción con el programa al desplegar el nombre de las estaciones/nodos cargados. La tercera opción permite ver los nodos adyacentes de un nodo elegido. La opción 0 termina el programa.
La estructura utilizada, como se mencionó anteriormente es un grafo ponderado. Se implemento en base a un grafo con listas de adyacencia. El algoritmo que se utiliza para la búsqueda de nodos es el algoritmo Dijkstra.

-----------------------------------------
1.2)Análisis de Complejidad

->void loadGraphList(std::string,int) 
->void loadNodeNames(std::string)
    Ambos algoritmos recorren un archivo txt para cargar los datos al programa. La repetición de sus procesos es la misma cantidad de veces que las líneas del archivo. Por lo tanto, ambos son de complejidad lineal.

->std::string Dijkstra(int,int)
    La literatura nos dice que si el grafo es implementado con una lista de adyacencia y se usa una cola de prioridad para su implementación la complejidad de la búsquedad es de O((V+E)logV). En el caso de esta implementación la búsqueda es de la misma complejidad, no obstante, el algoritmo es de complejidad lineal debido a la inicialización que se realiza en cada búsqueda. Los arreglos de permanencia y el que lleva registro de los costos de cada nodo se sobreescriben cada vez que se realiza una búsqueda nueva. Se usa un for para recorrer el arreglo entero.

->std::string printAdjList()
->std::string printAdjListWithCost()
->void neighborNodes(int)
    Recorren los nodos adyacentes de un nodo. En el peor de los casos tiene adyacencia con todos los nodos del grafo. Es de complejidad 0(n).
  
->void showInfo()
    Imprime un los  valores de dos atributos, lo que lo vuelve constante. 0(1)

->void showAllNodes()
    Recorre todos los nodos, al depender de la cantidad de registros es de complejidad lineal, O(n).

->std::string number2string(int)
->int string2number(std::string)
->template <class T> void swap(std::vector<T>&,int,int)
->std::string searchByNameDijkstra(std::string,std::string)
->void neighborNodesString(std::string)
    Estos cinco métodos de la clase graph son de complejidad constante, O(1). Todos son métodos auxiliares pues no tienen otra función más que realizar una llamada a otro método o hacer una misma acción cada vez que se llaman. 

-----------------------------------------
1.3)Casos de Prueba

**Se puede comprobar la veracidad de los casos de prueba con ayuda de los archivos CDMX_mapa_km.jpg y CDMX_mapa_km.jpg

---Lectura
-INPUT

2

-OUTPUT

Una lista de estaciones con su índice es desplegada

La lista debe contener los mismos nombres que los del archivo estaciones.txt

---Escritura
-INPUT

1

1

MIXCOAC

MORELOS

-OUTPUT

Se despliega en consola "[24]MIXCOAC [19]TACUBAYA [13]BALDERAS [14]SALTO DEL AGUA [15]PINO SUAREZ [16]CANDELARIA [17]SAN LAZARO [9]MORELOS"

En el archivo rutaMin.txt debe aparecer la misma ruta

----Búsqueda
-INPUT

1

1

EL ROSARIO

JAMAICA

-OUTPUT

Se despliega en consola "[0]EL ROSARIO [6]TACUBA [11]HIDALGO [12]BELLAS ARTES [14]SALTO DEL AGUA [15]PINO SUAREZ [21]CHABACANO [22]JAMAICA"

El archivo rutaMin.txt debe contener la misma ruta

En consola se muestran 14 km como distancia de la ruta

-INPUT

1

1

OCEANIA

LA RAZA

-OUTPUT

Se despliega en consola "[10]OCEANIA [5]CONSULADO [4]LA RAZA"

El archivo rutaMin.txt debe contener la misma ruta

En consola se muestran 6.7 km como distancia de la ruta

-INPUT

1

2

25

26

-OUTPUT

Se despliega en consola "[25]ZAPATA [26]ERMITA"

El archivo rutaMin.txt debe contener la misma ruta

En consola se muestran 3 km como distancia de la ruta

-INPUT

1

2

26

25

-OUTPUT

Se despliega en consola "[26]ERMITA [25]ZAPATA"

El archivo rutaMin.txt debe contener la misma ruta

En consola se muestran 3 km como distancia de la ruta

-----------------------------------------
GRAFO PONDERADO
-----------------------------------------
2.1)¿Qué es?
Un grafo ponderado es una estructura igual a los demás grafos con las característica de que a cada una de sus aristas se le asigna un valor. Este valor es conocido como valuación, ponderación o coste. Las aristas pueden ser direccionales o no direccionales. El camino entre un nodo y otro tiene un peso, este peso es la suma de la ponderación de las aristas de la ruta.

-----------------------------------------
2.2)Uso
Los nodos pueden representar entidades, organizaciones, individuos, etc, mientras que las aristas indican una relación cuantificable entre ellos. Este tipo de grafo se usa en casos donde las relaciones no son del mismo tipo en todos los casos. Estás relaciones pueden ser cosas abstractas como amistad hasta cosas físicas como distancias. Algunos ejemplos de uso pueden ser la comunicación entre dispositivos con una ponderación de los tiempos de respuesta, zonas geográficas con la distancia entre ellas como ponderación, neuronas y su intensidad de sinapsis, etc.

-----------------------------------------
2.3)Casos Reales
Los grafos tienen infinidad de aplicaciones.
Los grafos ponderados se usan comunmente para la creación de redes genómicas en biología computacional.
La creación de mapas electrónicos hace uso de grafos ponderados.
En la química se pueden modelar relaciones de moléculas con ellos.
Redes de comunicación pueden ser implementadas con grafos ponderados.
En sociología se usan para modelar interacciones sociales.

-----------------------------------------
2.4)Algoritmo
El algoritmo que se uso para el recorrido fue el algoritmo Dijkstra. El objetivo de este es encontrar el camino de coste mínimo. La idea es recorrer cada nodo vecino e ir registrando el coste de llegada y el nodo del que se provino en cada uno. Cada que se recorren todos los nodos vecinos de un nodo este se marca como permanente y se avanza al nodo con menor coste. El siguiente nodo visita a sus vecinos que no estén marcados con permanencia. Les suma su coste acumulado si no ha llegado nadie a ese nodo o al hacerlo se tiene un coste menor. Los nodos visitados van metiendose a una cola,la cual indica el nodo siguiente. Una vez que la cola queda vacía se obtiene el recorrido siguiendo el registro de los nodos de proveniencia. 
Un ejemplo se puede observar en el archivo "prueba.png" y "prueba2.png". En el primero se encuentra un grafo ponderado sin ser recorrido y en segundo se muestra el mismo grafo después de ser recorrido. A lado de cada nodo se ve el nodo de proveniencia y el coste acumulado. El recorrido del ejemplo es de A a H.

-----------------------------------------
2.5)Fuentes
López, B., &amp; Tony del C. Rosríguez Servín dice:. (2019, October 28). Algoritmo de Dijkstra. Retrieved December 02, 2020, from https://www.ingenieriaindustrialonline.com/investigacion-de-operaciones/algoritmo-de-dijkstra/
Matemáticas a Discreción. (2010, December 14). Tema 7: Grafos ponderados. Retrieved December 02, 2020, from https://blogs.ua.es/matematicadiscrecion/2011/01/06/tema-7-grafos-ponderados-sesion-21122010/
Promedia ufps. (2017, September 27). Rutas de costo mínimo: Dijkstra y Floyd Warshall. Retrieved December 2, 2020, from https://www.youtube.com/watch?v=UFZN0NmY1jQ&amp;t=374s
Ryder, A. (2018, April 01). Dijkstra's algorithm: Application, Complexity, Implementation, Explanation. Retrieved December 02, 2020, from https://iq.opengenus.org/dijkstras-algorithm-finding-shortest-path-between-all-nodes/







[![Run on Repl.it](https://repl.it/badge/github/Javier-P-C/ProyectoEstructuraGrafoPonderado)](https://repl.it/github/Javier-P-C/ProyectoEstructuraGrafoPonderado)
