---
created_date: "[[2024 08 02]]"
created_time: 19:28
etiquetas:
  - "[Mini essay](Mini%20essay.md)"
share: "true"
filename: para-que-sirve-el-datawarehouse
---
# ¿Para qué sirve el data warehouse?
Recientemente, me plantearon una pregunta desafiante pero legítima: ¿Para qué sirve un data warehouse? A continuación, intentaré explicarlo de manera clara y concisa.

## El contexto: Datos en sistemas empresariales
En los sistemas de software empresariales, existen datos valiosos para una institución. Tomemos como ejemplo una universidad:

| Sistema                  | Datos que maneja                                                                                                                                |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| ERP Académico            | Lista de cursos; Profesor de cada curso; Estudiantes de cada curso; Notas de cada estudiante en cada curso; Datos personales de los estudiantes |
| Sistema de RRHH          | Lista de personas contratadas (incluidos profesores) con su RUT y otros datos personales                                                        |
| Sistema de Investigación | Lista de publicaciones asociadas a profesores de la universidad                                                                                 |

## Análisis integrado
Ahora bien, ¿qué sucede si queremos analizar la relación entre cursos y publicaciones? Esta tarea no es posible utilizando estos sistemas de forma aislada; se requiere información de los tres. Es aquí donde entra en juego un data warehouse.

Un data warehouse tiene varias capacidades:
1. **Integración de datos**: Periódicamente obtiene y almacena información relevante de diversos sistemas.
2. **Análisis cruzado**: Tiene la capacidad de entregar, de manera conjunta, datos de múltiples fuentes, lo que permite realizar análisis cruzados como del ejemplo de arriba.
3. **Almacenamiento histórico**: No sólo guarda la última "foto", sino que también la historia, lo que facilita el análisis de evolución temporal.
4. **Capacidad de cálculo**: Puede realizar operaciones matemáticas y almacenar su resultado. Por ejemplo, calcular la cantidad de cursos por profesor por semestre.

Todas estas características están orientadas a facilitar análisis complejos y la obtención de datos "cruzados" (e.g., una lista con todas las publicaciones de todos los profesores con todos sus cursos y notas promedio por curso).

Ahora bien, la principal limitación de un data warehouse radica en su naturaleza de conexión: los datos siempre presentan un cierto retraso. Cuanto más grandes sean los sistemas fuente, mayor puede ser este retraso. Por ejemplo, algunos sistemas con bases de datos extremadamente grandes pueden requerir toda una noche para actualizar el data warehouse.

## Alternativas para datos en tiempo real

Cuando se requieren datos en tiempo real, existen otras opciones:
1. **Conexión directa** a la base de datos del sistema (o a una réplica).
2. **API** (Interfaz de Programación de Aplicaciones), que en esencia funciona de manera similar a una conexión directa a la base de datos.

Sin embargo, estas soluciones también tienen sus limitaciones. Las APIs generalmente están restringidas en cuanto a la cantidad de datos que pueden proporcionar. Por lo tanto, para grandes volúmenes de datos, es preferible optar por una conexión directa a la base de datos (o su réplica) o utilizar un data warehouse. Lamentablemente, ninguna opción es perfecta.

## En esencia
Para clarificar, podemos resumir las opciones de la siguiente manera:

|                            | Pocos datos o "a goteo"                 | Muchísimos datos "de una"                                           |
| -------------------------- | --------------------------------------- | ------------------------------------------------------------------- |
| **En tiempo real**         | API directa al sistema                  | Conexión directa a la base de datos del sistema o API especializada |
| **Pueden estar atrasados** | API directa al sistema o Data Warehouse | Data Warehouse                                                      |

## Evolución tecnológica
Es importante mencionar que existen tecnologías más modernas de warehousing, como Delta Lake, que intentan combinar lo mejor de ambos mundos, ofreciendo tanto la capacidad de manejar grandes volúmenes de datos como la posibilidad de acceder a información más actualizada.

En conclusión, un data warehouse es una herramienta fundamental para el análisis u obtención integrada de datos empresariales, especialmente cuando se requiere trabajar con grandes volúmenes de información proveniente de múltiples fuentes. Si bien tiene ciertas limitaciones en cuanto a la actualización de los datos, su capacidad para facilitar análisis complejos y multidimensionales lo convierte en un componente esencial de la arquitectura de datos de muchas organizaciones.