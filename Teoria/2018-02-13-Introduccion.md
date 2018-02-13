# Qué es NoSQL

Cualquier estudiante de la rama de Informática, ya sea a nivel de ciclos formativos o universitarios conoce lo que es una base de datos. Si preguntamos a estos alumnos o profesionales lo primero que les vendrá a la cabeza serán palabras como Oracle, MySQL, SQLite y a lo sumo SQL Server, PostgreSQL o MariaDB. Todas estas bases de datos lo que tienen en común es que son relacionales y utilizan el lenguaje SQL. Sin embargo, desde hace unos años se popularizaron el uso de otro tipo de bases de datos llamadas NoSQL, acrónimo de Not only SQL. Es decir, bases de datos que ni son relacionales ni utilizan el lenguaje SQL.

Si tuvieramos que resumir las características comunes en estos sistemas, son principalmente tres: **Ausencia de esquema** en los registros de datos, **escalabilidad horizontal** sencilla, y **velocidad**, aunque esto último no siempre es cierto.

La primera característica significa que los datos no tienen una definición de atributos fija, es decir: cada registro (o documento, como se les suele llamar en estos casos) puede contener una información con diferente forma cada vez, pudiendo así almacenar sólo los atributos que interesen en cada uno de ellos, facilitando el polimorfismo de datos bajo una misma colección de información. También se pueden almacenar estructuras de datos complejas en un sólo documento, como por ejemplo almacenar la información sobre una publicación de un blog (título, cuerpo de texto, autor, etc) junto a los comentarios y etiquetas vertidos sobre el mismo, todo en un único registro. Hacerlo así aumenta la **claridad** (al tener todos los datos relacionados en un mismo bloque de información) y el **rendimiento** (no hay que hacer un JOIN para obtener los datos relacionados, pues éstos se encuentran directamente en el mismo documento).

Con escalabilidad horizontal se refiere a la posibilidad de aumentar el rendimiento del sistema simplemente añadiendo más nodos, sin necesidad en muchos casos de realizar ninguna otra operación más que indicar al sistema cuáles son los nodos disponibles. Muchos sistemas NoSQL permiten utilizar consultas del tipo **Map-Reduce**, las cuales pueden ejecutarse en todos los nodos a la vez (cada uno operando sobre una porción de los datos) y reunir luego los resultados antes de devolverlos al cliente. La gran mayoría permiten también indicar otras cosas como el número de réplicas en que se hará una operación de escritura, para garantizar la disponibilidad. Y gracias al sharding y a no tener que replicar todos los datos en cada uno de los nodos, la información que se mueve entre las distintas instancias del motor de base de datos no tiene por qué ser demasiado intensiva. Por supuesto, seguiremos encontrándonos con problemas de escalabilidad inherentes al tipo de software que estemos construyendo, pero seguramente podamos resolverlos más fácilmente con la ayuda de estas características.

Por último, muchos de estos sistemas realizan operaciones directamente en memoria, y sólo vuelcan los datos a disco cada cierto tiempo. Esto permite que las operaciones de escritura sean realmente rápidas. Por supuesto, trabajar de este modo puede sacrificar fácilmente la durabilidad de los datos, y en caso de cuelgue o apagón se podrían perder operaciones de escritura o perder la consistencia. Normalmente, esto lo resuelven permitiendo que una operación de escritura haya de realizarse en más de un nodo antes de darla por válida, o disminuyendo el tiempo entre volcado y volcado de datos a disco. Pero claro, aún así, existe ese riesgo.

## Tipos de bases de datos

Como se mencionó en el apartado anterior, las bases de datos NoSQL al contrario que las SQL, no existe un único tipo o grupo, si no varios tipos según a lo que se oriente dicha base de datos. Con lo cual, cuando se comienza a aprender bases de datos NoSQL, hay que especificar qué tipo queremos aprender o dominamos.

1. **Base de datos de Documentos:** Este tipo de base de datos almacena la información como un documento, usando para habitualmente para ello una estructura simple como JSON, BSON o XML y donde se utiliza una clave única para cada registro. Este tipo de implementación permite, además de realizar búsquedas por clave–valor, realizar consultas más avanzadas sobre el contenidodel documento. Son las bases de datos NoSQL más versátiles.

2. **Almacenamiento Clave-Valor:** Son el modelo de base de datos NoSQL más popular, además de ser la más sencilla en cuanto a funcionalidad. En este tipo de sistema, cada elemento está identificado por una clave única, lo que permite la recuperación de la información de forma muy rápida, información que suele almacenarse como un objeto binario. Se caracterizan por ser muy eficientes tanto para las lecturas como para las escrituras. 

3. **Bases de datos de grafos:** Usadas para aquellos datos cuyas relaciones se pueden representar adecuadamente mediante un grafo. Los datos se almacenan en estructuras grafo con nodos (entidades), propiedades (información entre entidades) y líneas (conexiones entre las entidades). 

4. **Base de datos Columnar (o Columna ancha):** En vez de "tablas", en las bases de datos de columna tenemos familias de columnas que, son los contenedores de las filas. A diferencia de los RDBMS, no necesita conocer de antemano todas las columnas, cada fila no tiene por qué tener el mismo número de columnas. Este tipo de bases de datos se adecuan mejor a operaciones analíticas sobre grandes conjuntos de datos.


## Enlaces

[Genbetadev: El concepto NoSQL, o cómo almacenar tus datos en una base de datos no relacional](https://www.genbetadev.com/bases-de-datos/el-concepto-nosql-o-como-almacenar-tus-datos-en-una-base-de-datos-no-relacional)

[Un café con Oracle: ¿Qué es una Base de Datos NoSQL?](https://blogs.oracle.com/uncafeconoracle/qu-es-una-base-de-datos-nosql)

[PFC Rául Herranz Gómez, universidad Carlos III de Madrid (UC3M)](https://e-archivo.uc3m.es/bitstream/handle/10016/22895/PFC_raul_herranz_gomez_2014.pdf)

[PFC Sergio Bellido Sánchez, tema 2, universidad de Sevilla (US)](http://bibing.us.es/proyectos/abreproy/12037/fichero/PFC_Sergio_Bellido_Sanchez%252FTema2_Panoramico.pdf)

[Genbetadev: NoSQL y relaciones](https://www.genbetadev.com/bases-de-datos/nosql-y-relaciones)
