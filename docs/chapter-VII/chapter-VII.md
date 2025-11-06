# Capítulo VII: Product Implementation, Validation & Deployment

La implementación, validación y despliegue del producto constituyen fases críticas en el proceso de desarrollo, ya que garantizan que la visión conceptual inicialmente planteada se materialice en una solución funcional, confiable y accesible para los usuarios finales. A través de estas etapas, no solo se concreta el diseño teórico en una aplicación tangible y operativa, sino que también se evalúa su desempeño en condiciones reales, permitiendo identificar posibles deficiencias, corregir errores y optimizar su funcionamiento. Además, este proceso resulta fundamental para verificar la viabilidad técnica del producto, validar las hipótesis del equipo de desarrollo y asegurar que la experiencia del usuario cumpla con los estándares de calidad esperados, fortaleciendo así la propuesta de valor de la solución tecnológica.

## 7.1. Software Configuration Management

Con el propósito de asegurar un ciclo de vida robusto, eficiente y sostenible para el desarrollo de Mushroom, hemos adoptado un conjunto integral de herramientas tecnológicas y metodológicas que respaldan cada una de las etapas clave del proyecto. Estas herramientas nos permiten gestionar el proyecto de manera estructurada, especificar los requerimientos de forma precisa y organizada, diseñar interfaces coherentes y responsivas centradas en la experiencia del usuario, y llevar a cabo un desarrollo colaborativo siguiendo buenas prácticas de ingeniería de software.

En esta sección, se detallarán y justificarán las herramientas seleccionadas para cada uno de los componentes de la solución tecnológica. Específicamente, se abordarán las herramientas de gestión y organización del proyecto, las herramientas de diseño, y también las herramientas orientadas al desarrollo de frontend y backend, esenciales para la construcción de la interfaz de usuario y la lógica del servidor respectivamente.

Asimismo, se explicarán las tecnologías empleadas para la implementación y gestión de la base de datos, que aseguran el almacenamiento eficiente, seguro y escalable de la información, y las herramientas utilizadas en el desarrollo e implementación de las tecnologías emergentes relacionadas al Machine Learning. También se presentarán las herramientas adoptadas para la aplicación móvil, y, finalmente, la landing page.

### 7.1.1. Software Development Environment Configuration

A continuación, se presentan y fundamentan las herramientas adoptadas para el desarrollo de Mushroom, clasificadas según su función en las distintas áreas del ecosistema tecnológico de la solución: gestión y organización del proyecto, diseño de interfaces, desarrollo frontend y backend, gestión de base de datos, construcción de la aplicación móvil y diseño de la landing page. Cada una de estas herramientas cumple un rol clave en la arquitectura del sistema y contribuye al cumplimiento de los objetivos funcionales y no funcionales del producto. Para las herramientas basadas en SaaS (Software como Servicio), se proporcionará la URL de acceso a sus respectivas páginas web, mientras que para aquellas que requieren instalación local, se indicará la ruta de descarga adecuada.

**Project Management:**

Esta sección se enfoca en la planificación estratégica y supervisión operativa del proyecto a lo largo de todo su ciclo de vida, abarcando la coordinación integral del equipo de trabajo, la gestión de tareas individuales y colectivas, así como el seguimiento de las responsabilidades previamente definidas y asignadas, y su presentación y exposición a stakeholders. Con el fin de estructurar de manera eficiente esta gestión, se ha adoptado un enfoque basado en la aplicación de diversos métodos y herramientas de comunicación, coordinación y administración de recursos humanos. Estas prácticas permiten optimizar los flujos de trabajo, garantizar la trazabilidad de las actividades y fomentar la colaboración efectiva entre los distintos miembros del equipo multidisciplinario involucrado en el desarrollo de la solución de Mushroom.  

* **Reuniones de trabajo - Discord**

  Para la coordinación general del equipo de desarrollo, incluyendo tanto al equipo de front-end, back-end como al resto de las áreas técnicas y organizativas, utilizamos Discord como nuestra plataforma principal de comunicación. Discord es una herramienta de comunicación en tiempo real diseñada originalmente para comunidades de videojuegos, pero que ha sido ampliamente adoptada por equipos de trabajo técnico debido a su versatilidad, baja latencia en llamadas, interfaz intuitiva y capacidades de organización mediante canales temáticos y roles personalizados. Estas características la convierten en una solución idónea para Mushroom, desarrollado por el equipo de TeemoSolutions, al facilitar una comunicación fluida, continua y sin restricciones de tiempo para reuniones técnicas, sesiones de planificación, revisiones de código, discusiones de diseño, resolución de incidencias y coordinación general del proyecto.

  En Discord, se establecieron distintos canales organizados por bounded contexts y áreas funcionales del proyecto (front-end, back-end, base de datos, diseño, testing, etc.), lo cual permitió segmentar las conversaciones y asignar tareas de forma clara y estructurada. Además, se habilitaron canales de texto y voz para distintos tipos de reuniones (diarias, retrospectivas, planificación, diseño), optimizando la colaboración sincrónica y asincrónica del equipo. Se definieron también roles específicos dentro del servidor (como Product Owner, coordinador de diseño, responsable de base de datos), lo cual facilitó la asignación de responsabilidades y el flujo de trabajo colaborativo. Gracias a esta infraestructura comunicacional, se logró mantener una gestión eficiente del proyecto y un seguimiento preciso de las actividades durante todo el ciclo de vida del desarrollo de Mushroom.

  * Página oficial de Discord: https://discord.com/ 

* **Comunicación sincrónica y asincrónica - WhatsApp**

  Para la gestión de la comunicación sincrónica y asincrónica de todo el equipo de Mushroom se emplea WhatsApp como plataforma principal de mensajería instantánea. WhatsApp, con su amplia adopción y soporte multiplataforma (Android, iOS y escritorio), ofrece un canal confiable para el intercambio de mensajes de texto, notas de voz, llamadas de voz y videollamadas, garantizando comunicación continua y cifrada de extremo a extremo entre los miembros del proyecto. Esta elección se fundamenta en la familiaridad del grupo con la interfaz de usuario, la disponibilidad constante en dispositivos móviles y la posibilidad de compartir rápidamente archivos multimedia y documentos, lo que agiliza la resolución de consultas técnicas y la coordinación de actividades diarias.

  En esta plataforma, se ha configurado un chat grupal donde participan todos los integrantes del equipo, lo que facilita la difusión de información global, la asignación de tareas y el seguimiento de hitos o incidentes en tiempo real. Paralelamente, cada colaborador cuenta con la capacidad de establecer comunicación directa con el líder del equipo o con compañeros asignados a tareas específicas, posibilitando interacciones más enfocadas y oportunas para resolver dudas puntuales o recibir retroalimentación inmediata. Gracias a la versatilidad de WhatsApp, se logran establecer flujos de comunicación efectivos tanto para discusiones de alto nivel (mediante videoconferencias grupales) como para consultas rápidas (a través de mensajes o audios), fortaleciendo la cohesión del equipo y asegurando una coordinación eficiente del proyecto Mushroom.

  * Página oficial de WhatsApp: https://www.whatsapp.com/?lang=es_LA

* **Sesiones de Brainstorming y colaboración en tiempo real - Excalidraw**

  Para la facilitación de la ideación visual y la colaboración en tiempo real entre todos los miembros del equipo de Mushroom, se emplea Excalidraw como plataforma principal de pizarra digital colaborativa. Excalidraw es una herramienta de código abierto y uso gratuito que proporciona un lienzo virtual ilimitado, permitiendo a los participantes esbozar diagramas, flujos de trabajo y prototipos de manera libre y espontánea. Su interfaz minimalista y basada en vectores ofrece herramientas esenciales (líneas, formas, texto y colores básicos) para representar conceptos técnicos, arquitecturas de sistema, procesos de interacción y esquemas de integración de componentes sin necesidad de conocimientos avanzados en software de diseño. Además, Excalidraw garantiza un entorno orientado a la privacidad y seguridad, ya que no requiere registros complejos ni almacena información sensible de manera persistente.

  Dentro del proyecto de Mushroom, Excalidraw se empleó para sesiones de brainstorming y talleres de diseño, en los cuales se definieron tanto la arquitectura general del sistema (front-end, back-end, bases de datos y lógica de la aplicación móvil) como los flujos de usuarios y la interacción entre los distintos bounded contexts de forma rápida, sencilla y directa. De igual modo, se utilizaron sus capacidades de colaboración en tiempo real para la elaboración de diagramas Kanban simplificados, facilitando la asignación y visualización de tareas durante los sprints. Esta metodología visual permitió al equipo desglosar de manera clara y ordenada las actividades asociadas a cada componente, optimizando la comunicación interfuncional y acelerando la toma de decisiones en torno a la estructuración del proyecto.

  * Página oficial de Excalidraw: https://excalidraw.com/

* **Desarrollo de documentos de participación - Google Docs**

  Google Docs es un procesador de texto basado en la nube que habilita la creación, edición y almacenamiento de documentos en tiempo real, utilizando Google Drive como repositorio central. La plataforma ofrece un conjunto completo de funcionalidades dirigidas a entornos colaborativos y administrativos: edición simultánea con actualización en tiempo real, control de versiones automático con historial, comentarios y sugerencias, herramientas avanzadas de formato de texto y párrafo (estilos, plantillas, numeración y listas), inserción de objetos multimedia (imágenes, tablas, gráficos vinculados) y enlaces externos, además de correctores ortográfico y gramatical, y soporte para trabajo sin conexión mediante sincronización automática. Su arquitectura en la nube garantiza alta disponibilidad, escalabilidad en el almacenamiento y compatibilidad multiplataforma, lo que facilita tanto la accesibilidad remota como la integración con otros servicios de Google.

  En el contexto del proyecto de Mushroom, Google Docs se ha empleado como herramienta principal para la gestión y seguimiento de responsabilidades del equipo, permitiendo asignar y documentar tareas específicas, definir criterios de evaluación basados en la puntualidad de las entregas, la colaboración continua y la calidad de los entregables. Además, Google Docs ha servido como espacio para la redacción rápida de ideas textuales, la elaboración de reportes de incidencias (bugs, fallos de diseño o inconsistencias en el flujo de la aplicación) y la propuesta de cambios significativos en el alcance o la arquitectura, beneficiándose del control de cambios y del historial de versiones para mantener trazabilidad de las modificaciones. Gracias a estas capacidades, el equipo de Mushroom ha optimizado la comunicación documental y ha establecido un registro transparente de la evolución de cada actividad hasta la finalización del proyecto.

  * Página oficial de Google Docs: https://docs.google.com/document/u/0/

* **Presentaciones de alto impacto a stakeholders - Canva**

  Canva es una plataforma de diseño gráfico basada en la nube que facilita la creación de presentaciones de alto impacto orientadas a audiencias técnicas y no técnicas. Su entorno de trabajo proporciona una amplia variedad de plantillas profesionales, elementos visuales (gráficos, diagramas, iconografía) y herramientas de edición colaborativa, permitiendo al equipo de Mushroom construir diapositivas coherentes con la identidad visual del proyecto y adaptadas a distintos públicos, como inversionistas, aliados estratégicos y usuarios finales. Además, su capacidad para exportar presentaciones en formatos livianos (PDF, PPTX, vídeo) garantiza una distribución rápida y confiable de los contenidos, optimizando tanto la transferencia de archivos como la visualización en dispositivos con limitaciones de ancho de banda.

  En el marco de las entregas parciales y auditorías internas, utilizamos Canva no solo para el diseño de las exposiciones, sino también para grabar vídeos narrados directamente dentro de la plataforma, diapositiva por diapositiva. Esta funcionalidad permite generar presentaciones en formato multimedia que combinan voz, vídeo, animaciones de entrada y salida de elementos gráficos, así como transiciones personalizadas, de manera que la revisión periódica del avance se realiza con rapidez y calidad profesional. Los vídeos generados facilitan la auditoría técnica y la retroalimentación de los stakeholders, ya que integran el contexto visual de la interfaz de usuario, diagramas de arquitectura y métricas de desarrollo en un único recurso descargable junto al documento final de la presentación.

  * Página oficial de Canva: https://www.canva.com/

* **Gestión del desarrollo del proyecto, de Product Backlog y Sprint Backlogs - Jira Software**

  Jira Software es una plataforma de gestión de proyectos orientada a equipos de desarrollo ágil, que facilita la planificación, seguimiento y control de todas las actividades relacionadas con el ciclo de vida del software. Basada en la metodología Scrum, Jira permite configurar Product Backlogs y Sprint Backlogs de forma granular, definiendo historias de usuario, tareas técnicas y criterios de aceptación para cada funcionalidad o componente del sistema. Gracias a su flexibilidad, es posible parametrizar flujos de trabajo personalizados (workflows) que reflejen el proceso interno de revisión, aprobación y entrega de cada ítem. Además, Jira ofrece mecanismos de gestión de versiones, seguimiento de incidencias y generación de informes de progreso, lo cual garantiza una transparencia total sobre el estado de avance del proyecto y la identificación temprana de desviaciones con respecto a los plazos establecidos.

  Dentro de Mushroom, hemos configurado tableros Scrum que contienen los Product Backlogs y Sprint Backlogs correspondientes a cada iteración planificada. Cada miembro del equipo recibe asignaciones específicas con fechas límite claras para asegurar el cumplimiento de los objetivos de cada sprint, abarcando tareas de desarrollo de frontend, backend, base de datos y aplicación móvil. Los epics, historias de usuario y tareas técnicas se vinculan entre sí para visualizar dependencias y priorizar entregables críticos en cada ciclo de trabajo. A lo largo del sprint, se realizan reuniones diarias (daily stand-ups) y revisiones de sprint (sprint reviews) dentro de Jira, empleando tableros y filtros personalizados para validar el cumplimiento de los criterios de aceptación y detectar bloqueos.

  * Página oficial de Jira: https://www.atlassian.com/software/jira

**Requirement Management**

Esta sección se centra en la gestión integral de requisitos mediante el uso de plataformas para las actividades de Needfinding, elaboración y refinamiento de User Personas, análisis sistemático de entrevistas y mapeo de procesos As-Is y To-Be. Estas plataformas facilitan la construcción de arquetipos de usuario y la visualización de sus necesidades y expectativas a través de plantillas interactivas y reportes dinámicos, además de ofrecer un entorno colaborativo de pizarra digital para capturar insights de entrevistas, estructurar flujos de procesos actuales y diseñar estados futuros óptimos, permitiendo la trazabilidad bidireccional de cada requisito desde su identificación hasta su validación, así como la generación de artefactos compartidos que soportan la toma de decisiones basada en datos cualitativos y cuantitativos a lo largo del ciclo de vida del proyecto.

* **Desarrollo de diagramas de Needfinding con el enfoque UX (User Experience) - UXPressia**

  UXPressia es una plataforma especializada en la creación y gestión de artefactos de experiencia de usuario, orientada a la definición profunda de User Personas, Empathy Maps, Journey Maps e Impact Maps. Esta herramienta basada en la nube permite diseñar perfiles de usuarios detallados, describiendo atributos demográficos, comportamentales y motivacionales, lo cual resulta esencial para alinear los requisitos del producto con las necesidades reales de los usuarios finales. Además, UXPressia proporciona plantillas estandarizadas y capacidades de colaboración en tiempo real, garantizando que todo el equipo de Mushroom pueda contribuir simultáneamente a la codificación de insights de usuario, la identificación de pain points y la definición de oportunidades de mejora en cada etapa del ciclo de interacción.

  En el contexto de Mushroom, UXPressia se emplea para construir User Personas basados en investigaciones de mercado y datos de usuario, definiendo segmentos clave con objetivos y comportamientos específicos. A partir de estos perfiles, se generan Empathy Maps que detallan las emociones, pensamientos, acciones y frustraciones de cada segmento, permitiendo priorizar funcionalidades y diseñar flujos de interacción más empáticos. Asimismo, con Journey Maps, se mapean los puntos críticos del recorrido del usuario, desde la adquisición de una planta hasta el monitoreo constante con Mushroom, identificando momentos de valor y posibles fricciones en la experiencia. Finalmente, los Impact Maps facilitan la vinculación entre objetivos de negocio y actividades concretas de diseño e implementación, asegurando que todas las decisiones de desarrollo estén justificadas en métricas de impacto. Gracias a la trazabilidad y la interoperabilidad de UXPressia, el equipo multidisciplinario de TeemoSolutions logra un alineamiento exhaustivo entre investigación UX, diseño de producto y desarrollo técnico, cimentando una experiencia de usuario sólida y validada.

    * Página oficial de UXPressia: https://uxpressia.com/

* **EventStorming, Flows, Canvases y Mapeo As-Is y To-Be - Miro**

    Miro se configura como una plataforma colaborativa basada en un lienzo digital flexible que facilita la visualización y modelado de procesos complejos, integrando funcionalidades avanzadas para la creación de As-Is y To-Be Scenario Maps, así como para la realización de sesiones de EventStorming. Su infraestructura permite trabajar simultáneamente en un espacio infinito, soportando elementos gráficos como sticky notes, diagramas de flujo, plantillas personalizadas y conexiones semánticas entre objetos. Gracias a su compatibilidad con metodologías ágiles y técnicas de modelado de dominios, Miro resulta idóneo para la representación de artefactos de arquitecturas basadas en Bounded Contexts, ya que posibilita la creación de tableros especializados donde se delimita visualmente cada contexto, se establecen fronteras claras de responsabilidad y se documentan relaciones entre servicios, eventos y actores del sistema.

    En el marco del desarrollo de Mushroom, Miro se emplea para elaborar detallados As-Is Scenario Maps, que describen los flujos actuales de interacción del usuario y del dispositivo, así como To-Be Scenario Maps que muestran la evolución prevista tras la implementación de nuevas funcionalidades. Asimismo, se usó durante el desarrollo del EventStorming. En las sesiones de EventStorming, los participantes generan un mapa de eventos de dominio, identificando comandos, aggregates y resultados relevantes para los distintos módulos identificados. A continuación, estos eventos se agrupan en Bounded Contexts, diferenciando claramente los ámbitos de frontend, backend, base de datos y sistemas embebidos. Con los Flows y Canvases resultantes, se definen diagramas de secuencia y estructuras lógicas que guían la implementación técnica. Además, se realizan sesiones de brainstorming centradas exclusivamente en la profundización de cada Bounded Context, permitiendo asignar responsabilidades específicas y optimizar la cohesión interna.

    * Página oficial de Miro: https://miro.com/es/

**Product UX/UI Design**

Esta sección se orienta al diseño UX/UI mediante el aprovechamiento de herramientas especializadas para la definición de Style Guidelines, la creación de wireframes, mockups, wireflows, user flows y prototipos interactivos. En este sentido, usamos plataformas que actuan como eje central para la composición de sistemas de diseño escalables, gestión de bibliotecas de componentes, especificación de tokens de estilo y colaboración en tiempo real entre diseñadores y desarrolladores. También estructuramos diagramas de wireflows y userflows detallados que documentan la navegación y jerarquía de información, garantizando la coherencia entre la estructura de contenido y la experiencia interactiva, así como la iteración continua de prototipos navegables que permiten pruebas de usabilidad y refinamiento basado en métricas cualitativas y cuantitativas durante todo el ciclo de desarrollo.

* **UX/UI Design y Prototyping - Figma**

    Figma se emplea como la plataforma principal para el diseño visual y la elaboración de prototipos interactivos en Mushroom, abarcando desde la creación de wireframes iniciales hasta mock-ups de alta fidelidad y prototipos navegables. Gracias a su entorno colaborativo en tiempo real, los diseñadores pueden esbozar rápidamente la estructura básica de la interfaz, definiendo la colocación de componentes, jerarquías de contenido y flujos de navegación, y, de manera simultánea, recibir retroalimentación de desarrolladores frontend, backend y diseñadores. Figma soporta la parametrización de componentes reutilizables, lo que permite establecer sistemas de diseño consistentes, fáciles de mantener y escalables a lo largo de todo el proyecto. Asimismo, sus herramientas de prototipado incorporadas facilitan la simulación de interacciones, transiciones y estados dinámicos sin necesidad de codificación, posibilitando ensayos de usabilidad temprana y validación con usuarios reales antes de la implementación.

    Además, Figma se utiliza para definir y documentar las Style Guidelines o pautas de estilo de Mushroom, garantizando la coherencia visual y la uniformidad de la marca. Dentro de estas guías se especifican tipografías, paletas de colores, reglas de espaciado, estilos de íconos y comportamientos de interacción (por ejemplo, estados de hover, focus y active), de modo que todos los componentes gráficos se alineen con los estándares de accesibilidad y usabilidad. Las librerías de estilos compartidas facilitan la adopción de estas pautas por parte de los desarrolladores frontend y móvil, asegurando que los elementos de interfaz se implementen según las especificaciones establecidas. De esta manera, Figma no solo actúa como una herramienta de diseño, sino también como un repositorio central de la identidad visual de Mushroom, promoviendo la colaboración multidisciplinaria y acelerando el ciclo de diseño-implementación.

  *  Página oficial de Figma: https://figma.com/

* **Wireflows y User flows - LucidChart**

    Lucidchart se emplea como herramienta principal para la creación de Wireflows y User Flows en el proyecto Mushroom, aprovechando su capacidad para generar diagramas de flujo de alta calidad y su compatibilidad con múltiples tipos de modelado (UML, C4, BPMN, entre otros). A través de Lucidchart, el equipo de diseño y desarrollo puede esbozar de manera estructurada cómo interactúan los usuarios con la interfaz en cada paso del proceso, incorporando componentes visuales de alta fidelidad que permiten visualizar transiciones, estados de pantalla y puntos de decisión dentro de los flujos de interacción. Las plantillas prediseñadas y la biblioteca de formas personalizables facilitan la representación de íconos, botones, campos de entrada y elementos de navegación, garantizando que los Wireflows reflejen con precisión la estructura de las pantallas y que los User Flows documenten de forma detallada las rutas críticas de uso, desde la autenticación hasta las acciones de configuración.

    Además, Lucidchart ofrece funcionalidades de colaboración en tiempo real, lo que permite que varios miembros del equipo, diseñadores de UX, desarrolladores de frontend y backend, editen simultáneamente los diagramas, agreguen comentarios y realicen actualizaciones instantáneas sin necesidad de consolidar archivos estáticos. Gracias a las opciones de exportación en formatos SVG, PNG y PDF, así como a la capacidad de insertar enlaces interactivos dentro de los diagramas, Lucidchart se convierte en un repositorio completo de referencia para validar la usabilidad, optimizar rutas de navegación y asegurar que las implementaciones técnicas correspondan fielmente a los diseños planeados.

  * Página oficial de Lucidchart: https://lucidchart.com

**Product Architecture Design**

Esta sección se dedica al diseño de la arquitectura de producto a través de la elaboración de artefactos formales que describen la estructura, los componentes y las interacciones de la solución. Se generarán diagramas C4 para representar los niveles de contexto, contenedores, componentes y código, diagramas de clases UML para modelar entidades, atributos y relaciones, y diagramas entidad-relación para definir esquemas de base de datos lógicos y físicos. Adicionalmente, se incluirán diagramas de despliegue para describir la infraestructura de TI, y mapeos de APIs y dependencias de servicios que documentan puntos de integración. Estos artefactos, versionados y trazables, garantizan la coherencia conceptual y técnica, facilitan la comunicación entre equipos multidisciplinarios y soportan la escalabilidad, mantenibilidad y rendimiento óptimo del producto a lo largo de todo su ciclo de vida.

* **Diagramas UML - LucidChart**

  Lucidchart se emplea para la generación de diagramas de clases UML que representan la estructura y relaciones de las entidades dentro de cada Bounded Context de Mushroom. Gracias a su soporte nativo para el modelado UML, la herramienta permite definir clases con atributos, métodos y visibilidades, así como establecer relaciones de herencia, asociación, agregación y composición. Cada diagrama de clases refleja los conceptos clave del dominio y muestra cómo interactúan entre sí dentro de un contexto delimitado. La interfaz de arrastrar y soltar de Lucidchart facilita la creación y modificación de estas estructuras, mientras que las bibliotecas de formas UML garantizan el uso de notaciones estándar.

  Dentro de TeemoSolutions, se crearon diagramas de clases específicos para cada Bounded Context identificado mediante sesiones de EventStorming y mapeo en Miro. Estos diagramas, disponibles en Lucidchart, se mantienen versionados y accesibles para todo el equipo, facilitando la coherencia entre la arquitectura lógica y la capa de código en cada módulo del sistema.


  * Página oficial de Lucidchart: https://lucidchart.com

* **Diagramas C4 - Structurizr DSL**

  Structurizr DSL es un lenguaje específico de dominio basado en texto que facilita la creación y el versionado de diagramas C4 (Contexto, Contenedores y Componentes) de manera reproducible y colaborativa. A través de su sintaxis declarativa, permite definir elementos del sistema, como personas, sistemas externos y límites de contexto, en diagramas de Contexto; detallar las containers que componen la arquitectura en diagramas de Contenedores, y desglosar cada contenedor en sus componentes internos en diagramas de Componentes. Structurizr DSL incorpora convenciones para nombrar, etiquetar y ensamblar relaciones, así como la capacidad de generar vistas específicas basadas en filtros de etiquetas, lo que optimiza la trazabilidad de cambios y la comunicación de la arquitectura entre todos los miembros del equipo.

  EEn el contexto de Mushroom, Structurizr DSL se utilizó para documentar exhaustivamente la arquitectura modular del sistema siguiendo el modelo C4. Primero, se definió un diagrama de Contexto que situó a los usuarios frente a Mushroom, dejando claro qué sistemas externos interactúan con la solución. A continuación, en el diagrama de Contenedores, se representaron contenedores clave de toda la plataforma. Cada contenedor se etiquetó según su responsabilidad funcional y se describieron sus protocolos de comunicación. Finalmente, se generaron diagramas de Componentes para cada contenedor no trivial, especificando componentes de alto impacto y relevancia. Gracias a Structurizr DSL, estos diagramas se mantienen sincronizados con el repositorio de código, permitiendo actualizar la arquitectura textualmente y regenerar las vistas, lo que garantiza una documentación arquitectónica coherente y actualizada en todo momento.

    * Página oficial de Structurizr DSL: https://structurizr.com/dsl

* **Diagramas de base de datos - Vertabelo**

    Vertabelo es una herramienta de modelado de datos relacional basada en la nube que permite diseñar, visualizar y versionar esquemas de bases de datos de manera colaborativa y rigurosa. Emplea una interfaz gráfica intuitiva para la creación de entidades, atributos, relaciones (incluyendo claves primarias y foráneas), índices y restricciones, soportando diversos motores de bases de datos (PostgreSQL, MySQL, SQL Server, entre otros). Vertabelo facilita la generación automática de scripts DDL (Data Definition Language) exportables, que aseguran la coherencia entre el modelo lógico y la implementación física. Además, su sistema de versionado integrado permite mantener un historial de cambios detallado, realizar comparaciones entre distintas versiones del modelo y colaborar en tiempo real con diversos miembros del equipo, garantizando trazabilidad y control de modificaciones en el diseño de la base de datos.

    En el proyecto Mushroom, Vertabelo se utilizó para modelar de forma estructurada las distintas áreas de datos correspondientes a los Bounded Contexts identificados previamente. El equipo pudo generar el script DDL correspondiente, garantizar que los modelos respondieran a los requerimientos de escalabilidad y consultar la documentación. Asimismo, el versionado de los modelos permitió comparar iteraciones, revertir cambios en caso de inconsistencias y coordinar revisiones entre desarrolladores backend y especialistas en base de datos, asegurando que la implementación de la capa de almacenamiento de Mushroom estuviera alineada con la visión arquitectónica y los criterios de rendimiento definidos.

  *   Página oficial de Vertabelo: https://vertabelo.com/

**Software Development**

Esta sección contempla la definición estratégica del stack tecnológico y la configuración de los entornos de desarrollo requeridos para la implementación integral de cada uno de los componentes que conforman la solución digital, los cuales incluyen la Landing Page, la aplicación móvil (Mobile App), la aplicación web (Web App), los servicios web (Web Services) y los mecanismos de pruebas (Testing). Se establecerán los lineamientos técnicos y operativos que orientarán la selección de frameworks, arquitecturas y metodologías de codificación, con el objetivo de asegurar la coherencia tecnológica, la eficiencia en el desarrollo, la escalabilidad de las soluciones y su alineamiento con los principios de mantenibilidad, seguridad y rendimiento. Asimismo, se garantizará la integración fluida entre los distintos entornos de desarrollo y pruebas, permitiendo una colaboración efectiva entre equipos multidisciplinarios, una gestión eficiente del ciclo de vida del software y una trazabilidad completa desde la codificación inicial hasta el despliegue en producción.

* **Lenguajes de etiqueta y estilo - HTML5 & CSS3**

  HTML5 y CSS constituyen las tecnologías fundamentales para la construcción de la Landing Page de Mushroom y para la implementación de los aspectos estáticos de las plantillas en la aplicación web. Con HTML5, se define una estructura semántica robusta que facilita tanto la accesibilidad como el SEO. Se emplean etiquetas específicas para organizar el contenido de la Landing Page, asegurando claridad en la jerarquía de información y compatibilidad con estándares modernos de navegadores.

  Por su parte, CSS se encarga de la presentación visual y del comportamiento responsivo tanto de la Landing Page como de las plantillas estáticas de la aplicación web. Se aplican sistemas de diseño basados en CSS Grid para garantizar adaptabilidad en múltiples tamaños de pantalla, desde dispositivos móviles hasta pantallas de escritorio. Asimismo, se definen variables CSS para mantener coherencia en la paleta de colores y estilos tipográficos acordes con las Style Guidelines acordadas en Figma, permitiendo cambios globales de forma centralizada. Gracias a esta combinación de HTML5 y CSS, la Landing Page y las plantillas de Mushroom presentan un rendimiento óptimo, una experiencia de usuario uniforme y una base sólida para futuras iteraciones de diseño.

  * Página de guía de HTML5 de W3C (World Wide Web Consortium): https://dev.w3.org/html5/spec-LC/
  * Página de guía de HTML5 de W3Schools: https://www.w3schools.com/html/
  * Página de guía de CSS3 de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/CSS
  * Página de guía de CSS3 de W3Schools: https://www.w3schools.com/css/default.asp

* **Herramientas para la programación del Web Application (Front-End) - JavaScript & TypeScript, con Angular Framework**

  JavaScript es un lenguaje de programación interpretado, dinámico y orientado a prototipos, que se ejecuta directamente en el navegador y posibilita la creación de interfaces interactivas y reactivas. Gracias a su capacidad de manipular el Document Object Model (DOM) en tiempo real, JavaScript permite actualizar el contenido de páginas web sin necesidad de recargas completas, gestionar eventos de usuario (clics, desplazamientos) y realizar peticiones asíncronas a APIs. En el contexto de Mushroom, JavaScript sirve como base para la lógica de interacción en el frontend, gestionando comportamientos dinámicos y operaciones en tiempo real que mejoran la experiencia del usuario, como validaciones de formularios, animaciones y consumo de servicios REST. 

  TypeScript es un superset tipado de JavaScript, desarrollado por Microsoft, que incorpora un sistema de tipos estáticos opcionales, clases, interfaces y módulos. Al compilarse a JavaScript estándar, TypeScript añade una capa de verificación en tiempo de compilación que detecta errores de sintaxis y de tipo antes de que el código se ejecute en el navegador, lo cual incrementa la robustez y mantenibilidad. En el desarrollo de Mushroom, TypeScript facilita la detección temprana de inconsistencias, permitiendo refactorizaciones más seguras y documentación implícita mediante anotaciones de tipo. Su integración con entornos de desarrollo modernos ofrece autocompletado y refactorización asistida, lo que acelera la productividad del equipo y minimiza errores.

  El Framework Angular es una plataforma de desarrollo front-end basada en TypeScript que sigue una arquitectura basada en componentes, inyección de dependencias y un sistema modular. Angular organiza la aplicación en módulos que agrupan componentes, directivas, servicios y pipes de manera coherente, facilitando la escalabilidad y la separación de responsabilidades. Los componentes en Angular encapsulan la lógica de presentación, el estilo y el comportamiento, promoviendo la reutilización y la cohesión. Angular también proporciona un sistema de enrutamiento integrado que permite definir rutas y parámetros. Para la interfaz de usuario, se utiliza Angular Material, una colección de componentes UI que implementa las pautas de Material Design de Google. Angular Material ofrece una amplia variedad de elementos preconstruidos, como botones, barras de navegación, tarjetas, menús desplegables, diálogos y tablas, optimizados para accesibilidad y rendimiento. Al emplear Angular con JavaScript y TypeScript, junto con Angular Material, el equipo de Mushroom puede desarrollar un front-end consistente, modular y mantenible, con componentes estandarizados que garantizan coherencia visual, comportamiento uniforme y experiencias de usuario responsivas en múltiples dispositivos.

    * Página oficial de Angular: https://angular.dev/
    * Página de documentación oficial de Angular: https://docs.angular.lat/docs
    * Página de guía de JavaScript de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/JavaScript
    * Página oficial de TypeScript: https://www.typescriptlang.org/
    * Página de guía de TypeScript de W3Schools: https://www.w3schools.com/typescript/typescript_intro.php
    * Página oficial de Material Design: https://m3.material.io/
    * Página oficial de Angular Material: https://material.angular.dev/

* **Herramientas para la programación del Web Services (Back-End) - RESTful API con Java y con Spring Boot**

  Java es un lenguaje de programación multiparadigma, maduro y orientado a objetos, que se ejecuta sobre la Máquina Virtual de Java (JVM) y combina características de tipado estático con capacidades para programación funcional. Su ecosistema y herramientas (JDK, compiladores, gestores de dependencias como Maven/Gradle) permiten generar binarios portables y optimizados para entornos de producción. En el contexto de Mushroom, Java se utiliza para implementar la lógica de negocio del backend con precisión y robustez, aprovechando su sistema de tipos para definir modelos de datos estrictos y facilitar la detección temprana de errores en tiempo de compilación. Además, el ecosistema Java incluye un amplio conjunto de bibliotecas y proyectos probados (por ejemplo, Jackson para serialización JSON, bibliotecas de persistencia como JPA/Hibernate y utilidades para manejo de excepciones), lo que facilita la reutilización de componentes maduros para acceso a datos, serialización y conexión a servicios externos.

  Spring Boot (parte del ecosistema Spring) es un framework para desarrollar aplicaciones Java de manera productiva, modular y listo para producción, diseñado para construir servicios y aplicaciones modernas. Su enfoque “con convención sobre configuración” y su arquitectura basada en componentes permite configurar canales de procesamiento HTTP y gestionar de forma sencilla el ciclo de vida de la aplicación. En Mushroom, Spring Boot se emplea para hospedar el servidor de API RESTful, gestionando tareas como enrutamiento de endpoints (controladores REST), autenticación y autorización (con Spring Security y soporte para JWT), interacción con la base de datos (mediante Spring Data JPA / Hibernate), y registro estructurado de eventos (con herramientas de logging y trazabilidad).

  El Diseño de Arquitectura RESTful API se basa en principios de uniformidad, recursos identificables y operaciones basadas en verbos HTTP (GET, POST, PUT, DELETE). Este enfoque promueve una separación clara entre cliente y servidor, fomentando la reutilización y la escalabilidad del sistema. En el caso de Mushroom, la API RESTful define múltiples recursos que exponen operaciones CRUD y acciones específicas. Cada endpoint retorna respuestas en formato JSON (normalmente gestionado por Jackson), incluyendo códigos HTTP adecuados y encabezados para control de caché o paginación. Al adoptar RESTful API con Spring Boot y Java, se logra un backend que puede atender solicitudes simultáneas provenientes de la aplicación web, la aplicación móvil y el dispositivo embebido, garantizando coherencia en la representación de datos, facilidad para versionar la API y compatibilidad con estándares de seguridad como JWT (JSON Web Tokens) en la capa de autenticación.

    * Página oficial de Java (Oracle): https://www.oracle.com/java/
    * Guía y tutoriales de Java (Oracle): https://docs.oracle.com/javase/tutorial/
    * Página oficial de Spring Boot: https://spring.io/projects/spring-boot
    * Guía rápida de crear un servicio REST con Spring: https://spring.io/guides/gs/rest-service
    * Página de guía de RESTful API (principios generales): https://restfulapi.net/
    * Documentación de Spring sobre REST y Web MVC / WebFlux: https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#rest

* **Herramientas para la programación del Mobile Application - Dart con Flutter Framework**

  Dart es un lenguaje de programación de propósito general, desarrollado por Google, que está optimizado para crear aplicaciones de alto rendimiento en cliente. Con sintaxis moderna, tipado estático opcional y recolección de basura, Dart permite desarrollar código eficiente tanto para compilación anticipada (AOT) como para compilación just-in-time (JIT). Estas características hacen de Dart una opción idónea para aplicaciones móviles, donde la rapidez en el arranque y la fluidez en la interacción son cruciales. Además, su compatibilidad con la arquitectura de Flutter facilita la construcción de interfaces reactivas y la gestión de estado, utilizando un modelo de widgets declarativo que simplifica la creación de componentes reutilizables.

  El framework Flutter, también creado por Google, se apoya en Dart para proporcionar un kit de herramientas UI (UI toolkit) que compila de manera nativa tanto en iOS como en Android, asegurando un rendimiento cercano al código nativo. Flutter incluye un motor de renderizado propio, lo que permite dibujar cada elemento de la interfaz, animaciones y transiciones, con control total sobre los píxeles, sin depender de componentes nativos específicos de cada plataforma. Esto resulta en una experiencia visual y de interacción consistente en dispositivos diversos. En el contexto de Mushroom, Flutter y Dart se utilizan para desarrollar la aplicación móvil multiplataforma que complementa la funcionalidad del dispositivo IoT y la plataforma web. El equipo ha estructurado la aplicación en módulos claros, separando la capa de presentación, la capa de lógica de negocio y la capa de datos.


    * Página oficial de Flutter: https://flutter.dev/
    * Página de guía de Flutter: https://docs.flutter.dev/
    * Página oficial de Dart: https://dart.dev/
    * Página de guía de Dart: https://dart.dev/docs
    * Página de guía y seguimiento para el modelo del Material Design: https://m3.material.io/

* **Entornos de Desarrollo Integrado - Webstorm, Rider, Android Studio, PyCharm, Wokwi y Visual Studio Code**

  Las Entornos de Desarrollo Integrados (IDEs) constituyen herramientas fundamentales para optimizar la productividad y la calidad del código en cada área del proyecto Mushroom. En función del lenguaje y la tecnología utilizada, se han seleccionado entornos especializados que ofrecen características avanzadas de análisis estático, depuración, refactorización y soporte de frameworks específicos:

  * **Android Studio** se utiliza para el desarrollo de la aplicación móvil en Dart con Flutter, gracias a su integración nativa con SDKs de Android y emuladores. Android Studio incluye un editor Visual UI para diseñar interfaces de Flutter, un depurador con visualización de la jerarquía de widgets y herramientas de perfilado que miden el rendimiento en tiempo real (CPU, memoria, GPU). Su sistema de gestión de paquetes y el acceso directo al Flutter Inspector permiten inspeccionar y modificar la estructura de la UI sobre la marcha, ajustando propiedades de widgets, temas y estilos con retroalimentación instantánea.

  * **PyCharm** se ha adoptado como el IDE de referencia para el desarrollo en Python, principalmente en el desarrollo de la aplicación edge. PyCharm ofrece inspección de código basada en PEP8, autocompletado inteligente, análisis de dependencias y detección temprana de errores. Su integración con entornos virtuales (venv, Conda) facilita la gestión de librerías, y el depurador permite establecer puntos de interrupción tanto en código local como remoto (SSH), junto con la visualización de variables en tiempo real.

  * **Visual Studio Code (VS Code)** se configura como alternativa para aquellos miembros del equipo que no dispongan de acceso a WebStorm o Rider, o para el desarrollo en C++ de la aplicación embebida. VS Code soporta extensiones específicas, como C# for Visual Studio Code, C/C++ (Microsoft), Dart & Flutter, Angular Language Service y Prettier, que dotan al editor de capacidades de autocompletado, linting, depuración y tareas de construcción. Su arquitectura ligera y multiplataforma permite a los desarrolladores trabajar en entornos diversos con una configuración unificada.

  * **WebStorm** se emplea como el IDE principal para el desarrollo de JavaScript, TypeScript y el framework Angular. WebStorm ofrece inspecciones inteligentes de código, autocompletado contextual, navegación rápida entre símbolos y soporte nativo para Angular CLI, lo que permite generar componentes y servicios. Asimismo, facilita la configuración de tareas de compilación mediante archivos de configuración integrados. Su depurador integrado permite establecer puntos de interrupción en tiempo real, evaluando expresiones de JavaScript/TypeScript y trazando el flujo de ejecución del frontend, lo que resulta esencial para detectar problemas de rendimiento.

  Con esta selección de IDEs, el equipo de Mushroom garantiza que cada desarrollador disponga de un entorno adaptado a las necesidades de su área de trabajo, promoviendo un flujo de desarrollo ágil, coherente y alineado con las mejores prácticas de cada tecnología empleada.

    * Página oficial de Android Studio: https://developer.android.com/studio?hl=es-419
    * Página oficial de PyCharm: https://www.jetbrains.com/es-es/pycharm/#
    * Página oficial de Visual Studio Code: https://code.visualstudio.com/
    * Página oficial de Webstorm: https://www.jetbrains.com/es-es/webstorm/

Software Testing

Esta sección aborda la estrategia integral de aseguramiento de la calidad del software a través de la planificación, ejecución y seguimiento de actividades de verificación y validación orientadas a garantizar la funcionalidad, confiabilidad, usabilidad, seguridad y rendimiento de cada componente del sistema. Se establecerá un enfoque estructurado que incluirá pruebas a nivel unitario, de integración, de sistema y de aceptación. Asimismo, se definirá un conjunto de métricas clave, criterios de cobertura y protocolos de gestión de incidencias que permitan medir de manera objetiva el grado de cumplimiento de los requisitos funcionales y no funcionales. La planificación de pruebas estará alineada con el ciclo de vida del desarrollo, integrándose de forma continua en los flujos de trabajo para facilitar la detección temprana de errores, la reducción del retrabajo y la mejora sostenida del producto.

Behavior-Driven Development - Cucumber

Cucumber es una herramienta de Behavior-Driven Development (BDD) que permite la definición de criterios de aceptación en formato legible tanto para desarrolladores como para stakeholders, utilizando la sintaxis natural de Gherkin. Cada archivo de características (.feature) contiene escenarios estructurados en pasos que describen comportamientos esperados (“Given–When–Then”), facilitando la comunicación entre el equipo técnico y el equipo de producto.


Para la edición y ejecución de pruebas con Cucumber, empleamos Visual Studio Code junto con extensiones específicas. Estas extensiones habilitan resaltado de sintaxis, completado automático de palabras clave Gherkin, generación de definiciones de pasos, ejecución de escenarios directamente desde el editor y depuración de tests paso a paso. Con esta extensión garantizamos que las pruebas de aceptación sean siempre ejecutables, repetibles y estén enlazadas a los requisitos del negocio, permitiendo validar funcionalidades completas desde el nivel de API hasta la capa de presentación de forma integrada.


Página oficial de Cucumber: https://cucumber.io/
Página de guía de Cucumber: https://cucumber.io/docs/cucumber/

Unit-Testing con C# - XUnit.net

xUnit.net es un framework de pruebas unitarias para C# que sigue las mejores prácticas de diseño de tests y está estrechamente integrado con el ecosistema de .NET Core. xUnit utiliza convenciones de nomenclatura que detectan métodos de prueba mediante atributos como [Fact] y [Theory], lo que simplifica la escritura de tests individuales y de pruebas parametrizadas. En la implementación de Mushroom, xUnit se emplea para desarrollar pruebas exhaustivas de la lógica de negocio en el backend, cubriendo servicios, controladores y repositorios del API RESTful.


Gracias a la integración con herramientas de inyección de dependencias, es posible aislar componentes mediante mocks o stubs, lo que facilita la verificación de comportamientos en escenarios unitarios sin recurrir a bases de datos reales. Cada proyecto de prueba xUnit se configura con un archivo de proyecto .csproj que define referencias a los proyectos de producción, bibliotecas de aislamiento y adaptadores de test. Con el uso de XUnit, garantizamos la calidad y la confiabilidad de la solución Mushroom.


Página oficial de XUnit: https://xunit.net/
Página de guía de XUnit de Microsoft: https://learn.microsoft.com/es-es/dotnet/core/testing/unit-testing-csharp-with-xunit
Software Deployment
Esta sección se enfoca en la planificación y ejecución del proceso de despliegue de software, abarcando las herramientas y entornos necesarios para garantizar una transición controlada, segura y eficiente desde el entorno de desarrollo hacia los entornos de prueba, preproducción y producción. El enfoque adoptado permitirá minimizar riesgos asociados al lanzamiento de nuevas versiones, asegurar la reversibilidad ante fallos. Asimismo, se considerarán aspectos clave como la gestión de credenciales, la disponibilidad de infraestructura escalable, el control de acceso por entornos y la sincronización entre servicios interdependientes.

Despliegue de la Landing Page - Github Pages

GitHub Pages es un servicio de hosting estático que permite publicar sitios web y páginas de documentación directamente desde un repositorio de GitHub. Mediante la creación de una rama específica, se puede automatizar el despliegue de archivos HTML, CSS, JavaScript y activos estáticos cada vez que se realicen cambios en el repositorio. Al no requerir servidores backend ni bases de datos, ofrece una solución de hosting de bajo costo, con SSL/TLS automático y tiempos de despliegue rápidos, ideal para páginas informativas, blogs, documentación de proyectos y, en este caso, la Landing Page de Mushroom.


Para la Landing Page de Mushroom, cuya implementación se basa en HTML5, CSS y JavaScript, se ha configurado un workflow que compila y verifica el sitio estático al realizar un push en la rama principal. Una vez aprobados los cambios, el contenido se despliega automáticamente en GitHub Pages, asegurando que los usuarios externos accedan a la versión más reciente sin tiempos de inactividad. Además, se aprovechan las capacidades de GitHub Pages para personalizar el dominio, habilitar HTTPS y gestionar versiones históricas del sitio.


Página oficial de Github Pages: https://pages.github.com/

Despliegue de Aplicaciones Móviles - Firebase App Distribution

Firebase App Distribution es un servicio de Google diseñado para facilitar la entrega de aplicaciones móviles a probadores internos y externos antes de su publicación en tiendas oficiales. Funciona como una plataforma centralizada que permite subir paquetes compilados (APK para Android e IPA para iOS), gestionar versiones de prueba y distribuirlas a grupos de testers mediante invitaciones por correo electrónico o enlaces únicos. Entre sus ventajas destacan la facilidad para recopilar retroalimentación temprana, identificar errores en condiciones de uso reales y administrar diferentes canales de prueba sin necesidad de depender de procesos de publicación en Google Play Console o App Store Connect.


En el proyecto Mushroom, Firebase App Distribution se utiliza para el despliegue de la aplicación móvil desarrollada en Flutter/Dart, permitiendo que los miembros del equipo y los testers seleccionados instalen compilaciones preelaboradas en sus dispositivos físicos (tanto Android como iOS) de manera ágil y segura. Cada nueva versión del APK o IPA se carga automáticamente desde el proceso de integración continua, se etiqueta con un número de versión semántica y se comparte con los probadores a través de la consola de Firebase. Una vez enviada la invitación, los testers pueden instalar la aplicación en sus dispositivos móviles, ejecutar pruebas de funcionalidad, validar flujos críticos y proporcionar feedback directamente en la plataforma.


Página oficial de Firebase App Distribution: https://firebase.google.com/docs/app-distribution?hl=es-419
Software Documentation
Esta sección contempla la elaboración, estructuración y mantenimiento de la documentación técnica y funcional del software, con el propósito de asegurar la comprensión, trazabilidad y reutilización del conocimiento a lo largo de todo el ciclo de vida del proyecto. Se definirá un marco documental que abarque desde la especificación de requisitos, diseño arquitectónico y detalles de implementación, hasta manuales de instalación, configuración, uso, mantenimiento y pruebas, dirigidos tanto a usuarios técnicos como no técnicos. La documentación será generada de forma iterativa y colaborativa, promoviendo su alineación con los avances del desarrollo y su actualización continua frente a cambios en la solución. Asimismo, se priorizará la claridad, consistencia y estandarización del lenguaje técnico utilizado, integrando diagramas, ejemplos de uso, estructuras de datos, flujos de procesos y referencias cruzadas que faciliten su navegación y comprensión.

Control de versiones y repositorios - Github

GitHub sirve como plataforma centralizada de control de versiones para todo el ecosistema de Mushroom, gestionando el repositorio remotos. En cada repositorio se aplica el GitFlow Workflow, que organiza el trabajo en ramas estables (main/master), ramas de desarrollo (develop), ramas de características (feature), ramas de corrección de errores (hotfix) y ramas de liberación (release). Este enfoque estructurado permite coordinar el avance paralelo de múltiples funcionalidades sin comprometer la estabilidad de las versiones en producción. Adicionalmente, se emplean Conventional Commits para escribir commits uniformes y legibles, lo que facilita la generación automática de changelogs y la trazabilidad de los cambios. Para la numeración de versiones, se sigue el Semantic Versioning (SemVer), etiquetando cada liberación con un esquema Major.Minor.Patch.


Con el fin de aislar responsabilidades y optimizar la mantenibilidad, el código fuente de Mushroom se organiza en repositorios separados por aplicación y ramas separadas por Bounded Context. Esta separación garantiza que cada equipo trabaje con su respectivo conjunto de dependencias y políticas de acceso específicos, reduciendo el riesgo de conflictos entre módulos. Asimismo, se usa un repositorio separado para el desarrollo de reportes con respecto a la introducción del producto, sus procesos de definición de requisitos y requerimientos, su listado de product backlog, diagramas, estructuras, arquitecturas, y uso del código en el producto.


Página oficial de Github: https://github.com/
Página de guía de Markdown: https://www.markdownguide.org/

Documentación de Endpoints - Swagger

Swagger (OpenAPI) es un estándar para la documentación interactiva de APIs RESTful que permite describir de manera detallada los endpoints, parámetros, esquemas de datos, códigos de respuesta y modelos de autenticación de un servicio web. A través los modelos de especificación, Swagger genera una interfaz web (Swagger UI) que permite a los desarrolladores explorar cada ruta, probar peticiones en tiempo real y validar esquemas de solicitudes y respuestas sin necesidad de implementar clientes adicionales.


En Mushroom, Swagger se configura como parte del backend, de modo que con cada compilación de ASP .NET Core se actualiza la documentación de los recursos disponibles. Esto garantiza que los equipos de frontend (Angular), mobile (Flutter) e incluso el firmware embebido (C++) cuenten con una fuente confiable y siempre sincronizada de los contratos de la API. Además, Swagger permite exportar el documento OpenAPI a formatos como JSON o YAML para integrarlo en herramientas de generación de código. Gracias a esta implementación, la colaboración entre los diferentes contextos bounded de Mushroom se fortalece: cada equipo puede consultar, probar y consumir los endpoints de forma rápida y sin ambigüedades, reduciendo errores de integración y acelerando los ciclos de desarrollo.


Página oficial de Swagger: https://swagger.io/


### 7.1.2. Source Code Management

Para garantizar la trazabilidad y la coherencia en el desarrollo de todos los componentes de Mushroom, el equipo adoptará una estrategia de gestión de código fuente basada en GitHub. Este entorno centralizado no solo servirá como repositorio único para la Landing Page, los Web Services y las aplicaciones frontend, sino también como plataforma de colaboración, revisión de cambios y despliegue continuo. Cada repositorio dispondrá de su propia URL, que se detallará en esta sección, y contendrá tanto el código de producción como las pruebas unitarias y de integración/aceptación, garantizando así un ciclo de desarrollo transparente y fácilmente verificable.

Para organizar el flujo de trabajo en Git, se implementará el modelo GitFlow propuesto por Driessen (2010), definiendo ramas específicas para desarrollo (develop), producción (main), nuevas funcionalidades (feature/), preparaciones de lanzamiento (release/) y correcciones críticas (hotfix/). Las convenciones de nombrado para los lanzamientos seguirán las pautas de Semantic Versioning 2.0.0, de modo que cada versión refleje con claridad cambios importantes, características nuevas y correcciones de errores según su impacto semántico (Preston‑Werner, 2013). Asimismo, los mensajes de commit emplearán el estándar Conventional Commits, facilitando la generación automatizada de changelogs y mejorando la legibilidad del historial de cambios (Conventional Commits, 2020).

**Repositorios en GitHub:**

- Organization: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS

- Report: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-Report

- Landing Page: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-LandingPage

- Web Application: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging

- Mobile Application: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Movil

- Back-End Platform: https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging

Integrantes de la organización: En esta sección, se presentarán todos los usuarios que forman parte de la organización de GitHub del proyecto de Teemo Solutions, junto con sus nombres de usuario correspondientes. El objetivo es evitar confusiones sobre los autores de los commits en GitHub y facilitar la identificación de los colaboradores al revisar y analizar el reporte y el código desarrollado por nuestro equipo.

### 7.1.3. Source Code Style Guide & Conventions

### 7.1.4. Software Deployment Configuration

### 7.2. Solution Implementation

### 7.2.1. Sprint 1

#### 7.2.1.1. Sprint Planning 1

#### 7.2.1.2. Sprint Backlog 1

#### 7.2.1.3. Development Evidence for Sprint Review

#### 7.2.1.4. Testing Suite Evidence for Sprint Review

#### 7.2.1.5. Execution Evidence for Sprint Review

#### 7.2.1.6. Services Documentation Evidence for Sprint Review

#### 7.2.1.7. Software Deployment Evidence for Sprint Review

#### 7.2.1.8. Team Collaboration Insights during Sprint

## 7.3. Validation Interviews

### 7.3.1. Diseño de Entrevistas

### 7.3.2. Registro de Entrevistas

### 7.3.3. Evaluaciones según heurísticas

## 7.4.  Video About-the-Product
