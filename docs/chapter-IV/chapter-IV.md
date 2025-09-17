
# **CAPÍTULO IV: STRATEGIC-LEVEL SOFTWARE DESIGN**

## 4.1.	Strategic-Level Attribute-Driven Design.
Strategic Domain-Driven Design, o DDD estratégico es un enfoque arquitectónico que busca alinear la estructura del software con la lógica del negocio y la organización. Este enfoque es esencial para gestionar la complejidad en sistemas grandes y distribuidos, especialmente cuando múltiples equipos trabajan en diferentes partes del sistema.

Según Khononov (2021), el diseño orientado al dominio enfatiza la creación de contextos delimitados ("bounded contexts") que actúan como fronteras explícitas para mantener la coherencia del modelo en cada subdominio, así como el establecimiento de un lenguaje ubicuo ("ubiquitous language") compartido entre los equipos técnicos y los expertos del negocio para asegurar una comunicación precisa y libre de ambigüedades (Khononov, 2021).

Vernon (2016) propone una clara distinción entre dos espacios complementarios: el espacio del problema, dedicado a comprender en profundidad las necesidades y restricciones del negocio, y el espacio de la solución, enfocado en diseñar y aplicar patrones técnicos y arquitectónicos que respondan eficazmente a esos requerimientos. Esta división permite alinear la estrategia empresarial con las decisiones de diseño de software (Vernon, 2016).

Para abordar las decisiones estratégicas en el diseño de software utilizando Domain-Driven Design (DDD), el equipo ha implementado un proceso estructurado que combina técnicas colaborativas y herramientas visuales. Este enfoque facilita la identificación de límites naturales dentro del dominio del negocio, conocidos como Bounded Contexts, y promueve una comprensión compartida entre todos los participantes. 
### 4.1.1.	Design Purpose.

El propósito del diseño de Mushroom, solución desarrollada por Teemo Solutions, es responder a la creciente complejidad del comercio marítimo internacional, marcada por disrupciones geopolíticas, cierres de rutas estratégicas y condiciones climáticas adversas. En este contexto, el diseño de la arquitectura de la solución se orienta a proporcionar un sistema robusto, escalable y adaptable, capaz de integrar fuentes de datos heterogéneas y ofrecer a los usuarios información confiable en tiempo real.

La finalidad central del proceso de diseño es alinear la solución con la problemática identificada: la falta de herramientas integradas que permitan a navieras, operadoras logísticas y exportadores/importadores tomar decisiones proactivas ante interrupciones de las rutas. A través de un enfoque predictivo y modular, el diseño busca minimizar riesgos operativos, optimizar recursos y garantizar la continuidad de las cadenas de suministro globales.

Asimismo, el diseño se orienta a satisfacer las necesidades específicas de los segmentos objetivo:

- Para las empresas navieras y operadoras logísticas, se prioriza la capacidad de simular rutas, gestionar riesgos y optimizar la eficiencia operativa.
- Para los exportadores e importadores de alta rotación, el diseño asegura visibilidad en tiempo real, confiabilidad de datos y previsibilidad en las entregas, aspectos clave para mantener su competitividad.

En términos de negocio, el diseño persigue consolidar a Mushroom como una plataforma SaaS diferencial en el mercado, ofreciendo un valor agregado basado en la integración de múltiples variables críticas (clima, conflictos, tráfico marítimo y cierres portuarios). De este modo, el propósito del diseño no solo radica en la creación de una solución tecnológica, sino en fortalecer la resiliencia del comercio internacional mediante decisiones más ágiles, informadas y sostenibles.

### 4.1.2.	Attribute-Driven Design Inputs.

El proceso de Attribute-Driven Design (ADD) requiere identificar de manera explícita los insumos que guiarán las decisiones arquitectónicas de la solución. Estos inputs permiten alinear el diseño con la problemática detectada, garantizar el cumplimiento de los objetivos de negocio y atender de forma directa las necesidades de los segmentos objetivo.

En esta sección se presentan los tres tipos de insumos clave para el proceso de diseño:

- **Restricciones de diseño**

    Definen los límites dentro de los cuales debe construirse la solución, considerando factores tecnológicos, regulatorios, de integración o de recursos.

- **Requisitos funcionales**

    Especifican las capacidades principales que el sistema debe ofrecer para resolver los problemas identificados y entregar valor a los usuarios.

- **Requisitos de atributos de calidad**

    Describen los criterios no funcionales que garantizan el desempeño esperado del sistema, como disponibilidad, escalabilidad, seguridad o interoperabilidad, fundamentales en el contexto del comercio marítimo global.
#### 4.1.2.1.	Primary Functionality (Primary User Stories).

Las funcionalidades primarias de Mushroom se centran en garantizar que la solución cumpla con los requisitos funcionales más relevantes para la arquitectura y los segmentos objetivo. Estas funcionalidades fueron priorizadas porque representan la base para la planificación inteligente de rutas, el monitoreo en tiempo real, la gestión de riesgos, la interacción intuitiva del usuario y la generación de reportes operativos.

A continuación, se detallan los Epics y User Stories clave, con su respectiva relación a los objetivos arquitectónicos de la solución:

>Cabe señalar que este cuadro no constituye una duplicación del listado de User Stories del capítulo de Requirements. En este apartado se presentan únicamente aquellas Epics y User Stories cuya relevancia incide directamente en las decisiones de diseño arquitectónico.

| Epic / User Story ID | Título | Descripción | Criterios de Aceptación | Relacionado con (Epic ID) |
|----------------------|--------|-------------|--------------------------|---------------------------|
| **EPIC001** | Planificación Inteligente de Rutas Marítimas | Como desarrollador, quiero implementar un sistema que calcule rutas seguras y eficientes usando A*, considerando clima, cierres y peligrosidad. | Se debe garantizar que el sistema pueda calcular rutas seguras y eficientes considerando múltiples variables. | Epic principal (macro-funcionalidad) |
| **US001** | Sugerir ruta óptima | Como capitán, quiero que el sistema sugiera automáticamente la ruta más corta y segura según el algoritmo, para llegar eficientemente al puerto destino. | El sistema debe sugerir una ruta válida basada en los nodos del grafo considerando peligrosidad, clima y distancia. | EPIC001 |
| **US007** | Comprender la lógica detrás de la ruta seleccionada | Como empresario, quiero entender por qué se eligió una ruta determinada, para asegurarme de que se tomó una decisión eficiente y segura. | El sistema debe mostrar justificaciones como menor tiempo, menos emisiones, o evitar zonas bloqueadas. | EPIC001 |
| **EPIC002** | Monitoreo en Tiempo Real y Gestión Dinámica | Como desarrollador, quiero permitir a los usuarios seguir sus rutas en tiempo real y adaptar el trayecto ante eventos inesperados. | El sistema debe permitir monitoreo continuo y recalculo de rutas dinámico. | Epic principal (macro-funcionalidad) |
| **US005** | Recalcular ruta dinámicamente | Como capitán, quiero que el sistema recalcule la ruta si hay cambios inesperados durante la navegación. | Ante cambio de estado en una arista del grafo (por cierre o clima), debe generarse una nueva ruta sin intervención manual. | EPIC002 |
| **US006** | Visualizar posición actual del buque | Como empresario, quiero poder ver en tiempo real la ubicación del barco, para tener visibilidad del estado del envío. | La app debe mostrar la posición actual del buque usando coordenadas GPS integradas. | EPIC002 |
| **EPIC003** | Visualización y Reporte de Información | Como desarrollador, quiero que los usuarios puedan ver y descargar métricas operativas como tiempo, emisiones y consumo por viaje. | El sistema debe almacenar métricas y generar reportes accesibles para los usuarios. | Epic principal (macro-funcionalidad) |
| **US004** | Guardar datos del viaje completado | Como capitán, quiero que se guarden los datos del viaje realizado, para poder revisarlos o reportarlos al finalizar. | El sistema debe registrar tiempo, puerto de salida y llegada, consumo estimado y eventos ocurridos. | EPIC003 |
| **US009** | Obtener reporte del envío | Como empresario, quiero ver un informe al final del envío con los datos operativos, para evaluar el desempeño del servicio contratado. | El sistema debe generar un reporte descargable con tiempo total, ruta usada, eventos registrados y emisiones estimadas. | EPIC003 |
| **US010** | Visualizar historial de rutas contratadas | Como empresario, quiero ver un historial de rutas utilizadas en envíos pasados, para poder tomar decisiones basadas en evidencia. | El sistema debe listar todos los envíos previos con sus datos asociados, y permitir filtrado por fecha, destino o tipo de embarcación. | EPIC003 |
| **EPIC004** | Interacción del Usuario en Aplicación | Como desarrollador, quiero diseñar una interfaz web/móvil que permita a los capitanes y empresarios interactuar intuitivamente con Teemo. | La interfaz debe ser intuitiva, accesible y funcionar en dispositivos web y móviles. | Epic principal (macro-funcionalidad) |
| **EPIC005** | Notificaciones y Gestión de Riesgos | Como desarrollador, quiero implementar un sistema de alertas proactivas sobre riesgos marítimos o cierres de rutas, basado en eventos reales. | El sistema debe generar alertas automáticas y notificaciones oportunas ante riesgos o bloqueos. | Epic principal (macro-funcionalidad) |
| **US002** | Notificar eventos que afecten la ruta | Como capitán, quiero recibir alertas si una ruta se vuelve no viable, para evitar zonas bloqueadas o peligrosas. | Si una arista del grafo cambia a estado no viable, debe generarse una notificación y recalcular ruta automáticamente. | EPIC005 |
| **US003** | Mostrar clima proyectado en ruta | Como capitán, quiero ver la información climática relevante en mi ruta, para anticipar condiciones que puedan retrasar el viaje. | El sistema debe integrar datos climáticos externos y mostrarlos como superposición o información por tramo de ruta. | EPIC005 |
| **US008** | Recibir notificaciones de cambios en la entrega | Como empresario, quiero recibir alertas si hay desvíos o retrasos, para poder informar a mi equipo o ajustar operaciones. | Si el sistema recalcula la ruta, debe notificarse al usuario mediante la plataforma con motivo y nuevo ETA. | EPIC005 |


#### 4.1.2.2.	Quality attribute Scenarios.
#### 4.1.2.3.	Constraints.
### 4.1.3.	Architectural Drivers Backlog.
### 4.1.4.	Architectural Design Decisions.
### 4.1.5.	Quality Attribute Scenario Refinements.
## 4.2.	Strategic-Level Domain-Driven Design.
### 4.2.1.	EventStorming.
### 4.2.2.	Candidate Context Discovery.
### 4.2.3.	Domain Message Flows Modeling.
### 4.2.4.	Bounded Context Canvases.
### 4.2.5.	Context Mapping.
## 4.3.	Software Architecture.
### 4.3.1.	Software Architecture System Landscape Diagram.
### 4.3.1.	Software Architecture Context Level Diagrams.
### 4.3.2.	Software Architecture Container Level Diagrams.
### 4.3.3.	Software Architecture Deployment Diagrams.
