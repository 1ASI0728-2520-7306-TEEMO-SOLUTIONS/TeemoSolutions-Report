<style>
  body {
    font-family: 'Times New Roman', sans-serif;
    text-align: justify;
    font-size: 12px;
    margin-left: 2em;
    margin-right: 2em;
    line-height: 2;
  }
  
  p {
    text-indent: 2em; /* Sangría en el primer renglón de cada párrafo */
  }

  h1 {
    margin-left: 0; /* No aplica sangría para el título principal */
  }

  h2 {
    margin-left: 0; /* No aplica sangría para subtítulos de nivel 2 */
  }

  h3 {
    margin-left: 2em; /* Aplica una sangría de 2em para subtítulos de nivel 3 */
  }

  h4 {
    margin-left: 4em; /* Aplica una sangría de 4em para subtítulos de nivel 4 */
  }
</style>

# **CAPÍTULO VIII: EXPERIMENT-DRIVEN DEVELOPMENT**

## 8.1. Experiment Planning
### 8.1.1. As-Is Summary

La aplicación actual se centra en ofrecer una plataforma para la optimizacion de las rutas marítimas internacionales utilizando datos contextuales en tiempo real, inteligencia predictiva y análisis de riesgos.

Sin embargo, el rendimiento general es inconsistente, con tiempos de carga que a menudo superan los 3 segundos, lo que afecta la experiencia del usuario. La interfaz presenta limitaciones en términos de personalización, y no se adapta adecuadamente a diferentes condiciones de luz.

**Problemas detectados**

- Bajo rendimiento: La aplicación presenta demoras al acceder a distintas funcionalidades, lo que puede generar una experiencia frustrante para el usuario.

- Limitaciones en usabilidad: La ausencia de un modo oscuro reduce la comodidad al utilizar la plataforma en ambientes con poca iluminación.

- Experiencia de usuario inconsistente: La interfaz actual no está adaptada de forma óptima a distintos tipos de dispositivos, lo que provoca variaciones en la experiencia entre smartphones y equipos de escritorio.

- Accesibilidad restringida: No contar con soporte multilingüe impide que usuarios de otros idiomas puedan interactuar adecuadamente con la aplicación, lo que limita su alcance global.

**Objetivos de mejora:**


- Mejorar el rendimiento: Optimizar la arquitectura y el uso de recursos para lograr tiempos de carga inferiores a 2 segundos.

- Ampliar la accesibilidad y usabilidad: Incorporar un modo oscuro y rediseñar aspectos clave de la interfaz para facilitar el uso en distintas condiciones y dispositivos.

- Alcanzar nuevos públicos: Integrar traducciones al inglés y al chino con el fin de atraer una audiencia más amplia y diversa.

- Aumentar la interacción: Aplicar estrategias de gamificación para fomentar una mayor participación y fidelización de los usuarios dentro de la plataforma.


### 8.1.2. Raw Material: Assumptions, Knowledge Gaps, Ideas, Claims

**Assumptions (Supuestos):**

- Modo oscuro: Se parte del supuesto de que los usuarios valoran opciones de personalización visual, especialmente cuando trabajan en entornos de baja iluminación, por lo que implementar un modo oscuro podría mejorar la experiencia de navegación.

- Multilingüismo: Se asume que un porcentaje importante de usuarios habla otros idiomas, como inglés o chino, lo cual justifica la necesidad de ofrecer traducciones en la plataforma.

- Espacio colaborativo logístico: Se presupone que los usuarios valoran una sección donde puedan compartir rutas recomendadas, experiencias logísticas y reportes de eventos, lo cual aumentaría la participación activa dentro del sistema.

- Alertas personalizadas: Se considera que los recordatorios e indicadores contextuales pueden mejorar la gestión de rutas y decisiones operativas, elevando la satisfacción del usuario.

- Módulo de oportunidades comerciales: Se asume que existe interés por integrar un espacio donde navieras, brokers logísticos y exportadores puedan intercambiar servicios o asociarse para operaciones compartidas.

**Knowledge Gaps (Vacíos de conocimiento):**

- Preferencias visuales: Se requiere mayor información sobre cómo los usuarios perciben el diseño de la plataforma y si funciones como el modo oscuro realmente impactan en su comodidad.

- Perfil lingüístico de usuarios: Se necesita investigar más sobre la diversidad idiomática de los actuales y potenciales usuarios, para priorizar idiomas en futuras versiones.

- Utilidad de la sección colaborativa: Aún no se cuenta con datos que indiquen qué tipo de contenido (eventos, alertas, rutas alternativas) es más valorado en espacios colaborativos logísticos.

- Impacto de las notificaciones inteligentes: Hace falta evidencia sobre cómo las alertas personalizadas afectan la toma de decisiones o la fidelización del usuario en plataformas similares.

- Demanda de funcionalidades comerciales: No se dispone aún de un análisis profundo sobre la viabilidad e interés real de una sección dedicada a networking logístico o intercambio de servicios en el sector marítimo.

**Ideas (Propuestas de acción):**

- Aplicar encuestas dirigidas: Realizar encuestas y entrevistas a usuarios actuales para conocer su opinión sobre funciones propuestas como modo oscuro, alertas o espacio colaborativo.

- Desarrollar un módulo de comunidad logística: Crear una sección que permita a usuarios compartir experiencias, consejos operativos y rutas recomendadas ante disrupciones.

- Lanzar un estudio de mercado logístico: Investigar la viabilidad y expectativas de los usuarios frente a un marketplace o espacio de colaboración entre operadores logísticos.

- Analizar casos de éxito comparables: Estudiar plataformas del ámbito logístico o marítimo que han integrado características similares, para identificar buenas prácticas y errores a evitar.

**Claims (Afirmaciones):**

- Mejora en usabilidad: Se plantea que la inclusión de un modo oscuro contribuirá a una experiencia más confortable, especialmente para usuarios que operan en ambientes con poca luz.

- Mayor interacción del usuario: Se sostiene que la creación de una sección colaborativa donde se compartan experiencias logísticas puede aumentar el compromiso y la recurrencia en el uso de la plataforma.

- Incremento en satisfacción: Se afirma que las alertas inteligentes y personalizadas mejoran la gestión logística y refuerzan la percepción de valor por parte del usuario.

- Impulso a redes logísticas: Se propone que la integración de un módulo comercial/logístico puede fomentar alianzas, generar nuevas oportunidades de negocio y fortalecer la comunidad de usuarios.

### 8.1.3. Experiment-Ready Questions
| **Pregunta**                                                                                                                                      | **Confianza**                                                                                                                                 | **Riesgo**                                                                                            | **Impacto**                                                                                        | **Interés**                                                                                            | **Total Score** |
|---------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|-----------------|
| ¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo en la plataforma?              | 7 – Alta confianza; se trata de una funcionalidad estándar en plataformas de navegación con buen historial de adopción por parte de usuarios. | 2 – Bajo riesgo técnico; su implementación requiere mostrar datos ya disponibles en el sistema.       | 6 – Mejora la precisión y reduce errores sin modificar funcionalidades centrales.                  | 5 – Útil especialmente para operadores y capitanes que planifican rutas constantemente.                | **20**          |
| ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                                   | 6 – Algoritmos de rutas optimizadas son estándar en soluciones logísticas actuales.                                                           | 3 – Mejora sustancial en la eficiencia de navegación y uso de recursos.                               | 7 – Facilita la internacionalización de la solución.                                               | 6 – Atractivo para operadores logísticos y tomadores de decisiones que gestionan múltiples rutas.      | **22**          |
| ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?              | 7 – Los algoritmos de rutas dinámicas ya se usan en sistemas de navegación terrestre y aérea.                                                 | 4 – Riesgo medio por la dependencia de actualizaciones en tiempo real sobre el estado de los puertos. | 9 – Alto impacto operativo al mantener activa la planificación incluso en situaciones imprevistas. | 6 – Valorado por operadores que gestionan grandes volúmenes y no pueden arriesgar interrupciones.      | **26**          |
| ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?           | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?       | 2 – Bajo riesgo técnico; requiere integración de datos ya existentes.                                 | 8 – Mejora la visibilidad de operaciones, facilitando decisiones tácticas en tiempo real.          | 6 – Valioso para empresas que buscan eficiencia operativa sin depender de múltiples sistemas externos. | **23**          |
| ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido? | 7 – Existen sistemas similares en logística y transporte terrestre que ya ofrecen reportes post-ejecución.                                    | 3 – Requiere trazabilidad de datos durante la navegación, pero es técnicamente viable.                | 8 – Permite análisis y mejora continua del desempeño logístico.                                    | 7 – Valioso para usuarios que deben justificar rutas, responder a eventos o mejorar procesos futuros.  | **25**          |
| ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                   | 8 – Visualizaciones geográficas ya son estándar en aplicaciones de logística.                                                                 | 2 – Riesgo técnico bajo; se puede usar bibliotecas existentes para visualización de nodos.            | 7 – Mejora la comprensión de la red de puertos y facilita decisiones rápidas.                      | 6 – Importante para usuarios nuevos y operadores que planifican visualmente.                           | **23**          |
| ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                                | 6 – La persistencia de datos recientes es una práctica común en apps logísticas y de navegación.                                              | 3 – Bajo riesgo técnico, aunque puede haber dudas sobre almacenamiento local vs. servidor.            | 6 – Mejora la experiencia al evitar pérdidas de información reciente.                              | 5 – Apreciado por usuarios frecuentes que evalúan desempeño o repiten rutas.                           | **20**          |
| ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran? | 7 – Similar a sistemas de aeropuertos o plataformas portuarias con estado operativo en tiempo real.                                           | 3 – Requiere mantener actualizada la información del estado de cada puerto.                           | 9 – Altamente relevante para decisiones inmediatas (detención, descarga, abastecimiento).          | 7 – Fundamental para capitanes y jefes de ruta que manejan operaciones activas.                        | **26**          |

### 8.1.4. Question Backlog

| **Prioridad (1,2,3,5,8)** | **Pregunta**                                                                                                                                             |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **1**                     | ¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo (abierto o cerrado) en la plataforma? |
| **2**                     | ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                                          |
| **2**                     | ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?                     |
| **3**                     | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?                  |
| **3**                     | ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido?        |
| **3**                     | ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                          |
| **5**                     | ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                                       |
| **8**                     | ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran?        |



### 8.1.5. Experiment Cards

| **Question 1** |¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo (abierto o cerrado) en la plataforma? |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | Permitir que los usuarios visualicen claramente qué puertos están abiertos o cerrados puede optimizar la planificación de sus rutas. Esta funcionalidad reduciría errores de navegación al evitar seleccionar puertos inaccesibles, mejorando la eficiencia operativa y la satisfacción general. |
| **What**       | Diseñar una lista de puertos que indique de forma clara su nombre, país y estado operativo (abierto/cerrado), mediante texto y códigos visuales (colores o íconos). Esta funcionalidad debe estar accesible en la sección de navegación del sistema. |
| **Hypothesis** | Se espera que, tras implementar esta lista, al menos el 80% de los usuarios eviten puertos cerrados al planificar rutas y reduzcan el tiempo promedio de planificación en un 25%. |

| **Question 2** | ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                                                                                                                                                         |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | En logística marítima, reducir la distancia recorrida significa menor tiempo y menor consumo de recursos. Ofrecer rutas optimizadas permite a los usuarios tomar decisiones eficientes, reducir costos y aumentar la confiabilidad operativa.                           |
| **What**       | Desarrollar un algoritmo que calcule y muestre la ruta más corta entre dos puertos seleccionados, considerando distancias geográficas y disponibilidad. Mostrar los resultados visualmente sobre el mapa de navegación con detalles de distancia y puertos intermedios. |
| **Hypothesis** | Se espera que, tras implementar esta función, al menos el 70% de los usuarios elijan la ruta sugerida automáticamente y reporten una reducción del 20% en tiempo estimado de navegación.                                                                                |

| **Question 3** | ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?                                                                                                    |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | En operaciones marítimas, los cierres de puertos por clima o conflictos impactan gravemente la logística. Tener una función que recalcule rutas en tiempo real permite mantener operaciones fluidas y reducir demoras críticas.         |
| **What**       | Diseñar un sistema que detecte cierres de puertos registrados en la base de datos y actualice automáticamente la ruta hacia un destino alternativo, notificando al usuario y sugiriendo opciones de desvío sin interrumpir el servicio. |
| **Hypothesis** | Se espera que el 75% de los usuarios reporten una reducción en demoras logísticas y que el 60% utilicen la funcionalidad ante eventos imprevistos.                                                                                      |

| **Question 4** | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?                                                                                                           |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | Los operadores logísticos requieren información clara y accesible para monitorear sus embarques. Un reporte resumido de navegación ayudaría a identificar cuellos de botella, comparar rutas y mejorar el rendimiento general de las operaciones. |
| **What**       | Diseñar un panel de reporte con información clave como tiempos estimados y reales, desvíos, incidentes y duración total del trayecto, exportable en PDF o CSV, con filtros básicos.                                                               |
| **Hypothesis** | El 70% de los usuarios utilizarán la función regularmente, y al menos el 60% afirmarán que mejora la visibilidad y toma de decisiones operativas.                                                                                                 |

| **Question 5** | ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido?                                                                                                                                            |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | Los usuarios que supervisan rutas marítimas necesitan acceso a información histórica para evaluar decisiones pasadas, detectar errores, y mejorar futuras rutas. Un reporte final permite comprender el desempeño del trayecto de forma clara y estructurada.                                |
| **What**       | Diseñar una funcionalidad que genere un reporte automáticamente al finalizar el viaje. Este incluirá ruta seguida, eventos detectados (cierres, desvíos), tiempo total de recorrido y tiempos estimados vs. reales. Permitirá descargarlo en formato PDF o visualizarlo desde la plataforma. |
| **Hypothesis** | El 60% de los usuarios revisará el reporte al finalizar el viaje y al menos el 40% lo usará como insumo para modificar futuras decisiones logísticas.                                                                                                                                        |

| **Question 6** | ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                                                                                    |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | Los usuarios tienden a comprender mejor una red de transporte cuando la visualizan gráficamente. Un mapa esquemático de puertos facilita la planificación, evita confusión y mejora la experiencia de navegación.  |
| **What**       | Implementar un mapa interactivo con nodos representando puertos, líneas que conectan rutas navegables, y estados codificados por color (abierto/cerrado). Debe incluir funcionalidad de zoom y selección de nodos. |
| **Hypothesis** | Al menos el 70% de los usuarios considerará el mapa útil para comprender su trayecto, y el 50% lo utilizará activamente en la planificación de su viaje.                                                           |

| **Question 7** | ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                                                                                     |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | En entornos logísticos, registrar el último trayecto ayuda a validar decisiones previas, verificar tiempos de tránsito y retomar operaciones en caso de corte de sesión o emergencia.                  |
| **What**       | Implementar una función que almacene automáticamente el último viaje completo realizado, incluyendo puertos recorridos y tiempo estimado. Permitirá visualizarlo desde la pantalla de inicio o perfil. |
| **Hypothesis** | El 40% de los usuarios accederá al último viaje guardado al menos una vez por semana, y el 30% indicará que esto le ayudó a evaluar o continuar con operaciones anteriores.                            |

| **Question 8** | ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran?                                                         |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Why**        | Para decidir si detenerse, abastecerse o seguir navegando, los capitanes necesitan información confiable del puerto en tiempo real. El acceso inmediato a esta información reduce riesgos logísticos.     |
| **What**       | Diseñar una vista informativa que muestre el nombre, país y estado operativo (abierto/cerrado) del puerto donde se encuentra actualmente la embarcación, con actualización automática según localización. |
| **Hypothesis** | El 65% de los capitanes usará esta información al menos una vez por trayecto, y un 50% afirmará que contribuyó directamente a tomar decisiones operativas acertadas.                                      |

## 8.2. Experiment Design
### 8.2.1. Hypotheses

| **Question 1**      | ¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo (abierto o cerrado) en la plataforma?                                              |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si se proporciona una lista clara de puertos con su estado, los usuarios podrán tomar decisiones de navegación más precisas, evitando errores y mejorando la eficiencia del proceso de planificación. |
| **Hypothesis**      | La visualización de puertos disponibles reducirá en al menos un 25% los errores de planificación y el tiempo promedio requerido para definir una ruta.                                                |
| **Null Hypothesis** | La incorporación de una lista visible de puertos no tendrá un efecto significativo sobre la reducción de errores ni el tiempo de planificación.                                                       |

| **Question 2**      | ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                                                                            |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Ofrecer una ruta óptima directamente en la interfaz reduce la necesidad de cálculos manuales o externos, aumentando la eficiencia logística y reduciendo la incertidumbre para el usuario. |
| **Hypothesis**      | El uso del algoritmo de ruta más corta disminuirá el tiempo estimado de navegación y aumentará la precisión en la planificación en al menos un 20%.                                        |
| **Null Hypothesis** | La implementación de una ruta automática más corta no generará mejoras significativas en la planificación ni reducirá el tiempo estimado de viaje.                                         |

| **Question 3**      | ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?                                                           |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si el sistema recalcula automáticamente la ruta en caso de cierre de un puerto, se reduce el riesgo de interrupciones graves y se mantiene la continuidad operativa en entornos impredecibles. |
| **Hypothesis**      | El uso de esta funcionalidad disminuirá las interrupciones planificadas en al menos un 20% y aumentará la percepción de confiabilidad del sistema en un 25%.                                   |
| **Null Hypothesis** | El recálculo automático de rutas no tendrá un efecto significativo en la continuidad operativa ni en la percepción de confiabilidad del sistema.                                               |

| **Question 4**      | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?                                     |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Un informe de navegación que resuma el trayecto de los embarques permitirá a los operadores tomar decisiones más rápidas y acertadas, reduciendo errores y tiempos muertos. |
| **Hypothesis**      | La implementación del reporte sencillo aumentará la satisfacción de los operadores logísticos en un 25% y reducirá los errores operativos en al menos 15%.                  |
| **Null Hypothesis** | El reporte de navegación no tendrá un efecto significativo en la satisfacción de los usuarios ni en la eficiencia de las operaciones logísticas.                            |

| **Question 5**      | ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido?              |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si los usuarios cuentan con un reporte estructurado del viaje, podrán identificar errores, comparar con trayectos anteriores y mejorar el planeamiento futuro. |
| **Hypothesis**      | El uso del reporte de navegación aumentará en un 25% la capacidad de evaluación post-viaje y reducirá en un 15% la reincidencia de errores logísticos.         |
| **Null Hypothesis** | El reporte de navegación no impactará significativamente en la mejora de análisis ni en la toma de decisiones posteriores.                                     |

| **Question 6**      | ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                       |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si los usuarios tienen acceso a una representación visual clara de los puertos, podrán entender mejor su ubicación, relaciones y opciones de ruta.    |
| **Hypothesis**      | La incorporación del mapa esquemático incrementará en un 30% la comprensión de trayectos y disminuirá en un 20% los errores en la selección de rutas. |
| **Null Hypothesis** | El mapa esquemático no tendrá impacto relevante en la comprensión ni en la planificación de trayectos.                                                |

| **Question 7**      | ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                                                     |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si el sistema almacena automáticamente el último viaje, los usuarios podrán revisarlo fácilmente para analizar decisiones anteriores o retomarlo sin pérdida de datos. |
| **Hypothesis**      | Al menos el 40% de los usuarios accederá al último viaje guardado y lo utilizará como referencia en futuras decisiones dentro de los 3 días siguientes al viaje.       |
| **Null Hypothesis** | La opción de guardar el último viaje no será utilizada significativamente ni impactará en la trazabilidad o análisis por parte de los usuarios.                        |

| **Question 8**      | ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran?               |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Belief**          | Si los capitanes reciben información completa del puerto actual, tomarán decisiones más informadas respecto a detenciones, cambios de curso o abastecimiento.   |
| **Hypothesis**      | El 65% de los capitanes usará la información del puerto actual para validar su decisión de detenerse, y el 50% reportará una mejora en la eficiencia operativa. |
| **Null Hypothesis** | La información mostrada sobre el puerto actual no tendrá un impacto perceptible en las decisiones tomadas durante la navegación.                                |

### 8.2.2. Measures

| **Question 1** | ¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo (abierto o cerrado) en la plataforma?                                                                                   |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir el porcentaje de rutas que omiten correctamente puertos cerrados, así como el tiempo promedio que tarda un usuario en completar la planificación de una ruta. Comparar los resultados antes y después de habilitar la lista visible. |

| **Question 2** | ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                                                                                    |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir el tiempo estimado de navegación antes y después de usar la función de ruta automática, así como la frecuencia con la que los usuarios seleccionan la ruta sugerida frente a otras opciones. |

| **Question 3** | ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?                                                       |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir el número de interrupciones logísticas antes y después de usar el sistema de recálculo, además de encuestas de satisfacción relacionadas con confiabilidad ante eventos imprevistos. |

| **Question 4** | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?                                                                 |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir la frecuencia de uso del reporte, el tiempo promedio dedicado al análisis logístico y encuestas de percepción sobre visibilidad y control de rutas antes y después de habilitar la funcionalidad. |

| **Question 5** | ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido?                                 |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir el porcentaje de usuarios que consultan o descargan el reporte final tras su viaje, y cuántos indican que realizaron ajustes en decisiones futuras gracias a dicho reporte. |

| **Question 6** | ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                                                                              |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir la cantidad de veces que los usuarios interactúan con el mapa esquemático durante la planificación del viaje y cuántos indican que mejoraron su comprensión del trayecto gracias a esta visualización. |

| **Question 7** | ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                                                           |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir la frecuencia con la que los usuarios acceden al último viaje guardado y si utilizan esta información como base para planear, modificar o justificar nuevos trayectos. |

| **Question 8** | ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran?                             |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Measure**    | Medir el porcentaje de capitanes que consultan la información del puerto actual y reportan que esa información fue clave para su decisión de detenerse o continuar navegando. |

### 8.2.3. Conditions

| **Question 1**             | ¿Mejorará la toma de decisiones de los usuarios al incorporar una lista visible de puertos con su estado operativo (abierto o cerrado) en la plataforma?                                |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | El porcentaje de rutas correctamente planificadas (sin puertos cerrados) aumentará en al menos un 25% después de implementar la lista visible de puertos, medido con escenarios reales. |
| **Condición de Control**   | No se observará un aumento significativo en la precisión de planificación o reducción de errores sin la lista visible de puertos.                                                       |

| **Question 2**             | ¿Ayudará a optimizar la logística mostrar automáticamente la ruta más corta entre dos puertos en la plataforma?                          |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | El tiempo estimado de navegación se reducirá en un 20% o más en las rutas planificadas con la función de ruta automática.                |
| **Condición de Control**   | No habrá cambios significativos en el tiempo estimado de viaje o selección de rutas frente al método anterior sin sugerencia automática. |

| **Question 3**             | ¿Puede mejorar la confiabilidad del sistema recalcular la ruta automáticamente en caso de cierre de un puerto durante la navegación?         |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Los usuarios reportarán una reducción del 20% o más en interrupciones logísticas tras usar el sistema de recálculo.                          |
| **Condición de Control**   | No se observará diferencia significativa en interrupciones o percepción de confiabilidad entre usuarios con y sin acceso a la funcionalidad. |

| **Question 4**             | ¿Ayudaría a los operadores logísticos disponer de un reporte de navegación sencillo para monitorear el estado y desempeño de sus rutas?                                            |
|----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Los usuarios aumentarán en un 25% la satisfacción relacionada con la supervisión logística tras el uso del reporte, y se reducirá en un 15% el tiempo de análisis manual de rutas. |
| **Condición de Control**   | No habrá mejoras significativas en satisfacción ni reducción en tiempos de análisis tras la implementación del reporte.                                                            |

| **Question 5**             | ¿Mejorará la capacidad de análisis post-viaje ofrecer a los usuarios un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido?        |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Al menos el 40% de los usuarios consultarán el reporte final después del viaje y un 25% reportará mejoras en decisiones posteriores.                     |
| **Condición de Control**   | Los usuarios tendrán acceso al sistema sin reporte final, y se medirá si hay cambios en su comportamiento o planificación posterior sin esa herramienta. |

| **Question 6**             | ¿Ayudará a los usuarios a comprender mejor sus trayectos un mapa esquemático visual de los puertos disponibles?                                                 |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Se habilita el mapa esquemático interactivo y se mide si al menos el 50% de los usuarios lo utilizan y un 30% indica que mejoró su comprensión.                 |
| **Condición de Control**   | Se usa únicamente una lista textual sin visualización gráfica y se mide si existen diferencias significativas en la planificación y entendimiento del trayecto. |

| **Question 7**             | ¿Facilitará la evaluación y trazabilidad permitir que el sistema guarde automáticamente el último viaje realizado?                |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Se habilita la función de guardado automático y se mide si al menos el 40% accede al historial dentro de las 72 horas siguientes. |
| **Condición de Control**   | No se guarda el viaje anterior automáticamente; los usuarios deben registrar sus rutas manualmente si desean conservarlas.        |

| **Question 8**             | ¿Ayudará a tomar mejores decisiones permitir a los capitanes ver información detallada (nombre, país, estado) del puerto en el que se encuentran?     |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Mostrar información detallada del puerto actual y medir si al menos el 50% de los capitanes la usa para tomar decisiones de detención o continuidad.. |
| **Condición de Control**   | No se muestra información del puerto actual; el capitán debe basarse en su experiencia o información externa para decidir.                            |

### 8.2.4. Scale Calculations and Decisions

Este modelo se basa en el uso de métricas cuantificables para verificar el cumplimiento de las hipótesis formuladas en el desarrollo del proyecto. A cada hipótesis se le asigna un indicador de éxito que permite clasificar los resultados en distintos niveles de desempeño. Se considera que una hipótesis se valida de forma ideal cuando los resultados alcanzan exactamente el objetivo establecido; aceptable, cuando se sitúan entre el mínimo esperado y el ideal; y desfavorable, si están por debajo del umbral mínimo, lo cual sugiere la necesidad de revisar la funcionalidad o el enfoque aplicado. Adicionalmente, se reconoce un nivel excelente cuando la métrica supera el valor ideal en un 25% o más, lo que representa un logro destacado. Este enfoque facilita la toma de decisiones objetivas, basadas en datos, para validar, ajustar o rediseñar elementos clave dentro del proyecto Mushroom.

| **Factor**                                                                        | **Desfavorable**                                                 | **Aceptable**                                               | **Ideal**                                                             | **Excelente**                                                                                        | **Métrica**                                                                                                                                | **Decisión / Acción**                                                                                                                                                                                             | **Estado** |
|-----------------------------------------------------------------------------------|------------------------------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Visualización de puertos mejora la precisión de planificación de rutas en un 30%. | <20% de mejora en rutas planificadas correctamente.              | 20%–29% de mejora en la selección de puertos disponibles.   | 30% de mejora en la precisión de planificación.                       | 37.5% de mejora en exactitud y reducción de errores.                                                 | % de rutas sin errores + tiempo promedio de planificación.                                                                                 | Si se alcanza el valor ideal o excelente, mantener y extender esta funcionalidad a otros módulos de planificación. Si el resultado es desfavorable, rediseñar la interfaz de la lista y reforzar los indicadores  | X          |
| Ruta automática reduce el tiempo estimado de navegación en un 20%.                | <12% de reducción en tiempo estimado de navegación.              | 12%–19% de mejora en tiempos planificados.                  | 20% de mejora en eficiencia de navegación.                            | 25% de mejora en precisión y ahorro de tiempo/logística.                                             | Tiempo estimado de navegación + % de usuarios que aceptan la ruta sugerida.                                                                | Mantener el algoritmo de ruta automática como funcionalidad por defecto. Si el resultado es desfavorable, ajustar parámetros del cálculo o mejorar visualización de rutas para mayor comprensión.                 | X          |
| Recalcular rutas ante cierre mejora la continuidad operativa en un 25%.           | <15% de mejora en continuidad o reducción de interrupciones.     | 15%–24% de mejora en confiabilidad logística.               | 25% de mejora en continuidad operativa y percepción de confiabilidad. | 31.25% de mejora en métricas de continuidad y respuesta ante imprevistos.                            | Cantidad de interrupciones, rutas recalculadas correctamente, y puntuación en confiabilidad del sistema.                                   | Integrar algoritmo de recálculo con notificaciones inmediatas y sistema de contingencia visual para desvíos. Si es desfavorable, revisar fuentes de datos y frecuencia de actualización.                          | X          |
| Reporte de navegación sencillo mejora el control logístico y eficiencia en un 25% | <15% de mejora en visibilidad o reducción de tiempos.            | 15%–24% de mejora en control operativo y análisis de rutas. | 31.25% de mejora en percepción de control y eficiencia logística.     | Frecuencia de uso del reporte, reducción en tiempo de análisis, puntuación en visibilidad operativa. | Implementar reporte exportable con resumen de navegación. Si no se alcanzan métricas mínimas, ajustar contenido visual o nivel de detalle. | X                                                                                                                                                                                                                 |
| Generar reportes post-viaje mejora la trazabilidad y análisis en un 30%           | <20% de los usuarios accede o los usa para modificar decisiones. | 20%–29% de usuarios accede y aplica cambios.                | 30% accede al reporte y modifica decisiones futuras.                  | >37.5% accede y modifica decisiones.                                                                 | % de usuarios que acceden al reporte + % que modifican acciones posteriores.                                                               | Si es ideal o excelente, estandarizar esta funcionalidad en todas las rutas. Si es desfavorable, rediseñar el reporte para hacerlo más visual y útil.                                                             | X          |
| Visualización de puertos mejora la precisión de planificación de rutas en un 30%. | <20% de mejora en rutas planificadas correctamente.              | 20%–29% de mejora en la selección de puertos disponibles.   | 30% de mejora en la precisión de planificación.                       | >37.5% de mejora en exactitud y reducción de errores.                                                | % de rutas sin errores + tiempo promedio de planificación.                                                                                 | Si se alcanza el valor ideal o excelente, mantener y extender esta funcionalidad a otros módulos de planificación. Si el resultado es desfavorable, rediseñar la interfaz de la lista y reforzar los indicadores. | X          |
| Almacenar el último viaje incrementa la trazabilidad en un 25%.                   | <15% de usuarios accede al historial dentro de las 72 horas.     | 15%–24% accede.                                             | 25% accede.                                                           | >31.25% accede al historial.                                                                         | % de accesos al historial dentro de las 72 horas posteriores al viaje.                                                                     | Si es ideal o superior, mantener activado por defecto. Si es desfavorable, hacer más visible el botón o agregar alertas sugeridas.                                                                                | X          |
| Mostrar información del puerto actual mejora decisiones operativas en 40%.        | <25% usa la información para decisiones.                         | 25%–34% lo usa.                                             | 40% de uso en toma de decisiones.                                     | >50% de uso con impacto declarado.                                                                   | % de capitanes que consultan la información del puerto y reportan uso para decisión operativa.                                             | Si ideal o excelente, mantener como acceso rápido. Si es desfavorable, reubicar el botón o incorporar más datos contextuales.                                                                                     | X          |

### 8.2.5. Methods Selection

| **Herramienta**      | **Precio**                                       | **Capacidad de Análisis**                                                                              | **Sencillez**                                               | **Ventajas**                                                                                                                                |
|----------------------|--------------------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Google Analytics** | Plan gratuito con opción a créditos ampliables   | Análisis profundo de datos de usuarios, comportamiento y flujos de navegación.                         | Aprendizaje progresivo y visualización clara de métricas.   | Generación robusta de reportes y gran integración con otros servicios de Google (Ads, Search Console, etc.).                                |
| **Catchpoint**       | Basado en suscripción, incluye versión de prueba | Monitoreo avanzado de rendimiento y experiencia de usuario desde múltiples ubicaciones y dispositivos. | Interfaz detallada, dirigida a usuarios técnicos.           | Ideal para proyectos con alcance global; permite observar desempeño desde diferentes contextos geográficos en tiempo real.                  |
| **RedLine13**        | Gratuito con limitaciones                        | Plataforma enfocada en pruebas de carga, estrés y rendimiento de aplicaciones web y backend.           | Información condensada y centrada en simulaciones.          | Simulación de tráfico masivo, útil para validar la escalabilidad de servicios antes del despliegue en producción.                           |
| **Lighthouse**       | Gratuito, disponible para ejecución local        | Auditoría de experiencia del usuario: rendimiento, accesibilidad, SEO y buenas prácticas.              | Información simplificada y puntajes globales por categoría. | Métricas claras para mejorar la experiencia de usuario, identificar cuellos de botella y optimizar la calidad general de la aplicación web. |

### 8.2.6. Data Analytics: Goals, KPIs and Metrics Selection

Se llevaron a cabo pruebas de rendimiento, accesibilidad y mejores prácticas con Lighthouse en nuestra aplicación Agro Connect para evaluar su desempeño y optimizar la experiencia de usuario. A continuación, mostramos unos ejemplos de ambos segmentos objetivos.

<img src="../../assets/img/chapter-VIII/Test1.png" style="width:600px; height:auto;" alt="Test Pipeline Components">

<img src="../../assets/img/chapter-VIII/Test2.png" style="width:600px; height:auto;" alt="Test Pipeline Components">

<img src="../../assets/img/chapter-VIII/Test3.png" style="width:600px; height:auto;" alt="Test Pipeline Components">

<img src="../../assets/img/chapter-VIII/Test4.png" style="width:600px; height:auto;" alt="Test Pipeline Components">


### 8.2.7. Web and Mobile Tracking Plan

En Mushroom, nuestro objetivo es monitorear de forma estratégica tanto la versión web como móvil de la plataforma para optimizar la experiencia de los usuarios y mejorar la eficiencia operativa en la toma de decisiones logísticas. A medida que nos acercamos a la fase final del proyecto, se establecerá un plan de seguimiento robusto que permitirá evaluar el impacto real de las funcionalidades desarrolladas.

**Etapa 1: Implementación Inicial**

Durante esta primera fase se enfocará el monitoreo en la incorporación de nuevas funcionalidades clave y en la recolección de datos iniciales que servirán como línea base para futuras comparaciones.

- Recolección de Datos
Métricas de uso: Se medirá el número de usuarios activos, duración promedio de sesión, y tasa de conversión en funcionalidades críticas como simulación de rutas o recepción de alertas.

- Interacciones del usuario: Se registrarán clics, navegación por secciones específicas (como panel de riesgos o mapa logístico), y participación en el foro colaborativo.

- Feedback directo: A través de encuestas integradas y herramientas de retroalimentación, se recogerán impresiones sobre la usabilidad general y la utilidad de las funcionalidades añadidas.

**Análisis Comparativo**

Los datos recogidos se contrastarán con métricas históricas de la plataforma (previas a la actualización) para medir el impacto inmediato de las mejoras y determinar si se cumplen las hipótesis de valor.

**Etapa 2: Seguimiento Continuo**

Tras la implementación inicial, se establecerá un sistema de monitoreo continuo para mantener el control sobre el rendimiento y adaptar la plataforma a las necesidades cambiantes de los usuarios.

**Recolección de Datos**

- Métricas en tiempo real: Se emplearán herramientas como Google Analytics, Catchpoint o Lighthouse para observar el comportamiento del usuario en tiempo real.

- Segmentación de usuarios: Se analizarán patrones de uso por tipo de actor (navieras, exportadores, operadores logísticos), permitiendo decisiones más focalizadas.

- Tasa de retención: Se evaluará la retención de usuarios tras cada iteración para entender el impacto sostenido de las nuevas funcionalidades.

**Evaluación y Ajustes**

- Informes mensuales: Se elaborarán reportes periódicos con hallazgos clave, métricas de rendimiento y recomendaciones específicas.

- Iteración guiada por datos: Basándose en los resultados cuantitativos y el feedback cualitativo, se realizarán mejoras iterativas que aseguren que Mushroom evoluciona según las necesidades reales del ecosistema logístico.


## 8.3. Experimentation

### 8.3.1. To-Be User Stories

| **ID** | **Título**                                             | **Descripción**                                                                                                                                                                                               | **Criterios de aceptacion**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| US00   | Visualizar lista de puertos con su estado operativo   | Como usuario, quiero ver una lista de puertos con su estado operativo (abierto o cerrado), para evitar planificar rutas hacia puertos inaccesibles.                                                         | **Escenario 1:** Given que el usuario accede a la sección de navegación, When selecciona la opción de visualizar puertos, Then el sistema debe mostrar una lista con nombre, país y estado de cada puerto, And usar íconos o colores para indicar si están abiertos o cerrados. <br> **Escenario 2:** Given que el usuario desea ver solo puertos cerrados, When aplica el filtro correspondiente, Then el sistema debe mostrar únicamente los puertos no disponibles.                                                                                  |
| US01   | Mostrar ruta más corta entre dos puertos              | Como usuario, quiero que el sistema muestre la ruta más corta entre dos puertos, para ahorrar tiempo y recursos.                                                                                            | **Escenario 1:** Given que el usuario ha seleccionado un puerto de origen y uno de destino, When confirma la selección, Then el sistema debe calcular y mostrar visualmente la ruta más corta, And detallar distancia total y puertos intermedios. <br> **Escenario 2:** Given que existen múltiples rutas posibles, When el sistema determina cuál es la más corta, Then debe destacarla como la opción recomendada, And notificar al usuario con un mensaje o ícono.                                                                |
| US02   | Recalcular ruta automáticamente por cierre de puerto  | Como usuario, quiero que el sistema recalcule automáticamente la ruta si un puerto se cierra durante el trayecto, para mantener la continuidad operativa.                                                  | **Escenario 1:** Given que el sistema detecta el cierre de un puerto en la ruta activa, When ocurre este evento, Then el sistema debe recalcular automáticamente una ruta alternativa, And notificar al usuario sobre el desvío sugerido. <br> **Escenario 2:** Given que se ha generado una nueva ruta, When el usuario revisa los detalles, Then debe ver reflejado el cambio con los nuevos puertos y distancias, And recibir una alerta informativa.                                                                    |
| US03   | Ver reporte de navegación durante el viaje           | Como operador logístico, quiero un reporte de navegación en tiempo real para monitorear el estado de la ruta y tomar mejores decisiones.                                                                    | **Escenario 1:** Given que el usuario se encuentra navegando, When accede al panel de reporte, Then debe ver datos como tiempo estimado vs real, desvíos, incidentes y duración total del trayecto. <br> **Escenario 2:** Given que el usuario desea conservar el reporte, When selecciona la opción de exportar, Then el sistema debe permitir descargarlo en PDF o CSV, And aplicar filtros básicos como fechas o rutas.                                                                                                            |
| US04   | Generar reporte final post-viaje                    | Como usuario, quiero recibir un reporte final del viaje realizado para analizar los eventos y ajustar futuras rutas.                                                                                        | **Escenario 1:** Given que el trayecto ha finalizado, When se detecta el fin del viaje, Then el sistema debe generar un reporte que incluya la ruta tomada, tiempos, cierres y desvíos. <br> **Escenario 2:** Given que el reporte ha sido generado, When el usuario lo revisa, Then debe poder descargarlo en PDF o visualizarlo desde la plataforma.                                                                                                                                                            |
| US05   | Visualizar mapa esquemático de los puertos           | Como usuario, quiero visualizar un mapa esquemático con los puertos disponibles para planificar mis rutas de manera más visual e intuitiva.                                                                 | **Escenario 1:** Given que el usuario accede al mapa interactivo, When se cargan los datos, Then el sistema debe mostrar nodos representando puertos, líneas de conexión, y colores que indiquen su estado. <br> **Escenario 2:** Given que el usuario interactúa con el mapa, When hace clic en un nodo o hace zoom, Then el sistema debe ampliar la información del puerto seleccionado, And permitir elegirlo como origen o destino.                                                                                                   |
| US06   | Guardar automáticamente el último viaje              | Como usuario, quiero que el sistema guarde automáticamente mi último trayecto para revisarlo y usarlo como referencia en futuras decisiones.                                                                | **Escenario 1:** Given que el usuario ha finalizado un trayecto, When el sistema detecta su finalización, Then debe guardar automáticamente el viaje en el perfil, And etiquetarlo como “último viaje realizado”. <br> **Escenario 2:** Given que el usuario accede al historial, When consulta el último viaje, Then debe poder visualizar la ruta, tiempos y puertos recorridos, And continuar la planificación desde esa información.                                                                      |
| US07   | Ver información del puerto actual                   | Como capitán, quiero ver información detallada del puerto en el que me encuentro, para tomar decisiones inmediatas sobre detenerme o continuar.                                                             | **Escenario 1:** Given que el capitán se encuentra en un puerto, When consulta la vista informativa, Then el sistema debe mostrar nombre, país y estado operativo (abierto/cerrado) del puerto actual. <br> **Escenario 2:** Given que el puerto actual está cerrado, When el sistema presenta esta información, Then debe alertar al capitán con una advertencia visible, And sugerir rutas alternativas si corresponde.                                                             |

### 8.3.2. To-Be Product Backlog

| **ID**  | **Título**                                             | **Descripción (Formato User Story)**                                                                                                                                                                                      | **Story Points** |
|--------|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| US00   | Visualizar lista de puertos con su estado operativo    | Como usuario, quiero ver una lista de puertos con su estado operativo (abierto o cerrado), para evitar planificar rutas hacia puertos inaccesibles.                                                                      | 8                |
| US01   | Mostrar ruta más corta entre dos puertos               | Como usuario, quiero que el sistema muestre la ruta más corta entre dos puertos, para ahorrar tiempo y recursos.                                                                                                          | 8                |
| US02   | Recalcular ruta automáticamente por cierre de puerto   | Como usuario, quiero que el sistema recalcule automáticamente la ruta si un puerto se cierra durante el trayecto, para mantener la continuidad operativa.                                                               | 8                |
| US03   | Ver reporte de navegación durante el viaje             | Como operador logístico, quiero un reporte de navegación en tiempo real para monitorear el estado de la ruta y tomar mejores decisiones.                                                                                 | 5                |
| US04   | Generar reporte final post-viaje                       | Como usuario, quiero recibir un reporte final del viaje realizado para analizar los eventos y ajustar futuras rutas.                                                                                                     | 3                |
| US05   | Visualizar mapa esquemático de los puertos             | Como usuario, quiero visualizar un mapa esquemático con los puertos disponibles para planificar mis rutas de manera más visual e intuitiva.                                                                              | 5                |
| US06   | Guardar automáticamente el último viaje                | Como usuario, quiero que el sistema guarde automáticamente mi último trayecto para revisarlo y usarlo como referencia en futuras decisiones.                                                                             | 3                |
| US07   | Ver información del puerto actual                      | Como capitán, quiero ver información detallada del puerto en el que me encuentro, para tomar decisiones inmediatas sobre detenerme o continuar.                                                                          | 5                |

### 8.3.3. Pipeline-supported, Experiment-Driven To-Be Software Platform Lifecycle

### 8.3.3.1 To-Be Sprint Backlog

| **Sprint #1** | Sprint 1                                   |                |                                           |                                                                                               |                       |                 |        |
|---------------|--------------------------------------------|----------------|-------------------------------------------|-----------------------------------------------------------------------------------------------|-----------------------|-----------------|--------|
| User Story    |                                            | Work Item/Task |                                           |                                                                                               | Estimation<br>(Hours) | Assigned To     | Status |
| Id            | Title                                      | Id             | Title                                     | Description                                                                                   |                       |                 |        |
| US00          | Visualizar lista de puertos disponibles    | TK1            | Diseñar vista de listado de puertos       | Crear una lista visual con nombre, país y estado del puerto.                                  | 1 hora                | Jose M.         | Done   |
| US00          | Visualizar lista de puertos disponibles    | TK2            | Implementar filtro de estado del puerto   | Agregar opción para mostrar solo puertos cerrados o abiertos.                                 | 1 hora                | Jose M.         | Done   |
| US01          | Mostrar ruta más corta entre dos puertos   | TK3            | Diseñar lógica de cálculo de rutas        | Implementar algoritmo para calcular ruta más corta entre puertos.                             | 2 horas               | Fernando Lizano | Done   |
| US01          | Mostrar ruta más corta entre dos puertos   | TK4            | Mostrar ruta calculada al usuario         | Desplegar la ruta más corta en una vista con detalles.                                        | 1 hora                | Fernando Lizano | Done   |
| US02          | Recalcular ruta por cierre de puerto       | TK5            | Detectar cierre de puerto                 | Consultar base de datos y detectar si un puerto fue cerrado durante la navegación.            | 1 hora                | Jose M.         | Done   |
| US02          | Recalcular ruta por cierre de puerto       | TK6            | Sugerir nueva ruta                        | Notificar al usuario y sugerir automáticamente una nueva ruta alterna.                        | 1 hora                | Jose M.         | Done   |
| US03          | Ver reporte de navegación durante viaje    | TK7            | Mostrar información de trayecto actual    | Crear vista con tiempos estimados, reales y desviaciones mientras navega.                     | 1 hora                | Juan Pescoran   | Done   |
| US03          | Ver reporte de navegación durante viaje    | TK8            | Exportar reporte parcial                  | Permitir exportar datos actuales del viaje a CSV o PDF.                                       | 1 hora                | Juan Pescoran   | Done   |
| US04          | Generar reporte final post-viaje           | TK9            | Generar reporte automático post-viaje     | Crear informe con ruta tomada, eventos y comparación de tiempos estimados vs reales.          | 1 hora                | Jose M.         | Done   |
| US04          | Generar reporte final post-viaje           | TK10           | Descargar o visualizar reporte            | Habilitar visualización desde perfil y descarga en PDF.                                       | 1 hora                | Jose M.         | Done   |
| US05          | Visualizar mapa esquemático de puertos     | TK11           | Diseñar mapa interactivo                  | Crear mapa interactivo con puertos conectados, rutas y estados de operación.                  | 1 hora                | Jose M.         | Done   |
| US05          | Visualizar mapa esquemático de puertos     | TK12           | Añadir zoom y selección de nodos          | Habilitar zoom, clic en puertos y visualización contextual.                                   | 1 hora                | Jose M.         | Done   |
| US06          | Guardar automáticamente el último viaje    | TK13           | Almacenar último trayecto                 | Guardar automáticamente los datos del último trayecto finalizado.                             | 1 hora                | Augusto V.      | Done   |
| US06          | Guardar automáticamente el último viaje    | TK14           | Mostrar último viaje en pantalla inicial  | Permitir al usuario acceder fácilmente al último viaje desde su perfil.                       | 1 hora                | Augusto V.      | Done   |
| US07          | Ver información del puerto actual          | TK15           | Detectar ubicación y mostrar información  | Mostrar nombre, país y estado del puerto más cercano al usuario.                              | 1 hora                | Jose M.         | Done   |
| US07          | Ver información del puerto actual          | TK16           | Notificar si el puerto está cerrado       | Mostrar advertencia si el puerto está cerrado y sugerir cambiar ruta.                         | 1 hora                | Jose M.         | Done   |

#### 8.3.3.2. Implemented To-Be Landing Page Evidence



#### 8.3.3.3. Implemented To-Be Frontend-Web Application Evidence



#### 8.3.3.4. Implemented To-Be Native-Mobile Application Evidence



#### 8.3.3.5. Implemented To-Be RESTful API and/or Serverless Backend Evidence



#### 8.3.3.5. Team Collaboration Insights



### 8.3.4. To-Be Validation Interviews

#### 8.3.4.1. Diseño de Entrevistas



#### 8.3.4.2. Registro de Entrevistas



## 8.4. Experiment Aftermath & Analysis

### 8.4.1. Analysis and Interpretation of Results



### 8.4.2. Re-scored and Re-prioritized Question Backlog



## 8.5. Continuous Learning
### 8.5.1. Shareback Session Artifacts: Learning Workflow



## 8.6.  To-Be Software Platform Pre-launch
### 8.6.1. About-the-Product Intro Video



## Conclusiones

- La aplicación estructurada del enfoque Lean UX en nuestro proyecto Mushroom ha sido clave para definir con claridad los segmentos de usuarios, los competidores directos y las principales demandas del mercado. Desde los problem statements iniciales hasta los hypothesis statements y el desarrollo del Lean UX canvas, cada fase ha fortalecido tanto la agilidad como la precisión en el diseño y evolución de nuestra solución.
<br>
- A lo largo del capítulo II se llevó a cabo un análisis integral del entorno competitivo, junto con entrevistas y actividades de needfinding, lo cual permitió una comprensión profunda de los usuarios. Esta investigación fundamentó la propuesta de valor de Mushroom, asegurando que la solución responda directamente a necesidades reales del público objetivo.
<br>
- La identificación temprana de los requisitos del proyecto resultó esencial para cimentar una base sólida sobre la cual construir Mushroom. Herramientas como los empathy mappings, impact mappings, user personas, así como los As-Is y To-Be Scenario Mappings, ayudaron a visualizar y comprender los procesos del usuario antes y después de la implementación de nuestra aplicación. A su vez, las user stories detallaron cómo se espera que interactúen los usuarios con la solución, mientras que el product backlog permitió priorizar funcionalidades clave, optimizando el uso de recursos durante el desarrollo.
<br>
- La implementación del backend utilizando Spring Boot, junto con la alineación de los bounded contexts bajo la arquitectura DDD, permitió establecer una estructura técnica robusta y escalable. La documentación generada en Swagger fue fundamental para facilitar la comprensión de los distintos módulos del sistema y mejorar la colaboración entre los miembros del equipo. Además, las entrevistas de validación con usuarios proporcionaron retroalimentación valiosa: destacaron aspectos positivos como la utilidad de la Landing Page y la facilidad de navegación en la Web App, pero también señalaron oportunidades de mejora en aspectos como el diseño, la presentación de información y la navegación general. Estos aprendizajes ofrecen una base sólida para futuras iteraciones centradas en elevar la experiencia del usuario y la eficacia del producto final.

## Bibliografia

1. Lean UX, diseño centrado en el usuario y validación:

- Gothelf, J., & Seiden, J. (2021). Lean UX: Designing Great Products with Agile Teams (3rd ed.). O’Reilly Media.
- Norman, D. A. (2023). The Design of Everyday Things: Revised and Expanded Edition. Basic Books.
- Nielsen Norman Group. (2020-2024). UX Research & User-Centered Design.

2. Arquitectura backend, Spring Boot y DDD
- Evans, E. (2021). Domain-Driven Design: Tackling Complexity in the Heart of Software. Addison-Wesley.
- Walls, C. (2022). Spring in Action (6th ed.). Manning Publications.
- Richardson, C. (2019). Microservices Patterns: With examples in Java. Manning Publications.
- Khononov, V. (2021). Learning Domain-Driven Design: Aligning software architecture and business strategy (1st ed.) [Kindle version]. O’Reilly Media. 

3. Documentación de APIs y Swagger
- SmartBear Software. (2023). OpenAPI Specification (Swagger). https://swagger.io/specification/

4. UX y herramientas de diseño
- Interaction Design Foundation. (2023). User Personas, Journey Mapping, As-Is & To-Be Scenarios. https://www.interaction-design.org

5. Informacion de nuestra problematica:

India Briefing. (2024, enero 10). La actual crisis del Mar Rojo obliga al transporte marítimo mundial a buscar nuevas rutas. https://www.india-briefing.com/news/la-actual-crisis-del-mar-rojo-obliga-al-transporte-maritimo-mundial-a-buscar-nuevas-rutas-31590.html

- El Economista. (2024, enero 12). Tesla y Volvo frenan su producción de autos por la crisis del transporte marítimo en el mar Rojo. https://www.eleconomista.com.mx/empresas/Tesla-y-Volvo-frenan-su-produccion-de-autos-por-la-crisis-del-transporte-maritimo-en-el-mar-Rojo-20240112-0042.html
