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

# Capítulo III: Requirements Specification

Este capítulo establece de manera precisa la especificación de requisitos de Macetech, incorporando prácticas consolidadas en el análisis de requisitos. Siguiendo el marco propuesto por Robertson, Robertson y Reed (2024) en Mastering the Requirements Process, se adopta un enfoque estructurado que abarca la obtención, modelado y priorización de necesidades, con el propósito de elaborar un documento de requisitos que cumpla con criterios de claridad, completitud, consistencia, trazabilidad y capacidad de modificación. El punto de partida es un análisis detallado de los resultados obtenidos en la fase de investigación, que incluye estudios de usuarios, procesos de needfinding y análisis competitivo, desde los cuales se construye la estructura conceptual que servirá de base para todo el desarrollo. Como enfoque metodológico, se presentan las secciones de To-Be Scenario Mapping, User Stories, Impact Map y Product Backlog, lo que asegura un ciclo de vida del producto flexible y centrado en la entrega continua de valor.

## 3.1. To-Be Scenario Mapping

En esta sección se documenta el proceso metodológico y los resultados obtenidos del To-Be Scenario Mapping, una herramienta clave para diseñar la experiencia futura de cada User Persona y compararla con el escenario actual (As-Is). A partir de un análisis detallado de los mapas As-Is, se proyectan las acciones, pensamientos y emociones del usuario a través de las columnas Steps, Doing, Thinking y Feeling, de manera que quede claro cómo Macetech transformará cada etapa de la interacción.

El procedimiento seguido por el equipo incluyó las siguientes etapas, alineadas con las recomendaciones de Kalbach (2020) para el mapeo de experiencias:

1. Preparación: Revisión exhaustiva de los mapas As-Is existentes y definición del alcance para cada User Persona.

2. Lluvia de ideas individual: Generación de propuestas de mejora enfocadas en optimizar actividades, percepciones y motivaciones del usuario.

3. Revisión colaborativa: Consolidación de ideas, identificación de fases clave como columnas del mapa y validación de su relevancia.

4. Nombramiento de fases: Asignación de títulos descriptivos a cada columna, representando los estados ideales del flujo de interacción.

5. Comparación As-Is vs. To-Be: Identificación y análisis de las diferencias más significativas, destacando las innovaciones y beneficios esperados en términos de eficiencia, usabilidad y satisfacción.

A continuación se presentan capturas de los mapas To-Be Scenario Mapping generados en la herramienta asignada para cada User Persona, con sus respectivas filas Steps, Doing, Thinking y Feeling, que muestran de forma clara las mejoras proyectadas en la experiencia del usuario.

###### Figura 19
*To-Be Scenario Mapping de nuestro segmento de agencias de embarcaciones navieras*

<td><img src="../../assets/img/chapter-III/to-be-shipping-agency.png" style="width:1000px; height:auto;" alt=""></td>

###### Figura 20
*To-Be Scenario Mapping de nuestro segmento de transportistas marítimos*

<td><img src="../../assets/img/chapter-III/to-be-maritime-carrier.png" style="width:1000px; height:auto;" alt=""></td>

## 3.2. User Stories

En esta sección se describe la estructura y el propósito de nuestras User Stories y Epics, que formalizan los requisitos identificados a lo largo del ciclo de vida de Mushroom. El objetivo es traducir las necesidades y expectativas de los segmentos objetivos, así como los visitantes de la Landing Page y desarrolladores, en historias accionables, asegurando la satisfacción total de los usuarios finales. Cada Epic agrupa funcionalidades de alto nivel y sirve como un contenedor lógico para un conjunto de User Stories, mientras que estas últimas representan incrementos de valor independientes y verificables. Cada historia será acompañada de criterios de aceptación escritos en formato Gherkin (Given–When–Then), lo que permite una definición precisa y verificable de las condiciones para considerar un éxito.

El mapeo de Epics y User Stories seguirá las mejores prácticas de User Story Mapping, ayudándonos a "descubrir la historia completa" y a "construir el producto correcto" (Patton, 2021). Comenzaremos con un listado organizado de Epics que abarcan tanto la experiencia web, móvil y Landing Page con contenido segmentado para visitantes generales y subgrupos específicos. Luego, desglosaremos cada Epic en User Stories orientadas al usuario, y Technical Stories dirigidas al equipo de desarrollo, cubriendo tanto la interacción final como los requisitos de infraestructura.

Para garantizar la calidad y efectividad de nuestras historias, aplicaremos las recomendaciones de Stevenson (2020) sobre la redacción de User Stories y criterios de aceptación. Cada historia describirá el rol, la acción y el beneficio esperado, y sus criterios se mantendrán en tiempo presente, en tercera persona, sin referencias de interfaz, para asegurar que sean neutrales y evaluables. De esta manera, aseguramos que todo comportamiento previsto quede claramente definido y sea verificable.

| **Epic / Story ID** | **Título**                                   | **Descripción**                                                                                                                                  | 
|---------------------|----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| EPIC001             | Planificación Inteligente de Rutas Marítimas | Como desarrollador, quiero implementar un sistema que calcule rutas seguras y eficientes usando A*, considerando clima, cierres y peligrosidad. | 
| EPIC002             | Monitoreo en Tiempo Real y Gestión Dinámica  | Como desarrollador, quiero permitir a los usuarios seguir sus rutas en tiempo real y adaptar el trayecto ante eventos inesperados.              | 
| EPIC003             | Visualización y Reporte de Información       | Como desarrollador, quiero que los usuarios puedan ver y descargar métricas operativas como tiempo, emisiones y consumo por viaje.              |
| EPIC004             | Interacción del Usuario en Aplicación        | Como desarrollador, quiero diseñar una interfaz web/móvil que permita a los capitanes y empresarios interactuar intuitivamente con Teemo.       |
| EPIC005             | Notificaciones y Gestión de Riesgos          | Como desarrollador, quiero implementar un sistema de alertas proactivas sobre riesgos marítimos o cierres de rutas, basado en eventos reales.   |

Las User Stories son una herramienta fundamental para definir los requisitos del proyecto. Cada User Story incluye criterios de aceptación que deben ser comprobables y redactados en tiempo presente, tercera persona, siguiendo la estructura de Gherkin (Given-When-Then). Además, se consideran User Stories para el sitio web estático (Landing Page) y Technical Stories para los features del RESTful API.

###### Tabla 11
Listado de épicas e historias de usuario a desarrollar en el proyecto de Mushroom

| **Epic / Story ID** | **Título**                                                | **Descripción**                                                                                                                                             | **Criterios de Aceptación**                                                                                                                                                         | **Relacionado con (Epic ID)** |
|---------------------|-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| US001               | Sugerir ruta óptima                                 | Como capitán, quiero que el sistema sugiera automáticamente la ruta más corta y segura según el algoritmo, para llegar eficientemente al puerto destino. | El sistema debe sugerir una ruta válida basada en los nodos del grafo considerando peligrosidad, clima y distancia.                                                                 | EPIC001                       |
| US002               | Notificar eventos que afecten la ruta                     | Como capitán, quiero recibir alertas si una ruta se vuelve no viable, para evitar zonas bloqueadas o peligrosas.                                           | Si una arista del grafo cambia a estado no viable, debe generarse una notificación y recalcular ruta automáticamente.                                                               | EPIC005                       |
| US003               | Mostrar clima proyectado en ruta                          | Como capitán, quiero ver la información climática relevante en mi ruta, para anticipar condiciones que puedan retrasar el viaje.                           | El sistema debe integrar datos climáticos externos y mostrarlos como superposición o información por tramo de ruta.                                                                  | EPIC005                       |
| US004               | Guardar datos del viaje completado                        | Como capitán, quiero que se guarden los datos del viaje realizado, para poder revisarlos o reportarlos al finalizar.                                       | El sistema debe registrar tiempo, puerto de salida y llegada, consumo estimado y eventos ocurridos.                                                                                  | EPIC003                       |
| US005               | Recalcular ruta dinámicamente                             | Como capitán, quiero que el sistema recalcule la ruta si hay cambios inesperados durante la navegación.                                                    | Ante cambio de estado en una arista del grafo (por cierre o clima), debe generarse una nueva ruta sin intervención manual.                                                           | EPIC002                       |
| US006               | Visualizar posición actual del buque                      | Como empresario, quiero poder ver en tiempo real la ubicación del barco, para tener visibilidad del estado del envío.                                      | La app debe mostrar la posición actual del buque usando coordenadas GPS integradas.                                                                                                  | EPIC002                       |
| US007               | Comprender la lógica detrás de la ruta seleccionada       | Como empresario, quiero entender por qué se eligió una ruta determinada, para asegurarme de que se tomó una decisión eficiente y segura.                   | El sistema debe mostrar justificaciones como menor tiempo, menos emisiones, o evitar zonas bloqueadas.                                                                               | EPIC001                       |
| US008               | Recibir notificaciones de cambios en la entrega           | Como empresario, quiero recibir alertas si hay desvíos o retrasos, para poder informar a mi equipo o ajustar operaciones.                                  | Si el sistema recalcula la ruta, debe notificarse al usuario mediante la plataforma con motivo y nuevo ETA.                                                                          | EPIC005                       |
| US009               | Obtener reporte del envío                                 | Como empresario, quiero ver un informe al final del envío con los datos operativos, para evaluar el desempeño del servicio contratado.                     | El sistema debe generar un reporte descargable con tiempo total, ruta usada, eventos registrados y emisiones estimadas.                                                              | EPIC003                       |
| US010               | Visualizar historial de rutas contratadas                 | Como empresario, quiero ver un historial de rutas utilizadas en envíos pasados, para poder tomar decisiones basadas en evidencia.                          | El sistema debe listar todos los envíos previos con sus datos asociados, y permitir filtrado por fecha, destino o tipo de embarcación.                                               | EPIC003                       |

##### 3.3. Impact Mapping.

##### Segmento 1:
<td><img src="../../assets/img/chapter-III/Impact-Mapping-2.png" style="width:1000px; height:auto;" alt=""></td>

##### Segmento 2: Capitán o Jefe de Navegación
<td><img src="../../assets/img/chapter-III/Impact-Mapping-1.png" style="width:1000px; height:auto;" alt=""></td>

##### 3.4. Product Backlog.
# **Product Backlog - Funcionalidades de Teemo**

# **Product Backlog - Funcionalidades de Teemo**

| **ID** | **Título** | **Descripción (Formato User Story)** | **Story Points** |
|-------|-------------|---------------------------------------|------------------|
| US01 | Visualizar lista de puertos disponibles | Como usuario, quiero visualizar una lista de puertos disponibles para poder saber por donde no puedo navegar. | 8 |
| US02 | Mostrar ruta más corta entre dos puertos | Como usuario, quiero que el sistema calcule y muestre la ruta más corta entre dos puertos, para optimizar el tiempo de viaje. | 8 |
| US03 | Permitir seleccionar puerto de origen y destino | Como usuario, quiero seleccionar manualmente el puerto de salida y el de llegada para personalizar mi trayecto. | 8 |
| US04 | Mostrar información básica del viaje | Como usuario, quiero visualizar información básica del viaje como tiempo estimado y cantidad de nodos recorridos para tener control de mi navegación. | 2 |
| US05 | Reporte de navegación | Como usuario, quiero recibir un reporte final de mi viaje para analizar la ruta tomada, eventos ocurridos y tiempos de recorrido. | 3 |
| US06 | Visualizar mapa esquemático de los puertos | Como usuario, quiero ver un mapa esquemático de los puertos para entender gráficamente el trayecto. | 3 |
| US07 | Guardar último viaje realizado | Como usuario, quiero guardar el último viaje realizado para poder revisarlo posteriormente y evaluar mi desempeño. | 2 |
| US08 | Ver información del puerto actual | Como capitán, quiero ver información de los puertos, para evaluar si puedo detenerme.El sistema debe mostrar nombre, país y estado (abierto/cerrado) de los puertos. | 5 |
| US09 | Iniciar sesión | Como usuario registrado, quiero iniciar sesión para acceder a mi cuenta para usar el programa | 2 |
| US10 | Registrar un usuario | Como nuevo usuario, quiero registrarme en la plataforma para poder acceder a todas sus funcionalidades | 2 |
| US11 | Puertos intermedios | Como capitan, quiero  poder añadir puertos intermedios a la ruta para poder redirigirme correctamente a el por si existe alguna emergencia. | 8 |
| US12 | Historial de rutas |  Como capitán, quiero guardar una ruta personalizada después de calcularla, para reutilizarla en futuros viajes similares. | 5 |
| US13 | Rutas más Buscadas |  Como usuario, quiero poder visualizar las rutas mas buscadas entre los demas usuarios, para para ver si una coincide con la que estoy buscando. | 5 |
| US14 | Cálculo de Incoterms |  Como usuario, quiero poder calcular el monto total que me costará una importacion o exportacion, para poder armar un presupuesto acorde a la operación. | 8 |
| US15 | Cálculo de distancia |  Como usuario, quiero poder visualizar la distancia total que se recorre entre los puertos de origen, intermedios, y destino, para poder tomar dimension del tiempo que llevará el trayecto. | 3 |
| US16 | Preferencia de notificaciones |  Como usuario, quiero poder elegir las notificaciones que me interesan recibir, como cierres de ruta o alertas de clima en distintas zonas, para poder tener en cuenta estos factores al elegir la ruta que quiero seguir. | 3 |
