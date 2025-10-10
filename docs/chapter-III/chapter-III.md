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

| **Epic / Story ID** | **Título** | **Descripción** | **Criterios de aceptación** | **Relacionado con (Epic ID)** |
|---------------------|------------|-----------------|-----------------------------|--------------------------|
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

## 3.3. Requisitos Funcionales

| **ID** | **Actor** | **Descripción** |
|--------|-----------|-----------------|
| RF001 | Agencias de embarcaciones navieras / Exportadores e importadores de alta rotación | El sistema debe permitir al visitante acceder a la landing page pública con contenido informativo sobre la propuesta de valor, casos de uso y formulario de contacto (contenido estático). | 
| RF002 | Agencias de embarcaciones navieras / Exportadores e importadores de alta rotación | El sistema debe permitir al visitante entrar directamente a la Single Page Application a través de un Call-to-Action en la sección de encabezado, después de mostrar las funcionalidades y antes de llegar al footer. |
| RF003 | Agencias de embarcaciones navieras / Exportadores e importadores de alta rotación | El sistema debe permitir a un usuario registrarse creando una cuenta con email válido y contraseña que cumpla políticas mínimas (longitud mínima de 8 caracteres, letras minúsculas y mayúsculas, un número y un símbolo), y enviar un correo de verificación para activar la cuenta. |
| RF004 | Agencias de embarcaciones navieras / Exportadores e importadores de alta rotación | El sistema debe permitir al usuario iniciar sesión con credenciales válidas y, tras autenticación exitosa, emitir token de sesión con roles asociados. | 
| RF005 | Agencias de embarcaciones navieras | El sistema debe permitir listar todos los puertos registrados con su estado operativo (operativo / cerrado / restringido) y metadatos básicos: nombre, continente, latitud y longitud. |
| RF006 | Agencias de embarcaciones navieras | El sistema debe permitir buscar y seleccionar un puerto origen y un puerto destino válidos para iniciar el cálculo de rutas, validando que ambos pertenezcan al grafo de navegación y no sean idénticos. |
| RF007 | Agencias de embarcaciones navieras | El sistema debe calcular la ruta optimizada mediante criterio múltiple entre origen y destino. El objetivo del multi-criterio es minimizar la distancia en millas náuticas y minimizar el puntaje de riesgo. Debe devolver nodos, distancia total en nm y ETA. La implementación debe  documentar que la prioridad operacional es distancia mínima junto al menor riesgo. | 
| RF008 | Agencias de embarcaciones navieras | El sistema debe presentar, junto con la ruta calculada, un desglose con distancia total de la ruta, tiempo estimado, combustible usado estimado y posible riesgo. | 
| RF009 | Agencias de embarcaciones navieras | El sistema debe devolver las top-3 alternativas para el caso, evaluadas por la el modelo de Inteligencia (AI/algoritmo) priorizando menor distancia y menor riesgo, e incluir métricas comparativas (ETA, distancia, riesgo).
| RF010 | Agencias de embarcaciones navieras | El sistema debe permitir al usuario solicitar una justificación cuantitativa de por qué una ruta fue elegida frente a otra, devolviendo valores numéricos del total de la ruta en una pequeña notificación. | 
| RF011 | Agencias de embarcaciones navieras | El sistema debe almacenar automáticamente el último viaje realizado en el historial para futura consulta. Se debe mantener registros de tiempo de nombre, tiempo de inicio, tiempo de fin, ruta usada con puerto origen y destino, distancia recorrida (nm) y emisiones. | 
| RF012 | Agencias de embarcaciones navieras | El sistema debe permitir al usuario generar un reporte descargable de cada uno de los viajes realizados en la aplicación (PDF/CSV), los cuales deben mostrar el tipo de inicio, tiempo de fin, ruta usada con puerto origen y destino, distancia (nm) y emisiones detalladas. | 
| RF013 | Agencias de embarcaciones navieras | El sistema debe exponer un historial de rutas que permita filtrar por fecha, origen y destino, y paginar resultados para consultas de gran volumen. | 
| RF014 | Agencias de embarcaciones navieras | El sistema debe consultar las restricciones del puerto según su estado operativo y rechazar automáticamente la inclusión de un puerto de llegada no apto, informando una breve justificación (texto corto) del motivo. |
| RF015 | Agencias de embarcaciones navieras | El sistema debe detectar eventos externos (cierres de puerto, incidentes, cambios de estado, forecast) y recalcular automáticamente la ruta activa cuando su viabilidad cambie. Se debe registrar la nueva ruta sugerida y la diferencia de métricas. | 
| RF016 | Agencias de embarcaciones navieras | El sistema debe permitir a cada usuario configurar preferencias de notificaciones (tipos de alertas y canales) y aplicar dichas preferencias a las entregas de notificaciones. | 
| RF017 | Agencias de embarcaciones navieras | El sistema debe permitir consultar la ficha de un puerto seleccionado en el mapa, devolviendo: nombre, continente y estado operativo con restricciones. Las restricciones incluirán una breve justificación. | 
| RF018 | Agencias de embarcaciones navieras | El sistema debe visualizar la geometría de la ruta y los identificadores de tramo para renderizar mapas y mostrar una animación esperada del viaje. | 
| RF019 | Agencias de embarcaciones navieras | El sistema debe ofrecer funcionalidad de “Rutas más buscadas” que agregue y devuelva las rutas más consultadas por otros usuarios durante un período configurable, permitiendo filtrado por continente o puertos específicos. |
| RF020 | Exportadores e importadores de alta rotación | El sistema debe calcular el coste estimado completo asociado a una operación (incoterms) cuando el usuario proporcione parámetros (peso, valor de la mercadería, incoterm preferible, origen/destino), devolviendo desglose de flete, seguros y total estimado, además del Incoterm recomendado según los datos. | 
| RF021 | Agencias de embarcaciones navieras / Exportadores e importadores de alta rotación | El sistema debe ingerir pronósticos meteorológicos y datos oceanográficos, mapearlos a aristas del grafo y marcar su validez para que los consumidores usen la versión más reciente o el último forecast válido (y afectar tiempos/riesgo donde corresponda).| 

## 3.4. Requisitos No Funcionales

| **ID** | **Categoría (QA)** | **Descripción** |
|--------|--------------------|-----------------|
| RNF001 | Rendimiento | El tiempo de respuesta de todas las páginas de la aplicación debe ser de 2.0 segundos como máximo. Para peticiones en base a las funcionalidades de cálculo de rutas y valores predictivos, debe ser 5.0 segundos como máximo. Ambas métricas son bajo una carga de 100 peticiones concurrentes. |
| RNF002 | Usabilidad | El sistema debe permitir que el 90% de los usuarios objetivos completen las tareas relacionadas a funcionalidades principales (calcular ruta, puntaje de rutas, ver tiempo estimado de llegada) en un máximo de tres pasos o interacciones dentro de la aplicación, tanto en web como en móvil. |
| RNF003 | Disponibilidad | El sistema debe garantizar una disponibilidad del 99 % mensual para los servicios de funcionalidades principales (calcular ruta, puntaje de rutas, ver tiempo estimado de llegada) durante el horario de operación 24/7. Las ventanas planificadas de mantenimiento no contabilizan disponibilidad siempre que se notifiquen con al menos 72 horas de antelación. |
| RNF004 | Seguridad | Toda la información sensible y las claves secretas deben almacenarse cifradas utilizando el estándar Advanced Encryption Standard (AES) con claves de 256 bits, y las comunicaciones entre componentes deben emplear TLP; no se debe almacenar ninguna contraseña en texto plano. |
| RNF005 | Mantenimiento | El tiempo medio para recuperar el servicio ante un fallo crítico operativo, medido desde la detección hasta la restauración o mitigación inicial, no debe exceder los 30 minutos. Este tiempo incluye la activación de procedimientos de respuesta y la aplicación de la corrección o el cambio de configuración necesario. |
| RNF006 | Escalabilidad | La arquitectura debe poder escalar la capa de cálculo de rutas y el servicio de estimación de tiempos y riesgos de modo que soporten aumentos de demanda del 75% y un aumento del 50% en el volumen de datos sin que el tiempo de respuesta de las funciones exceda los 5.0 segundos para el 90% de solicitudes. |
| RNF007 | Fiabilidad | La tasa de errores en procesos de cálculo de rutas y estimación de riesgos (Tanto en la ruta principal como en las rutas alternativas) no debe ser superior al 0.5% del total de cálculos en cualquier periodo mensual. Si se sobrepasa este umbral, el sistema debe generar una alerta crítica y abrir un incidente de operación.|
| RNF008 | Privacidad | Los datos personales deben tratarse conforme a la política interna de privacidad de la aplicación. Deben retenerse durante un periodo predeterminado de 2 años y deben estar disponibles para su eliminación por solicitud del titular dentro de 30 días hábiles y todos los accesos a datos personales deben registrarse con identificación del solicitante y motivo.|
| RNF009 | Accesibilidad | Las vistas críticas de la solución desplegadas en la web y en la aplicación móvil deben cumplir los criterios de accesibilidad de nivel AA de las directrices de contenido accesible para la web, con un puntaje mínimo de 90%. La conformidad se verificará mediante auditorías automatizadas y pruebas manuales con usuarios.|
| RNF010 | Integridad de datos | La plataforma debe garantizar la integridad de los datos expuestos en la aplicación y datos ingresados por los usuarios o APIs externas, de forma que el porcentaje de pérdida o corrupción detectada en la ingestión no supere el 0.05% durante observación de 24 horas. Se debe tener un registro de estados para verificar la integridad en todo momento. |
| RNF011 | Compatibilidad | La plataforma debe ser compatible con los entornos y fuentes de datos más utilizados por los usuarios finales. Específicamente, debe operar correctamente en Google Chrome, Mozilla FireFox, Microsoft Edge, por parte de escritorio, y en móvil debe operar tanto en Android como iOS. La comprobación se realizará con pruebas de integración automática. Al menos el 90% de las pruebas de compatibilidad deben pasar sin intervención manual. |

## 3.5. Impact Mapping

##### Segmento 1:
<td><img src="../../assets/img/chapter-III/Impact-Mapping-2.png" style="width:1000px; height:auto;" alt=""></td>

##### Segmento 2: Capitán o Jefe de Navegación
<td><img src="../../assets/img/chapter-III/Impact-Mapping-1.png" style="width:1000px; height:auto;" alt=""></td>

##### 3.4. Product Backlog

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
