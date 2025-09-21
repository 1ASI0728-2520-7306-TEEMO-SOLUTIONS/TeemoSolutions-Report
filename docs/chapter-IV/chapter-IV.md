
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
Esta sección describe los escenarios relacionados con los atributos de calidad que influyen significativamente en las decisiones de diseño arquitectónico del sistema. Dichos escenarios provienen de los requisitos no funcionales ya definidos y ejemplifican circunstancias importantes que el sistema debe afrontar de manera eficiente.

| **Atributo**     | **Fuente**        | **Estímulo**                                                                 | **Artefacto**                     | **Entorno**                              | **Respuesta**                                                                                       | **Medida**                                                                 |
|-------------------|-------------------|-------------------------------------------------------------------------------|-----------------------------------|-------------------------------------------|-----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| Rendimiento       | Usuario (capitán o empresario) | Se consulta cálculo de ruta o valores predictivos bajo carga concurrente.     | Backend de cálculo de rutas y predicciones | Carga de 100 peticiones concurrentes       | El sistema procesa las solicitudes y entrega resultados en el tiempo esperado.                      | Tiempo de respuesta ≤ 2 s (páginas) y ≤ 5 s (cálculo) con 100 peticiones concurrentes. |
| Usabilidad        | Usuario objetivo  | Un usuario con conocimientos básicos interactúa con la aplicación para calcular una ruta. | Interfaz web/móvil                | Entorno normal de operación                | El usuario completa la acción principal en pocos pasos sin dificultad adicional.                    | ≥90% de usuarios completan tareas críticas en máximo 3 pasos.              |
| Disponibilidad    | Usuario/Operador  | Se requiere utilizar las funciones principales (calcular ruta, ETA, puntaje) en cualquier momento. | Servicios principales              | Operación 24/7                             | El sistema mantiene los servicios disponibles sin interrupciones no planificadas.                   | ≥99% disponibilidad mensual.                                               |
| Seguridad         | Sistema externo / atacante | Se intenta acceder a información sensible o interceptar comunicaciones.       | Módulos de datos y comunicaciones | Entorno de red pública                     | El sistema protege datos sensibles y claves secretas mediante cifrado.                              | AES-256 aplicado a datos sensibles, TLS en comunicaciones, 0 contraseñas en texto plano. |
| Mantenimiento     | Equipo de soporte | Ocurre un fallo crítico que detiene la operación de la plataforma.            | Plataforma completa                | Entorno productivo                         | Se activa protocolo de recuperación y se restablece el servicio en un tiempo controlado.             | Tiempo medio de recuperación ≤ 30 minutos.                               |
| Escalabilidad     | Usuarios simultáneos | Se incrementa la demanda de peticiones y volumen de datos en un 75% y 50%.    | Capa de cálculo y predicción       | Entorno de alta demanda                    | El sistema escala horizontal/verticalmente manteniendo los tiempos de respuesta aceptables.          | ≤5 segundos de respuesta en el 90% de solicitudes.                        |
| Fiabilidad        | Usuario / Sistema | Se realizan múltiples cálculos de rutas y estimaciones de riesgo.             | Motor de cálculo de rutas          | Operación continua                         | El sistema completa los cálculos con mínima tasa de error y genera alertas en caso de fallos.        | Error ≤ 0.5% mensual; alerta crítica e incidente si se supera.            |
| Privacidad        | Usuario titular   | Un usuario solicita eliminación de sus datos personales.                      | Sistema de gestión de datos        | Operación normal                           | El sistema elimina la información personal y registra el acceso y motivo.                           | Eliminación en ≤ 30 días hábiles; retención máxima de 2 años.             |
| Accesibilidad     | Usuario final     | Accede a la aplicación desde web o móvil con diferentes capacidades.          | Interfaces web y móvil             | Entorno de operación normal                | La solución cumple estándares de accesibilidad definidos.                                           | Puntuación ≥ 90% nivel AA (WCAG).                                        |
| Integridad de datos | Usuario / Sistema | Se ingresa o recibe información desde APIs externas.                          | Base de datos y módulos de ingestión | Operación continua                         | El sistema garantiza la integridad de datos sin pérdidas ni alteraciones significativas.             | Pérdida ≤ 0.05% en 24h, con registro de estados para verificación.        |
| Compatibilidad    | Usuario final     | Se accede a la plataforma desde navegadores y sistemas móviles distintos.     | Aplicación web y móvil             | Diversos entornos (Chrome, Firefox, Edge, Android, iOS) | El sistema funciona correctamente en navegadores y móviles más usados.                              | ≥90% de pruebas de compatibilidad pasan sin intervención manual.          |

#### 4.1.2.3.	Constraints.
En esta sección se agrupan las condiciones obligatorias que surgen directamente de las exigencias del negocio. Estas limitaciones deben cumplirse para garantizar que la solución planteada sea factible y responda adecuadamente a lo esperado. Dentro de este marco de restricciones se define el espacio en el que se puede diseñar y desarrollar la aplicación. A continuación, se detallan los principales constraints representados como Technical Stories, los cuales funcionan como referencias prácticas para orientar el proceso de construcción del sistema.

| **ID**    | **Título**                                      | **Descripción**                                                                                                                                   | **Criterios de Aceptación**                                                                                                            | **Relacionado con (Epic ID)** |
|-----------|-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| TUS001    | Uso de Algoritmo A* para planificación de rutas | El sistema debe calcular rutas seguras y eficientes utilizando el algoritmo A*, combinando datos de clima, cierres portuarios y riesgos detectados. | Las rutas generadas deben provenir del algoritmo A*, validando resultados en al menos el 90% de los casos de prueba.                   | EPIC001                       |
| TUS002    | Plataforma SaaS en la nube                      | Mushroom debe desplegarse como solución SaaS basada en la nube para garantizar acceso global, disponibilidad continua y escalabilidad.              | El sistema debe estar accesible desde cualquier región con al menos 99% de disponibilidad mensual garantizada.                          | EPIC002 / EPIC004             |
| TUS003    | Integración con APIs externas                   | El sistema debe consumir datos en tiempo real de fuentes externas (clima, tráfico marítimo, geopolítica) a través de APIs públicas o privadas.      | La plataforma debe integrarse exitosamente con al menos 3 fuentes externas verificadas durante pruebas de integración.                   | EPIC001 / EPIC005             |
| TUS004    | Cifrado de datos sensibles                      | Toda la información sensible y credenciales deben almacenarse cifradas con AES-256 y transmitirse con TLS 1.3.                                      | Ninguna contraseña debe almacenarse en texto plano; las pruebas de seguridad deben confirmar encriptación de datos sensibles.            | EPIC005                       |
| TUS005    | Compatibilidad Web y Móvil                      | La solución debe estar disponible como aplicación web y aplicación móvil (Android/iOS) con funcionalidades equivalentes en ambas plataformas.      | La interfaz debe superar pruebas de compatibilidad en Chrome, Firefox, Edge, Android e iOS con ≥90% de éxito en pruebas automáticas.     | EPIC004                       |
| TUS006    | Reportes descargables en PDF/Excel              | Los reportes de viaje y métricas operativas deben poder exportarse en formatos estándar (PDF y Excel) para uso empresarial.                         | El sistema debe generar archivos descargables correctamente formateados en ambos formatos.                                              | EPIC003                       |
| TUS007    | Notificaciones en tiempo real                   | Las alertas y notificaciones deben enviarse en tiempo real a los usuarios mediante la aplicación web y móvil.                                       | Los usuarios deben recibir notificaciones dentro de los 5 segundos posteriores al evento disparador.                                    | EPIC005                       |

### 4.1.3.	Architectural Drivers Backlog.
El Architectural Drivers Backlog se construyó tras un proceso iterativo de priorización realizado en el Quality Attribute Workshop (QAW). En este taller se identificaron los Functional Drivers, los Quality Attribute Drivers y los Constraints más relevantes para Mushroom, considerando su impacto en los stakeholders principales (navieras, exportadores/importadores y operadores logísticos) y la complejidad técnica que representan en el diseño arquitectónico. 

| Driver ID |	Título de Driver |	Descripción	| Importancia para Stakeholders (High, Medium, Low) |	Impacto en Architecture Technical Complexity (High, Medium, Low) |
|-----------|------------------|--------------|---------------------------------------------------|------------------------------------------------------------------|
| FD-01 | Planificación inteligente de rutas | Calcular rutas seguras y eficientes en tiempo real utilizando A* considerando clima, cierres portuarios y riesgos. | High | High |
| FD-02 | Monitoreo y recalculo dinámico | Permitir seguimiento de buques en tiempo real y recalcular rutas automáticamente ante eventos inesperados. | High | High |
| QAD-01 | Rendimiento en cálculo de rutas | Responder a solicitudes de cálculo de rutas bajo cargas concurrentes manteniendo baja latencia. | High | High |
| QAD-02 | Disponibilidad 24/7 | Garantizar que las funciones principales (cálculo, monitoreo, alertas) estén siempre disponibles. | High | High |
| CT-01 | Uso de algoritmo A* | La planificación de rutas debe basarse obligatoriamente en el algoritmo A*. | High | High |
| CT-02 | Plataforma SaaS en la nube | Mushroom debe desplegarse como SaaS global para garantizar acceso, disponibilidad y escalabilidad. | High | High |
| QAD-03 | Seguridad y cifrado de datos | Proteger credenciales y comunicaciones con cifrado AES-256 y TLS 1.3. | High | High |
| CT-03 | Integración con APIs externas | Consumo de datos en tiempo real (clima, tráfico marítimo, geopolítica) mediante APIs externas. | High | High |
| FD-03 | Visualización y reportes de información | Mostrar rutas, métricas y generar reportes descargables en PDF/Excel. | High | Medium |
| FD-04 | Notificaciones y alertas | Enviar notificaciones proactivas sobre riesgos, cierres de rutas y cambios de ETA. | High | Medium |
| QAD-04 | Escalabilidad | Adaptarse a incrementos en usuarios, datos y peticiones sin degradar el rendimiento. | High | High |
| QAD-05 | Usabilidad y accesibilidad | La interfaz debe ser intuitiva, accesible (web/móvil) y usable por distintos perfiles. | High | Medium |
| CT-04 | Compatibilidad web y móvil | La aplicación debe ser funcional en navegadores y sistemas móviles (Android/iOS). | Medium | Medium |
| QAD-06 | Trazabilidad y explicabilidad | Explicar de manera comprensible las decisiones del motor de ruteo. | Medium | Medium |
| CT-05 | Reportes descargables | Generar reportes operativos exportables en PDF y Excel. | Medium | Low |

### 4.1.4.	Architectural Design Decisions.

Durante el Quality Attribute Workshop (QAW) el equipo analizó los drivers de mayor prioridad y, en cada iteración, se identificó el driver crítico (funcional, de calidad o constraint), se seleccionaron los patrones candidatos que podían dar respuesta, se evaluaron sus pros y contras considerando el impacto en la arquitectura y la satisfacción de los stakeholders, y finalmente se tomó una decisión basada en los trade-offs entre complejidad, escalabilidad, rendimiento y facilidad de implementación.

<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; text-align: center; width: 100%;">
  <thead style="background-color: #333; color: #fff;">
    <tr>
      <th>Driver ID</th>
      <th>Título de Driver</th>
      <th colspan="2">Pattern 1</th>
      <th colspan="2">Pattern 2</th>
      <th colspan="2">Pattern 3</th>
    </tr>
    <tr style="background-color: #444; color: #fff;">
      <th></th>
      <th></th>
      <th>Pro</th>
      <th>Con</th>
      <th>Pro</th>
      <th>Con</th>
      <th>Pro</th>
      <th>Con</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td rowspan="2">FD-01</td>
      <td rowspan="2">Planificación inteligente de rutas</td>
      <td>Flexibilidad para intercambiar algoritmos (A*, Dijkstra, ML)</td>
      <td>Complejidad en pruebas unitarias</td>
      <td>Separación clara de etapas (ingestión, cálculo, optimización)</td>
      <td>Posible latencia si no se optimizan colas</td>
      <td>Extensibilidad para agregar heurísticas</td>
      <td>Mayor overhead de arquitectura</td>
    </tr>
    <tr></tr>
    <tr>
      <td rowspan="2">FD-02</td>
      <td rowspan="2">Monitoreo y recalculo dinámico</td>
      <td>Reacción inmediata a eventos externos (clima, cierres)</td>
      <td>Mayor complejidad en debugging</td>
      <td>Notificaciones automáticas y desacoplamiento</td>
      <td>Difícil de escalar si hay muchos suscriptores</td>
      <td>Optimiza lectura/escritura y recalculo</td>
      <td>Mayor complejidad en sincronización</td>
    </tr>
    <tr></tr>
    <tr>
      <td rowspan="2">QAD-01</td>
      <td rowspan="2">Rendimiento en cálculo de rutas</td>
      <td>Reducción de latencia en consultas repetidas</td>
      <td>Riesgo de datos obsoletos</td>
      <td>Uso de threads para cálculos en paralelo</td>
      <td>Sobrecarga de coordinación</td>
      <td>Distribución de carga entre instancias</td>
      <td>Dependencia de infraestructura en la nube</td>
    </tr>
    <tr></tr>
    <tr>
      <td rowspan="2">QAD-02</td>
      <td rowspan="2">Disponibilidad 24/7</td>
      <td>Alta disponibilidad ante fallos</td>
      <td>Costos de infraestructura</td>
      <td>Aísla fallos en servicios externos</td>
      <td>Puede generar latencia inicial</td>
      <td>Recuperación automática ante caídas</td>
      <td>Configuración compleja</td>
    </tr>
    <tr></tr>
    <tr>
      <td rowspan="2">QAD-03</td>
      <td rowspan="2">Seguridad y cifrado de datos</td>
      <td>Cumple GDPR/IMO</td>
      <td>Penalización mínima en rendimiento</td>
      <td>Estándar y escalable</td>
      <td>Riesgo en manejo de expiración</td>
      <td>Máxima protección en red pública</td>
      <td>Complejidad de implementación</td>
    </tr>
    <tr></tr>
    <tr>
      <td rowspan="2">CT-02</td>
      <td rowspan="2">Plataforma SaaS en la nube</td>
      <td>Escalabilidad y despliegue independiente</td>
      <td>Mayor complejidad en orquestación</td>
      <td>Escala automática y pago por uso</td>
      <td>Menor control de rendimiento</td>
      <td>Simplicidad inicial para MVP</td>
      <td>Escalabilidad limitada a largo plazo</td>
    </tr>
    <tr></tr>
  </tbody>
</table>


 
### 4.1.5.	Quality Attribute Scenario Refinements.

Al finalizar el Quality Attribute Workshop (QAW), el equipo priorizó los escenarios de atributos de calidad más críticos para el éxito de Mushroom. Se consideraron tanto los requisitos de negocio como las expectativas de los stakeholders, poniendo especial énfasis en la capacidad del sistema para mantenerse disponible 24/7, responder con baja latencia bajo cargas concurrentes, garantizar seguridad en la transmisión y almacenamiento de datos, y escalar conforme aumente la demanda.

<!-- Escenario 1: Rendimiento -->
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:100%; background-color:#1c1c1c; color:#fff;">
  <tr><th colspan="2" style="background-color:#333;">Scenario Refinement for Scenario 1</th></tr>
  <tr><td style="width:30%;">Scenario(s):</td><td>Cálculo de rutas bajo alta carga concurrente</td></tr>
  <tr><td>Business Goals:</td><td>Garantizar tiempos de respuesta rápidos para cálculos críticos, incluso bajo demanda elevada.</td></tr>
  <tr><td>Relevant Quality Attributes:</td><td>Rendimiento, Fiabilidad</td></tr>
  <tr><td>Stimulus:</td><td>Se reciben múltiples solicitudes de cálculo de rutas simultáneamente (≥100).</td></tr>
  <tr><td>Stimulus Source:</td><td>Usuarios concurrentes (capitanes/empresarios).</td></tr>
  <tr><td>Environment:</td><td>Operación normal con alta concurrencia.</td></tr>
  <tr><td>Artifact (if Known):</td><td>Motor de cálculo de rutas y predicciones.</td></tr>
  <tr><td>Response:</td><td>Procesar solicitudes sin degradación significativa del servicio.</td></tr>
  <tr><td>Response Measure:</td><td>Tiempo de respuesta ≤ 2 segundos para el 95% de las solicitudes.</td></tr>
  <tr><td>Questions:</td><td>¿Qué mecanismos de cache y paralelismo se aplicarán?</td></tr>
  <tr><td>Issues:</td><td>Posible saturación de infraestructura en picos de demanda.</td></tr>
</table>
<br>

<!-- Escenario 2: Disponibilidad -->
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:100%; background-color:#1c1c1c; color:#fff;">
  <tr><th colspan="2" style="background-color:#333;">Scenario Refinement for Scenario 2</th></tr>
  <tr><td style="width:30%;">Scenario(s):</td><td>Acceso continuo a funciones críticas del sistema</td></tr>
  <tr><td>Business Goals:</td><td>Asegurar continuidad operativa de la plataforma para usuarios globales.</td></tr>
  <tr><td>Relevant Quality Attributes:</td><td>Disponibilidad, Fiabilidad</td></tr>
  <tr><td>Stimulus:</td><td>Usuario intenta calcular ruta o consultar estado en cualquier momento.</td></tr>
  <tr><td>Stimulus Source:</td><td>Operadores y capitanes.</td></tr>
  <tr><td>Environment:</td><td>Entorno de operación productivo (24/7).</td></tr>
  <tr><td>Artifact (if Known):</td><td>Servicios principales (cálculo, notificaciones).</td></tr>
  <tr><td>Response:</td><td>El sistema mantiene los servicios activos sin interrupciones no planificadas.</td></tr>
  <tr><td>Response Measure:</td><td>≥ 99% de disponibilidad mensual garantizada.</td></tr>
  <tr><td>Questions:</td><td>¿Cómo se manejarán redundancias y failover?</td></tr>
  <tr><td>Issues:</td><td>Costos adicionales por infraestructura redundante.</td></tr>
</table>
<br>

<!-- Escenario 3: Seguridad -->
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:100%; background-color:#1c1c1c; color:#fff;">
  <tr><th colspan="2" style="background-color:#333;">Scenario Refinement for Scenario 3</th></tr>
  <tr><td style="width:30%;">Scenario(s):</td><td>Protección de datos sensibles y credenciales</td></tr>
  <tr><td>Business Goals:</td><td>Cumplir con regulaciones internacionales y generar confianza en clientes.</td></tr>
  <tr><td>Relevant Quality Attributes:</td><td>Seguridad, Privacidad</td></tr>
  <tr><td>Stimulus:</td><td>Intento de acceder o interceptar información sensible.</td></tr>
  <tr><td>Stimulus Source:</td><td>Atacante externo en red pública.</td></tr>
  <tr><td>Environment:</td><td>Comunicación a través de internet.</td></tr>
  <tr><td>Artifact (if Known):</td><td>Módulos de datos y comunicaciones.</td></tr>
  <tr><td>Response:</td><td>El sistema cifra datos y bloquea accesos no autorizados.</td></tr>
  <tr><td>Response Measure:</td><td>0 filtraciones de datos en pruebas de seguridad; cifrado AES-256 y TLS 1.3 activos.</td></tr>
  <tr><td>Questions:</td><td>¿Cómo se gestionarán las llaves de cifrado?</td></tr>
  <tr><td>Issues:</td><td>Posible impacto en rendimiento por encriptación.</td></tr>
</table>
<br>

<!-- Escenario 4: Escalabilidad -->
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:100%; background-color:#1c1c1c; color:#fff;">
  <tr><th colspan="2" style="background-color:#333;">Scenario Refinement for Scenario 4</th></tr>
  <tr><td style="width:30%;">Scenario(s):</td><td>Aumento en volumen de datos y peticiones</td></tr>
  <tr><td>Business Goals:</td><td>Mantener el desempeño del sistema pese al crecimiento en uso.</td></tr>
  <tr><td>Relevant Quality Attributes:</td><td>Escalabilidad, Rendimiento</td></tr>
  <tr><td>Stimulus:</td><td>Incremento del 75% en peticiones y 50% en volumen de datos.</td></tr>
  <tr><td>Stimulus Source:</td><td>Usuarios y fuentes de datos externas.</td></tr>
  <tr><td>Environment:</td><td>Entorno de alta demanda.</td></tr>
  <tr><td>Artifact (if Known):</td><td>Capa de cálculo y predicción.</td></tr>
  <tr><td>Response:</td><td>El sistema escala horizontal y verticalmente según la carga.</td></tr>
  <tr><td>Response Measure:</td><td>Tiempo de respuesta ≤ 3 segundos pese al incremento de carga.</td></tr>
  <tr><td>Questions:</td><td>¿Qué balanceo de carga se aplicará?</td></tr>
  <tr><td>Issues:</td><td>Riesgo de costos altos en nube por escalado dinámico.</td></tr>
</table>

<!-- Escenario 5: Usabilidad -->
<table border="1" cellspacing="0" cellpadding="6" style="border-collapse: collapse; width:100%; background-color:#1c1c1c; color:#fff;">
  <tr><th colspan="2" style="background-color:#333;">Scenario Refinement for Scenario 5</th></tr>
  <tr><td style="width:30%;">Scenario(s):</td><td>Interacción de un usuario con conocimientos básicos para calcular una ruta</td></tr>
  <tr><td>Business Goals:</td><td>Facilitar el uso de la aplicación incluso a usuarios sin experiencia técnica, reduciendo fricción en la adopción.</td></tr>
  <tr><td>Relevant Quality Attributes:</td><td>Usabilidad, Accesibilidad</td></tr>
  <tr><td>Stimulus:</td><td>Un usuario con conocimientos básicos interactúa con la aplicación para calcular una ruta.</td></tr>
  <tr><td>Stimulus Source:</td><td>Usuario final (capitán o empresario).</td></tr>
  <tr><td>Environment:</td><td>Operación normal en aplicación web/móvil.</td></tr>
  <tr><td>Artifact (if Known):</td><td>Interfaz web/móvil de Mushroom.</td></tr>
  <tr><td>Response:</td><td>El usuario completa la acción principal en pocos pasos sin dificultad adicional.</td></tr>
  <tr><td>Response Measure:</td><td>≥ 90% de los usuarios logran calcular una ruta en menos de 3 pasos durante pruebas de usabilidad.</td></tr>
  <tr><td>Questions:</td><td>¿Qué métricas de usabilidad se medirán (tiempo de tarea, tasa de éxito, errores)?</td></tr>
  <tr><td>Issues:</td><td>Necesidad de pruebas de UX iterativas y soporte multilenguaje.</td></tr>
</table>


## 4.2.	Strategic-Level Domain-Driven Design.
### 4.2.1.	EventStorming.
### 4.2.2.	Candidate Context Discovery.
### 4.2.3.	Domain Message Flows Modeling.
### 4.2.4.	Bounded Context Canvases.
### 4.2.5.	Context Mapping.
## 4.3.	Software Architecture.
### 4.3.1.	Software Architecture System Landscape Diagram.

<img src="../..//assets/img/chapter-IV/system-landscape.png">

### 4.3.1.	Software Architecture Context Level Diagrams.

<img src="../..//assets/img/chapter-IV/context-level.png">

### 4.3.2.	Software Architecture Container Level Diagrams.

<img src="../..//assets/img/chapter-IV/container-diagram.png">

### 4.3.3.	Software Architecture Deployment Diagrams.

<img src="../..//assets/img/chapter-IV/deployment-diagram.png">

