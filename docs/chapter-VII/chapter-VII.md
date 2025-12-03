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

  Para la coordinación general del equipo de desarrollo, incluyendo tanto al equipo de front-end, back-end como al resto de las áreas técnicas y organizativas, utilizamos Discord como nuestra plataforma principal de comunicación. Discord es una herramienta de comunicación en tiempo real diseñada originalmente para comunidades de videojuegos, pero que ha sido ampliamente adoptada por equipos de trabajo técnico debido a su versatilidad, baja latencia en llamadas, interfaz intuitiva y capacidades de organización mediante canales temáticos y roles personalizados. Estas características la convierten en una solución idónea para Mushroom, desarrollado por el equipo de TeemoSolutions, al facilitar una comunicación fluida, continua y sin restricciones de tiempo para reuniones técnicas, sesiones de planificación, revisiones de código, discusiones de diseño, resolución de incidencias y coordinación general del proyecto.<br><br>

  En Discord, se establecieron distintos canales organizados por bounded contexts y áreas funcionales del proyecto (front-end, back-end, base de datos, diseño, testing, etc.), lo cual permitió segmentar las conversaciones y asignar tareas de forma clara y estructurada. Además, se habilitaron canales de texto y voz para distintos tipos de reuniones (diarias, retrospectivas, planificación, diseño), optimizando la colaboración sincrónica y asincrónica del equipo. Se definieron también roles específicos dentro del servidor (como Product Owner, coordinador de diseño, responsable de base de datos), lo cual facilitó la asignación de responsabilidades y el flujo de trabajo colaborativo. Gracias a esta infraestructura comunicacional, se logró mantener una gestión eficiente del proyecto y un seguimiento preciso de las actividades durante todo el ciclo de vida del desarrollo de Mushroom.<br><br>

  * Página oficial de Discord: https://discord.com/ <br><br>

* **Comunicación sincrónica y asincrónica - WhatsApp**

  Para la gestión de la comunicación sincrónica y asincrónica de todo el equipo de Mushroom se emplea WhatsApp como plataforma principal de mensajería instantánea. WhatsApp, con su amplia adopción y soporte multiplataforma (Android, iOS y escritorio), ofrece un canal confiable para el intercambio de mensajes de texto, notas de voz, llamadas de voz y videollamadas, garantizando comunicación continua y cifrada de extremo a extremo entre los miembros del proyecto. Esta elección se fundamenta en la familiaridad del grupo con la interfaz de usuario, la disponibilidad constante en dispositivos móviles y la posibilidad de compartir rápidamente archivos multimedia y documentos, lo que agiliza la resolución de consultas técnicas y la coordinación de actividades diarias.<br><br>

  En esta plataforma, se ha configurado un chat grupal donde participan todos los integrantes del equipo, lo que facilita la difusión de información global, la asignación de tareas y el seguimiento de hitos o incidentes en tiempo real. Paralelamente, cada colaborador cuenta con la capacidad de establecer comunicación directa con el líder del equipo o con compañeros asignados a tareas específicas, posibilitando interacciones más enfocadas y oportunas para resolver dudas puntuales o recibir retroalimentación inmediata. Gracias a la versatilidad de WhatsApp, se logran establecer flujos de comunicación efectivos tanto para discusiones de alto nivel (mediante videoconferencias grupales) como para consultas rápidas (a través de mensajes o audios), fortaleciendo la cohesión del equipo y asegurando una coordinación eficiente del proyecto Mushroom.<br><br>

  * Página oficial de WhatsApp: https://www.whatsapp.com/?lang=es_LA <br><br>

* **Sesiones de Brainstorming y colaboración en tiempo real - Excalidraw**

  Para la facilitación de la ideación visual y la colaboración en tiempo real entre todos los miembros del equipo de Mushroom, se emplea Excalidraw como plataforma principal de pizarra digital colaborativa. Excalidraw es una herramienta de código abierto y uso gratuito que proporciona un lienzo virtual ilimitado, permitiendo a los participantes esbozar diagramas, flujos de trabajo y prototipos de manera libre y espontánea. Su interfaz minimalista y basada en vectores ofrece herramientas esenciales (líneas, formas, texto y colores básicos) para representar conceptos técnicos, arquitecturas de sistema, procesos de interacción y esquemas de integración de componentes sin necesidad de conocimientos avanzados en software de diseño. Además, Excalidraw garantiza un entorno orientado a la privacidad y seguridad, ya que no requiere registros complejos ni almacena información sensible de manera persistente.<br><br>

  Dentro del proyecto de Mushroom, Excalidraw se empleó para sesiones de brainstorming y talleres de diseño, en los cuales se definieron tanto la arquitectura general del sistema (front-end, back-end, bases de datos y lógica de la aplicación móvil) como los flujos de usuarios y la interacción entre los distintos bounded contexts de forma rápida, sencilla y directa. De igual modo, se utilizaron sus capacidades de colaboración en tiempo real para la elaboración de diagramas Kanban simplificados, facilitando la asignación y visualización de tareas durante los sprints. Esta metodología visual permitió al equipo desglosar de manera clara y ordenada las actividades asociadas a cada componente, optimizando la comunicación interfuncional y acelerando la toma de decisiones en torno a la estructuración del proyecto.<br><br>

  * Página oficial de Excalidraw: https://excalidraw.com/ <br><br>

* **Desarrollo de documentos de participación - Google Docs**

  Google Docs es un procesador de texto basado en la nube que habilita la creación, edición y almacenamiento de documentos en tiempo real, utilizando Google Drive como repositorio central. La plataforma ofrece un conjunto completo de funcionalidades dirigidas a entornos colaborativos y administrativos: edición simultánea con actualización en tiempo real, control de versiones automático con historial, comentarios y sugerencias, herramientas avanzadas de formato de texto y párrafo (estilos, plantillas, numeración y listas), inserción de objetos multimedia (imágenes, tablas, gráficos vinculados) y enlaces externos, además de correctores ortográfico y gramatical, y soporte para trabajo sin conexión mediante sincronización automática. Su arquitectura en la nube garantiza alta disponibilidad, escalabilidad en el almacenamiento y compatibilidad multiplataforma, lo que facilita tanto la accesibilidad remota como la integración con otros servicios de Google.<br><br>

  En el contexto del proyecto de Mushroom, Google Docs se ha empleado como herramienta principal para la gestión y seguimiento de responsabilidades del equipo, permitiendo asignar y documentar tareas específicas, definir criterios de evaluación basados en la puntualidad de las entregas, la colaboración continua y la calidad de los entregables. Además, Google Docs ha servido como espacio para la redacción rápida de ideas textuales, la elaboración de reportes de incidencias (bugs, fallos de diseño o inconsistencias en el flujo de la aplicación) y la propuesta de cambios significativos en el alcance o la arquitectura, beneficiándose del control de cambios y del historial de versiones para mantener trazabilidad de las modificaciones. Gracias a estas capacidades, el equipo de Mushroom ha optimizado la comunicación documental y ha establecido un registro transparente de la evolución de cada actividad hasta la finalización del proyecto.<br><br>

  * Página oficial de Google Docs: https://docs.google.com/document/u/0/ <br><br>

* **Presentaciones de alto impacto a stakeholders - Canva**

  Canva es una plataforma de diseño gráfico basada en la nube que facilita la creación de presentaciones de alto impacto orientadas a audiencias técnicas y no técnicas. Su entorno de trabajo proporciona una amplia variedad de plantillas profesionales, elementos visuales (gráficos, diagramas, iconografía) y herramientas de edición colaborativa, permitiendo al equipo de Mushroom construir diapositivas coherentes con la identidad visual del proyecto y adaptadas a distintos públicos, como inversionistas, aliados estratégicos y usuarios finales. Además, su capacidad para exportar presentaciones en formatos livianos (PDF, PPTX, vídeo) garantiza una distribución rápida y confiable de los contenidos, optimizando tanto la transferencia de archivos como la visualización en dispositivos con limitaciones de ancho de banda.<br><br>

  En el marco de las entregas parciales y auditorías internas, utilizamos Canva no solo para el diseño de las exposiciones, sino también para grabar vídeos narrados directamente dentro de la plataforma, diapositiva por diapositiva. Esta funcionalidad permite generar presentaciones en formato multimedia que combinan voz, vídeo, animaciones de entrada y salida de elementos gráficos, así como transiciones personalizadas, de manera que la revisión periódica del avance se realiza con rapidez y calidad profesional. Los vídeos generados facilitan la auditoría técnica y la retroalimentación de los stakeholders, ya que integran el contexto visual de la interfaz de usuario, diagramas de arquitectura y métricas de desarrollo en un único recurso descargable junto al documento final de la presentación.<br><br>

  * Página oficial de Canva: https://www.canva.com/ <br><br>

* **Gestión del desarrollo del proyecto, de Product Backlog y Sprint Backlogs - Jira Software**

  Jira Software es una plataforma de gestión de proyectos orientada a equipos de desarrollo ágil, que facilita la planificación, seguimiento y control de todas las actividades relacionadas con el ciclo de vida del software. Basada en la metodología Scrum, Jira permite configurar Product Backlogs y Sprint Backlogs de forma granular, definiendo historias de usuario, tareas técnicas y criterios de aceptación para cada funcionalidad o componente del sistema. Gracias a su flexibilidad, es posible parametrizar flujos de trabajo personalizados (workflows) que reflejen el proceso interno de revisión, aprobación y entrega de cada ítem. Además, Jira ofrece mecanismos de gestión de versiones, seguimiento de incidencias y generación de informes de progreso, lo cual garantiza una transparencia total sobre el estado de avance del proyecto y la identificación temprana de desviaciones con respecto a los plazos establecidos.<br><br>

  Dentro de Mushroom, hemos configurado tableros Scrum que contienen los Product Backlogs y Sprint Backlogs correspondientes a cada iteración planificada. Cada miembro del equipo recibe asignaciones específicas con fechas límite claras para asegurar el cumplimiento de los objetivos de cada sprint, abarcando tareas de desarrollo de frontend, backend, base de datos y aplicación móvil. Los epics, historias de usuario y tareas técnicas se vinculan entre sí para visualizar dependencias y priorizar entregables críticos en cada ciclo de trabajo. A lo largo del sprint, se realizan reuniones diarias (daily stand-ups) y revisiones de sprint (sprint reviews) dentro de Jira, empleando tableros y filtros personalizados para validar el cumplimiento de los criterios de aceptación y detectar bloqueos.<br><br>

  * Página oficial de Jira: https://www.atlassian.com/software/jira <br><br>

**Requirement Management**

Esta sección se centra en la gestión integral de requisitos mediante el uso de plataformas para las actividades de Needfinding, elaboración y refinamiento de User Personas, análisis sistemático de entrevistas y mapeo de procesos As-Is y To-Be. Estas plataformas facilitan la construcción de arquetipos de usuario y la visualización de sus necesidades y expectativas a través de plantillas interactivas y reportes dinámicos, además de ofrecer un entorno colaborativo de pizarra digital para capturar insights de entrevistas, estructurar flujos de procesos actuales y diseñar estados futuros óptimos, permitiendo la trazabilidad bidireccional de cada requisito desde su identificación hasta su validación, así como la generación de artefactos compartidos que soportan la toma de decisiones basada en datos cualitativos y cuantitativos a lo largo del ciclo de vida del proyecto.

* **Desarrollo de diagramas de Needfinding con el enfoque UX (User Experience) - UXPressia**

  UXPressia es una plataforma especializada en la creación y gestión de artefactos de experiencia de usuario, orientada a la definición profunda de User Personas, Empathy Maps, Journey Maps e Impact Maps. Esta herramienta basada en la nube permite diseñar perfiles de usuarios detallados, describiendo atributos demográficos, comportamentales y motivacionales, lo cual resulta esencial para alinear los requisitos del producto con las necesidades reales de los usuarios finales. Además, UXPressia proporciona plantillas estandarizadas y capacidades de colaboración en tiempo real, garantizando que todo el equipo de Mushroom pueda contribuir simultáneamente a la codificación de insights de usuario, la identificación de pain points y la definición de oportunidades de mejora en cada etapa del ciclo de interacción.<br><br>

  En el contexto de Mushroom, UXPressia se emplea para construir User Personas basados en investigaciones de mercado y datos de usuario, definiendo segmentos clave con objetivos y comportamientos específicos. A partir de estos perfiles, se generan Empathy Maps que detallan las emociones, pensamientos, acciones y frustraciones de cada segmento, permitiendo priorizar funcionalidades y diseñar flujos de interacción más empáticos. Asimismo, con Journey Maps, se mapean los puntos críticos del recorrido del usuario, desde la adquisición de una planta hasta el monitoreo constante con Mushroom, identificando momentos de valor y posibles fricciones en la experiencia. Finalmente, los Impact Maps facilitan la vinculación entre objetivos de negocio y actividades concretas de diseño e implementación, asegurando que todas las decisiones de desarrollo estén justificadas en métricas de impacto. Gracias a la trazabilidad y la interoperabilidad de UXPressia, el equipo multidisciplinario de TeemoSolutions logra un alineamiento exhaustivo entre investigación UX, diseño de producto y desarrollo técnico, cimentando una experiencia de usuario sólida y validada.<br><br>

    * Página oficial de UXPressia: https://uxpressia.com/ <br><br>

* **EventStorming, Flows, Canvases y Mapeo As-Is y To-Be - Miro**

    Miro se configura como una plataforma colaborativa basada en un lienzo digital flexible que facilita la visualización y modelado de procesos complejos, integrando funcionalidades avanzadas para la creación de As-Is y To-Be Scenario Maps, así como para la realización de sesiones de EventStorming. Su infraestructura permite trabajar simultáneamente en un espacio infinito, soportando elementos gráficos como sticky notes, diagramas de flujo, plantillas personalizadas y conexiones semánticas entre objetos. Gracias a su compatibilidad con metodologías ágiles y técnicas de modelado de dominios, Miro resulta idóneo para la representación de artefactos de arquitecturas basadas en Bounded Contexts, ya que posibilita la creación de tableros especializados donde se delimita visualmente cada contexto, se establecen fronteras claras de responsabilidad y se documentan relaciones entre servicios, eventos y actores del sistema.<br><br>

    En el marco del desarrollo de Mushroom, Miro se emplea para elaborar detallados As-Is Scenario Maps, que describen los flujos actuales de interacción del usuario y del dispositivo, así como To-Be Scenario Maps que muestran la evolución prevista tras la implementación de nuevas funcionalidades. Asimismo, se usó durante el desarrollo del EventStorming. En las sesiones de EventStorming, los participantes generan un mapa de eventos de dominio, identificando comandos, aggregates y resultados relevantes para los distintos módulos identificados. A continuación, estos eventos se agrupan en Bounded Contexts, diferenciando claramente los ámbitos de frontend, backend, base de datos y sistemas externos. Con los Flows y Canvases resultantes, se definen diagramas de secuencia y estructuras lógicas que guían la implementación técnica. Además, se realizan sesiones de brainstorming centradas exclusivamente en la profundización de cada Bounded Context, permitiendo asignar responsabilidades específicas y optimizar la cohesión interna.<br><br>

    * Página oficial de Miro: https://miro.com/es/ <br><br>

**Product UX/UI Design**

Esta sección se orienta al diseño UX/UI mediante el aprovechamiento de herramientas especializadas para la definición de Style Guidelines, la creación de wireframes, mockups, wireflows, user flows y prototipos interactivos. En este sentido, usamos plataformas que actuan como eje central para la composición de sistemas de diseño escalables, gestión de bibliotecas de componentes, especificación de tokens de estilo y colaboración en tiempo real entre diseñadores y desarrolladores. También estructuramos diagramas de wireflows y userflows detallados que documentan la navegación y jerarquía de información, garantizando la coherencia entre la estructura de contenido y la experiencia interactiva, así como la iteración continua de prototipos navegables que permiten pruebas de usabilidad y refinamiento basado en métricas cualitativas y cuantitativas durante todo el ciclo de desarrollo.

* **UX/UI Design y Prototyping - Figma**

    Figma se emplea como la plataforma principal para el diseño visual y la elaboración de prototipos interactivos en Mushroom, abarcando desde la creación de wireframes iniciales hasta mock-ups de alta fidelidad y prototipos navegables. Gracias a su entorno colaborativo en tiempo real, los diseñadores pueden esbozar rápidamente la estructura básica de la interfaz, definiendo la colocación de componentes, jerarquías de contenido y flujos de navegación, y, de manera simultánea, recibir retroalimentación de desarrolladores frontend, backend y diseñadores. Figma soporta la parametrización de componentes reutilizables, lo que permite establecer sistemas de diseño consistentes, fáciles de mantener y escalables a lo largo de todo el proyecto. Asimismo, sus herramientas de prototipado incorporadas facilitan la simulación de interacciones, transiciones y estados dinámicos sin necesidad de codificación, posibilitando ensayos de usabilidad temprana y validación con usuarios reales antes de la implementación. <br><br>

    Además, Figma se utiliza para definir y documentar las Style Guidelines o pautas de estilo de Mushroom, garantizando la coherencia visual y la uniformidad de la marca. Dentro de estas guías se especifican tipografías, paletas de colores, reglas de espaciado, estilos de íconos y comportamientos de interacción (por ejemplo, estados de hover, focus y active), de modo que todos los componentes gráficos se alineen con los estándares de accesibilidad y usabilidad. Las librerías de estilos compartidas facilitan la adopción de estas pautas por parte de los desarrolladores frontend y móvil, asegurando que los elementos de interfaz se implementen según las especificaciones establecidas. De esta manera, Figma no solo actúa como una herramienta de diseño, sino también como un repositorio central de la identidad visual de Mushroom, promoviendo la colaboración multidisciplinaria y acelerando el ciclo de diseño-implementación. <br><br>

  *  Página oficial de Figma: https://figma.com/ <br><br>

* **Wireflows y User flows - LucidChart**

    Lucidchart se emplea como herramienta principal para la creación de Wireflows y User Flows en el proyecto Mushroom, aprovechando su capacidad para generar diagramas de flujo de alta calidad y su compatibilidad con múltiples tipos de modelado (UML, C4, BPMN, entre otros). A través de Lucidchart, el equipo de diseño y desarrollo puede esbozar de manera estructurada cómo interactúan los usuarios con la interfaz en cada paso del proceso, incorporando componentes visuales de alta fidelidad que permiten visualizar transiciones, estados de pantalla y puntos de decisión dentro de los flujos de interacción. Las plantillas prediseñadas y la biblioteca de formas personalizables facilitan la representación de íconos, botones, campos de entrada y elementos de navegación, garantizando que los Wireflows reflejen con precisión la estructura de las pantallas y que los User Flows documenten de forma detallada las rutas críticas de uso, desde la autenticación hasta las acciones de configuración.<br><br>

    Además, Lucidchart ofrece funcionalidades de colaboración en tiempo real, lo que permite que varios miembros del equipo, diseñadores de UX, desarrolladores de frontend y backend, editen simultáneamente los diagramas, agreguen comentarios y realicen actualizaciones instantáneas sin necesidad de consolidar archivos estáticos. Gracias a las opciones de exportación en formatos SVG, PNG y PDF, así como a la capacidad de insertar enlaces interactivos dentro de los diagramas, Lucidchart se convierte en un repositorio completo de referencia para validar la usabilidad, optimizar rutas de navegación y asegurar que las implementaciones técnicas correspondan fielmente a los diseños planeados.<br><br>

  * Página oficial de Lucidchart: https://lucidchart.com <br><br>

**Product Architecture Design**

Esta sección se dedica al diseño de la arquitectura de producto a través de la elaboración de artefactos formales que describen la estructura, los componentes y las interacciones de la solución. Se generarán diagramas C4 para representar los niveles de contexto, contenedores, componentes y código, diagramas de clases UML para modelar entidades, atributos y relaciones, y diagramas entidad-relación para definir esquemas de base de datos lógicos y físicos. Adicionalmente, se incluirán diagramas de despliegue para describir la infraestructura de TI, y mapeos de APIs y dependencias de servicios que documentan puntos de integración. Estos artefactos, versionados y trazables, garantizan la coherencia conceptual y técnica, facilitan la comunicación entre equipos multidisciplinarios y soportan la escalabilidad, mantenibilidad y rendimiento óptimo del producto a lo largo de todo su ciclo de vida.

* **Diagramas UML - LucidChart**

  Lucidchart se emplea para la generación de diagramas de clases UML que representan la estructura y relaciones de las entidades dentro de cada Bounded Context de Mushroom. Gracias a su soporte nativo para el modelado UML, la herramienta permite definir clases con atributos, métodos y visibilidades, así como establecer relaciones de herencia, asociación, agregación y composición. Cada diagrama de clases refleja los conceptos clave del dominio y muestra cómo interactúan entre sí dentro de un contexto delimitado. La interfaz de arrastrar y soltar de Lucidchart facilita la creación y modificación de estas estructuras, mientras que las bibliotecas de formas UML garantizan el uso de notaciones estándar.<br><br>

  Dentro de TeemoSolutions, se crearon diagramas de clases específicos para cada Bounded Context identificado mediante sesiones de EventStorming y mapeo en Miro. Estos diagramas, disponibles en Lucidchart, se mantienen versionados y accesibles para todo el equipo, facilitando la coherencia entre la arquitectura lógica y la capa de código en cada módulo del sistema.<br><br>

  * Página oficial de Lucidchart: https://lucidchart.com <br><br>

* **Diagramas C4 - Structurizr DSL**

  Structurizr DSL es un lenguaje específico de dominio basado en texto que facilita la creación y el versionado de diagramas C4 (Contexto, Contenedores y Componentes) de manera reproducible y colaborativa. A través de su sintaxis declarativa, permite definir elementos del sistema, como personas, sistemas externos y límites de contexto, en diagramas de Contexto; detallar las containers que componen la arquitectura en diagramas de Contenedores, y desglosar cada contenedor en sus componentes internos en diagramas de Componentes. Structurizr DSL incorpora convenciones para nombrar, etiquetar y ensamblar relaciones, así como la capacidad de generar vistas específicas basadas en filtros de etiquetas, lo que optimiza la trazabilidad de cambios y la comunicación de la arquitectura entre todos los miembros del equipo.<br><br>

  EEn el contexto de Mushroom, Structurizr DSL se utilizó para documentar exhaustivamente la arquitectura modular del sistema siguiendo el modelo C4. Primero, se definió un diagrama de Contexto que situó a los usuarios frente a Mushroom, dejando claro qué sistemas externos interactúan con la solución. A continuación, en el diagrama de Contenedores, se representaron contenedores clave de toda la plataforma. Cada contenedor se etiquetó según su responsabilidad funcional y se describieron sus protocolos de comunicación. Finalmente, se generaron diagramas de Componentes para cada contenedor no trivial, especificando componentes de alto impacto y relevancia. Gracias a Structurizr DSL, estos diagramas se mantienen sincronizados con el repositorio de código, permitiendo actualizar la arquitectura textualmente y regenerar las vistas, lo que garantiza una documentación arquitectónica coherente y actualizada en todo momento.<br><br>

    * Página oficial de Structurizr DSL: https://structurizr.com/dsl <br><br>

* **Diagramas de base de datos - Vertabelo**

    Vertabelo es una herramienta de modelado de datos relacional basada en la nube que permite diseñar, visualizar y versionar esquemas de bases de datos de manera colaborativa y rigurosa. Emplea una interfaz gráfica intuitiva para la creación de entidades, atributos, relaciones (incluyendo claves primarias y foráneas), índices y restricciones, soportando diversos motores de bases de datos (PostgreSQL, MySQL, SQL Server, entre otros). Vertabelo facilita la generación automática de scripts DDL (Data Definition Language) exportables, que aseguran la coherencia entre el modelo lógico y la implementación física. Además, su sistema de versionado integrado permite mantener un historial de cambios detallado, realizar comparaciones entre distintas versiones del modelo y colaborar en tiempo real con diversos miembros del equipo, garantizando trazabilidad y control de modificaciones en el diseño de la base de datos.<br><br>

    En el proyecto Mushroom, Vertabelo se utilizó para modelar de forma estructurada las distintas áreas de datos correspondientes a los Bounded Contexts identificados previamente. El equipo pudo generar el script DDL correspondiente, garantizar que los modelos respondieran a los requerimientos de escalabilidad y consultar la documentación. Asimismo, el versionado de los modelos permitió comparar iteraciones, revertir cambios en caso de inconsistencias y coordinar revisiones entre desarrolladores backend y especialistas en base de datos, asegurando que la implementación de la capa de almacenamiento de Mushroom estuviera alineada con la visión arquitectónica y los criterios de rendimiento definidos.<br><br>

  *   Página oficial de Vertabelo: https://vertabelo.com/ 

**Software Development**

Esta sección contempla la definición estratégica del stack tecnológico y la configuración de los entornos de desarrollo requeridos para la implementación integral de cada uno de los componentes que conforman la solución digital, los cuales incluyen la Landing Page, la aplicación móvil (Mobile App), la aplicación web (Web App), los servicios web (Web Services) y los mecanismos de pruebas (Testing). Se establecerán los lineamientos técnicos y operativos que orientarán la selección de frameworks, arquitecturas y metodologías de codificación, con el objetivo de asegurar la coherencia tecnológica, la eficiencia en el desarrollo, la escalabilidad de las soluciones y su alineamiento con los principios de mantenibilidad, seguridad y rendimiento. Asimismo, se garantizará la integración fluida entre los distintos entornos de desarrollo y pruebas, permitiendo una colaboración efectiva entre equipos multidisciplinarios, una gestión eficiente del ciclo de vida del software y una trazabilidad completa desde la codificación inicial hasta el despliegue en producción.

* **Lenguajes de etiqueta y estilo - HTML5 & CSS3**

  HTML5 y CSS constituyen las tecnologías fundamentales para la construcción de la Landing Page de Mushroom y para la implementación de los aspectos estáticos de las plantillas en la aplicación web. Con HTML5, se define una estructura semántica robusta que facilita tanto la accesibilidad como el SEO. Se emplean etiquetas específicas para organizar el contenido de la Landing Page, asegurando claridad en la jerarquía de información y compatibilidad con estándares modernos de navegadores.<br><br>

  Por su parte, CSS se encarga de la presentación visual y del comportamiento responsivo tanto de la Landing Page como de las plantillas estáticas de la aplicación web. Se aplican sistemas de diseño basados en CSS Grid para garantizar adaptabilidad en múltiples tamaños de pantalla, desde dispositivos móviles hasta pantallas de escritorio. Asimismo, se definen variables CSS para mantener coherencia en la paleta de colores y estilos tipográficos acordes con las Style Guidelines acordadas en Figma, permitiendo cambios globales de forma centralizada. Gracias a esta combinación de HTML5 y CSS, la Landing Page y las plantillas de Mushroom presentan un rendimiento óptimo, una experiencia de usuario uniforme y una base sólida para futuras iteraciones de diseño.<br><br>

  * Página de guía de HTML5 de W3C (World Wide Web Consortium): https://dev.w3.org/html5/spec-LC/ <br><br>
  * Página de guía de HTML5 de W3Schools: https://www.w3schools.com/html/ <br><br>
  * Página de guía de CSS3 de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/CSS <br><br>
  * Página de guía de CSS3 de W3Schools: https://www.w3schools.com/css/default.asp <br><br>

* **Herramientas para la programación del Web Application (Front-End) - JavaScript & TypeScript, con Angular Framework**

  JavaScript es un lenguaje de programación interpretado, dinámico y orientado a prototipos, que se ejecuta directamente en el navegador y posibilita la creación de interfaces interactivas y reactivas. Gracias a su capacidad de manipular el Document Object Model (DOM) en tiempo real, JavaScript permite actualizar el contenido de páginas web sin necesidad de recargas completas, gestionar eventos de usuario (clics, desplazamientos) y realizar peticiones asíncronas a APIs. En el contexto de Mushroom, JavaScript sirve como base para la lógica de interacción en el frontend, gestionando comportamientos dinámicos y operaciones en tiempo real que mejoran la experiencia del usuario, como validaciones de formularios, animaciones y consumo de servicios REST. <br><br>

  TypeScript es un superset tipado de JavaScript, desarrollado por Microsoft, que incorpora un sistema de tipos estáticos opcionales, clases, interfaces y módulos. Al compilarse a JavaScript estándar, TypeScript añade una capa de verificación en tiempo de compilación que detecta errores de sintaxis y de tipo antes de que el código se ejecute en el navegador, lo cual incrementa la robustez y mantenibilidad. En el desarrollo de Mushroom, TypeScript facilita la detección temprana de inconsistencias, permitiendo refactorizaciones más seguras y documentación implícita mediante anotaciones de tipo. Su integración con entornos de desarrollo modernos ofrece autocompletado y refactorización asistida, lo que acelera la productividad del equipo y minimiza errores.<br><br>

  El Framework Angular es una plataforma de desarrollo front-end basada en TypeScript que sigue una arquitectura basada en componentes, inyección de dependencias y un sistema modular. Angular organiza la aplicación en módulos que agrupan componentes, directivas, servicios y pipes de manera coherente, facilitando la escalabilidad y la separación de responsabilidades. Los componentes en Angular encapsulan la lógica de presentación, el estilo y el comportamiento, promoviendo la reutilización y la cohesión. Angular también proporciona un sistema de enrutamiento integrado que permite definir rutas y parámetros. Para la interfaz de usuario, se utiliza Angular Material, una colección de componentes UI que implementa las pautas de Material Design de Google. Angular Material ofrece una amplia variedad de elementos preconstruidos, como botones, barras de navegación, tarjetas, menús desplegables, diálogos y tablas, optimizados para accesibilidad y rendimiento. Al emplear Angular con JavaScript y TypeScript, junto con Angular Material, el equipo de Mushroom puede desarrollar un front-end consistente, modular y mantenible, con componentes estandarizados que garantizan coherencia visual, comportamiento uniforme y experiencias de usuario responsivas en múltiples dispositivos.<br><br>

    * Página oficial de Angular: https://angular.dev/ <br><br>
    * Página de documentación oficial de Angular: https://docs.angular.lat/docs <br><br>
    * Página de guía de JavaScript de Mozilla Developer Network: https://developer.mozilla.org/es/docs/Web/JavaScript <br><br>
    * Página oficial de TypeScript: https://www.typescriptlang.org/ <br><br>
    * Página de guía de TypeScript de W3Schools: https://www.w3schools.com/typescript/typescript_intro.php <br><br>
    * Página oficial de Material Design: https://m3.material.io/ <br><br>
    * Página oficial de Angular Material: https://material.angular.dev/ <br><br>

* **Herramientas para la programación del Web Services (Back-End) - RESTful API con Java y con Spring Boot**

  Java es un lenguaje de programación multiparadigma, maduro y orientado a objetos, que se ejecuta sobre la Máquina Virtual de Java (JVM) y combina características de tipado estático con capacidades para programación funcional. Su ecosistema y herramientas (JDK, compiladores, gestores de dependencias como Maven/Gradle) permiten generar binarios portables y optimizados para entornos de producción. En el contexto de Mushroom, Java se utiliza para implementar la lógica de negocio del backend con precisión y robustez, aprovechando su sistema de tipos para definir modelos de datos estrictos y facilitar la detección temprana de errores en tiempo de compilación. Además, el ecosistema Java incluye un amplio conjunto de bibliotecas y proyectos probados (por ejemplo, Jackson para serialización JSON, bibliotecas de persistencia como JPA/Hibernate y utilidades para manejo de excepciones), lo que facilita la reutilización de componentes maduros para acceso a datos, serialización y conexión a servicios externos.<br><br>

  Spring Boot (parte del ecosistema Spring) es un framework para desarrollar aplicaciones Java de manera productiva, modular y listo para producción, diseñado para construir servicios y aplicaciones modernas. Su enfoque “con convención sobre configuración” y su arquitectura basada en componentes permite configurar canales de procesamiento HTTP y gestionar de forma sencilla el ciclo de vida de la aplicación. En Mushroom, Spring Boot se emplea para hospedar el servidor de API RESTful, gestionando tareas como enrutamiento de endpoints (controladores REST), autenticación y autorización (con Spring Security y soporte para JWT), interacción con la base de datos (mediante Spring Data JPA / Hibernate), y registro estructurado de eventos (con herramientas de logging y trazabilidad).<br><br>

  El Diseño de Arquitectura RESTful API se basa en principios de uniformidad, recursos identificables y operaciones basadas en verbos HTTP (GET, POST, PUT, DELETE). Este enfoque promueve una separación clara entre cliente y servidor, fomentando la reutilización y la escalabilidad del sistema. En el caso de Mushroom, la API RESTful define múltiples recursos que exponen operaciones CRUD y acciones específicas. Cada endpoint retorna respuestas en formato JSON (normalmente gestionado por Jackson), incluyendo códigos HTTP adecuados y encabezados para control de caché o paginación. Al adoptar RESTful API con Spring Boot y Java, se logra un backend que puede atender solicitudes simultáneas provenientes de la aplicación web y la aplicación móvil, garantizando coherencia en la representación de datos, facilidad para versionar la API y compatibilidad con estándares de seguridad como JWT (JSON Web Tokens) en la capa de autenticación.<br><br>

    * Página oficial de Java (Oracle): https://www.oracle.com/java/ <br><br>
    * Guía y tutoriales de Java (Oracle): https://docs.oracle.com/javase/tutorial/ <br><br>
    * Página oficial de Spring Boot: https://spring.io/projects/spring-boot <br><br>
    * Guía rápida de crear un servicio REST con Spring: https://spring.io/guides/gs/rest-service <br><br>
    * Página de guía de RESTful API (principios generales): https://restfulapi.net/ <br><br>
    * Documentación de Spring sobre REST y Web MVC / WebFlux: https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#rest <br><br>

* **Herramientas para la programación del Mobile Application - Dart con Flutter Framework**

  Dart es un lenguaje de programación de propósito general, desarrollado por Google, que está optimizado para crear aplicaciones de alto rendimiento en cliente. Con sintaxis moderna, tipado estático opcional y recolección de basura, Dart permite desarrollar código eficiente tanto para compilación anticipada (AOT) como para compilación just-in-time (JIT). Estas características hacen de Dart una opción idónea para aplicaciones móviles, donde la rapidez en el arranque y la fluidez en la interacción son cruciales. Además, su compatibilidad con la arquitectura de Flutter facilita la construcción de interfaces reactivas y la gestión de estado, utilizando un modelo de widgets declarativo que simplifica la creación de componentes reutilizables.<br><br>

  El framework Flutter, también creado por Google, se apoya en Dart para proporcionar un kit de herramientas UI (UI toolkit) que compila de manera nativa tanto en iOS como en Android, asegurando un rendimiento cercano al código nativo. Flutter incluye un motor de renderizado propio, lo que permite dibujar cada elemento de la interfaz, animaciones y transiciones, con control total sobre los píxeles, sin depender de componentes nativos específicos de cada plataforma. Esto resulta en una experiencia visual y de interacción consistente en dispositivos diversos. En el contexto de Mushroom, Flutter y Dart se utilizan para desarrollar la aplicación móvil multiplataforma que complementa la funcionalidad de la plataforma web. El equipo ha estructurado la aplicación en módulos claros, separando la capa de presentación, la capa de lógica de negocio y la capa de datos.<br><br>

    * Página oficial de Flutter: https://flutter.dev/ <br><br>
    * Página de guía de Flutter: https://docs.flutter.dev/ <br><br>
    * Página oficial de Dart: https://dart.dev/ <br><br>
    * Página de guía de Dart: https://dart.dev/docs <br><br>
    * Página de guía y seguimiento para el modelo del Material Design: https://m3.material.io/ <br><br>

* **Entornos de Desarrollo Integrado - Webstorm, Rider, Android Studio, PyCharm, Wokwi y Visual Studio Code**

  Las Entornos de Desarrollo Integrados (IDEs) constituyen herramientas fundamentales para optimizar la productividad y la calidad del código en cada área del proyecto Mushroom. En función del lenguaje y la tecnología utilizada, se han seleccionado entornos especializados que ofrecen características avanzadas de análisis estático, depuración, refactorización y soporte de frameworks específicos:<br><br>

  * **Android Studio** se utiliza para el desarrollo de la aplicación móvil en Dart con Flutter, gracias a su integración nativa con SDKs de Android y emuladores. Android Studio incluye un editor Visual UI para diseñar interfaces de Flutter, un depurador con visualización de la jerarquía de widgets y herramientas de perfilado que miden el rendimiento en tiempo real (CPU, memoria, GPU). Su sistema de gestión de paquetes y el acceso directo al Flutter Inspector permiten inspeccionar y modificar la estructura de la UI sobre la marcha, ajustando propiedades de widgets, temas y estilos con retroalimentación instantánea. <br><br>

  * **PyCharm** se ha adoptado como el IDE de referencia para el desarrollo en Python, principalmente en el desarrollo de la aplicación edge. PyCharm ofrece inspección de código basada en PEP8, autocompletado inteligente, análisis de dependencias y detección temprana de errores. Su integración con entornos virtuales (venv, Conda) facilita la gestión de librerías, y el depurador permite establecer puntos de interrupción tanto en código local como remoto (SSH), junto con la visualización de variables en tiempo real. <br><br>

  * **Visual Studio Code (VS Code)** se configura como alternativa para aquellos miembros del equipo que no dispongan de acceso a WebStorm o Pycharm. VS Code soporta extensiones específicas, como Dart & Flutter, Angular Language Service y Prettier, que dotan al editor de capacidades de autocompletado, linting, depuración y tareas de construcción. Su arquitectura ligera y multiplataforma permite a los desarrolladores trabajar en entornos diversos con una configuración unificada. <br><br>

  * **WebStorm** se emplea como el IDE principal para el desarrollo de JavaScript, TypeScript y el framework Angular. WebStorm ofrece inspecciones inteligentes de código, autocompletado contextual, navegación rápida entre símbolos y soporte nativo para Angular CLI, lo que permite generar componentes y servicios. Asimismo, facilita la configuración de tareas de compilación mediante archivos de configuración integrados. Su depurador integrado permite establecer puntos de interrupción en tiempo real, evaluando expresiones de JavaScript/TypeScript y trazando el flujo de ejecución del frontend, lo que resulta esencial para detectar problemas de rendimiento. <br><br>

  Con esta selección de IDEs, el equipo de Mushroom garantiza que cada desarrollador disponga de un entorno adaptado a las necesidades de su área de trabajo, promoviendo un flujo de desarrollo ágil, coherente y alineado con las mejores prácticas de cada tecnología empleada.<br><br>

    * Página oficial de Android Studio: https://developer.android.com/studio?hl=es-419 <br><br>
    * Página oficial de PyCharm: https://www.jetbrains.com/es-es/pycharm/# <br><br>
    * Página oficial de Visual Studio Code: https://code.visualstudio.com/ <br><br>
    * Página oficial de Webstorm: https://www.jetbrains.com/es-es/webstorm/ <br><br>

**Software Testing**

Esta sección aborda la estrategia integral de aseguramiento de la calidad del software a través de la planificación, ejecución y seguimiento de actividades de verificación y validación orientadas a garantizar la funcionalidad, confiabilidad, usabilidad, seguridad y rendimiento de cada componente del sistema. Se establecerá un enfoque estructurado que incluirá pruebas a nivel unitario, de integración, de sistema y de aceptación. Asimismo, se definirá un conjunto de métricas clave, criterios de cobertura y protocolos de gestión de incidencias que permitan medir de manera objetiva el grado de cumplimiento de los requisitos funcionales y no funcionales. La planificación de pruebas estará alineada con el ciclo de vida del desarrollo, integrándose de forma continua en los flujos de trabajo para facilitar la detección temprana de errores, la reducción del retrabajo y la mejora sostenida del producto.

  * **Behavior-Driven Development - Cucumber**

    Cucumber es una herramienta de Behavior-Driven Development (BDD) que permite la definición de criterios de aceptación en formato legible tanto para desarrolladores como para stakeholders, utilizando la sintaxis natural de Gherkin. Cada archivo de características (.feature) contiene escenarios estructurados en pasos que describen comportamientos esperados (“Given–When–Then”), facilitando la comunicación entre el equipo técnico y el equipo de producto.<br><br> 

    Para la edición y ejecución de pruebas con Cucumber, empleamos Visual Studio Code junto con extensiones específicas. Estas extensiones habilitan resaltado de sintaxis, completado automático de palabras clave Gherkin, generación de definiciones de pasos, ejecución de escenarios directamente desde el editor y depuración de tests paso a paso. Con esta extensión garantizamos que las pruebas de aceptación sean siempre ejecutables, repetibles y estén enlazadas a los requisitos del negocio, permitiendo validar funcionalidades completas desde el nivel de API hasta la capa de presentación de forma integrada. <br><br>

    * Página oficial de Cucumber: https://cucumber.io/ <br><br>
    * Página de guía de Cucumber: https://cucumber.io/docs/cucumber/ 
  
**Software Deployment**

Esta sección se enfoca en la planificación y ejecución del proceso de despliegue de software, abarcando las herramientas y entornos necesarios para garantizar una transición controlada, segura y eficiente desde el entorno de desarrollo hacia los entornos de prueba, preproducción y producción. El enfoque adoptado permitirá minimizar riesgos asociados al lanzamiento de nuevas versiones, asegurar la reversibilidad ante fallos. Asimismo, se considerarán aspectos clave como la gestión de credenciales, la disponibilidad de infraestructura escalable, el control de acceso por entornos y la sincronización entre servicios interdependientes.

* **Despliegue de la Landing Page - Github Pages**

  GitHub Pages es un servicio de hosting estático que permite publicar sitios web y páginas de documentación directamente desde un repositorio de GitHub. Mediante la creación de una rama específica, se puede automatizar el despliegue de archivos HTML, CSS, JavaScript y activos estáticos cada vez que se realicen cambios en el repositorio. Al no requerir servidores backend ni bases de datos, ofrece una solución de hosting de bajo costo, con SSL/TLS automático y tiempos de despliegue rápidos, ideal para páginas informativas, blogs, documentación de proyectos y, en este caso, la Landing Page de Mushroom.<br><br>

  Para la Landing Page de Mushroom, cuya implementación se basa en HTML5, CSS y JavaScript, se ha configurado un workflow que compila y verifica el sitio estático al realizar un push en la rama principal. Una vez aprobados los cambios, el contenido se despliega automáticamente en GitHub Pages, asegurando que los usuarios externos accedan a la versión más reciente sin tiempos de inactividad. Además, se aprovechan las capacidades de GitHub Pages para personalizar el dominio, habilitar HTTPS y gestionar versiones históricas del sitio.<br><br>

  * Página oficial de Github Pages: https://pages.github.com/ <br><br>

* **Despliegue de Aplicaciones Móviles - Firebase App Distribution**

    Firebase App Distribution es un servicio de Google diseñado para facilitar la entrega de aplicaciones móviles a probadores internos y externos antes de su publicación en tiendas oficiales. Funciona como una plataforma centralizada que permite subir paquetes compilados (APK para Android e IPA para iOS), gestionar versiones de prueba y distribuirlas a grupos de testers mediante invitaciones por correo electrónico o enlaces únicos. Entre sus ventajas destacan la facilidad para recopilar retroalimentación temprana, identificar errores en condiciones de uso reales y administrar diferentes canales de prueba sin necesidad de depender de procesos de publicación en Google Play Console o App Store Connect. <br><br>

    En el proyecto Mushroom, Firebase App Distribution se utiliza para el despliegue de la aplicación móvil desarrollada en Flutter/Dart, permitiendo que los miembros del equipo y los testers seleccionados instalen compilaciones preelaboradas en sus dispositivos físicos (tanto Android como iOS) de manera ágil y segura. Cada nueva versión del APK o IPA se carga automáticamente desde el proceso de integración continua, se etiqueta con un número de versión semántica y se comparte con los probadores a través de la consola de Firebase. Una vez enviada la invitación, los testers pueden instalar la aplicación en sus dispositivos móviles, ejecutar pruebas de funcionalidad, validar flujos críticos y proporcionar feedback directamente en la plataforma. <br><br>

  * Página oficial de Firebase App Distribution: https://firebase.google.com/docs/app-distribution?hl=es-419 

**Software Documentation**

Esta sección contempla la elaboración, estructuración y mantenimiento de la documentación técnica y funcional del software, con el propósito de asegurar la comprensión, trazabilidad y reutilización del conocimiento a lo largo de todo el ciclo de vida del proyecto. Se definirá un marco documental que abarque desde la especificación de requisitos, diseño arquitectónico y detalles de implementación, hasta manuales de instalación, configuración, uso, mantenimiento y pruebas, dirigidos tanto a usuarios técnicos como no técnicos. La documentación será generada de forma iterativa y colaborativa, promoviendo su alineación con los avances del desarrollo y su actualización continua frente a cambios en la solución. Asimismo, se priorizará la claridad, consistencia y estandarización del lenguaje técnico utilizado, integrando diagramas, ejemplos de uso, estructuras de datos, flujos de procesos y referencias cruzadas que faciliten su navegación y comprensión.

* **Control de versiones y repositorios - Github**

  GitHub sirve como plataforma centralizada de control de versiones para todo el ecosistema de Mushroom, gestionando el repositorio remotos. En cada repositorio se aplica el GitFlow Workflow, que organiza el trabajo en ramas estables (main/master), ramas de desarrollo (develop), ramas de características (feature), ramas de corrección de errores (hotfix) y ramas de liberación (release). Este enfoque estructurado permite coordinar el avance paralelo de múltiples funcionalidades sin comprometer la estabilidad de las versiones en producción. Adicionalmente, se emplean Conventional Commits para escribir commits uniformes y legibles, lo que facilita la generación automática de changelogs y la trazabilidad de los cambios. Para la numeración de versiones, se sigue el Semantic Versioning (SemVer), etiquetando cada liberación con un esquema Major.Minor.Patch.<br><br>

  Con el fin de aislar responsabilidades y optimizar la mantenibilidad, el código fuente de Mushroom se organiza en repositorios separados por aplicación y ramas separadas por Bounded Context. Esta separación garantiza que cada equipo trabaje con su respectivo conjunto de dependencias y políticas de acceso específicos, reduciendo el riesgo de conflictos entre módulos. Asimismo, se usa un repositorio separado para el desarrollo de reportes con respecto a la introducción del producto, sus procesos de definición de requisitos y requerimientos, su listado de product backlog, diagramas, estructuras, arquitecturas, y uso del código en el producto.<br><br>

  * Página oficial de Github: https://github.com/ <br><br>
  * Página de guía de Markdown: https://www.markdownguide.org/ <br><br>

* **Documentación de Endpoints - Swagger**

  Swagger (OpenAPI) es un estándar para la documentación interactiva de APIs RESTful que permite describir de manera detallada los endpoints, parámetros, esquemas de datos, códigos de respuesta y modelos de autenticación de un servicio web. A través los modelos de especificación, Swagger genera una interfaz web (Swagger UI) que permite a los desarrolladores explorar cada ruta, probar peticiones en tiempo real y validar esquemas de solicitudes y respuestas sin necesidad de implementar clientes adicionales.<br><br>

  En Mushroom, Swagger se configura como parte del backend, de modo que con cada compilación de ASP .NET Core se actualiza la documentación de los recursos disponibles. Esto garantiza que los equipos de frontend (Angular) y mobile (Flutter) cuenten con una fuente confiable y siempre sincronizada de los contratos de la API. Además, Swagger permite exportar el documento OpenAPI a formatos como JSON o YAML para integrarlo en herramientas de generación de código. Gracias a esta implementación, la colaboración entre los diferentes contextos bounded de Mushroom se fortalece: cada equipo puede consultar, probar y consumir los endpoints de forma rápida y sin ambigüedades, reduciendo errores de integración y acelerando los ciclos de desarrollo. <br><br>

    * Página oficial de Swagger: https://swagger.io/

### 7.1.2. Source Code Management

Para garantizar la trazabilidad y la coherencia en el desarrollo de todos los componentes de Mushroom, el equipo adoptará una estrategia de gestión de código fuente basada en GitHub. Este entorno centralizado no solo servirá como repositorio único para la Landing Page, los Web Services y las aplicaciones frontend, sino también como plataforma de colaboración, revisión de cambios y despliegue continuo. Cada repositorio dispondrá de su propia URL, que se detallará en esta sección, y contendrá tanto el código de producción como las pruebas unitarias y de integración/aceptación, garantizando así un ciclo de desarrollo transparente y fácilmente verificable.

Para organizar el flujo de trabajo en Git, se implementará el modelo GitFlow propuesto por Driessen (2010), definiendo ramas específicas para desarrollo (develop), producción (main), nuevas funcionalidades (feature/), preparaciones de lanzamiento (release/) y correcciones críticas (hotfix/). Las convenciones de nombrado para los lanzamientos seguirán las pautas de Semantic Versioning 2.0.0, de modo que cada versión refleje con claridad cambios importantes, características nuevas y correcciones de errores según su impacto semántico (Preston‑Werner, 2013). Asimismo, los mensajes de commit emplearán el estándar Conventional Commits, facilitando la generación automatizada de changelogs y mejorando la legibilidad del historial de cambios (Conventional Commits, 2020).

**Repositorios en GitHub:**

- **Organization:** https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS <br><br>

- **Report:** https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-Report <br><br>

- **Landing Page:** https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-LandingPage <br><br>

- **Web Application:** https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging <br><br>

- **Mobile Application:** https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Movil <br><br>

- **Back-End Platform:** https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS/Teemo-Backend-Staging <br><br>

**Integrantes de la organización:** 

En esta sección, se presentarán todos los usuarios que forman parte de la organización de GitHub del proyecto de Teemo Solutions, junto con sus nombres de usuario correspondientes. El objetivo es evitar confusiones sobre los autores de los commits en GitHub y facilitar la identificación de los colaboradores al revisar y analizar el reporte y el código desarrollado por nuestro equipo.

###### Tabla 217

*Modelo de integrantes del equipo de Teemo Solutions dentro de la página de organización de Github*

|**Nombre de Usuario**|**Imagen de Perfil**|**Nombre del Integrante del Equipo**|
| ----- | ------ | ----- |
| JoseRiega | <img src="/assets/img/chapter-VII/github-profile/jose-riega-github-profile-picture.jpeg" alt="Riega Salas, Jose Miguel"> |  Riega Salas, Jose Miguel - u202211254 |
| RubDaShen | <img src="/assets/img/chapter-VII/github-profile/ruben-mallma-github-profile-picture.jpeg" alt="Mallma Quispe, Rubén Elías"> | Mallma Quispe, Rubén Elías - u202214234 |
| Fasz0711 | <img src="/assets/img/chapter-VII/fabrizio-sanchez-github-profile-picture.png" alt="Sanchez Zamora, Fabrizio Alessandro"> |  Sanchez Zamora, Fabrizio Alessandro - u202213652 |
| FlavioTrigueros | <img src="/assets/img/chapter-VII/flavio-trigueros-github-profile-picture.jpeg" alt="Trigueros Chumacero, Flavio Eduardo"> | Trigueros Chumacero, Flavio Eduardo - u202210190 |
| AldhaValenzuelaH | <img src="/assets/img/chapter-VII/aldhair-valenzuela-github-profile-picture.jpeg" alt="Valenzuela Huillcaya, Aldhair Johan Juan"> |  Valenzuela Huillcaya, Aldhair Johan Juan - u20201f572 |

**GitFlow Workflow**:

En nuestro proyecto adoptamos el modelo GitFlow para estructurar el control de versiones mediante ramas primarias y secundarias. Las ramas primarias consisten en main, que alberga la versión estable actualmente en producción, y develop, donde se integran de forma continua todas las funcionalidades y correcciones antes de preparar un nuevo lanzamiento (Driessen, 2010).

También presentamos ramas secundarias de feature, hotfix o release. Cada rama secundaria termina fusionándose de vuelta a develop mediante pull requests que el equipo revisa para garantizar calidad y coherencia. Este flujo promueve una colaboración ordenada, un historial de cambios claro y minimiza riesgos al pasar a producción.

**GitFlow Implementation:**

  Para implementar el flujo de trabajo Gitflow utilizando Git como nuestra herramienta de control de versiones, nos basamos en la entrada de blog "A successful Git branching model" de Vincent Driessen. Esta referencia nos permitió establecer las convenciones detalladas que serán aplicadas en nuestro proyecto (Driessen, 2010).

  ###### Figura 172

  _Evidencia del uso de Gitflow para el desarrollo en los repositorios de Macetech_

  <img src="/assets/img/capitulo-6/evidence/gitflow-evidence.png" alt="Evidencia de GitFlow">

- **Master o Main branch**

  La rama principal constituye la versión estable y desplegada en producción de nuestro proyecto. En ella reside el código que se encuentra actualmente operativo, garantizando que cualquier commit en esta rama represente una versión lista para producción. Para mantener su integridad, solo se fusionarán cambios procedentes de ramas de “release” o “hotfix” correctamente validadas.

      Notación: main o master

- **Develop branch**

  La rama de desarrollo aglutina todas las nuevas implementaciones y correcciones aprobadas, que serán parte de la siguiente versión. Actúa como un entorno de integración continua donde se integran y prueban de forma colectiva las contribuciones de las distintas “feature branches”. Una vez que la develop branch alcanza la estabilidad requerida, se crea una rama de “release” y, tras las validaciones finales, sus cambios se fusionan de vuelta tanto a main como a develop para sincronizar el historial. <br><br>

      Notación: develop

- **Feature branch**

  Cada nueva característica o mejora se desarrolla de forma aislada en una rama específica, derivada de develop. Esto facilita el trabajo concurrente de varios desarrolladores sin interferir con el código de otros equipos. Al finalizar el desarrollo y las pruebas unitarias de la funcionalidad, la “feature branch” se fusiona de nuevo en develop, aportando la nueva capacidad al conjunto de funcionalidades en preparación para el próximo lanzamiento.<br><br>

      Notación: feature/

      Ejemplo: feature/iam

- **Hotfix branch**
Las ramas de corrección urgente (hotfix/*) se crean a partir de la rama main para resolver errores críticos en producción que requieren atención inmediata. Su objetivo es aislar y corregir fallos sin interrumpir el flujo de desarrollo de nuevas funcionalidades. Una vez validada la solución mediante pruebas unitarias y, de ser necesario, pruebas de integración, la rama hotfix se fusiona tanto en main (para desplegar la corrección) como en develop (para asegurar que el arreglo se incorpore al ciclo de desarrollo continuo).

      Notación: hotfix/

      Ejemplo: hotfix/login-error

- **Release branch**
Las ramas de preparación de versión (release/*) se generan a partir de develop cuando el conjunto de funcionalidades y correcciones está listo para liberarse. En esta rama se realizan los últimos ajustes, pruebas de aceptación y actualizaciones de documentación o metadatos (número de versión, cambios en el changelog). Tras completar estas tareas, la rama release se fusiona en main (puesta en producción) y en develop (para recoger posibles ajustes realizados durante la preparación).

      Notación: release/

      Ejemplo: release/1.2.0

**Conventional Commits**

Conventional Commits es un estándar para formatear los mensajes de confirmación en Git de manera consistente y semántica. Al aplicar esta convención, cada commit comunica de forma precisa la naturaleza del cambio, lo que facilita la revisión del historial, la generación automática de registros de cambios y la integración con herramientas de automatización de versiones (Conventional Commits, 2020).

La especificación establece un esquema estructurado, compuesto por un encabezado y un cuerpo, que promueve la claridad y uniformidad en los mensajes, de modo que cualquier miembro del equipo pueda entender rápidamente el propósito y alcance de cada cambio.

La estructura de un commit debe seguir las siguientes pautas:

```
git commit -m “<tipo>[alcance opcional]: <título>“ -m “<descripción>”

con

feat(rama): verbo + descripción breve en inglés

```
En este formato, "rama" debe indicar la rama en la que se han realizado los cambios propuestos para una nueva funcionalidad de la plataforma. La descripción debe estar escrita en inglés y comenzar con un verbo que refleje claramente la naturaleza del cambio implementado. A continuación, se presenta una lista de distintos tipos de conventional commits y una tabla con verbos recomendados para los mensajes de commit:

**Tipos De Conventional Commits**

```
1. feat: Usado para describir una nueva funcionalidad añadida al código.
2. fix: Indica que un bug fue arreglado o que se le dio solución a un problema.
3. docs: Aplicado para cambios o mejoras en la documentación de código.
4. style: Describe cambios relacionados al formato del código, como espacios en blanco, indentación, etc. Cosas que no afectan la funcionalidad, sino su presentación al desarrollador.
5. refactor: Usado para modificaciones al código que no arreglan bugs o añaden nuevas funcionalidades, más bien son modificaciones que mejoran su estructura y legibilidad.
6. test: Indica la adición o modificación de un test unitario o un test funcional.
7. chore: Usado para cambios en un proceso de build o en tareas de mantenimiento que no están directamente relacionados con el mismo código.
8. perf: Describe mejoras de rendimiento en el código.

```

###### Tabla 218

*Modelo de escritura de verbos para todos los commits realizados en el proyecto de Github*

| Verbo | Traducción | Uso en el proyecto de programación |
|-------|------------|------------------------------------|
|Add  |Añadir  | Utilizado para añadir nuevas funcionalidades, componentes o módulos al frontend. Ideal para commits en los que se implementan nuevas vistas, estilos o scripts, incrementando la capacidad del sistema sin afectar las funcionalidades existentes.  |
|Create  |Crear  | Empleado para la creación de nuevos componentes, estilos o rutas en la aplicación frontend. Este verbo se usa cuando se inicia el desarrollo de una nueva característica o diseño dentro del sistema, estableciendo la base técnica sobre la cual se expandirá la funcionalidad. |
|Update  |Actualizar  | Usado para realizar modificaciones menores en las funcionalidades existentes del frontend, como la actualización de estilos, optimización de scripts o ajustes en la lógica de interacción. Se aplica en casos donde los cambios no alteran significativamente la estructura, pero mejoran el rendimiento o corrigen comportamientos. |
|Modify  |Modificar  | Aplicado cuando se realizan cambios significativos en la lógica del frontend, como la reestructuración de componentes o la implementación de nuevas políticas de diseño en la capa de presentación. Esto incluye cambios que afectan la arquitectura general o que impactan directamente en la interacción entre componentes. |
|Correct  | Corregir  | Utilizado para corregir errores menores en la implementación del frontend, como ajustes en las validaciones de formularios, corrección de rutas de navegación, o fallos en configuraciones que afectan el correcto funcionamiento de la interfaz. Este verbo se reserva para pequeñas correcciones sin grandes implicaciones. |
|Fix  |Arreglar  | Usado para solucionar bugs críticos o problemas que afectan directamente la funcionalidad del frontend. Esto puede incluir arreglar errores en la lógica de interacción, problemas de visualización o fallos en la autenticación de usuarios. También es comúnmente utilizado para resolver errores en la integración continua o el despliegue automático. |
|Delete  |Borrar  | Aplicado para la eliminación de componentes, estilos o recursos que ya no son necesarios en el frontend. Debe utilizarse cuando se elimina código obsoleto o componentes que han sido reemplazados por implementaciones más eficientes o actualizadas. |
|Drop  |Tirar  | Exclusivo para la eliminación de rutas, estilos o configuraciones en el frontend. Debe ser utilizado con precaución, ya que este tipo de cambios puede tener implicaciones críticas en la presentación de datos y la estructura general de la interfaz. Suele aplicarse cuando se reorganiza o limpia el sistema de archivos en el proceso de migración o refactorización. |

Esta norma sigue los principios de Conventional Commits, una convención ligera para estructurar y nombrar los commits. Esta convención proporciona un conjunto claro de reglas para crear un historial de cambios detallado y coherente, lo que facilita la automatización de procesos como el versionado semántico y el seguimiento de características, correcciones y modificaciones críticas. Su implementación mejora la trazabilidad del desarrollo, simplifica las revisiones y asegura una mayor transparencia en el control de versiones (Conventional Commits, 2020).

**Estructura del Mensaje de Commit:**

|type: description|
|-----------------|

**Versionado Semántico:**

Para garantizar una gestión clara y predecible de las versiones de lanzamiento, nuestro proyecto adoptará el esquema de versionado semántico 2.0.0. Este estándar define una convención de tres números, mayor, menor y parche, que refleja el grado de cambio introducido en cada lanzamiento:

* **Major (X.0.0):** incrementa cuando se realizan cambios incompatibles con versiones anteriores.

* **Minor (0.Y.0):** incrementa al añadir nuevas funcionalidades de manera retrocompatible (que son compatibles con versiones anteriores).

* **Patch (0.0.Z):** incrementa al corregir errores compatibles y realizar mejoras menores.

|Major.Minor.Patch|
|-----------------|

Al aplicar Semantic Versioning, cada número comunicará de manera inequívoca la naturaleza y el alcance de las modificaciones, facilitando la coordinación entre equipos, la automatización de despliegues y la generación de documentación de cambios (Preston‑Werner, 2013).

### 7.1.3. Source Code Style Guide & Conventions

En esta sección describiremos las convenciones y buenas prácticas que guiarán la escritura, organización y estructuración del código frontend de nuestra solución. Nos centraremos en los lenguajes y frameworks clave —Flutter, Dart, HTML, CSS, JavaScript, Angular, TypeScript— así como en tecnologías de backend y pruebas —C#, ASP NET Core, C++, Python, RESTful API, Wokwi y xUnit— para asegurar un desarrollo coherente, mantenible y escalable, y facilitar la colaboración entre todos los miembros del equipo.

Asimismo, presentaremos las pautas específicas para optimizar la experiencia de usuario, incluyendo la gestión de componentes visuales, la mejora del rendimiento en la renderización y el manejo fluido de las interacciones. Para ello, nos apoyaremos en las siguientes referencias oficiales y guías de estilo:

HTML5 Syntax (W3Schools)
https://www.w3schools.com/html/html5_syntax.asp

Google HTML/CSS Style Guide
https://google.github.io/styleguide/htmlcssguide.html

Angular Style Guide
https://angular.io/guide/styleguide

JavaScript Style Guide (Google)
https://google.github.io/styleguide/jsguide.html

Mozilla Developer Network JavaScript Code Style Guide
https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide/JavaScript

JavaScript Conventions (W3Schools)
https://www.w3schools.com/js/js_conventions.asp

TypeScript Handbook: Style Guide
https://www.typescriptlang.org/docs/handbook/declaration-files/style-guide.html

Flutter Official Documentation
https://docs.flutter.dev/get-started/learn-flutter

Flutterverso: Recursos de Aprendizaje
https://github.com/rafathefull/flutterverso

Dart Language Tour
https://dart.dev/language

Dart Libraries Catalog
https://dart.dev/libraries

Angular Style Guide
https://angular.dev/style-guide

C# Coding Conventions
https://docs.microsoft.com/dotnet/csharp/fundamentals/coding-style/coding-conventions

ASP NET Core Guidelines
https://docs.microsoft.com/aspnet/core/fundamentals/?view=aspnetcore-6.0

RESTful API Design Best Practices
https://restfulapi.net/

C++ Core Guidelines
https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines

PEP 8 – Python Style Guide
https://peps.python.org/pep-0008/

Wokwi Documentation
https://docs.wokwi.com/

xUnit Documentation
https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-csharp-with-xunit 

#### Convenciones que usaremos:

**HTML**

**1. Etiquetas en minúsculas**

Todas las etiquetas deben ir en lowercase para cumplir con el estándar HTML5 y garantizar compatibilidad entre navegadores.

    <!DOCTYPE html>
    <html lang="es">
      <head>
        <meta charset="utf-8">
        <title>Título de la página</title>
      </head>
      <body>
        <header>…</header>
      </body>
    </html>

**2. Cierre explícito de todos los elementos**

Asegurar que cada etiqueta de apertura <tag> tenga su correspondiente </tag>, incluso en elementos semánticos.

    <section>
      <article>
        <p>Texto del artículo.</p>
      </article>
    </section>

**3. Atributos en minúsculas y comillas dobles**

Todos los nombres de atributos deben ir en lowercase. Los valores siempre entre comillas dobles. 

Orden recomendado: 
- id
- class
- src/href
- alt
- atributos de accesibilidad (aria-…).

      <img
        id="logo"
        class="site-logo"
        src="logo.svg"
        alt="Logotipo de la empresa"
        width="150"
        height="60"
        loading="lazy"
        aria-hidden="true"
      >

**4. Textos alternativos y dimensiones en imágenes**

Incluir siempre "alt" descriptivo para accesibilidad.

Definir width y height (o usar CSS) para evitar cambios de layout en carga.

Emplear loading="lazy" para optimizar rendimiento en imágenes fuera de pantalla.

**5. Indentación y espaciado limpio**

Usar 2 espacios por nivel de anidado.

No dejar espacios antes ni después del signo "="" en atributos.

Insertar líneas en blanco para separar bloques lógicos (head, header, main, footer).

---

**CSS**

**1. Nomenclatura clara (BEM opcional)**

Clases y IDs descriptivos que reflejen el componente y su estado.

Ejemplo BEM:

    .card { … }
    .card__header { … }
    .card__header--collapsed { … }


**2. Agrupación de selectores relacionados**

Agrupar selectores que comparten propiedad para evitar duplicación.

    .btn,
    .link {
      cursor: pointer;
      text-decoration: none;
    }

**3. Shorthand siempre que sea posible**

Reducir líneas usando propiedades abreviadas.

    margin: 0 auto;
    border: none;

**4. Unidades en cero sin sufijos**

Evitar 0px, usar directamente 0.

    padding: 0;

**5. Orden alfabético de declaraciones**

Facilita encontrar y agregar propiedades.

    .modal {
      background-color: rgba(0,0,0,0.5);
      border-radius: 4px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.3);
      color: #fff;
      display: flex;
      padding: 1rem;
    }

**6. Breakpoints y media queries al final**

Mantener todas las media queries al final del bloque del componente.

    .container { … }
    @media (max-width: 600px) {
      .container { … }
    }

---

**TypeScript**

**1. Estructura de archivos y nomenclatura**

Archivos: kebab-case.ts para módulos; directorios en kebab-case.

Clases e interfaces en PascalCase.

Funciones y variables en lowerCamelCase.

**2. Bloques y llaves**

Cada declaración y llave debe ir en su propia línea.

    export class UserService {
      constructor(private http: HttpClient) {}

      fetchUsers(): Observable<User[]> {
        return this.http.get<User[]>('/api/users');
      }
    }

**3. Imports ordenados y agrupados**

1. Módulos de Angular/terceros

2. Módulos internos de la aplicación

3. Importaciones de estilos y activos

        import { Component } from '@angular/core';
        import { UserService } from './user.service';
        import './styles.css';

**4. Uso de const y let**

"const" por defecto; "let" solo cuando la variable cambia.

Nunca usar "var" porque tiene alcance de función, no de bloque, y puede causar problemas en redeclaración.

**5. Tipos explícitos y genéricos**

Definir tipos de parámetros y retornos.

Utilizar genéricos para colecciones y promesas.

    function getItem<T>(id: string): Promise<T> { … }

**6. Decoradores y metadatos (Angular)**

Siempre incluir "selector", "templateUrl/template", "styleUrls".

Orden en componentes: 

1. Propiedades públicas
2. Constructor
3. Ciclos de vida
4. Métodos privados

---

**C#**

**1. Nomenclatura**

PascalCase para clases, interfaces (IService), métodos públicos, propiedades, eventos.

camelCase para campos privados (_logger opcional), variables locales, parámetros.

**2. Estructura de archivo**

Nombre del archivo = nombre de la clase pública.

"using" statements fuera del "namespace" y ordenados alfabéticamente.

**3. Indentación y estilo de llaves**

Tabuladores claros por nivel. Llaves en línea nueva (Allman style).

    namespace MyApp.Services
    {
        public class OrderService
        {
            public async Task ProcessAsync(Order order)
            {
                // …
            }
        }
    }

**4. Organización de miembros**

1. Constantes
2. Campos 
3. Constructores
4. Propiedades
5. Métodos
6. Eventos

Separar bloques con línea en blanco.

**5. Comentarios y documentación**

"///" summary para documentar APIs públicas.

"//" para aclarar lógica compleja o decisiones de diseño.

**6. Buenas prácticas**

Uso de async/await para operaciones I/O.

Expresiones LINQ para manipulación de colecciones.

Operadores null-safe (?., ??).

Interpolación de cadenas ($"Usuario: {user.Name}").

**7. Verificación de estilo**

Configurar un ".editorconfig" con reglas de indentación y espacios.

Emplear analizadores Roslyn (StyleCop, SonarLint) en el pipeline de CI para garantizar cumplimiento.

---

**Angular**

**1. Estructura de módulos y carpetas**

Agrupar por funcionalidad (feature modules), no por tipo de archivo.

    src/
      app/
        core/           ← servicios y singleton providers
        shared/         ← componentes, directivas y pipes reutilizables
        features/
          users/
            users.module.ts
            users-routing.module.ts
            components/
            services/

**2. Nomenclatura de archivos y clases**

**Componentes:** kebab-case.component, **clase:** PascalCaseComponent

**Módulos:** kebab-case.module.ts, **clase:** PascalCaseModule.

**Servicios:** kebab-case.service.ts, **clase:** PascalCaseService.

**Rutas:** kebab-case-routing.module.ts.

**3. Decoradores y metadatos**

Orden dentro de un componente:

    @Component({ … })
    export class UserProfileComponent implements OnInit {
      // 1. Propiedades públicas
      @Input() userId!: string;

      // 2. Inyección de dependencias en el constructor
      constructor(private userService: UserService) {}

      // 3. Ciclos de vida (ngOnInit, ngOnDestroy, …)
      ngOnInit(): void { … }

      // 4. Métodos públicos
      onEdit(): void { … }

      // 5. Métodos privados
      private loadData(): void { … }
    }

**4. Imports ordenados**

1. Angular core
2. Angular modules
3. Servicios y componentes propios
4. Estilos y activos

        import { Component, OnInit } from '@angular/core';
        import { RouterModule } from '@angular/router';

        import { UserService } from '../services/user.service';

        import './user-profile.component.css';

**5. Plantillas y estilos**

Evitar lógica compleja en el template; delegar a métodos del componente.

Usar OnPush para detección de cambios cuando sea posible.

Encapsulación de estilos: "ViewEncapsulation.Emulated" (por defecto).

---

**ASP NET Core**

**1. Arquitectura y estructura de proyecto**

    src/
      MyApp.Api/           <- proyecto principal: controladores y configuración HTTP
      MyApp.Core/          <- entidades de dominio e interfaces
      MyApp.Infrastructure/ <- implementaciones de repositorios y contextos de datos
      MyApp.Tests/         <- pruebas unitarias e integración

**2. Program.cs y Startup.cs**

Configurar servicios (builder.Services.AddScoped<…>()) antes de app.Build().

Definir middleware en orden lógico: seguridad, enrutamiento, CORS, logs.

**3. Controladores y rutas**

Decorar con [ApiController] y [Route("api/[controller]")].

Acciones: verbos HTTP explícitos ([HttpGet], [HttpPost]).

Devolver ActionResult<T> o IActionResult para flexibilidad de status codes.

**4. Inyección de dependencias**

Registrar interfaces y clases en ConfigureServices.

No usar "new" dentro de controladores; siempre pedir dependencias por constructor.

**5. Configuración y secretos**

Variables de configuración en appsettings.json y appsettings.{Environment}.json.

Secretos locales con Secret Manager (dotnet user-secrets).

No guardar credenciales en código.

---

**RESTful API**

**1. URI y estructura de endpoints**

Sustantivos en plural: /api/users, /api/orders/{id}/items.

No incluir verbo: el método HTTP determina la acción.

**2. Verbos HTTP**

GET para lectura, POST para creación, PUT para actualización completa, PATCH para actualización parcial, DELETE para eliminación.

**3. Códigos de estado**

200 OK, 201 Created (+ Location), 204 No Content,

400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error.

**4. Versionado**

Versionar en la ruta: /api/v1/users.

Mantener compatibilidad hacia atrás mientras se publique v2.

**5. Hateoas y DTOs**

Incluir enlaces de navegación cuando aplique.

No exponer directamente entidades de base de datos; usar DTOs.

---

**Python**

**1. PEP 8: Estilo de código**

Indentación de 4 espacios (no tabuladores).

Longitud de línea menor o igual 79 caracteres.

Líneas en blanco para separar funciones y clases.

**2. Nomenclatura**

Funciones y variables: snake_case.

Clases: PascalCase.

Constantes: UPPER_SNAKE_CASE.

**3. Imports ordenados**

1. Librerías estándar
2. Librerías de terceros
3. Módulos locales

Separados por línea en blanco.

    import os
    import sys

    import requests

    from myapp.utils import helper

**4. Docstrings**

Triple comilla ("""…""") para módulos, funciones y clases.

Seguir formato Google o NumPy style.

**5. Tipado estático (opcional)**

Utilizar hints en funciones y variables.

    def fetch_data(url: str) -> dict[str, Any]:
        """Obtiene datos de la URL dada."""

### 7.1.4. Software Deployment Configuration

En esta sección, procederemos a detallar de manera exhaustiva la configuración necesaria para implementar y desplegar nuestra solución. A lo largo de este análisis, enfatizaremos las mejores prácticas que deben seguirse, así como las herramientas más adecuadas a utilizar y los flujos de trabajo recomendados para garantizar una implementación eficaz y coordinada de ambas partes de nuestra solución. Además, discutiremos cómo cada decisión técnica impacta en la funcionalidad y la experiencia del usuario, proporcionando así un enfoque integral para el desarrollo de nuestras aplicaciones.

**Landing Page:**

**1. Creación del repositorio en GitHub:**
Abrir GitHub, crear un nuevo repositorio público con un nombre claro y descriptivo para el Landing Page, y subir todos los archivos HTML, CSS, JavaScript y recursos asociados. Esta base organizará el flujo de trabajo y facilitará la colaboración del equipo.

###### Figura 75

_Repositorio de la Landing Page de Mushroom_

<img src="/assets/img/chapter-VII/deployment/landing-page/landing-page-deployment-evidence-1.png" alt="Evidencia de Uso de Github Pages">

**2. Habilitación de GitHub Pages:**
En la sección Settings -> Pages, activar GitHub Pages para el repositorio. Ahí se puede elegir la rama de despliegue y, opcionalmente, un dominio personalizado, siguiendo la interfaz guiada que ofrece GitHub.

###### Figura 76

_Habilitación de Github Pages de la Landing Page de Mushroom_

<img src="/assets/img/chapter-VII/deployment/landing-page/landing-page-deployment-evidence-2.png" alt="Evidencia de Uso de Github Pages en Settings">

**3. Configuración de la rama y directorio de publicación:**
Dentro de Settings -> Pages, seleccionar la rama main y el directorio raíz desde el que se servirán los archivos estáticos. Esto define exactamente qué contenido se publicará en el sitio.

**4. Selección definitiva de la rama de despliegue:**
Confirmar en el apartado Branch que la rama elegida (main) contiene la versión actualizada del Landing Page. Mantener las demás opciones en valores predeterminados salvo requisitos especiales.

**5. Verificación del enlace público:**
Tras guardar la configuración, GitHub generará automáticamente la URL de acceso al sitio. Cualquier push a la rama main actualizará en tiempo real la página desplegada.

###### Figura 77

_Verificación del enlace público de la Landing Page de Macetech_

<img src="/assets/img/chapter-VII/deployment/landing-page/landing-page-deployment-evidence-3.png" alt="Evidencia de Uso de Github Pages">

**6. Pruebas finales y acceso al sitio:**
Acceder al enlace generado (https://1asi0732-2510-4441-teemo-solutions.github.io/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-LandingPage/), comprobar funcionamiento y apariencia en distintos navegadores y dispositivos, y corregir posibles desviaciones de forma inmediata para garantizar una experiencia óptima.

---

**Web Application**

**1. Creación y configuración del proyecto en Firebase**
Accede a Firebase Console, crea un nuevo proyecto o selecciona el existente asociado a la Web Application. En el menú lateral, habilita App Distribution y registra tu aplicación web, vinculándola al dominio que servirá los archivos estáticos.

En tu entorno local, instala la herramienta de línea de comandos de Firebase y autentícate con firebase login. Asegúrate de haber seleccionado el proyecto correcto con firebase use.

###### Figura 78

_Selección y configuración del proyecto de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-1.png" alt="Evidencia de despliegue en Firebase">

**2. Construcción de la aplicación**
Ejecuta el comando de build de tu framework para generar los archivos estáticos listos para producción en la carpeta de salida designada.

###### Figura 79

_Construcción de la aplicación para el proyecto de la Web Application de Mushrooom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-2.png" alt="Evidencia de despliegue en Firebase">

**3. Configuración de Firebase Hosting**
Inicializa Firebase Hosting con firebase init, selecciona el proyecto y la carpeta de salida generada en el paso anterior. Cuando se te pregunte si deseas sobrescribir archivos de configuración, confirma solo los necesarios.

###### Figura 80

_Configuración de Firebase Hosting para el despliegue de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-3.png" alt="Evidencia de despliegue en Firebase">

**4. Despliegue en App Distribution**
Utilizar comandos (firebase deploy) de despliegue en Firebase para subir el paquete de la Web Application a App Distribution. Este comando empaqueta automáticamente el build y lo hace disponible para el grupo de desarrolladores configurado.

###### Figura 81

_Despliegue de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-4.png" alt="Evidencia de despliegue en Firebase">

**5. Obtención del enlace de distribución**
Una vez completada la subida, Firebase mostrará en consola la URL de App Distribution. Comparte este enlace con los desarrolladores o stakeholders para que puedan acceder y descargar la última versión de la Web Application directamente desde Firebase App Distribution.

###### Figura 82

_Página de la Web Application de Mushroom ya desplegada_

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-1.jpg" alt="Evidencia de despliegue en Firebase">

### 7.2. Solution Implementation

La implementación de la página estática de negocio, los servicios y las aplicaciones es un paso fundamental en nuestro proceso de desarrollo. Nos permite materializar el diseño y la funcionalidad planificados, transformando los conceptos en productos tangibles y listos para su uso. Esta fase nos permite traducir las especificaciones y requisitos en código, desarrollando la estructura de la página, los servicios y las aplicaciones de acuerdo con las necesidades identificadas.

### 7.2.1. Sprint 1

El primer sprint es un hito importante en nuestro proceso de desarrollo ágil. Durante este período, nos enfocamos en la implementación de las características y funcionalidades prioritarias identificadas en la planificación inicial. Esto implica traducir los requisitos y especificaciones en código funcional, desarrollando las bases de nuestro producto de manera iterativa.

#### 7.2.1.1. Sprint Planning 1

El sprint planning es una reunión en la metodología ágil donde el equipo planifica las actividades del próximo sprint. Define qué trabajo se hará, cuánto tiempo tomará y quién será responsable. El objetivo es establecer un plan claro y alcanzable para el equipo, fomentando la colaboración y asegurando que todos estén alineados en cuanto a objetivos y prioridades.

###### Tabla 219
*Sprint Planning del primer sprint de desarrollo de Mushroom de TeemoSolutions*

<table  style="text-align: center;">
    <tbody>
        <tr>
			<td colspan="1">Sprint #</td>
            <td colspan="1"> Sprint 1  </td>
		</tr>
        <tr>
			<td colspan="2">Sprint Planning Background</td>
		</tr>
        <tr>
			<td colspan="1">Date</td>
            <td colspan="1"> 2025-11-01 </td>
		</tr>
        <tr>
			<td colspan="1">Time</td>
            <td colspan="1"> 17:20</td>
		</tr>
        <tr>
			<td colspan="1">Location</td>
            <td colspan="1">Discord (Reunión virtual)</td>
		</tr>
        <tr>
			<td colspan="1">Prepared By</td>
            <td colspan="1"> Trigueros Chumacero, Flavio Eduardo - Team Leader</td>
		</tr>
        <tr>
			<td colspan="1"> Attendees (to planning meeting)</td>
            <td colspan="1">Mallma Quispe, Rubén Elías; Riega Salas, Jose Miguel; Valenzuela Huillcaya, Aldhair Johan Juan; Sanchez Zamora, Fabrizio Alessandro; Trigueros Chumacero, Flavio Eduardo
 </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 1 – 1 Review Summary </td>
            <td colspan="1">El Sprint 1 se concentró en establecer las capacidades núcleo de la plataforma necesarias para las pruebas operativas en este proceso de mejora continua e innovadora. Se entregó una versión mínima viable que permite solicitar rutas, visualizarlas en móvil, registrar consultas y generar evidencia para trazabilidad; además, el equipo dejó el entorno de desarrollo y las integraciones básicas listas para continuar con las siguientes iteraciones. En la revisión se validaron los flujos end-to-end y se priorizaron mejoras en la experiencia de captura de interesados, soporte de internacionalización (i18n) y métricas de rendimiento y trazabilidad más visibles para facilitar la evaluación técnica y comercial. 
            </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 1 – 1 Retrospective Summary </td>
            <td colspan="1">Tras completar el sprint, el equipo identificó áreas de mejora en la estimación de esfuerzo, la granularidad de las tareas y la coordinación entre disciplinas; parte del alcance previsto quedó pendiente por problemas de priorización y gestión del tiempo. Como resultado, el equipo acuerda ajustar la descomposición de historias, reforzar las definiciones de “done” y mejorar la comunicación diaria para asegurar que los elementos críticos avancen en el próximo sprint.</td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 1 Goal</td>
            <td><strong>Nuestro enfoque es</strong> validar las capacidades operativas mínimas de Mushroom para soportar decisiones de ruteo basadas en evidencia, mediante el desarrollo y despliegue de un flujo completo que permita calcular rutas multi-criterio, visualizar geometría y animaciones en móvil, persistir consultas para trazabilidad y ofrecer justificaciones cuantitativas comparables; todo ello integrado con los endpoints de historial y generación de reportes para que operadores y probadores puedan usar la plataforma en condiciones reales. <br><br> <strong>Creemos que esto proporciona</strong> una base técnica y comercial verificable que reduce la incertidumbre operativa, aumenta la confianza de los usuarios en las recomendaciones del sistema y genera datos reales para priorizar las mejoras de IA y UX en las siguientes iteraciones; además, facilita la medición de impacto operacional y la preparación de pilotos con clientes tempranos. <br><br> <strong>Esto se confirmará</strong> cuando el 80 % de las solicitudes de cálculo de ruta reciban respuesta completa en 10 segundos o menos, cuando se hayan persistido al menos 20 rutas en el historial para trazabilidad y auditoría.
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 1 Velocity </td>
            <td colspan="1">46</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">46</td>
		</tr>
</tbody>
</table>

#### 7.2.1.2. Sprint Backlog 1

En este primer sprint del proceso de mejora, nos enfocamos en la implementación de las funcionalidades relacionadas a tecnologías emergentes planeadas para nuestro producto, además de otras funciones pequeñas que mejoren la calidad y la facilidad de navegación, incluyendo el cálculo de rutas optimizadas según distintos datos disponibles, la justificación cuantitativa de elección de distintas rutas y las políticas de cálculo de Incoterms junto a un sistema de almacenamiento. 

Estas características son fundamentales para establecer la base del proceso de mejora continua e innovador de nuestro producto y proporcionar una experiencia de usuario sólida y coherente.

###### Tabla 220
*Sprint Backlog del primer sprint de desarrollo de Mushroom de TeemoSolutions*

<table>
  <tbody>
    <tr>
      <td>Sprint #</td>
      <td colspan="7">Sprint 1</td>
    </tr>
    <tr>
      <td colspan="2">User Story</td>
      <td colspan="6">Work - Item / Task</td>
    </tr>
    <tr>
      <td>Id</td>
      <td>Title</td>
      <td>Task Id</td>
      <td>Task Title</td>
      <td>Task Description</td>
      <td>Estimation (Hours)</td>
      <td>Assigned To</td>
      <td>Status (To-Do / In-Process / To-Review / Done)</td>
    </tr>
    <tr>
      <td>US-18</td>
      <td>Mapa interactivo en la aplicación móvil</td>
      <td>T1</td>
      <td>Implementar vista de mapa móvil</td>
      <td>Desarrollar pantalla y contenedor de mapa interactivo en la app móvil (markers, zoom, pan).</td>
      <td>6</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T2</td>
      <td>Integrar datos de puertos y marcadores</td>
      <td>Consumir API de puertos y renderizar markers con estados operativos (operativo/restringido).</td>
      <td>2</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T3</td>
      <td>QA y correcciones</td>
      <td>Pruebas en dispositivos, corrección de bugs y optimización de rendimiento inicial.</td>
      <td>4</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-36</td>
      <td>Visualización geométrica y animación de rutas para la aplicación móvil</td>
      <td>T4</td>
      <td>Implementar renderer de geometría y animación</td>
      <td>Agregar motor en cliente para dibujar GeoJSON, segmentos y animar la progresión entre nodos.</td>
      <td>6</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T5</td>
      <td>Definir/parsear formato GeoJSON</td>
      <td>Definir cómo se consumirá la geometría (schema mínimo) y parseo en cliente móvil.</td>
      <td>3</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T6</td>
      <td>Pruebas y ajuste de rendimiento</td>
      <td>Probar animaciones, optimizar uso de CPU/GPU en dispositivos y ajustes visuales.</td>
      <td>3</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-25</td>
      <td>Cálculo de ruta optimizada multi-criterio para la aplicación web</td>
      <td>T7</td>
      <td>Integración del motor de cálculo (backend)</td>
      <td>Implementar/consumir endpoint que solicite al motor A* los resultados optimizados.</td>
      <td>8</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T8</td>
      <td>Desarrollar UI de solicitud y presentación de ruta</td>
      <td>Formulario/flow para seleccionar origen/destino, mostrar nodos, distancia y ETA.</td>
      <td>8</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T9</td>
      <td>Tests e2e y unitarios</td>
      <td>Pruebas automáticas para la integración web-backend y validación de métricas devueltas.</td>
      <td>4</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-26</td>
      <td>Cálculo de ruta optimizada multi-criterio para la aplicación móvil</td>
      <td>T10</td>
      <td>Implementar llamada a API de cálculo desde móvil</td>
      <td>Consumir endpoint de cálculo y manejar respuestas (top route, nodos, ETA).</td>
      <td>8</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T11</td>
      <td>UIs para mostrar nodos/ETA/distancia</td>
      <td>Diseñar y programar vistas móviles con detalle de ruta y métricas clave.</td>
      <td>8</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T12</td>
      <td>QA y pruebas en dispositivos</td>
      <td>Pruebas en diferentes dispositivos y corrección de UI/UX y errores de integración.</td>
      <td>4</td>
      <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-31</td>
      <td>Justificación cuantitativa de elección para la aplicación web</td>
      <td>T13</td>
      <td>Implementar consumo del endpoint de comparación</td>
      <td>Consumir API que devuelve deltas numéricos entre rutas y drivers principales.</td>
      <td>6</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T14</td>
      <td>Panel UI para justificar elección</td>
      <td>Crear componente que muestre las diferencias (delta distancia, ETA, riesgo) y texto explicativo.</td>
      <td>4</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T15</td>
      <td>Pruebas y validación</td>
      <td>QA para verificar expresiones numéricas y consistencia con datos del backend.</td>
      <td>2</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-32</td>
      <td>Justificación cuantitativa de elección para la aplicación móvil</td>
      <td>T16</td>
      <td>Consumir endpoint de comparación en móvil</td>
      <td>Lógica para solicitar comparación y recibir deltas numéricos para mostrar en móvil.</td>
      <td>6</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T17</td>
      <td>UI móvil para mostrar justificación</td>
      <td>Diseñar componente móvil que muestre diferencias numéricas y explicación breve.</td>
      <td>4</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T18</td>
      <td>QA móvil</td>
      <td>Pruebas funcionales en móvil y ajuste de formatos numéricos/localización.</td>
      <td>2</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-43</td>
      <td>Almacenamiento automático de la última ruta consultada para la aplicación web</td>
      <td>T19</td>
      <td>Integración cliente con persistencia</td>
      <td>Implementar llamada desde la UI para guardar la ruta seleccionada al historial.</td>
      <td>6</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T20</td>
      <td>Soporte backend para persistir</td>
      <td>Endpoint para recibir la ruta final seleccionada y persistir metadatos (ID, distancia, emisiones).</td>
      <td>4</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T21</td>
      <td>Verificación y reintentos</td>
      <td>Mecanismo de reintento si falla la persistencia y notificación al usuario si no se guarda.</td>
      <td>2</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-44</td>
      <td>Almacenamiento automático de la última ruta consultada para la aplicación móvil</td>
      <td>T22</td>
      <td>Implementar almacenamiento desde móvil</td>
      <td>Call a endpoint para persistir la última ruta desde la app móvil y manejo de éxito/fallo.</td>
      <td>6</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T23</td>
      <td>Cache local y sincronización</td>
      <td>Guardar localmente si no hay conexión y sincronizar en background cuando vuelva la conectividad.</td>
      <td>4</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T24</td>
      <td>QA y pruebas de sincronización</td>
      <td>Pruebas con conexiones intermitentes y verificación de consistencia de datos.</td>
      <td>2</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS-18</td>
      <td>API: persistencia de historial de viajes</td>
      <td>T25</td>
      <td>Diseñar esquema DB para historial</td>
      <td>Modelado de tabla/colección con campos: id, user, routeName, start/end, distance_nm, emissions, timestamps.</td>
      <td>4</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T26</td>
      <td>Implementar POST de trips</td>
      <td>Endpoint que persiste el payload del viaje y devuelve id de registro.</td>
      <td>6</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T27</td>
      <td>Tests y documentación</td>
      <td>Tests unitarios/integración y documentación OpenAPI del endpoint.</td>
      <td>2</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-47</td>
      <td>Historial de rutas con filtros y paginación para la aplicación web</td>
      <td>T28</td>
      <td>UI historial con filtros</td>
      <td>Crear pantalla con filtros por fecha/origen/destino y paginación en web.</td>
      <td>6</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T29</td>
      <td>Integración con API de historial</td>
      <td>Consumir TS-20, mostrar resultados paginados y manejar estados vacíos/errores.</td>
      <td>4</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T30</td>
      <td>QA funcional</td>
      <td>Pruebas de filtros, casos límite y rendimiento de paginación.</td>
      <td>2</td>
      <td>Trigueros Chumacero, Flavio Eduardo</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-48</td>
      <td>Historial de rutas con filtros y paginación para la aplicación móvil</td>
      <td>T31</td>
      <td>UI historial móvil</td>
      <td>Desarrollar pantalla de historial con filtros y paginación adecuada para móvil.</td>
      <td>6</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T32</td>
      <td>Integración con API de historial</td>
      <td>Consumir endpoint TS-20 y mostrar resultados con paginación/infinite scroll.</td>
      <td>4</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T33</td>
      <td>QA móvil</td>
      <td>Pruebas de usabilidad y consistencia de paginación en dispositivos móviles.</td>
      <td>2</td>
      <td>Sanchez Zamora, Fabrizio Alessandro</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS-20</td>
      <td>API historial: filtros y paginación</td>
      <td>T34</td>
      <td>Implementar GET /api/trips</td>
      <td>Endpoint con filtros por fecha/origen/destino y parámetros de paginación (limit/offset/page).</td>
      <td>6</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T35</td>
      <td>Indexación y optimización de consultas</td>
      <td>Crear índices y optimizar consultas para rendimiento en grandes volúmenes de datos.</td>
      <td>4</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T36</td>
      <td>Tests y documentación</td>
      <td>Tests de integración, pruebas de límite y OpenAPI docs.</td>
      <td>2</td>
      <td>Riega Salas, Jose Miguel</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-39</td>
      <td>Estimación de coste e Incoterm recomendado para la aplicación web</td>
      <td>T37</td>
      <td>Formulario web para parámetros</td>
      <td>Formulario para ingresar peso, valor, preferencia de Incoterm, origen/destino.</td>
      <td>3</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T38</td>
      <td>Integración con servicio pricing</td>
      <td>Consumir TS-16 y mostrar desglose de flete, seguro y recomendación de Incoterm.</td>
      <td>3</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T39</td>
      <td>QA y validación de cálculo</td>
      <td>Pruebas con distintos inputs y verificación de consistencia del desglose.</td>
      <td>2</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>US-40</td>
      <td>Estimación de coste e Incoterm recomendado para la aplicación móvil</td>
      <td>T40</td>
      <td>Formulario móvil para parámetros</td>
      <td>Implementar UI móvil para ingresar parámetros y solicitar estimación.</td>
      <td>3</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T41</td>
      <td>Integración con servicio pricing</td>
      <td>Consumir TS-16 y mostrar desglose y recomendación en móvil.</td>
      <td>3</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T42</td>
      <td>QA móvil</td>
      <td>Pruebas en móvil y validación de formatos monetarios/localización.</td>
      <td>2</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td>TS-16</td>
      <td>Servicio de pricing y reglas comerciales (Incoterms)</td>
      <td>T43</td>
      <td>Implementar lógica de cálculo</td>
      <td>Servicio que calcula flete estimado, seguros y aplica reglas para recomendar Incoterm.</td>
      <td>4</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T44</td>
      <td>Integración API y tests</td>
      <td>Exponer endpoint y crear tests unitarios/integración del cálculo.</td>
      <td>3</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td>T45</td>
      <td>Documentación</td>
      <td>Documentar parámetros, respuesta y ejemplos de uso.</td>
      <td>1</td>
      <td>Mallma Quispe, Rubén Elías</td>
      <td>Done</td>
    </tr>
  </tbody>
</table>


#### 7.2.1.3. Development Evidence for Sprint Review

En esta sección se explica y presenta los avances en implementación con relación a los productos de la solución según el alcance del Sprint 1. En esta iteración, se implementaron las primeras funciones de mejora continua e innovadora con nuestra tecnología emergente de Inteligencia Artificial (IA). Se integró el cálculo de mejor ruta con distintos datos disponibles por ruta, tanto en móvil y web, además de la visualización de mapas, mejoras de UI y diseño de las políticas y de la calculadora de Incoterms actualizados.

Se mostrarán los commits clave por cada repositorio específico, los cuales muestran el ciclo de vida del proyecto, y toda la información que se usó, usa y usará para el desarrollo del proyecto:

###### Tabla 221
*Development Evidence del primer sprint de desarrollo de Mushroom*

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|cbb6368|feat: UI adaptation and integration for the AI|-|2025-11-01|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|de803d7|feat: update route calculation and visualization features|-|2025-11-02|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|1479ead|feat: update map route and information|-|2025-11-04|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|5ac8080|feat: fix map on phone|-|2025-11-04|
|FlavioTrigueros/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|69c68f6|feat: update incoterm page and form|-|2025-11-05|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|940e08d|feat: UI dashboard adaptation|-|2025-11-06|
|Fasz0711/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|fsanchez_branch|240004c|feat: add PDF and Excel download functionality in incoterm calculator|-|2025-11-06|
|RubDaShen/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|d4c8864|refactor: calculate incoterm|-|2025-11-06|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|b9f89a0|feat: fix buttons and UI in selector ports|-|2025-11-06|
|Fasz0711/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|fsanchez_branch|fbc1e63|feat: add settings screen and navigation to settings, pdf generation for shipment reports and fix links for quick buttons|-|2025-11-10|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|6a542c9|feat: UI dashboard changes|-|2025-11-11|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|b66e502|feat: Port dehabilitation and route recalculation|-|2025-11-11|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|ffeead8|feat: UI and parameters adapted|-|2025-11-11|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|b213ecf|feat: add curvature to the map|-|2025-11-11|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|825351f|feat: Recalculated route v2|-|2025-11-12|
|FlavioTrigueros/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|843b52b|feat: apply inmediate route history save|-|2025-11-13|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|22d6e49|feat: add IA service and UI|-|2025-11-13|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|4103e16|feat: implement weather delay prediction and land mask service for route visualization|-|2025-11-13|
|FlavioTrigueros/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|a2a356b|feat: update route history function|-|2025-11-14|

#### 7.2.1.4. Testing Suite Evidence for Sprint Review

Para la ejecución de las pruebas automatizadas se decidió utilizar Cucumber con sintaxis Gherkin, integrándolo en Visual Studio Code para facilitar la escritura y mantenimiento de los escenarios en las historias de usuario en este sprint 1. Esta elección permite definir casos de prueba en un lenguaje natural alineado con las historias de usuario, asegurando que el comportamiento esperado de la aplicación sea comprendido por todos los involucrados. 

###### Tabla 222
*Testing Suite Evidence del primer sprint de desarrollo de Mushroom*

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|FlavioTrigueros/[TeemoSolutions-AcceptanceCriteria-Gherkin](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-Report)|main|b73525f|test: gherkin test for sprint 1|-|2025-11-14|

#### 7.2.1.5. Execution Evidence for Sprint Review

El equipo ha implementado con éxito las mejoras continuas e innovadoras de Mushroom para que funcione como una herramienta operativa con tecnología emergente Se completaron los flujos que permiten calcular rutas optimizadas, visualizar la geometría y la animación de trayectos en dispositivos móviles, solicitar justificaciones cuantitativas entre alternativas y persistir las consultas para trazabilidad. Todas las historias asignadas a este sprint se ejecutaron y entregaron integradas, lo que permitió validar el recorrido completo desde la selección de puertos hasta el almacenamiento del registro de la ruta.

###### Figura 83
*Muestra con evidencia de la selección de puertas con la geometría incluida en la aplicación móvil*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-1.jpg" alt="Mobile App Evidence 1">

###### Figura 84
*Muestra con evidencia de la animación de rutas entre dos puertos en la aplicación móvil*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-2.jpg" alt="Mobile App Evidence 2">

###### Figura 85
*Muestra con evidencia de cierre automático de puertos en la aplicación móvil*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-3.jpg" alt="Mobile App Evidence 3">

###### Figura 86
*Muestra con evidencia del cálculo de Incoterms en la aplicación móvil*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-4.jpg" alt="Mobile App Evidence 4">

En paralelo se desarrollaron las funciones asociadas a la gestión operativa. Se diseñó e implementó el API de persistencia de viajes y el servicio de historial con filtros y paginación. También se puso en marcha el servicio de pricing básico que estima costos y sugiere Incoterms, integrándolo con las vistas web y móviles para que los usuarios obtengan desglose y recomendaciones comerciales en el mismo flujo de decisión.

###### Figura 87
*Muestra con evidencia de los endpoints de puertos en el Web Services*

<img src="/assets/img/chapter-VII/evidence/web-services/evidence-web-services-1.jpg" alt="Web Services Evidence 1">

###### Figura 88
*Muestra con evidencia de los endpoints de rutas en el Web Services*

<img src="/assets/img/chapter-VII/evidence/web-services/evidence-web-services-2.jpg" alt="Web Services Evidence 2">

Para mejorar la experiencia se trabajó en una interfaz móvil y web coherente y fluida que facilita la interpretación de métricas y justificaciones, se adoptaron mecanismos de reintento y sincronización para la persistencia en condiciones de conectividad variable, y se dejó preparado el entorno para soportar internacionalización e instrumentos de telemetría. Con esta base, el equipo dispone ahora de un producto mínimo operativo que permite recoger feedback real de operadores y priorizar las mejoras de inteligencia y rendimiento en los próximos sprints.

###### Figura 89
*Muestra con evidencia de la administración de puertos habilitados y deshabilitados en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-1.jpg" alt="Web Application Evidence 1">

###### Figura 90
*Muestra con evidencia de la función de deshabilitación de puertos en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-2.jpg" alt="Web Application Evidence 2">

###### Figura 91
*Muestra con evidencia de la función de cambio de estado operativo en puertos por riesgo en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-3.jpg" alt="Web Application Evidence 3">

###### Figura 92
*Muestra con evidencia de la función de cálculo de Incoterms recomendados en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-4.jpg" alt="Web Application Evidence 4">

#### 7.2.1.6. Services Documentation Evidence for Sprint Review

En esta sección, presentamos la relación de Endpoints documentados con OpenAPI, que están directamente vinculados con el alcance del Sprint 1 de Mushroom. Iniciamos con una breve introducción que resume los logros alcanzados en relación con la Documentación de Web Services durante este período de desarrollo. A continuación, proporcionamos una tabla detallada que enumera cada Endpoint, junto con las acciones implementadas y los enlaces correspondientes a la documentación desplegada o la URL local en Sprints anteriores al despliegue de Web Services.

En la tabla, se indican las acciones soportadas para cada Endpoint, incluyendo el verbo HTTP (GET, POST, PUT, DELETE, PATCH), la sintaxis de llamada, la especificación de posibles parámetros y se incluye un ejemplo junto con una explicación del response correspondiente. 

###### Tabla 223
*Listado de Endpoints de Eventos de Mushroom de TeemoSolutions*

|Método|	Descripción|	Ejemplo de llamada|Parámetros|	Respuesta|
|-|-|-|-|-|
|GET	|Lista puertos origen asociados a eventos; útil para feeds de eventos geopolíticos/navegación.	|GET /api/events/origin-ports	|Ninguno|	200 OK → ["portId1","portId2", ...]|

###### Tabla 224
*Listado de Endpoints del desglose de los Incoterms de Mushroom de TeemoSolutions*

|Método	|Descripción	|Ejemplo de llamada	|Parámetros	|Respuesta|
|-|-|-|-|-|
|POST|	Calcula desglose de coste y recomienda Incoterm según parámetros comerciales y ruta.|	POST /api/incoterms/calculate
Body: { "cargoType":"", "cargoValue":0, "originPort":"P1", "destinationPort":"P2", ... }	|Body JSON con campos como cargoType, cargoValue, cargoWeight, seller, buyer, sellerCountry, buyerCountry, paymentTerms, insurance (bool), originPort, destinationPort, distance (num), etc.|	200 OK → objeto IncotermCalculationResult con marketConditions, recommendedIncoterm (code/name/description/costBreakdown), alternatives (lista), routeDetails (distance/estimatedTime/riskLevel) y warnings.|

###### Tabla 225
*Listado de Endpoints de los Puertos de Mushroom*

|Método	|Descripción	|Ejemplo de llamada|	Parámetros	|Respuesta|
|-|-|-|-|-|
|POST|	Crear un puerto con nombre, coordenadas y continente.	|POST /api/ports | Body: { "name":"Callao", "coordinates": { "latitude": -12.0, "longitude": -77.0 }, "continent":"South America" }	Body JSON: name (string), coordinates.latitude (number), coordinates.longitude (number), continent (string)	| 200 OK → { "id":"string","name":"string","coordinates":{ "latitude":0,"longitude":0 },"continent":"string" }|
|GET|	Obtener detalle de un puerto por id.|	GET /api/ports/{portId}	|Path: portId (string)	|200 OK → PortResource { id, name, coordinates, continent }|
|DELETE	|Eliminar puerto por id.	|DELETE /api/ports/{portId}|	Path: portId (string)|	200 OK → success (no content or simple status)|
|GET|	Obtener todos los puertos registrados (listado).	|GET /api/ports/all-ports|	Ninguno|	200 OK → Array de PortResource|
|GET|	Buscar puerto por nombre.|	GET /api/ports/name/{name}	|Path: name (string)|	200 OK → PortResource (o 404 si no existe)|

###### Tabla 226
*Listado de Endpoints de Rutas asignadas entre puertos de Mushroom*

|Método	|Descripción	|Ejemplo de llamada	|Parámetros	|Respuesta|
|-|-|-|-|-|
|GET|	Listar rutas registradas o históricas.	|GET /api/routes/all-routes	|Ninguno	|200 OK → Array de objetos con { id, homePort, homePortContinent, destinationPort, destinationPortContinent, distance }|
|POST	|Calcular ruta óptima entre dos puertos (A* + pesos).|	POST /api/routes/calculate-optimal-route?startPort=CALLAO&endPort=ROTTERDAM	|Query: startPort (string), endPort (string)	|200 OK → { "optimalRoute":[...], "totalDistance":0, "warnings":[...], "coordinatesMapping": { portId: { latitude, longitude } } }
|GET|	Obtener distancia entre dos puertos.|	GET /api/routes/distance-between-ports?startPort=CALLAO&endPort=ROTTERDAM	|Query: startPort (string), endPort (string)	|200 OK → { "distance": 0, "messages":["string"], "meta": { ... } }|

###### Tabla 227
*Listado de Endpoints de Inteligencia Artificial relacionadas a la predicción de estado de rutas de Mushroom*

|Método	|Descripción	|Ejemplo de llamada|	Parámetros|	Respuesta|
|-|-|-|-|-|
|POST	|Predecir demora por condiciones meteorológicas/oceanográficas entre origen y destino (modelo ML).|	POST /api/ai/predict-weather-delay| Body: { "distanceKm":1000, "cruiseSpeedKnots":20, "avgWindKnots":15, "maxWaveM":3, "departureTimeIso":"2025-11-14T10:00:00Z", "originLat":-12.0464, "originLon":-77.0428, "destLat":35.6762, "destLon":139.6503 }	Body JSON: distanceKm (num), cruiseSpeedKnots (num), avgWindKnots (num), maxWaveM (num), departureTimeIso (ISO string), originLat/Long, destLat/Long	|200 OK → Modelo devuelve predicción (estructura dependiente del modelo). En swagger original la respuesta es un objeto vacío como placeholder; en producción se espera { "estimatedDelayHours": number, "confidence": number, "factors":[...], "notes": "string" } o estructura análoga. |

#### 7.2.1.7. Software Deployment Evidence for Sprint Review

**1. Creación y configuración del proyecto en Firebase**
Accede a Firebase Console, crea un nuevo proyecto o selecciona el existente asociado a la Web Application. En el menú lateral, habilita App Distribution y registra tu aplicación web, vinculándola al dominio que servirá los archivos estáticos.

En tu entorno local, instala la herramienta de línea de comandos de Firebase y autentícate con firebase login. Asegúrate de haber seleccionado el proyecto correcto con firebase use.

###### Figura 93

_Selección y configuración del proyecto de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-1.png" alt="Evidencia de despliegue en Firebase">

**2. Construcción de la aplicación**
Ejecuta el comando de build de tu framework para generar los archivos estáticos listos para producción en la carpeta de salida designada.

###### Figura 94

_Construcción de la aplicación para el proyecto de la Web Application de Mushrooom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-2.png" alt="Evidencia de despliegue en Firebase">

**3. Configuración de Firebase Hosting**
Inicializa Firebase Hosting con firebase init, selecciona el proyecto y la carpeta de salida generada en el paso anterior. Cuando se te pregunte si deseas sobrescribir archivos de configuración, confirma solo los necesarios.

###### Figura 95

_Configuración de Firebase Hosting para el despliegue de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-3.png" alt="Evidencia de despliegue en Firebase">

**4. Despliegue en App Distribution**
Utilizar comandos (firebase deploy) de despliegue en Firebase para subir el paquete de la Web Application a App Distribution. Este comando empaqueta automáticamente el build y lo hace disponible para el grupo de desarrolladores configurado.

###### Figura 96

_Despliegue de la Web Application de Mushroom en Firebase_

<img src="/assets/img/chapter-VII/deployment/web-application/web-app-deployment-4.png" alt="Evidencia de despliegue en Firebase">

**5. Obtención del enlace de distribución**
Una vez completada la subida, Firebase mostrará en consola la URL de App Distribution. Comparte este enlace con los desarrolladores o stakeholders para que puedan acceder y descargar la última versión de la Web Application directamente desde Firebase App Distribution.

###### Figura 97

_Página de la Web Application de Mushroom ya desplegada_

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-1.jpg" alt="Evidencia de despliegue en Firebase">

#### 7.2.1.8. Team Collaboration Insights during Sprint

Durante el Sprint 1, nos enfocamos en el desarrollo colaborativo de las mejoras continuas e innovadoras para el Web Application y Mobile Application de Mushroom, junto a las mejoras de Web Services. Cada miembro del equipo contribuyó con sus habilidades y conocimientos. Esta colaboración se refleja en los numerosos commits realizados en nuestros repositorios de código, los cuales están respaldados por capturas de pantalla adjuntas para una documentación detallada.

Nuestro equipo se reunió tanto en persona como virtualmente para asignar tareas y discutir la estrategia de desarrollo del proyecto. Estas reuniones fueron cruciales para clarificar nuestras responsabilidades individuales y asegurar un desempeño óptimo. Para maximizar la eficiencia, decidimos asignar a cada miembro del equipo una sección específica del código para desarrollar, lo que nos permitió avanzar rápidamente y cumplir con los plazos establecidos.

Además, programamos sesiones regulares de brainstorming y resolución de problemas, donde compartimos ideas y abordamos cualquier duda o dificultad que surgiera durante el proceso de desarrollo. 

###### Figura 98
*Reporte completo de contribuciones para el desarrollo del Web Application de Mushroom en el Sprint 1.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/pulse-web-app-sprint1.png" alt="Pulse for Web Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/total-contribution-web-app-sprint1.png" alt="Contribution for Web Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/contributors-web-app-sprint1-.png" alt="Individual Contributions for Web Application">

###### Figura 99
*Reporte completo de contribuciones para el desarrollo del Mobile Application de Mushroom en el Sprint 1.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/pulse-mobile-app-sprint1.png" alt="Pulse for Mobile Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/total-contribution-mobile-app-sprint1.png" alt="Contribution for Mobile Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/contributors-mobile-app-sprint1.png" alt="Individual Contributions for Mobile Application">

###### Figura 100
*Reporte completo de contribuciones para el desarrollo del Web Services de Mushroom en el Sprint 1.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/pulse-web-services-sprint1.png" alt="Pulse for Web Services">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/total-contribution-web-services-sprint1.png" alt="Contribution for Web Services">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/contributors-web-services-sprint1.png" alt="Individual Contributions for Web Services">

---

### 7.2.2. Sprint 2

El segundo sprint es el último hito requerido para nuestro proceso de mejora continua con tecnologías emergentes y desarrollo ágil. Durante este período, nos enfocamos en la implementación final de nuestro modelo de Machine Learning junto con los pipelines de obtención de datos oceanográficos y meterológicos, las cuales son bases para nuestra propuesta emergente. Seguiremos un modelo iterativo, traduciendo los requisitos y especificaciones en código funcional.

#### 7.2.2.1. Sprint Planning 2

El sprint planning es una reunión en la metodología ágil donde el equipo planifica las actividades del próximo sprint. Define qué trabajo se hará, cuánto tiempo tomará y quién será responsable. El objetivo es establecer un plan claro y alcanzable para el equipo, fomentando la colaboración y asegurando que todos estén alineados en cuanto a objetivos y prioridades.

###### Tabla 228
*Sprint Planning del segundo sprint de desarrollo de Mushroom de TeemoSolutions*

<table  style="text-align: center;">
    <tbody>
        <tr>
			<td colspan="1">Sprint #</td>
            <td colspan="1"> Sprint 2</td>
		</tr>
        <tr>
			<td colspan="2">Sprint Planning Background</td>
		</tr>
        <tr>
			<td colspan="1">Date</td>
            <td colspan="1"> 2025-11-16</td>
		</tr>
        <tr>
			<td colspan="1">Time</td>
            <td colspan="1"> 21:10</td>
		</tr>
        <tr>
			<td colspan="1">Location</td>
            <td colspan="1">Discord (Reunión virtual)</td>
		</tr>
        <tr>
			<td colspan="1">Prepared By</td>
            <td colspan="1">Trigueros Chumacero, Flavio Eduardo - Team Leader</td>
		</tr>
        <tr>
			<td colspan="1"> Attendees (to planning meeting)</td>
            <td colspan="1">Mallma Quispe, Rubén Elías; Riega Salas, Jose Miguel; Valenzuela Huillcaya, Aldhair Johan Juan; Sanchez Zamora, Fabrizio Alessandro; Trigueros Chumacero, Flavio Eduardo
 </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 2 – 2 Review Summary </td>
            <td colspan="1">El Sprint 2 se concentró en integrar y desarrollar las funcionalidades referentes a las tecnologías emergentes planteadas para la mejora continua de nuestro proyecto. Se entregó la versión final completa que permite solicitar rutas, visualizarlas, y aplicarles distintas métricas basadas en la obtención de datos de APIs externas de oceanografía y meteorología. Luego, el modelo de Machine Learning analizara los datos y, a partir de eso, brindara sus propias recomendaciones, mediciones de riesgo y caminos alternativos más viables. Junto a estas funcionalidades, se realizó el despliegue de los servicios web y el BackEnd. En la revisión se validaron los flujos end-to-end y se priorizaron mejoras en la experiencia de captura de interesados y métricas de rendimiento y trazabilidad más visibles para facilitar la evaluación técnica.
            </td>
		</tr>
         <tr>
			<td colspan="1">Sprint 2 – 2 Retrospective Summary </td>
            <td colspan="1">Tras completar este segundo sprint, el equipo identificó aún más oportunidades de mejora en un futuro para la aplicación, agregando nuevas tecnologías emergentes para el desarrollo de aún más alternativas de rutas, evaluación profunda de Incoterms, visualización dinámica e incluso posible añadido de funciones IoT para seguimiento en vivo de cada embarcación en las rutas establecidas. Junto a estas oportunidades de mejora, incluimos unas pequeñas áreas de mejora en nuestro sprint actual, más centrado en las áreas de rendimiento de los procesos de identificación de rutas alternativas, identificación de rutas de riesgo y mejorar la comunicación diaria entre distintos integrantes del grupo.</td>
		</tr>
         <tr>
			<td colspan="2">Sprint Goal & User Stories </td>
		</tr>
         <tr>
			<td>Sprint 1 Goal</td>
            <td><strong>Nuestro enfoque es</strong> validar las capacidades operativas mínimas de Mushroom para soportar decisiones de ruteo basadas en evidencia, mediante el desarrollo y despliegue de un flujo completo que permita calcular rutas multi-criterio, visualizar geometría y animaciones en móvil, persistir consultas para trazabilidad y ofrecer justificaciones cuantitativas comparables; todo ello integrado con los endpoints de historial y generación de reportes para que operadores y probadores puedan usar la plataforma en condiciones reales. <br><br> <strong>Creemos que esto proporciona</strong> una base técnica y comercial verificable que reduce la incertidumbre operativa, aumenta la confianza de los usuarios en las recomendaciones del sistema y genera datos reales para priorizar las mejoras de IA y UX en las siguientes iteraciones; además, facilita la medición de impacto operacional y la preparación de pilotos con clientes tempranos. <br><br> <strong>Esto se confirmará</strong> cuando el 80 % de las solicitudes de cálculo de ruta reciban respuesta completa en 10 segundos o menos, cuando se hayan persistido al menos 20 rutas en el historial para trazabilidad y auditoría.
</td>
		</tr>
        <tr>
			<td colspan="1">Sprint 2 Velocity </td>
            <td colspan="1">44</td>
		</tr>
        <tr>
			<td colspan="1">Sum of Story Points </td>
            <td colspan="1">44</td>
		</tr>
</tbody>
</table>

#### 7.2.2.2. Sprint Backlog 2

En el Sprint 2 del proceso de mejora continua de Mushroom el equipo centrará su trabajo en la capa de inteligencia operacional y en las integraciones necesarias para que dicha inteligencia sea explotable por usuarios web y móviles. Se implementarán el pipeline de ingestión y normalización de pronósticos meteorológicos y oceanográficos, el motor híbrido de ruteo, el servicio de generación y scoring de alternativas (top-3) con justificación cuantitativa, y el pipeline de eventos que dispara recalculos automáticos y persiste las diferencias métricas. Además se desarrollarán las integraciones front-to-back para presentar alternativas y validez de forecast en la UI.

Estas entregas establecen la base técnica para decisiones operativas reproducibles en entornos volátiles: aseguran que el motor use datos actualizados, que las alternativas sean justificables numéricamente y que los cambios por eventos se registren y notifiquen.

###### Tabla 229
*Sprint Backlog del segundo sprint de desarrollo de Mushroom de TeemoSolutions*

<table>
  <tbody>
    <tr>
      <td>Sprint #</td>
      <td colspan="7">Sprint 2</td>
    </tr>
    <tr>
      <td colspan="2">User Story</td>
      <td colspan="6">Work - Item / Task</td>
    </tr>
    <tr>
      <td>Id</td>
      <td>Title</td>
      <td>Task Id</td>
      <td>Task Title</td>
      <td>Task Description</td>
      <td>Estimation (Hours)</td>
      <td>Assigned To</td>
      <td>Status (To-Do / In-Process / To-Review / Done)</td>
    </tr>
<tr>
  <td>TS-15</td>
  <td>Pipeline ingestión meteorológica y mapeo a grafo</td>
  <td>T46</td>
  <td>Diseño de esquema y normalización</td>
  <td>Definir esquema interno del forecast, mapeo a aristas del grafo y reglas de vigencia/versionado.</td>
  <td>6</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T47</td>
  <td>Implementación del pipeline y actualización del grafo</td>
  <td>Consumer que procesa feeds, normaliza datos, actualiza atributos de aristas (tiempo, riesgo, vigencia) y versión del forecast.</td>
  <td>10</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T48</td>
  <td>Tests, monitor y documentación</td>
  <td>Crear pruebas con datasets, métricas de ingestión, alertas y documentación de esquema/contratos.</td>
  <td>4</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td>TS-09</td>
  <td>Motor A*/AI con servicio de cálculo de rutas (ML híbrido)</td>
  <td>T49</td>
  <td>Implementar núcleo A* con interfaz de pesos dinámicos</td>
  <td>Desarrollar motor A* modular que acepte pesos por arista y exponga interfaz para inyectar factores dinámicos.</td>
  <td>8</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T50</td>
  <td>Integración con proveedor de pesos ML</td>
  <td>Conectar servicio con el componente que devuelve pesos dinámicos (modelo ML), normalizar entradas y outputs.</td>
  <td>8</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T51</td>
  <td>Endpoint y pruebas de rendimiento</td>
  <td>Exponer endpoint de cálculo, añadir métricas de latencia y tests de carga básicos para validar tiempos.</td>
  <td>4</td>
  <td>Riega Salas, Jose Miguel</td>
  <td>Done</td>
</tr>
<tr>
  <td>TS-11</td>
  <td>API para generación y ranking de alternativas</td>
  <td>T52</td>
  <td>Implementar generación y scoring</td>
  <td>Desarrollar proceso que genere variantes (mutaciones del camino) y calcule puntaje combinado (distancia, riesgo, emisiones).</td>
  <td>8</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T53</td>
  <td>Exponer API y cache</td>
  <td>Crear endpoint que entregue top-3 con justificación y añadir cache corto para respuestas frecuentes.</td>
  <td>8</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T54</td>
  <td>Tests, validación y docs</td>
  <td>Pruebas de exactitud del ranking, casos límite y documentación OpenAPI del nuevo endpoint.</td>
  <td>4</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td>TS-13</td>
  <td>Pipeline de eventos y recalculo automático</td>
  <td>T55</td>
  <td>Consumidor de eventos y validación</td>
  <td>Implementar ingesta de eventos externos (webhooks/cola), validar esquema y normalizar payloads.</td>
  <td>4</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T56</td>
  <td>Trigger de recalculo y persistencia de diferencias</td>
  <td>Disparar recalculo en motor A*, persistir nueva ruta y registrar diferencia métricas frente a la previa.</td>
  <td>6</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T57</td>
  <td>Monitoreo y reintentos</td>
  <td>Agregar mecanismo de reintentos y alertas para eventos corruptos o fallos críticos.</td>
  <td>2</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-29</td>
  <td>Top-3 alternativas en la aplicación web</td>
  <td>T58</td>
  <td>Frontend: consumir top-3 y presentar ranking</td>
  <td>Implementar componente que solicite el endpoint de alternativas y muestre rutas ordenadas con métricas comparativas.</td>
  <td>8</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T59</td>
  <td>Integración con justificación numérica</td>
  <td>Solicitar comparación entre rutas para mostrar deltas y una breve explicación que justifique el ranking.</td>
  <td>8</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T60</td>
  <td>QA y pruebas UX</td>
  <td>Verificar consistencia de métricas, estados de error y comportamiento con datos parciales.</td>
  <td>4</td>
  <td>Trigueros Chumacero, Flavio Eduardo</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-33</td>
  <td>Recalculo automático ante eventos en la aplicación web</td>
  <td>T61</td>
  <td>Backend: lógica de detección y recalculo</td>
  <td>Implementar punto de enlace que reciba la notificación de recalculo y ejecute el proceso con persistencia.</td>
  <td>6</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T62</td>
  <td>Persistencia de nueva ruta y diferencias</td>
  <td>Guardar la ruta recalculada y registrar deltas (distance, ETA, riesgo) en historial comparativo.</td>
  <td>4</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T63</td>
  <td>Notificación y estado en UI</td>
  <td>Marcar la ruta activa como actualizada y exponer estado en la UI para que el usuario revise cambios.</td>
  <td>2</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-37</td>
  <td>Ingestión de pronósticos y mapeo a aristas en la aplicación web</td>
  <td>T64</td>
  <td>Backend: endpoint para consultar validez de forecast por arista</td>
  <td>Exponer API que devuelva por tramo la versión del forecast, vigencia y los parámetros que afectan tiempo/riesgo.</td>
  <td>8</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T65</td>
  <td>Frontend para mostrar validez del forecast en la vista de ruta</td>
  <td>Integrar la información de vigencia/versión en la presentación de la ruta y resaltar aristas con forecast activo.</td>
  <td>8</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T66</td>
  <td>QA y validación de datos</td>
  <td>Probar escenarios con forecasts caducos, múltiples versiones y ausencia de datos.</td>
  <td>4</td>
  <td>Valenzuela Huillcaya, Aldhair Johan Juan</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-30</td>
  <td>Top-3 alternativas en la aplicación móvil</td>
  <td>T67</td>
  <td>Implementar consumo de top-3 en móvil</td>
  <td>Agregar lógica en app móvil para solicitar y recibir top-3 con métricas comparativas y ranking.</td>
  <td>8</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T68</td>
  <td>Diseñar vistas de comparación en móvil</td>
  <td>Crear pantallas para mostrar rutas alternativas, deltas y selección de opción preferida.</td>
  <td>8</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T69</td>
  <td>QA móvil</td>
  <td>Pruebas en dispositivos, manejo de errores de red y consistencia con versión web.</td>
  <td>4</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-34</td>
  <td>Recalculo automático ante eventos en la aplicación móvil</td>
  <td>T70</td>
  <td>Móvil: consumidor de notificaciones de recalculo</td>
  <td>Implementar en móvil la recepción de eventos que indiquen recalculo y actualizar la ruta activa.</td>
  <td>6</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T71</td>
  <td>Persistencia local y sincronización</td>
  <td>Guardar cambios localmente y sincronizar estado con backend; manejar conflictos simples.</td>
  <td>4</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T72</td>
  <td>Notificación al usuario y QA</td>
  <td>Mostrar notificación clara al usuario sobre la nueva sugerencia y validar comportamiento en pruebas.</td>
  <td>2</td>
  <td>Mallma Quispe, Rubén Elías</td>
  <td>Done</td>
</tr>
<tr>
  <td>US-38</td>
  <td>Ingestión de pronósticos y mapeo a aristas en la aplicación móvil</td>
  <td>T73</td>
  <td>Consumir endpoint de validez de forecast en móvil</td>
  <td>Implementar llamada en móvil para obtener estado/vigencia del forecast por tramo y mapear en UI.</td>
  <td>8</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T74</td>
  <td>Indicar visibilidad/alertas por tramo</td>
  <td>Marcar en el mapa móvil las secciones con forecast vigente o caducado e incluir tooltip explicativo.</td>
  <td>8</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
<tr>
  <td></td>
  <td></td>
  <td>T75</td>
  <td>QA móvil y localización</td>
  <td>Validar formatos de fecha/hora, unidades y visualización en distintos dispositivos.</td>
  <td>4</td>
  <td>Sanchez Zamora, Fabrizio Alessandro</td>
  <td>Done</td>
</tr>
  </tbody>
</table>      

#### 7.2.2.3. Development Evidence for Sprint Review

En esta sección se documentan los avances de implementación correspondientes al alcance definido para el Sprint 2. Durante esta iteración el equipo entregó las capacidades necesarias para dotar a Mushroom de inteligencia operacional: se implementó el pipeline de ingestión, normalización y versionado de pronósticos meteorológicos y oceanográficos y su mapeo a las aristas del grafo; se desarrolló el motor híbrido de ruteo y el servicio de generación y scoring de alternativas que devuelve un top-3 justificable numéricamente; además se puso en marcha el pipeline de ingestión de eventos que dispara recalculos automáticos, se persistieron las diferencias métricas y se añadieron endpoints para exponer la validez de forecast por tramo. Complementariamente se integraron las piezas front-to-back para mostrar alternativas y la validez del forecast en web y móvil, y se realizaron pruebas, monitorización y documentación técnica asociada.

A continuación se presentan los commits clave por repositorio, los artefactos generados y los registros de despliegue que demuestran el ciclo de vida de las entregas y los datos empleados durante el desarrollo.

###### Tabla 230
*Development Evidence del segundo sprint de desarrollo de Mushroom*

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|4fd36cf|feat: Enhance route history component with pagination and filtering features|-|2025-11-16|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|5cffa44|feat: add preprocessing for weather model with new features and encoders|-|2025-11-18|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|09f7142|fix: update NoaaAlertsClient to use WebClient directly and ensure query parameters are encoded|-|2025-11-19|
|FlavioTrigueros/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|cf1aeb8|feat: Refactor map component|-|2025-11-19|
|Fasz0711/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|4c3fec7|feat: Add Vanta.js background effects and improve layout for map and route history components|-|2025-11-19|
|RubDaShen/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|b5bdc92|feat: Remove success modal display after route creation|-|2025-11-19|
|RubDaShen/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|89b326e|feat: add Jeddah port and update routes to include connections to Aden|-|2025-11-22|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|5216dc4|feat: Implement dark mode styling across various components|-|2025-11-22|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|45bcad1|feat: integrate authentication headers in API services for secure requests|-|2025-11-22|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|d891192|feat: add Livorno port and update routes with new connections|-|2025-11-24|
|FlavioTrigueros/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|12c66fe|feat: Remove configuration modal and enhance route label resolution with fallback names|-|2025-11-24|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|d8f88cc|feat: implement route history feature with recent routes display and loading from backend|-|2025-11-24|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|7f475f5|feat: enhance AuthenticatedUserResource with roles and add report endpoints to API|-|2025-11-25|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|0ae4552|feat: add RouteReportController and services for generating PDF and Excel reports|-|2025-11-25|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|dbba4ad|feat: implement PortOverview API with operational status filtering and response structure|-|2025-11-25|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|2ab5119|feat: Enhance report download functionality with support for Excel format and improve user feedback on download status|-|2025-11-25|
|FlavioTrigueros/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|5f8429f|feat: Refactor nearby port service and component to support enhanced port overview with operational status and improved data handling|-|2025-11-25|
|FlavioTrigueros/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|13bbf7c|feat: refactor dashboard screen to improve route loading and add help dialog|-|2025-11-25|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|67822f2|feat: add popular routes endpoint and implement route popularity tracking|-|2025-11-26|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|65428ee|feat: Revamp configuration modal with enhanced theme customization options and improved UI elements|-|2025-11-26|
|FlavioTrigueros/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|b2754fc|feat: Add popular routes loading state and error handling in dashboard component|-|2025-11-26|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|62b52e4|feat: enhance route history loading, and improve dashboard navigation|-|2025-11-26|
|RubDaShen/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|cc5e5ad|feat: added email confirmation|-|2025-11-27|
|RubDaShen/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|79a2bb0|feat: email|-|2025-11-27|
|RubDaShen/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|a7cb4b7|feat: Enhance popular route mapping with fallback handling and normalization functions|-|2025-11-27|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|83dd6a0|feat: Add Dockerfile and nginx configuration for Angular application deployment|-|2025-11-28|
|AldhaValenzuelaH/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|aldha_branch|022c9ba|feat: add cancel port and waypoints in map|-|2025-11-28|
|AldhaValenzuelaH/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|66d90e0|feat: implement notification system for port status changes with read tracking|-|2025-11-30|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|ac38251|feat: Implement notification service with UI integration for real-time notifications|-|2025-11-30|
|JoseRiega/[Teemo-Backend-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-Backend-Staging)|master|66d90e0|feat: add new routes to DataInitializer for enhanced route coverage|-|2025-12-01|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|4747fdb|feat: Add risk level handling and UI updates for delay overlay component|-|2025-12-02|
|AldhaValenzuelaH/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|21d03c0|feat: Enhance risk level determination with delay hours consideration|-|2025-12-02|
|JoseRiega/[Teemo-FrontEnd-Staging](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/Teemo-FrontEnd-Staging)|main|b5c6d59|feat: Add user profile component and enhance user-related functionality across the application|-|2025-12-02|
|Fasz0711/[TeemoSolutions-mobile](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-mobile)|fsanchez_branch|5c34426|feat: add notifications screen, and integrate notification handling|-|2025-12-02|

#### 7.2.2.4. Testing Suite Evidence for Sprint Review

Para la ejecución de las pruebas automatizadas en el Sprint 2 se mantiene Cucumber con sintaxis Gherkin integrado en Visual Studio Code, ampliando su uso más allá de las pruebas funcionales de interfaz para cubrir escenarios de aceptación end-to-end relacionados con pipelines de ingestión de forecast, disparo de eventos y recalculo de rutas, y la generación y ranking de alternativas. Esta aproximación permite describir en lenguaje natural escenarios complejos facilitando la validación por parte de stakeholders no técnicos y la trazabilidad entre historias de usuario y pruebas. Los escenarios de Cucumber se complementan con suites de pruebas unitarias e integración (para los servicios backend y jobs) y con pruebas de rendimiento básicas, todo ello orquestado en el flujo de CI para ejecución automática en cada despliegue.

###### Tabla 231
*Testing Suite Evidence del segundo sprint de desarrollo de Mushroom*

| Repository | Branch | Commit ID | Commit Message | Commit Message Body | Commited on (Date) |
| ---------- | ------ | --------- | -------------- | ------------------- | ------------------ |
|FlavioTrigueros/[TeemoSolutions-AcceptanceCriteria-Gherkin](https://github.com/1ASI0728-2520-7306-TEEMO-SOLUTIONS/TeemoSolutions-Report)|main|b62595f|test: gherkin test for sprint 2|-|2025-12-02|

#### 7.2.2.5. Execution Evidence for Sprint Review

El equipo ha completado las entregas planificadas del Sprint 2, dotando a Mushroom de su capa de inteligencia operacional. Se implementaron y desplegaron los pipelines de ingestión, normalización y versionado de pronósticos meteorológicos y oceanográficos con mapeo a las aristas del grafo; se desarrolló el motor híbrido de ruteo (A* con pesos dinámicos aportados por modelos ML) y el servicio de generación y scoring de alternativas que devuelve un top-3 justificable numéricamente. Además, se puso en marcha el pipeline de eventos que ingiere notificaciones externas y dispara recalculos automáticos, persiste las rutas resultantes y registra las diferencias métricas.

###### Figura 101
*Muestra con evidencia de la selección de puertos con alertas presentadas con Inteligencia Artificial y manejo de APIs*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-5.png" alt="Mobile App Evidence 5">

###### Figura 102
*Muestra con evidencia de la animación de rutas entre dos puertos en la aplicación móvil*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-6.png" alt="Mobile App Evidence 6">

###### Figura 103
*Muestra con evidencia del cálculo y recomendación de Incoterm para una ruta*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-7.png" alt="Mobile App Evidence 7">

###### Figura 104
*Muestra con evidencia de la explicación con IA generativa del porque otras alternativas de Incoterm no son adecuadas*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-8.png" alt="Mobile App Evidence 8">

###### Figura 105
*Muestra con evidencia de los reportes de ruta con opción para descarga en PDF o Excel*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-9.png" alt="Mobile App Evidence 9">

###### Figura 106
*Muestra con evidencia de las notificaciones tras deshabilitación de puertos*

<img src="/assets/img/chapter-VII/evidence/mobile-app/evidence-mobile-app-10.png" alt="Mobile App Evidence 10">

Estas capacidades se integraron con las vistas web y móviles para exponer alternativas, deltas cuantitativos y la vigencia del forecast; se añadieron mecanismos de reintento y sincronización para condiciones de conectividad variable, y se completaron pruebas, monitorización y documentación técnica asociada. Durante la iteración se validaron flujos end-to-end con datos de prueba, se recogieron métricas clave de desempeño (latencia de cálculo y tasa de ingestión) y se corrigieron cuellos de botella identificados, mejorando la estabilidad del servicio.

###### Figura 107
*Muestra con evidencia de los endpoints de puertos en el Web Services*

<img src="/assets/img/chapter-VII/evidence/web-services/evidence-web-services-1.jpg" alt="Web Services Evidence 1">

###### Figura 108
*Muestra con evidencia de los endpoints de rutas en el Web Services*

<img src="/assets/img/chapter-VII/evidence/web-services/evidence-web-services-2.jpg" alt="Web Services Evidence 2">

Con esto, el producto alcanza una base robusta para decisiones operativas reproducibles y queda listo para pilotos controlados y para la próxima fase centrada en afinar la precisión de los modelos, ampliar cobertura de fuentes de datos y escalar el procesamiento.

###### Figura 109
*Muestra con evidencia de la administración de puertos habilitados y deshabilitados en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-1.jpg" alt="Web Application Evidence 1">

###### Figura 110
*Muestra con evidencia de la función de deshabilitación de puertos en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-2.jpg" alt="Web Application Evidence 2">

###### Figura 111
*Muestra con evidencia de la función de cambio de estado operativo en puertos por riesgo en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-3.jpg" alt="Web Application Evidence 3">

###### Figura 112
*Muestra con evidencia de la función de cálculo de Incoterms recomendados en el Web Application*

<img src="/assets/img/chapter-VII/evidence/web-app/evidence-web-app-4.jpg" alt="Web Application Evidence 4">

#### 7.2.2.6. Services Documentation Evidence for Sprint Review

En esta sección se presenta el conjunto de endpoints documentados con OpenAPI que soportan las entregas del Sprint 2 de Mushroom. Se incluye una breve introducción que resume los avances en la documentación de Web Services durante la iteración y a continuación una tabla detallada que lista cada endpoint, los verbos HTTP soportados, la sintaxis de llamada, parámetros relevantes y ejemplos de petición y respuesta. 

La documentación incorpora además esquemas (request/response), códigos de error y notas sobre contratos de datos y vigencia. Para cada entrada se indican, cuando procede, las URLs locales utilizadas en los entornos de desarrollo y enlaces a la especificación OpenAPI correspondiente.

###### Tabla 232
*Listado de Endpoints de Eventos de Mushroom*

|Método|	Descripción|	Ejemplo de llamada|Parámetros|	Respuesta|
|-|-|-|-|-|
|GET	|Lista puertos origen asociados a eventos; útil para feeds de eventos geopolíticos/navegación.	|GET /api/events/origin-ports	|Ninguno|	200 OK → ["portId1","portId2", ...]|

###### Tabla 233
*Listado de Endpoints del desglose de los Incoterms de Mushroom*

|Método	|Descripción	|Ejemplo de llamada	|Parámetros	|Respuesta|
|-|-|-|-|-|
|POST|	Calcula desglose de coste y recomienda Incoterm según parámetros comerciales y ruta.|	POST /api/incoterms/calculate
Body: { "cargoType":"", "cargoValue":0, "originPort":"P1", "destinationPort":"P2", ... }	|Body JSON con campos como cargoType, cargoValue, cargoWeight, seller, buyer, sellerCountry, buyerCountry, paymentTerms, insurance (bool), originPort, destinationPort, distance (num), etc.|	200 OK → objeto IncotermCalculationResult con marketConditions, recommendedIncoterm (code/name/description/costBreakdown), alternatives (lista), routeDetails (distance/estimatedTime/riskLevel) y warnings.|

###### Tabla 234
*Listado de Endpoints de los Puertos de Mushroom*

|Método	|Descripción	|Ejemplo de llamada|	Parámetros	|Respuesta|
|-|-|-|-|-|
|POST|	Crear un puerto con nombre, coordenadas y continente.	|POST /api/ports | Body: { "name":"Callao", "coordinates": { "latitude": -12.0, "longitude": -77.0 }, "continent":"South America" }	Body JSON: name (string), coordinates.latitude (number), coordinates.longitude (number), continent (string)	| 200 OK → { "id":"string","name":"string","coordinates":{ "latitude":0,"longitude":0 },"continent":"string" }|
|GET|	Obtener detalle de un puerto por id.|	GET /api/ports/{portId}	|Path: portId (string)	|200 OK → PortResource { id, name, coordinates, continent }|
|DELETE	|Eliminar puerto por id.	|DELETE /api/ports/{portId}|	Path: portId (string)|	200 OK → success (no content or simple status)|
|GET|	Obtener todos los puertos registrados (listado).	|GET /api/ports/all-ports|	Ninguno|	200 OK → Array de PortResource|
|GET|	Buscar puerto por nombre.|	GET /api/ports/name/{name}	|Path: name (string)|	200 OK → PortResource (o 404 si no existe)|

###### Tabla 235
*Listado de Endpoints de Rutas asignadas entre puertos de Mushroom*

|Método	|Descripción	|Ejemplo de llamada	|Parámetros	|Respuesta|
|-|-|-|-|-|
|GET|	Listar rutas registradas o históricas.	|GET /api/routes/all-routes	|Ninguno	|200 OK → Array de objetos con { id, homePort, homePortContinent, destinationPort, destinationPortContinent, distance }|
|POST	|Calcular ruta óptima entre dos puertos (A* + pesos).|	POST /api/routes/calculate-optimal-route?startPort=CALLAO&endPort=ROTTERDAM	|Query: startPort (string), endPort (string)	|200 OK → { "optimalRoute":[...], "totalDistance":0, "warnings":[...], "coordinatesMapping": { portId: { latitude, longitude } } }
|GET|	Obtener distancia entre dos puertos.|	GET /api/routes/distance-between-ports?startPort=CALLAO&endPort=ROTTERDAM	|Query: startPort (string), endPort (string)	|200 OK → { "distance": 0, "messages":["string"], "meta": { ... } }|

###### Tabla 236
*Listado de Endpoints de Inteligencia Artificial relacionadas a la predicción de estado de rutas de Mushroom*

|Método	|Descripción	|Ejemplo de llamada|	Parámetros|	Respuesta|
|-|-|-|-|-|
|POST	|Predecir demora por condiciones meteorológicas/oceanográficas entre origen y destino (modelo ML).|	POST /api/ai/predict-weather-delay| Body: { "distanceKm":1000, "cruiseSpeedKnots":20, "avgWindKnots":15, "maxWaveM":3, "departureTimeIso":"2025-11-14T10:00:00Z", "originLat":-12.0464, "originLon":-77.0428, "destLat":35.6762, "destLon":139.6503 }	Body JSON: distanceKm (num), cruiseSpeedKnots (num), avgWindKnots (num), maxWaveM (num), departureTimeIso (ISO string), originLat/Long, destLat/Long	|200 OK → Modelo devuelve predicción (estructura dependiente del modelo). En swagger original la respuesta es un objeto vacío como placeholder; en producción se espera { "estimatedDelayHours": number, "confidence": number, "factors":[...], "notes": "string" } o estructura análoga. |

#### 7.2.2.7. Software Deployment Evidence for Sprint Review

Para el desarrollo de este sprint 2 no hemos realizado ningún proceso de despliegue debido a que todas las áreas y productos respectivos ya estaban desplegados desde el sprint 1, incluyendo los modelos ONNX con respecto a la IA y la app móvil y web.

#### 7.2.1.8. Team Collaboration Insights during Sprint

Durante el Sprint 2 el equipo trabajó de forma coordinada para entregar la capa de inteligencia operacional de Mushroom con pipelines de ingestión y versionado de forecast, motor híbrido de ruteo, generación y ranking de alternativas y el pipeline de eventos con recalculo automático. 

Cada integrante aportó desde su especialidad (backend, mobile, frontend), lo que se refleja en commits, pull requests y merges documentados en los repositorios y en la ejecución de pipelines de CI. La comunicación se sostuvo mediante reuniones periódicas, revisiones de código y pair programming en tareas críticas, lo que permitió distribuir responsabilidades, resolver bloqueos rápidamente y mantener la calidad del código y la trazabilidad de las decisiones técnicas.

Además, programamos sesiones regulares de brainstorming y resolución de problemas, donde compartimos ideas y abordamos cualquier duda o dificultad que surgiera durante el proceso de desarrollo. 

###### Figura 113
*Reporte completo de contribuciones para el desarrollo del Web Application de Mushroom en el Sprint 2.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/pulse-web-app-sprint2.png" alt="Pulse for Web Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/total-contribution-web-app-sprint2.png" alt="Contribution for Web Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-application/contributors-web-app-sprint2.png" alt="Individual Contributions for Web Application">

###### Figura 114
*Reporte completo de contribuciones para el desarrollo del Mobile Application de Mushroom en el Sprint 1.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/pulse-mobile-app-sprint2.png" alt="Pulse for Mobile Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/total-contribution-mobile-app-sprint2.png" alt="Contribution for Mobile Application">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/mobile-application/contributors-mobile-app-sprint2.png" alt="Individual Contributions for Mobile Application">

###### Figura 115
*Reporte completo de contribuciones para el desarrollo del Web Services de Mushroom en el Sprint 1.*

<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/pulse-web-services-sprint2.png" alt="Pulse for Web Services">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/total-contribution-web-services-sprint2.png" alt="Contribution for Web Services">
<img src="/assets/img/chapter-VII/team-collaboration-insights/sprint1/web-services/contributors-web-services-sprint2.png" alt="Individual Contributions for Web Services"

---

## 7.3. Validation Interviews

Con el objetivo de validar las funcionalidades, beneficios y nivel de adopción potencial de la solución Mushroom, se realizaron entrevistas con personas que representan a nuestros segmentos objetivo. Estas entrevistas permitieron recopilar percepciones reales sobre la utilidad, facilidad de uso y valor percibido de la solución, así como identificar oportunidades de mejora. Las respuestas obtenidas ayudaron a confirmar hipótesis clave del producto y a ajustar el diseño en función de las necesidades y expectativas de los usuarios.

### 7.3.1. Diseño de Entrevistas

Estas son las preguntas que se le hicieron a cada entrevistado: 

1. ¿Crees que permitir a los capitanes ver información detallada del puerto (nombre, país, estado) ayudaría a tomar mejores decisiones?

2. ¿Consideras que guardar automáticamente el último viaje realizado facilitaría la evaluación y trazabilidad de las operaciones?

3. ¿Crees que ofrecer un reporte final que incluya la ruta tomada, eventos y tiempos de recorrido mejoraría la capacidad de análisis post-viaje?

5. ¿Incrementará la satisfacción del usuario la integración de un sistema de notificaciones personalizadas ante eventos críticos en rutas marítimas?

4. ¿Consideras útil que el formulario de registro incluya una lista desplegable con empresas navieras internacionales reconocidas, para validar el proceso de identificación y asociación con una organización?

6. ¿Te resultaría valioso que la plataforma calcule los costos aproximados de importación o exportación según los tipos de Incoterm, para anticipar gastos logísticos?

### 7.3.2. Registro de Entrevistas

Entrevista 1:
https://youtu.be/Y2cJzHYxXtw

 <img src="/assets/img/chapter-VII/EvidenciaEntrevista1.png" style="width:500px; height:auto;" alt="entrevista1">

Entrevista 2:
https://youtu.be/XF05WypyvtU 

 <img src="/assets/img/chapter-VII/EvidenciaEntrevista2.png" style="width:500px; height:auto;" alt="entrevista2">

Entrevista 3:
https://youtu.be/M0mf7QSNkeE

 <img src="/assets/img/chapter-VII/EvidenciaEntrevista3.png" style="width:500px; height:auto;" alt="entrevista3">

### 7.3.3. Evaluaciones según heurísticas

<center> <b> UX Heuristics & Principles Evaluation </b> </center>
<center> <b> Usability – Inclusive Design – Information Architecture </b> </center>

- **CARRERA:** Ingeniería de Software
- **CURSO:** Arquitecturas De Software Emergentes
- **SECCIÓN:** 7306
- **PROFESORES:** Ernesto Ocampo Tello
- **AUDITOR:** Teemo
- **CLIENTE:** Teemo
- **SITE o APP A EVALUAR:** Mushroom


---

### TAREAS EVALUADAS

El alcance de esta evaluación incluye las principales interacciones detectadas en las pantallas web y móviles proporcionadas:

1. Selección de puertos de origen y destino
2. Búsqueda de puertos
3. Visualización de ruta marítima
4. Interpretación de alertas geopolíticas
5. Visualización del mapa de ruta
6. Lectura de detalles de la ruta (distancia, tiempo, riesgo)
7. Visualización del desglose de Incoterms recomendados
8. Revisión de alternativas de Incoterms
9. Interpretación del porcentaje de compatibilidad de cada Incoterm
10. Consulta de costos totales y desglosados
11. Navegación hacia reportes generados
12. Uso de filtros en la sección de reportes
13. Descarga de reportes (PDF / Excel)
14. Visualización de lista de reportes
15. Acceso al detalle de cada reporte
16. Interacción con botones de acción (View / Download)
17. Uso de la sección de configuración
18. Gestión de notificaciones y modo oscuro

---

### ESCALA DE SEVERIDAD

| **Nivel** | **Descripción**                                                                        |
| --------- | -------------------------------------------------------------------------------------- |
| **1**     | Problema superficial, baja frecuencia o impacto. No urgente.                           |
| **2**     | Problema menor, afecta fluidez. Prioridad baja.                                        |
| **3**     | Problema mayor, afecta tareas clave. Alta prioridad.                                   |
| **4**     | Problema crítico, bloquea funciones esenciales. Debe corregirse antes del lanzamiento. |

---

### Tabla de Problemas Detectados

###### *Resumen de la evaluación heurística de la aplicación (web + móvil)*

| #  | Problema                                                                                                             | Severidad | Heurística violada                           |
| -- | -------------------------------------------------------------------------------------------------------------------- | --------- | -------------------------------------------- |
| 1  | Las listas de puertos no muestran cuántos resultados coinciden con la búsqueda                                       | 2         | Visibilidad del estado del sistema           |
| 2  | La selección de puertos depende del color y puede ser poco clara                                                     | 2         | Consistencia y estándares                    |
| 3  | Las alertas geopolíticas no se diferencian visualmente por nivel de riesgo                                           | 3         | Visibilidad / Reconocer situaciones críticas |
| 4  | En la vista inicial no se indica claramente que la ruta tiene múltiples puertos intermedios                          | 2         | Correspondencia entre sistema y mundo real   |
| 5  | La sección “Información de la Ruta” repite campos (distancia total) causando ruido visual                            | 1         | Estética y diseño minimalista                |
| 6  | El mapa no permite zoom ni interacción                                                                               | 3         | Control y libertad del usuario               |
| 7  | El porcentaje de compatibilidad del Incoterm no explica cómo se calcula                                              | 2         | Ayuda y documentación                        |
| 8  | El desglose de costos no muestra totales por categoría o explicación del cálculo                                     | 2         | Reconocer en lugar de recordar               |
| 9  | No hay retroalimentación después de presionar “Crear Informe”                                                        | 3         | Feedback inmediato                           |
| 10 | Los botones “Volver al formulario”, “Crear informe”, “Descargar PDF/Excel” no mantienen consistencia visual entre sí | 2         | Consistencia y estándares                    |
| 11 | El filtro de reportes no tiene etiquetas claras (solo “All”)                                                         | 2         | Claridad de acciones                         |
| 12 | En reportes, el botón “View” no indica qué información mostrará                                                      | 2         | Correspondencia sistema–mundo real           |
| 13 | El estado “Calculado” no explica si el reporte está finalizado o en borrador                                         | 2         | Visibilidad del sistema                      |
| 14 | Los reportes no muestran un icono distintivo para su tipo o estado                                                   | 1         | Visibilidad del estado del sistema           |
| 15 | El menú de configuración usa un diseño muy compacto que puede generar toques accidentales                            | 2         | Prevención de errores                        |
| 16 | No se explica qué tipo de notificaciones se habilitan                                                                | 2         | Claridad de acciones                         |
| 17 | El interruptor de modo oscuro no muestra vista previa o explicación                                                  | 1         | Ayuda y documentación                        |
| 18 | La vista de reportes no muestra paginación ni scroll infinito                                                        | 3         | Control y libertad del usuario               |


### DESCRIPCIÓN DETALLADA DE PROBLEMAS


##### **PROBLEMA #1**

**Severidad:** 2
**Heurística violada:** Visibilidad del estado del sistema

**Problema:**
La caja de búsqueda de puertos no indica cuántos resultados coinciden con el texto ingresado.

**Recomendación:**
Mostrar una etiqueta “X resultados encontrados” para apoyar la navegación.

---

##### **PROBLEMA #2**

**Severidad:** 2
**Heurística violada:** Consistencia y estándares

**Problema:**
La selección de un puerto se representa únicamente con un fondo azul tenue, lo cual puede pasar desapercibido.

**Recomendación:**
Añadir un check, borde o icono que acompañe el estado de selección.

---

##### **PROBLEMA #3**

**Severidad:** 3
**Heurística violada:** Visibilidad / Reconocer situaciones críticas

**Problema:**
Las alertas geopolíticas de los puertos son todas idénticas visualmente, aunque algunas pueden ser más graves.

**Recomendación:**
Incluir niveles de riesgo (bajo, medio, alto) con colores diferenciados.

---

##### **PROBLEMA #4**

**Severidad:** 2
**Heurística violada:** Correspondencia entre sistema y mundo real

**Problema:**
En la primera vista, la ruta no deja claro que existen puertos intermedios como Busan → Shanghai.

**Recomendación:**
Añadir una sección “Puertos intermedios” antes del mapa.

---

##### **PROBLEMA #5**

**Severidad:** 1
**Heurística violada:** Estética y diseño minimalista

**Problema:**
El campo “Distancia Total” se repite en múltiples tarjetas.

**Recomendación:**
Agrupar información redundante.

---

##### **PROBLEMA #6**

**Severidad:** 3
**Heurística violada:** Control y libertad del usuario

**Problema:**
El mapa no ofrece zoom, movimientos, ni permite ver detalles adicionales.

**Recomendación:**
Habilitar interacción táctil estándar (pan, zoom).

---

##### **PROBLEMA #7**

**Severidad:** 2
**Heurística violada:** Ayuda y documentación

**Problema:**
El 98% de compatibilidad del Incoterm no explica su cálculo.

**Recomendación:**
Añadir tooltip “¿Cómo se calcula la compatibilidad?”.

---

##### **PROBLEMA #8**

**Severidad:** 2
**Heurística violada:** Reconocer en lugar de recordar

**Problema:**
El desglose de costos es correcto, pero no explica cómo se llegó al total.

**Recomendación:**
Agregar subtotales o notas aclaratorias.

---

##### **PROBLEMA #9**

**Severidad:** 3
**Heurística violada:** Feedback inmediato

**Problema:**
Tras presionar “Crear Informe”, no hay confirmación visible.

**Recomendación:**
Incluir un loader, mensaje “Generando reporte…” o toast de éxito.

---

##### **PROBLEMA #10**

**Severidad:** 2
**Heurística violada:** Consistencia y estándares

**Problema:**
Los botones de acción con tamaños y colores distintos generan confusión visual.

**Recomendación:**
Uniformizar color primario / secundario en toda la vista.

---

##### **PROBLEMA #11**

**Severidad:** 2
**Heurística violada:** Claridad de acciones

**Problema:**
El filtro de reportes solo indica `All`, sin mostrar opciones disponibles.

**Recomendación:**
Añadir etiquetas claras: `Calculado`, `Pendiente`, `Entregado`.

---

##### **PROBLEMA #12**

**Severidad:** 2
**Heurística violada:** Correspondencia sistema–mundo real

**Problema:**
El botón “View” no deja claro qué detalle se mostrará.

**Recomendación:**
Cambiar por “Ver Detalles” o acompañar con un icono de documento.

---

##### **PROBLEMA #13**

**Severidad:** 2
**Heurística violada:** Visibilidad del estado del sistema

**Problema:**
El estado “Calculado” es ambiguo: no se sabe si significa finalizado o en progreso.

**Recomendación:**
Agregar texto complementario o tooltip.

---

##### **PROBLEMA #14**

**Severidad:** 1
**Heurística violada:** Visibilidad

**Problema:**
Los reportes no usan iconos diferenciadores para tipo, estado o prioridad.

**Recomendación:**
Agregar iconos estándar (documento, alerta, reloj, etc.).

---

##### **PROBLEMA #15**

**Severidad:** 2
**Heurística violada:** Prevención de errores

**Problema:**
En configuración, los interruptores están muy próximos entre sí y pueden generar clics accidentales.

**Recomendación:**
Aumentar separación vertical.

---

##### **PROBLEMA #16**

**Severidad:** 2
**Heurística violada:** Claridad de acciones

**Problema:**
“Habilitar notificaciones” no especifica qué tipo de alertas enviará la app.

**Recomendación:**
Añadir un subtítulo:
“Recibirás alertas de rutas, riesgos, costos y eventos importantes”.

---

##### **PROBLEMA #17**

**Severidad:** 1
**Heurística violada:** Ayuda y documentación

**Problema:**
El interruptor de modo oscuro no deja claro qué elementos cambiarán.

**Recomendación:**
Agregar una vista previa o pequeño mockup.

---

##### **PROBLEMA #18**

**Severidad:** 3
**Heurística violada:** Control y libertad del usuario

**Problema:**
La lista de reportes no incluye paginación, scroll infinito ni agrupación.

**Recomendación:**
Implementar paginación o carga progresiva.

## 7.4.  Video About-the-Product

El Video About-the-Product constituye una pieza audiovisual diseñada estratégicamente para comunicar, de manera clara y atractiva, el valor diferencial de la solución digital desarrollada. Orientado principalmente a dos públicos objetivos, los visitantes del Landing Page interesados en el modelo de negocio, y los usuarios finales de las aplicaciones que desean comprender mejor sus funcionalidades, este video sintetiza los aspectos clave del producto desde una perspectiva funcional, técnica y experiencial.

En un lenguaje accesible y alineado con el tono comunicacional de la marca, el video presenta las características principales de cada uno de los componentes desarrollados (Web Services y Aplicaciones de la Web y Mobile), destacando cómo la solución aborda los principales pain points de nuestros dos segmentos objetivos identificados.

El contenido incluye una descripción breve del modelo de negocio freemium-suscripción, las funcionalidades de identificación y presentación de rutas entre puertos, y las recomendaciones inteligentes según distintos datos externos, todo a través de la interfaz de usuario. Complementando esta explicación, se incorpora al menos un testimonio real de usuario participante en las entrevistas de validación de Mushroom, quien destaca la utilidad de la solución.

Esta sección también especifica los enlaces oficiales al video, tanto en su versión publicada en Microsoft Stream como en YouTube, esta última utilizada para su incrustación en el Landing Page. Asimismo, se detalla su duración total y se incluye un screenshot representativo del contenido audiovisual, asegurando su adecuada contextualización dentro del ecosistema digital del proyecto.

[Vídeo About-The-Product](https://youtu.be/KDW8eWmyO9s)

Duración: 5:35 minutos

###### Figura 204

_Evidencia del desarrollo del vídeo About-The-Product de Mushroom_

<img src="/assets/img/chapter-VII/about-the-product-evidence.png" alt="Video About The Product">
