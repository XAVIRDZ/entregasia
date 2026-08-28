Guion de Exposición: Sistemas Expertos
Estructura y discurso continuo para presentación académica
Tema: Fundamentos y Arquitectura de Sistemas
Expertos

DIAPOSITIVA 1 Introducción a los Sistemas Expertos
Buenos días a todos. Hoy voy a presentarles el tema de los Sistemas Expertos, uno de los pilares fundamentales
e históricos de la Inteligencia Artificial.
Actualmente, cuando hablamos de IA, solemos pensar de inmediato en redes neuronales, aprendizaje profundo o
modelos estadísticos masivos. Sin embargo, antes de la popularización del aprendizaje automático, la inteligencia
artificial resolvió problemas industriales, médicos y científicos de gran complejidad mediante la representación
formal del conocimiento humano y la lógica simbólica.
Un Sistema Experto es un software diseñado específicamente para emular la capacidad de decisión y
razonamiento de un especialista humano en un área delimitada. En esta presentación analizaré su arquitectura
interna, la diferencia entre datos y conocimiento, sus motores de inferencia, su evolución histórica y los distintos
tipos de sistemas expertos que existen.

DIAPOSITIVA 2 El Concepto de Conocimiento en IA 
Para entender cómo funciona este tipo de sistemas, primero debemos definir con claridad qué entendemos por
conocimiento en ciencias computacionales, diferenciándolo de los datos y la información.
[Apoyo en diapositiva: Jerarquía Dato → Información → Conocimiento]
Un dato es un valor atómico sin contexto; por ejemplo, el número 39 °C. La información surge cuando a ese dato
le añadimos estructura y significado: "El paciente presenta una temperatura de 39 °C". Pero el conocimiento va un
paso más allá: es la información procesada e integrada con experiencia práctica, reglas lógicas y juicio crítico. Por
ejemplo: "Si la temperatura es mayor a 38.5 °C y existe dolor articular, entonces deducimos un cuadro de infección
febril activa".
En un sistema experto, el conocimiento no solo incluye hechos formales, sino también heurísticas: reglas
prácticas derivadas de la experiencia directa del experto que permiten resolver problemas complejos sin necesidad
de recorrer todas las combinaciones posibles.


DIAPOSITIVA 3 Base de Conocimiento (Knowledge Base) 3:30 - 5:30 min
El núcleo donde se almacena este saber es la Base de Conocimiento. A diferencia de una base de datos
convencional —que guarda tablas y registros estáticos—, una base de conocimiento almacena afirmaciones
lógicas, relaciones ontológicas y reglas de producción.
El formato de representación más común son las Reglas de Producción, estructuradas bajo la premisa SI
<condición> ENTONCES <acción/conclusión>. Por ejemplo, en un entorno de redes: "SI un host no
responde al ping Y la interfaz está activa, ENTONCES verificar la tabla ARP o las reglas de firewall".
Un aspecto arquitectónico clave que quiero destacar es el desacoplamiento total: la base de conocimiento está
completamente separada del algoritmo de inferencia. Esto permite que el conocimiento de los especialistas se
actualice, corrija o expanda continuamente sin tener que modificar una sola línea del código fuente del motor.

DIAPOSITIVA 4 Motor de Inferencia (Inference Engine)
Si la Base de Conocimiento representa la memoria, el Motor de Inferencia es el cerebro del sistema. Es el
componente encargado de procesar los hechos conocidos, evaluar las reglas y deducir nuevas conclusiones
aplicando reglas lógicas como el Modus Ponens.
Para lograr esto, el motor opera bajo dos estrategias principales:
Encadenamiento hacia adelante (Forward Chaining): Se guía por los datos. Parte de los hechos
observados y evalúa qué reglas se satisfacen para generar nuevas deducciones de manera progresiva. Es
ideal para monitoreo en tiempo real, síntesis y diagnóstico preliminar.
Encadenamiento hacia atrás (Backward Chaining): Se guía por metas. Parte de una hipótesis que se
desea comprobar y trabaja en reversa, buscando si en la base de hechos se cumplen las premisas
necesarias para validar dicha hipótesis. Es común en auditorías, análisis forense y diagnóstico médico.
Además, cuando varias reglas pueden activarse al mismo tiempo, el motor aplica algoritmos de resolución de
conflictos basados en criterios como prioridad, especificidad o recencia de los datos.

DIAPOSITIVA 5 Línea de Tiempo y Evolución Histórica
A continuación, presento los hitos históricos más relevantes que marcaron la consolidación de estos sistemas:
Año /
Periodo

Sistema / Hito Aporte Principal

1965

DENDRAL
(Stanford)

Pionero absoluto. Identificación de estructuras moleculares mediante espectrometría
de masas.

1972 - 1976 MYCIN (Shortliffe)

Diagnóstico de infecciones en sangre y prescripción antibiótica; introdujo factores de
certeza.
1978 - 1980 XCON / R1 (DEC)

Primer gran éxito comercial. Configuración automatizada de servidores VAX con
gran ahorro de costos.

1980 - 1995 Era de los Shells Separación formal del motor y creación de entornos reutilizables (CLIPS, PROLOG).
Actualidad

Sistemas
Híbridos

Integración neuro-simbólica (redes neuronales + grafos de conocimiento y motores
de reglas).

Como podemos observar, en 1965 DENDRAL demostró que una computadora podía deducir compuestos químicos
complejos. Más tarde, MYCIN probó que un sistema podía rivalizar con médicos especialistas al incorporar
razonamiento bajo incertidumbre. Finalmente, con XCON en 1980, la industria comprobó que estos sistemas
generaban un retorno de inversión millonario, consolidando la viabilidad comercial de la IA.

DIAPOSITIVA 6 Tipos de Sistemas Expertos 
Dependiendo de la naturaleza del problema y del tipo de conocimiento a modelar, clasificamos los sistemas
expertos en cuatro categorías principales:
Basados en Reglas (Rule-Based): Emplean lógica proposicional o de predicados estructurada en reglas
deterministas. Son el estándar cuando los procesos están claramente normados, como en regulaciones
fiscales, protocolos de configuración o auditorías.
Basados en Casos (Case-Based Reasoning - CBR): Resuelven problemas nuevos adaptando soluciones
documentadas de experiencias pasadas mediante las fases de Recuperar, Reutilizar, Revisar y Retener. Se
aplican ampliamente en mesas de ayuda técnica y jurisprudencia legal.
Basados en Lógica Difusa (Fuzzy Expert Systems): Permiten procesar variables imprecisas o continuas,
como "temperatura moderada" o "presión elevada", mediante funciones de pertenencia gradual. Son
esenciales en control automático de procesos industriales y robótica.
Basados en Redes Bayesianas (Probabilísticos): Modelan relaciones de causa-efecto e incertidumbre a
través de grafos acíclicos dirigidos y probabilidades condicionales.
•

DIAPOSITIVA 7 Módulo de Explicación, Balance y Conclusiones 13:00 - 15:00 min
Para concluir, quiero destacar una característica distintiva de los sistemas expertos: el Módulo de Explicación. A
diferencia de otros modelos donde el resultado es una caja negra, un sistema experto es capaz de justificar su
respuesta respondiendo con claridad a dos preguntas esenciales: "¿Por qué se solicita este dato?" y "¿Cómo se
llegó a esta conclusión?".
En cuanto a su balance técnico, sus mayores ventajas son la disponibilidad ininterrumpida, la estandarización
objetiva de decisiones y la preservación del conocimiento institucional frente a la rotación de personal. Por otro
lado, su principal reto sigue siendo el cuello de botella en la adquisición del conocimiento (extraer y formalizar la
experiencia humana) y su rigidez para razonar fuera del dominio específico para el que fueron construidos.
Hoy en día, estos principios siguen plenamente vigentes mediante la IA Neuro-Simbólica, donde combinamos la
capacidad perceptual del aprendizaje profundo con la explicabilidad y el rigor lógico de los sistemas expertos.
Muchas gracias por su atención; quedo a su disposición para cualquier pregunta.
