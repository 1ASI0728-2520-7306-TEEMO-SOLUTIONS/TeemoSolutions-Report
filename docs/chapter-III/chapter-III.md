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

| **Orden** | **User Story** | **Título**                              | **Descripción**                                                                                                                                                                                            | **Story Points** |
|-----------|----------------|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| 1         | US001          | Acceso a la sección de Resumen           | Como visitante, quiero acceder a la sección de información de la página de resumen para obtener información clara sobre la aplicación.                                                            | 2                |
| 2         | US002          | Acceso a la sección de Características   | Como visitante, quiero poder acceder a la página de "Características" para enterarme de las características claves de la aplicación.                                                              | 1                |
| 3         | US003          | Envío de Correos a los CEO de Easylogistics | Como visitante, quiero enviar correos con información adicional sobre las funcionalidades de la aplicación.                                                                                         | 2                |
| 4         | US004          | Registro de Nuevos Usuarios             | Como visitante, quiero poder registrarme como usuario para ponerme en contacto para el uso de la aplicación.                                                                                        | 3                |
| 5         | US005          | Información de Funcionalidades          | Como visitante, quiero ver un sector que detalle todas las funcionalidades que ofrece la aplicación.                                                                                                   | 2                |
| 6         | US006          | Sector de Planes Disponibles            | Como visitante, quiero ver los diferentes planes que ofrece la aplicación para escoger el que mejor se adapte a mis necesidades.                                                                      | 3                |
| 7         | US007          | Sector de Preguntas Frecuentes          | Como visitante, quiero tener acceso a un sector de preguntas frecuentes para obtener respuestas rápidas a dudas comunes.                                                                               | 2                |
| 8         | US008          | Conexión de Easylogistics con la Aplicación | Como visitante, quiero conocer cómo Easylogistics está conectado con esta aplicación para entender mejor su propósito y origen.                                                                         | 3                |
| 9         | US009          | Conexión de Datos del Formulario a Firebase | Como desarrollador, quiero conectar los datos del formulario de contacto a una base de datos de Firebase para almacenar y gestionar las consultas de los usuarios.                                 | 2                |
| 10        | US010          | Registro de Usuario                     | Como visitante, quiero poder registrarme como usuario para acceder a todas las funcionalidades de la aplicación.                                                                                     | 2                |
| 11        | US011          | Inicio de Sesión                        | Como usuario registrado, quiero poder iniciar sesión para acceder a mi cuenta y utilizar las funcionalidades de la aplicación.                                                                      | 2                |
| 12        | US012          | Recuperación de Contraseña              | Como usuario, quiero poder recuperar mi contraseña en caso de olvidarla para poder acceder nuevamente a mi cuenta.                                                                                    | 3                |
| 13        | US013          | Configuración de Cuenta                 | Como usuario, quiero poder configurar mi cuenta para personalizar mi experiencia en la aplicación.                                                                                                  | 2                |
| 14        | US014          | Crear Contenido                         | Como administrador, quiero poder crear nuevo contenido para mantener la información actualizada en la aplicación.                                                                                     | 3                |
| 15         | US015          | Leer Contenido                          | Como usuario, quiero poder leer el contenido disponible en la aplicación para obtener información relevante.                           | 3               |
| 16        | US016          | Actualizar Contenido                    | Como administrador, quiero poder actualizar el contenido existente para mantener la información relevante y actualizada.              | 2               |
| 17         | US017          | Eliminar Contenido                      | Como administrador, quiero poder eliminar contenido obsoleto para mantener la información actualizada en la aplicación.               | 3               |
| 18         | US018          | Agregar Comentarios                     | Como usuario, quiero poder agregar comentarios en el contenido para compartir mis opiniones y experiencias.                           | 1                |
| 19         | US019          | Leer Comentarios                        | Como usuario, quiero poder leer los comentarios en el contenido para conocer las opiniones y experiencias de otros usuarios.          | 2                |
| 20         | US020          | Moderar Comentarios                     | Como administrador, quiero poder moderar los comentarios para asegurar que cumplan con las normas de la comunidad.                    | 3               |
| 21         | US021          | Recibir Notificaciones                  | Como usuario, quiero recibir notificaciones para estar al tanto de las actualizaciones y eventos importantes en la aplicación| 1 
| 22        | US022          | Filtrar Contenido                       | Como usuario, quiero poder filtrar el contenido para ver solo la información que me interesa.        | 2                |
| 23        | US023          | Buscar Contenido                        | Como usuario, quiero poder buscar contenido específico para encontrar información rápidamente.        | 3                |
| 24        | US024          | Visualizar Calendario                   | Como usuario, quiero poder visualizar un calendario con todos mis eventos para tener una vista general de mis actividades. | 2               |
| 25        | US025          | Agregar Eventos al Calendario           | Como usuario, quiero poder agregar eventos al calendario para planificar mis actividades.             | 3               |
| 26        | US026          | Editar Eventos                          | Como usuario, quiero poder editar eventos en el calendario para actualizar la información de mis actividades. | 2               |
| 27        | US027          | Eliminar Eventos                        | Como usuario, quiero poder eliminar eventos del calendario para mantener mi agenda actualizada.       | 3               |
| 28        | US028          | Acceso a la Página de Inicio            | Como visitante, quiero poder acceder a la página de inicio para obtener información clara sobre la aplicación. | 2                | 
|29        | US029          | Incluir el cambio de idioma (I18n)            | Como visitante, quiero que la aplicación soporte los idiomas español e inglés para poder utilizarla en mi idioma preferido. | 2                |



| **Orden** | **User Story** | **Título**                                        | **Descripción**                                                                                                                                                                          | **Story Points** |
|-----------|----------------|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| 1         | TS001          | Crear Cuenta de Usuario                           | **Como** desarrollador, **quiero** permitir a los usuarios crear una cuenta                                                                                                              | 1                |
| 2         | TS002          | Iniciar Sesión                                    | **Como** desarrollador, **quiero** permitir a los usuarios iniciar sesión con sus credenciales                                                                                           | 2                |
| 3         | TS003          | Reconfigurar credenciales                         | **Como** desarrollador, **quiero** permitir a los usuarios restaurar y cambiar sus credenciales e información personal.                                                                  | 1                |
| 4         | TS004          | Buscar hoteles                                    | **Como** desarrollador, **quiero** implementar una funcionalidad de búsqueda de hoteles por nombre, propietario ubicación y precio.                                                      | 3                |
| 5         | TS005          | Agregar paginas de hotel                          | **Como** desarrollador, **quiero** permitir a las empresas hoteleras agregar nuevas páginas de hotel en la aplicación.                                                                   | 2                |
| 6         | TS006          | Actualizar Información de la página               | **Como** desarrollador, **quiero** permitir a las empresas hoteleras actualizar la información de sus hoteles en sus páginas.                                                            | 1                |
| 7         | TS007          | Eliminar página de hotel                          | **Como** desarrollador, **quiero** permitir a los administradores eliminar su página de hotel.                                                                                           | 3                |
| 8         | TS008          | Implementar Sistema de Valoración y reseñas       | **Como** desarrollador, **quiero** implementar un sistema de valoración y opinión para que los usuarios puedan calificar los hoteles.                                                    | 3                |
| 9         | TS009          | Implementar Funcionalidad de guardado             | **Como** desarrollador, **quiero** permitir a los usuarios guardar una página de hotel en su cuenta y marcarlo según lo prefiera.                                                        | 2                |
| 10        | TS010          | Configurar Notificaciones de Nuevas Publicaciones | **Como** desarrollador, **quiero** crear un sistema que notifique a los usuarios sobre nuevas recomedaciones de hotel, avisos del hotel que reservaron, mensajes de otros usuarios, etc. | 1                |
| 11        | TS011          | Implementar Funcionalidad de Filtros en Búsqueda  | **Como** desarrollador, **quiero** añadir filtros a la búsqueda para refinar resultados de hoteles según sus criterios.                                                                  | 2                |
| 12        | TS012          | Implementar Funcionalidad de Exportación de Datos | **Como** desarrollador, **quiero** permitir a los usuarios exportar datos de reservas y otros trámites en formatos como docx, pdf o xml.                                                 | 3                |
| 13        | TS013          | Implementar Funcionalidad de tramites             | **Como** desarrollador, **quiero** permitir a los usuarios realizar trámites en la aplicación.                                                                                           | 3                |
| 14        | TS014          | Integrar API de Recomendaciones                   | **Como** desarrollador, **quiero** integrar una API externa para obtener recomendaciones de hoteles basadas en las preferencias del usuario y su información.                            | 3                |
| 15        | TS015          | Implementar Funcionalidad de comunidad            | **Como** desarrollador, **quiero** permitir a los usuarios crear y comentar en foros y circulos de discuciones.                                                                          | 3                |
| 16        | TS016          | Implementar Sistema de Mensajes Internos          | **Como** desarrollador, **quiero** implementar un sistema de mensajes internos para comunicación entre usuarios.                                                                         | 2                |
| 17        | TS017          | Implementar Sistema de reservas                   | **Como** desarrollador, **quiero** implementar un sistema de procesamiento de reservaciones                                                                                              | 3                |
| 18        | TS018          | Implementar editor de páginas web básico          | **Como** desarrollador, **quiero** implementar un editor de páginas web básico para las empresas de hoteles                                                                              | 3                | 
