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
##### 3.1. To-Be Scenario Mapping.
###### Segmento 1: Agencia de embarcaciones navieras

<td><img src="../../assets/img/chapter-III/TO-BE_1.png" style="width:1000px; height:auto;" alt=""></td>

###### Segmento 2: Transportista marítimo

<td><img src="../../assets/img/chapter-III/TO-BE_2.png" style="width:1000px; height:auto;" alt=""></td>

##### 3.2. User Stories.

Tabla de épicas establecidas para las historias de usuarios de TeemoSolutions

| **Epic / Story ID** | **Título**                                   | **Descripción**                                                                                                                                  | 
|---------------------|----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| EPIC001             | Planificación Inteligente de Rutas Marítimas | Como desarrollador, quiero implementar un sistema que calcule rutas seguras y eficientes usando A*, considerando clima, cierres y peligrosidad. | 
| EPIC002             | Monitoreo en Tiempo Real y Gestión Dinámica  | Como desarrollador, quiero permitir a los usuarios seguir sus rutas en tiempo real y adaptar el trayecto ante eventos inesperados.              | 
| EPIC003             | Visualización y Reporte de Información       | Como desarrollador, quiero que los usuarios puedan ver y descargar métricas operativas como tiempo, emisiones y consumo por viaje.              |
| EPIC004             | Interacción del Usuario en Aplicación        | Como desarrollador, quiero diseñar una interfaz web/móvil que permita a los capitanes y empresarios interactuar intuitivamente con Teemo.       |
| EPIC005             | Notificaciones y Gestión de Riesgos          | Como desarrollador, quiero implementar un sistema de alertas proactivas sobre riesgos marítimos o cierres de rutas, basado en eventos reales.   |

Las User Stories son una herramienta fundamental para definir los requisitos del proyecto. Cada User Story incluye criterios de aceptación que deben ser comprobables y redactados en tiempo presente, tercera persona, siguiendo la estructura de Gherkin (Given-When-Then). Además, se consideran User Stories para el sitio web estático (Landing Page) y Technical Stories para los features del RESTful API.


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
| US01 | Visualizar lista de puertos disponibles | Como usuario, quiero visualizar una lista de puertos disponibles para poder seleccionar el puerto de origen y destino en mi navegación. | 1 |
| US02 | Mostrar ruta más corta entre dos puertos | Como usuario, quiero que el sistema calcule y muestre la ruta más corta entre dos puertos, para optimizar el tiempo de viaje. | 5 |
| US03 | Permitir seleccionar puerto de origen y destino | Como usuario, quiero seleccionar manualmente el puerto de salida y el de llegada para personalizar mi trayecto. | 2 |
| US04 | Simular cierre de puerto en la ruta | Como administrador, quiero poder simular el cierre de un puerto o tramo para evaluar el impacto en la navegación y planificar alternativas. | 3 |
| US05 | Notificar al usuario si la ruta es afectada | Como usuario, quiero recibir notificaciones cuando un cierre afecte mi ruta, para poder actuar rápidamente y evitar retrasos. | 2 |
| US06 | Recalcular la ruta en caso de cierre | Como usuario, quiero que el sistema recalcule automáticamente la mejor ruta disponible cuando ocurra un cierre, para seguir avanzando sin interrupciones. | 5 |
| US07 | Mostrar información básica del viaje | Como usuario, quiero visualizar información básica del viaje como tiempo estimado y cantidad de nodos recorridos para tener control de mi navegación. | 2 |
| US08 | Reporte de navegación sencillo | Como usuario, quiero recibir un reporte final de mi viaje para analizar la ruta tomada, eventos ocurridos y tiempos de recorrido. | 3 |
| US09 | Visualizar mapa esquemático de las rutas | Como usuario, quiero ver un mapa esquemático de los puertos y rutas conectadas para entender gráficamente el trayecto. | 3 |
| US10 | Guardar último viaje realizado | Como usuario, quiero guardar el último viaje realizado para poder revisarlo posteriormente y evaluar mi desempeño. | 2 |



