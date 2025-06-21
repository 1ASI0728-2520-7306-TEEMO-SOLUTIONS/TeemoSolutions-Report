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
| **Pregunta**                                                                                              | **Confianza**                                                                     | **Riesgo**                                                                            | **Impacto**                                                                                     | **Interés**                                                                                   | **Total Score** |
| --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------- |
| ¿Mejorará la experiencia de los usuarios incorporar un **modo oscuro** en la plataforma web?              | 7 – Es una funcionalidad cada vez más esperada en plataformas modernas.           | 2 – Bajo riesgo técnico; implementación estandarizada.                                | 6 – Mejora la usabilidad, aunque no afecta funciones core del sistema.                          | 5 – Interés moderado, sobre todo en usuarios que operan en condiciones de baja luz.           | **20**          |
| ¿Se ampliará el alcance de usuarios al añadir **traducciones** (inglés, chino) en la plataforma?          | 6 – Puede captar nuevos mercados, aunque dependerá del perfil real de usuarios.   | 3 – Riesgo medio por la complejidad de mantener versiones multilingües actualizadas.  | 7 – Facilita la internacionalización de la solución.                                            | 6 – Atractivo para usuarios globales y clientes corporativos fuera del mundo hispanohablante. | **22**          |
| ¿Incrementará la participación de usuarios crear un **foro de eventos y rutas recomendadas**?             | 8 – Experiencias similares en plataformas B2B indican aumento en la interacción.  | 4 – Riesgo medio por la necesidad de moderación y control de calidad del contenido.   | 8 – Puede incentivar la colaboración entre actores del sector logístico.                        | 7 – Probable interés entre operadores y agentes logísticos con experiencia compartida.        | **27**          |
| ¿Mejorará la satisfacción de usuarios un sistema de **alertas personalizadas sobre disrupciones**?        | 9 – Alta confianza; soluciones similares en logística muestran buena recepción.   | 2 – Bajo riesgo; funcionalidad común en apps empresariales.                           | 9 – Alto impacto en la gestión operativa y toma de decisiones en tiempo real.                   | 8 – Muy relevante para quienes buscan proactividad en la planificación logística.             | **28**          |
| ¿Fortalecerá el vínculo con el ecosistema global una sección de **oportunidades comerciales/logísticas**? | 7 – Basado en el interés de navieras y exportadores en plataformas colaborativas. | 4 – Riesgo medio por la presencia de competidores ya establecidos en el comercio B2B. | 10 – Potencial alto para abrir nuevas conexiones y generar ingresos por comisiones o servicios. | 6 – Interés moderado al inicio, pero puede crecer con la implementación y campañas asociadas. | **27**          |

### 8.1.4. Question Backlog

| **Prioridad (1,2,3,5,8)** | **Pregunta**                                                                                                                                          |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1**                     | ¿Mejorará la experiencia de los usuarios al incorporar un **modo oscuro** en la plataforma web de *Mushroom*?                                         |
| **3**                     | ¿Aumentará la audiencia incorporar **traducciones** al inglés, chino u otros idiomas para mejorar la accesibilidad de la plataforma?                  |
| **3**                     | ¿Fomentará la participación entre usuarios la implementación de un **foro colaborativo** para compartir alertas logísticas, rutas y buenas prácticas? |
| **5**                     | ¿Incrementará la satisfacción del usuario la integración de un sistema de **notificaciones personalizadas** ante eventos críticos en rutas marítimas? |
| **5**                     | ¿Fortalecerá la conexión con nuevos mercados una **sección de oportunidades comerciales** para navieras, exportadores y operadores logísticos?        |

### 8.1.5. Experiment Cards

| **Question** | ¿Mejorará la experiencia de los usuarios al añadir un modo oscuro a la plataforma web de Mushroom? |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Why**      | Incluir un modo oscuro puede mejorar la experiencia visual de los usuarios, especialmente para quienes trabajan en turnos nocturnos o en entornos con poca iluminación. Esta funcionalidad reduce la fatiga ocular y puede aumentar el tiempo efectivo de uso, mejorando así el compromiso general. |
| **What**     | Desarrollar un modo oscuro que pueda activarse fácilmente desde las preferencias del usuario. Esto implica adaptar los colores de fondo, texto e íconos en toda la interfaz para ofrecer una navegación más cómoda sin comprometer la legibilidad o funcionalidad. |
| **Hypothesis** | Se espera que, tras la implementación del modo oscuro, el 60% de los usuarios reporten una mejor experiencia de uso y que el tiempo promedio de sesión aumente en al menos un 25%. |

| **Question** | ¿Incrementará la participación de los usuarios al implementar un foro logístico para compartir alertas y rutas sugeridas? |
|--------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Why**      | Un espacio colaborativo fortalece la comunidad, permite compartir experiencias útiles y genera mayor compromiso entre actores logísticos. |
| **What**     | Crear un foro moderado dentro de la plataforma donde los usuarios puedan compartir rutas, alertas y recomendaciones prácticas, con funciones de filtrado y control de calidad del contenido. |
| **Hypothesis** | Se estima que la participación aumente en un 30% respecto al periodo anterior a su implementación, especialmente entre usuarios activos y recurrentes. |

| **Question** | ¿Se expandirá la audiencia de Mushroom con la incorporación de traducciones al inglés, chino u otros idiomas clave? |
|--------------|-------------------------------------------------------------------------------------------------------------------------|
| **Why**      | Las traducciones mejoran la accesibilidad global y posicionan la plataforma en mercados internacionales con alto potencial logístico. |
| **What**     | Traducir la interfaz y contenidos principales a inglés y chino, implementando un sistema automatizado que permita actualizar las traducciones conforme se actualiza la plataforma. |
| **Hypothesis** | La base de usuarios de habla inglesa o china crecerá un 15% dentro de los tres meses siguientes a la publicación de la versión multilingüe. |

| **Question** | ¿Mejorará la satisfacción de los usuarios la integración de notificaciones personalizadas ante disrupciones logísticas? |
|--------------|----------------------------------------------------------------------------------------------------------------------------|
| **Why**      | Las alertas proactivas mejoran la toma de decisiones y la planificación, especialmente ante eventos inesperados como cierres de puertos, tormentas o conflictos en rutas clave. |
| **What**     | Desarrollar un sistema de notificaciones configurables basado en eventos externos, ubicación geográfica y preferencias del usuario. Las alertas deben ser útiles, oportunas y fáciles de gestionar. |
| **Hypothesis** | Se proyecta que la tasa de uso de herramientas de planificación aumente un 40% y que la satisfacción general del usuario se eleve en un 20%, especialmente en usuarios operativos. |

| **Question** | ¿Fortalecerá la conexión con otros actores del mercado logístico una sección de oportunidades comerciales dentro de Mushroom? |
|--------------|----------------------------------------------------------------------------------------------------------------------------------|
| **Why**      | Permite crear alianzas estratégicas, publicar ofertas y demandas de servicios logísticos, y conectar actores relevantes del ecosistema marítimo. Esto podría convertir a Mushroom en un hub de colaboración sectorial. |
| **What**     | Implementar una sección tipo marketplace donde operadores, navieras o clientes puedan listar servicios, buscar socios y cerrar tratos. Incluir filtros inteligentes y medidas de seguridad para garantizar transacciones confiables. |
| **Hypothesis** | Se espera que las conexiones comerciales dentro de la plataforma aumenten un 50% en los primeros seis meses desde el lanzamiento del módulo de comercio colaborativo. |

## 8.2. Experiment Design
### 8.2.1. Hypotheses

| **Question** | ¿Mejorará la experiencia de los usuarios al añadir un modo oscuro a la plataforma web de Mushroom? |
|--------------|------------------------------------------------------------------------------------------------------|
| **Belief**   | Al incluir un modo oscuro, se mejora la usabilidad para usuarios que operan en ambientes con poca luz, reduciendo la fatiga visual y aumentando tanto la satisfacción como el tiempo de permanencia en la plataforma. |
| **Hypothesis** | La implementación de un modo oscuro incrementará el tiempo promedio de uso y la satisfacción del usuario en al menos un 20%. |
| **Null Hypothesis** | La habilitación del modo oscuro no afectará significativamente el tiempo de uso ni la satisfacción del usuario. |

| **Question** | ¿Aumentará la audiencia al agregar traducciones al sistema en idiomas como inglés o chino? |
|--------------|----------------------------------------------------------------------------------------------|
| **Belief**   | Ofrecer la plataforma en múltiples idiomas facilitará el acceso de usuarios internacionales, aumentando la base de clientes y mejorando la aceptación en nuevos mercados logísticos. |
| **Hypothesis** | La implementación de traducciones al inglés y chino aumentará la cantidad de usuarios de estos mercados en un 15% en los tres meses posteriores al lanzamiento. |
| **Null Hypothesis** | La inclusión de traducciones no tendrá un impacto significativo en el número de nuevos usuarios de mercados de habla inglesa o china. |

| **Question** | ¿Mejorará la participación de los usuarios la implementación de un foro logístico para compartir alertas y consejos? |
|--------------|------------------------------------------------------------------------------------------------------------------------|
| **Belief**   | Un foro de colaboración fomentará la interacción entre operadores logísticos, generando una comunidad activa y más comprometida con la plataforma. |
| **Hypothesis** | La implementación del foro aumentará la participación de los usuarios en un 30% en comparación con el período anterior a su habilitación. |
| **Null Hypothesis** | La introducción del foro no tendrá un efecto significativo en la participación de los usuarios. |

| **Question** | ¿Mejorará la satisfacción del usuario la integración de notificaciones personalizadas ante eventos logísticos críticos? |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| **Belief**   | Las notificaciones personalizadas ayudarán a los usuarios a gestionar sus operaciones de forma más organizada y proactiva, mejorando la experiencia general. |
| **Hypothesis** | La integración de este sistema aumentará la tasa de finalización de tareas o acciones logísticas en un 40% y la satisfacción general del usuario en un 20%. |
| **Null Hypothesis** | La implementación de notificaciones personalizadas no tendrá un efecto significativo en la tasa de finalización de tareas ni en la satisfacción del usuario. |

| **Question** | ¿Aumentaría la conexión con otros mercados la inclusión de una sección comercial dentro de Mushroom? |
|--------------|------------------------------------------------------------------------------------------------------------------|
| **Belief**   | Una sección comercial permitirá a los usuarios publicar servicios, buscar aliados estratégicos y realizar transacciones, fomentando un ecosistema logístico más dinámico. |
| **Hypothesis** | La implementación de esta sección generará un incremento del 50% en el número de conexiones comerciales o transacciones en los primeros seis meses. |
| **Null Hypothesis** | La inclusión de la sección comercial no tendrá un efecto significativo en la cantidad de transacciones realizadas. |

### 8.2.2. Measures

| **Question** | ¿Mejorará la experiencia de los usuarios al añadir un modo oscuro a la plataforma web de Mushroom? |
|--------------|------------------------------------------------------------------------------------------------------|
| **Measure**  | Medir la satisfacción de los usuarios a través de encuestas y puntuaciones de experiencia visual antes y después de habilitar el modo oscuro. Esto permitirá evaluar si la nueva funcionalidad mejora la comodidad visual y la percepción general de la plataforma. |

| **Question** | ¿Aumentará la audiencia al agregar traducciones al sistema en idiomas como inglés o chino? |
|--------------|----------------------------------------------------------------------------------------------|
| **Measure**  | Analizar la cantidad de usuarios nuevos provenientes de países de habla inglesa y china, así como el tráfico en la plataforma antes y después de implementar las traducciones. Comparar métricas para determinar el impacto en la audiencia internacional. |

| **Question** | ¿Mejorará la participación de los usuarios la implementación de un foro logístico para compartir alertas y consejos? |
|--------------|------------------------------------------------------------------------------------------------------------------------|
| **Measure**  | Evaluar la cantidad de publicaciones, comentarios e interacciones dentro del foro. Comparar estos datos con el periodo previo a su lanzamiento. Complementar con encuestas para medir la percepción del valor que aporta esta funcionalidad. |

| **Question** | ¿Mejorará la satisfacción del usuario la integración de notificaciones personalizadas ante eventos logísticos críticos? |
|--------------|--------------------------------------------------------------------------------------------------------------------------|
| **Measure**  | Medir la tasa de finalización de tareas o respuestas ante alertas antes y después de implementar el sistema de notificaciones. Complementar con encuestas que evalúen la satisfacción general respecto a la utilidad de esta nueva función. |

| **Question** | ¿Aumentaría la conexión con otros mercados la inclusión de una sección comercial dentro de Mushroom? |
|--------------|------------------------------------------------------------------------------------------------------------------|
| **Measure**  | Contar el número de transacciones realizadas dentro del módulo comercial y analizar métricas de uso (visitas, publicaciones, contactos) antes y después de su implementación. Evaluar si se incrementa la actividad comercial dentro del ecosistema de la plataforma. |

### 8.2.3. Conditions

| **Question** | ¿Mejorará la experiencia de los usuarios al añadir un modo oscuro a la plataforma web de Mushroom? |
|--------------|-----------------------------------------------------------------------------------------------------|
| **Condición Experimental** | La satisfacción del usuario aumentará en un 20% después de implementar el modo oscuro, medido a través de encuestas y puntajes de valoración de la experiencia visual. |
| **Condición de Control**   | No habrá un aumento significativo en la satisfacción del usuario tras la implementación del modo oscuro. |

| **Question** | ¿Aumentará la audiencia al agregar traducciones al sistema en idiomas como inglés o chino? |
|--------------|---------------------------------------------------------------------------------------------|
| **Condición Experimental** | Se espera un aumento del 15% en el número de usuarios provenientes de países de habla inglesa y china tras habilitar las traducciones correspondientes. |
| **Condición de Control**   | No habrá un aumento significativo en el número de usuarios de países de habla inglesa y china tras la implementación de las traducciones. |

| **Question** | ¿Mejorará la participación de los usuarios la implementación de un foro logístico para compartir alertas y consejos? |
|--------------|-----------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | La participación de los usuarios aumentará en un 30% después de la implementación del foro, medido por el número de interacciones y publicaciones. |
| **Condición de Control**   | No habrá un aumento significativo en la participación de los usuarios tras la implementación del foro. |

| **Question** | ¿Mejorará la satisfacción del usuario la integración de notificaciones personalizadas ante eventos logísticos críticos? |
|--------------|---------------------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | La tasa de finalización de tareas aumentará en un 25% después de implementar el sistema de notificaciones personalizadas. |
| **Condición de Control**   | No habrá un aumento significativo en la tasa de finalización de tareas tras la implementación del sistema de notificaciones. |

| **Question** | ¿Fortalecerá la conexión con otros mercados la inclusión de una sección comercial dentro de Mushroom? |
|--------------|----------------------------------------------------------------------------------------------------------------|
| **Condición Experimental** | Se espera que el número de transacciones en la nueva sección de comercio aumente en un 50% durante un período específico tras su implementación. |
| **Condición de Control**   | No habrá un aumento significativo en el número de transacciones en la sección de comercio durante el mismo período. |

### 8.2.4. Scale Calculations and Decisions

Este modelo se basa en el uso de métricas cuantificables para verificar el cumplimiento de las hipótesis formuladas en el desarrollo del proyecto. A cada hipótesis se le asigna un indicador de éxito que permite clasificar los resultados en distintos niveles de desempeño. Se considera que una hipótesis se valida de forma ideal cuando los resultados alcanzan exactamente el objetivo establecido; aceptable, cuando se sitúan entre el mínimo esperado y el ideal; y desfavorable, si están por debajo del umbral mínimo, lo cual sugiere la necesidad de revisar la funcionalidad o el enfoque aplicado. Adicionalmente, se reconoce un nivel excelente cuando la métrica supera el valor ideal en un 25% o más, lo que representa un logro destacado. Este enfoque facilita la toma de decisiones objetivas, basadas en datos, para validar, ajustar o rediseñar elementos clave dentro del proyecto Mushroom.



| **Factor** | **Desfavorable** | **Aceptable** | **Ideal** | **Excelente** | **Métrica** | **Decisión / Acción** | **Estado** |
|-----------|------------------|----------------|-----------|----------------|-------------|------------------------|------------|
| Modo oscuro mejora la experiencia del usuario en un 30% (satisfacción y tiempo de uso). | <20% de mejora | 20%-29% de mejora | 30% de mejora | >37.5% de mejora | Aumento en puntuación de satisfacción y tiempo de uso promedio | Implementar modo oscuro con alternancia entre claro y oscuro para mejorar comodidad visual. | X |
| Traducciones aumentan la audiencia internacional en un 15%. | <10% de aumento | 10%-14% de aumento | 15% de aumento | >18.75% de aumento | Nuevos usuarios de países de habla inglesa o china | Traducir la interfaz y contenido clave al inglés y chino. | X |
| Foro logístico incrementa la participación del usuario en un 30%. | <20% de incremento | 20%-29% de incremento | 30% de incremento | >37.5% de incremento | Número de publicaciones, respuestas e interacciones | Desarrollar foro con categorías temáticas logísticas para facilitar el intercambio entre usuarios. | X |
| Notificaciones personalizadas mejoran la satisfacción en un 25%. | <15% de mejora | 15%-24% de mejora | 25% de mejora | >31.25% de mejora | Tasa de finalización de tareas y puntaje de satisfacción general | Integrar sistema de alertas configurables sobre eventos críticos y recordatorios. | X |
| Sección comercial aumenta transacciones y conexiones en un 40%. | <25% de aumento | 25%-39% de aumento | 40% de aumento | >50% de aumento | Cantidad de transacciones realizadas dentro del módulo comercial | Añadir sección de marketplace logístico para facilitar ofertas y demandas de servicios. | X |

### 8.2.5. Methods Selection

| **Herramienta**   | **Precio**                                      | **Capacidad de Análisis**                                                                                      | **Sencillez**                                                         | **Ventajas**                                                                                                                                   |
|-------------------|--------------------------------------------------|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| **Google Analytics** | Plan gratuito con opción a créditos ampliables  | Análisis profundo de datos de usuarios, comportamiento y flujos de navegación.                                  | Aprendizaje progresivo y visualización clara de métricas.             | Generación robusta de reportes y gran integración con otros servicios de Google (Ads, Search Console, etc.).                               |
| **Catchpoint**    | Basado en suscripción, incluye versión de prueba | Monitoreo avanzado de rendimiento y experiencia de usuario desde múltiples ubicaciones y dispositivos.           | Interfaz detallada, dirigida a usuarios técnicos.                      | Ideal para proyectos con alcance global; permite observar desempeño desde diferentes contextos geográficos en tiempo real.                  |
| **RedLine13**     | Gratuito con limitaciones                        | Plataforma enfocada en pruebas de carga, estrés y rendimiento de aplicaciones web y backend.                    | Información condensada y centrada en simulaciones.                    | Simulación de tráfico masivo, útil para validar la escalabilidad de servicios antes del despliegue en producción.                           |
| **Lighthouse**    | Gratuito, disponible para ejecución local         | Auditoría de experiencia del usuario: rendimiento, accesibilidad, SEO y buenas prácticas.                        | Información simplificada y puntajes globales por categoría.           | Métricas claras para mejorar la experiencia de usuario, identificar cuellos de botella y optimizar la calidad general de la aplicación web. |

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

| User Story ID | Titulo                             | Descripción                                                                                                  | Criterio de Aceptación                                                                                                                                                                                                                         |
|---------------|------------------------------------|--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BS01          | Implementación del modo oscuro     | Como capitán, quiero utilizar la aplicación en modo oscuro para evitar problemas de visión en la oscuridad.  | Scenario 1: Utilizar la aplicación en un entorno oscuro. <br>Given el capitan utiliza la aplicación en modo oscuro <br>When ingresa a la página web <br>And selecciona el modo oscuro <br>So la aplicación cambiara los colores de la interfaz |
| BS02          | Implementación del multilenguaje   | Como empresario, quiero utilizar la aplicación en mi idioma principal para familiarizarme con el contenido.  | Scenario 1: Utilizar la aplicación en ingles.<br>Given el empresario no entiende el idioma principal<br>When selecciona el cambio de idioma<br>And selecciona el ingles<br>So la aplicación cambiara el idioma al ingles                       |
| BS03          | Interacción en foros colaborativos | Como capitán, quiero interactuar con otros usuarios para intercambiar información relevante de la rutas.     | Scenario 1: Utilizar la aplicacion en ingles.<br>Given el empresario no entiende el idioma principal<br>When selecciona el cambio de idioma<br>And selecciona el ingles<br>So la aplicación cambiara el idioma al ingles                                                                                                                                                                                                                                               |
| BS04          | Notificaciones personalizadas      | Como capitán, quiero recibir información más especifica para mantenerme informado de manera rápida.          | Scenario 1: Utilizar la aplicacion en ingles.<br>Given el empresario no entiende el idioma principal<br>When selecciona el cambio de idioma<br>And selecciona el ingles<br>So la aplicación cambiara el idioma al ingles                                                                                                                                                                                                                                               |
| BS05          | Sección Comercial                  | Como empresario, quiero interactuar con otros usuarios para acordar negocios relacionados a la via maritima. | Scenario 1: Negociar en una sección comercial<br>Given el empresario quiere encontrar clientes<br>When selecciona la sección comercial<br>And reciba información de las ofertas o solicitudes<br>So buscara negociar con el cliente.                                                                                                                                                                                                                                               |

### 8.3.2. To-Be Product Backlog

| # Orden | User Story ID | Titulo                             | Story Point (1,2,3,5,8) |
|---------|---------------|------------------------------------|-------------------------|
| 1       | BS01          | Implementación del modo oscuro     | 1                       |
| 2       | BS02          | Implementación del multilenguaje   | 3                       |
| 3       | BS03          | Interacción en foros colaborativos | 3                       |
| 4       | BS04          | Notificaciones personalizadas      | 5                       |
| 5       | BS05          | Sección Comercial                  | 5                       |

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

3. Documentación de APIs y Swagger
- SmartBear Software. (2023). OpenAPI Specification (Swagger). https://swagger.io/specification/

4. UX y herramientas de diseño
- Interaction Design Foundation. (2023). User Personas, Journey Mapping, As-Is & To-Be Scenarios. https://www.interaction-design.org

5. Informacion de nuestra problematica:

India Briefing. (2024, enero 10). La actual crisis del Mar Rojo obliga al transporte marítimo mundial a buscar nuevas rutas. https://www.india-briefing.com/news/la-actual-crisis-del-mar-rojo-obliga-al-transporte-maritimo-mundial-a-buscar-nuevas-rutas-31590.html

- El Economista. (2024, enero 12). Tesla y Volvo frenan su producción de autos por la crisis del transporte marítimo en el mar Rojo. https://www.eleconomista.com.mx/empresas/Tesla-y-Volvo-frenan-su-produccion-de-autos-por-la-crisis-del-transporte-maritimo-en-el-mar-Rojo-20240112-0042.html