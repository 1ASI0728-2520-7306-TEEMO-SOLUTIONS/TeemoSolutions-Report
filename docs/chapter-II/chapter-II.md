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

# Capítulo II: Requirements Elicitation & Analysis

## 2.1. Competidores

### 2.1.1 Análisis Competitivo
<table>
  <tr>
    <th colspan="22">Competitive Analysis Landscape</th>
  </tr>
  <tr>
    <td colspan="1">¿Por qué llevar a cabo el análisis?</td>
    <td colspan="17">Este análisis nos ayuda a entender las particularidades de cada sitio web o aplicación, identificar la competencia en el mercado y planificar cómo abordar las oportunidades. También nos permite trabajar en la mejora continua de nuestras áreas de desarrollo.</td>
  </tr>
  <tr>
    <td colspan="2">(En la cabecera colocar por cada competidor su nombre )</td>
    <td>MarineTraffic <br></td>
    <td>Windward<br></td>
    <td>FleetMon<br></td>
</tr>
  <tr>
    <td rowspan="2">Perfil</td>
    <td>Overview</td>
    <td>MarineTraffic es una plataforma global de seguimiento de embarcaciones en tiempo real basada en datos AIS. Permite visualizar la posición de barcos, itinerarios, historial de rutas, y datos portuarios. Se usa ampliamente por operadores logísticos, agencias navieras y entusiastas del sector marítimo.</td>
    <td>	Windward es una solución avanzada de inteligencia marítima que utiliza inteligencia artificial para evaluar riesgos, prever comportamientos sospechosos y optimizar operaciones navieras. Sus clientes incluyen gobiernos, aseguradoras y grandes navieras.</td>
    <td>FleetMon ofrece datos AIS en tiempo real y servicios de análisis para rastreo de flotas, predicción de llegadas a puerto, y documentación logística. Su interfaz está dirigida tanto a usuarios corporativos como a operadores individuales.
  </td>
  </tr>
  <tr>
  <td>Ventaja Competitiva</td>
  <td>Alta cobertura AIS global, interfaz amigable, muy popular en el sector, especialmente para monitoreo pasivo de tráfico.</td>
    <td>Potente capacidad analítica predictiva, análisis de riesgos en profundidad, clientes de alto nivel institucional.</td>
    <td>Versatilidad en el rastreo de flotas con herramientas personalizadas y buena documentación para desarrolladores.</td>
    </tr>
<tr>
    <td rowspan="2">Perfil de Marketing</td>
    <td>Mercado Objetivo</td>
    <td>Agencias logísticas, operadores portuarios, entusiastas del tracking marítimo.</td>
    <td>Gobiernos, aseguradoras marítimas, grandes navieras.</td>
    <td>Operadores logísticos, navieras pequeñas y medianas, desarrolladores.</td>
  </tr>
  <tr>
  <td>Estrategias de Marketing</td>
  <td>SEO, presencia en ferias marítimas, partnerships con puertos y armadores.</td>
    <td>Relaciones institucionales, ventas B2B, participación en foros de seguridad marítima.</td>
    <td>Marketing técnico, tutoriales API, contenido especializado.</td>
    </tr>
<tr>
    <td rowspan="3">Perfil de Producto</td>
    <td>Productos y Servicios</td>
    <td>Seguimiento AIS global, historial de rutas, tráfico portuario, alertas personalizadas, informes mensuales.</td>
    <td>Análisis de riesgo, predicción de comportamiento de flotas, detección de actividad sospechosa, insights de cumplimiento normativo.
</td>
    <td>Seguimiento de flotas, predicción de ETA, bases de datos de barcos, alertas personalizadas, informes descargables.</td>
  </tr>
  <tr>
  <td>Precios y Costos</td>
  <td>Planes desde $25 al mes hasta más de $250, dependiendo de acceso a datos históricos, API, y cobertura satelital.</td>
    <td>Modelo enterprise, precios personalizados (usualmente desde $1,000+ mensuales).<br>
-Membresías: desde S/ 15 por mes hasta S/ 120 por año.</td>
    <td>Planes desde €29 por mes hasta más de €150 mensuales. Acceso API premium se cobra adicional.</td>
    </tr>
<td>Canales de distribución (Web y/o Móvil)</td>
  <td>Web, app móvil, API.</td>
    <td>Web, consultoría directa, integración con plataformas empresariales.</td>
    <td>Web, app móvil, API para integración.</td>
    </tr>
<tr>
    <td rowspan="4">Análisis SWOT</td>
    <td>Fortalezas</td>
    <td>Cobertura global, interfaz intuitiva, alta adopción.</td>
    <td>Inteligencia predictiva avanzada, prestigio institucional.</td>
    <td>Flexibilidad, personalización, buen soporte para desarrolladores.</td>
  </tr>
  <tr>
  <td>Debilidades</td>
  <td>Menor enfoque analítico, poco personalizable.</td>
    <td>Precio alto, no enfocado en usuarios operativos.</td>
    <td>Menor alcance global que MarineTraffic.</td>
    </tr>
<td>Oportunidades</td>
  <td>Expansión de APIs e integración con puertos.</td>
    <td>Colaboraciones con aseguradoras y gobiernos.</td>
    <td>Expansión hacia soluciones logísticas especializadas.</td>
    </tr>
<td>Amenazas</td>
  <td>Saturación de plataformas similares.</td>
    <td>Alto costo de entrada limita adopción.</td>
    <td>Competencia con MarineTraffic y VesselFinder.</td>
</table>

### 2.1.2. Estrategias y tácticas frente a competidores.

Teemo puede diferenciarse de sus competidores enfocándose en rutas críticas como el Mar Rojo, ofreciendo visualizaciones específicas, mapas de riesgo interactivos y alertas geopolíticas en tiempo real. A diferencia de herramientas reactivas, Teemo puede adoptar un enfoque proactivo con simuladores de rutas seguras y predicción de congestión mediante algoritmos inteligentes. Además, al priorizar una experiencia de usuario simplificada y localizada para capitanes y agencias pequeñas, con soporte offline y en idiomas clave como árabe e inglés, puede ganar terreno donde otros no llegan. Su modelo de precios accesible, con planes escalables y pruebas gratuitas, lo hace ideal para PYMEs del sector. Complementariamente, Teemo puede fortalecer su propuesta con alianzas en puertos estratégicos del Mar Rojo, una comunidad colaborativa estilo “Waze marítimo” para reportes en tiempo real, e integrar contexto geopolítico explicativo con fuentes verificadas, generando así una plataforma marítima más segura, útil y centrada en los usuarios más afectados por las crisis actuales.

## 2.2. Entrevistas
Las entrevistas buscan entender mejor a los usuarios y cómo usan la tecnología. Queremos saber qué piensan sobre los servicios en línea, los problemas que han tenido y qué esperan sobre nuestro proyecto.

### 2.2.1 Diseño de entrevistas 

**Preguntas para ambos segmentos**

- Presentación:
    - ¿Cual es su nombre?
    - ¿Que edad tiene?
    - ¿En qué Distrito vive?
    - ¿Estado Civil?
    - ¿Cual es su ocupación? ¿Estudia y/o trabaja?

**Preguntas para Empresas Navieras y Operadoras Logísticas Globales**
- ¿Cuál es su rol a bordo o dentro del equipo de planificación de rutas del crucero?
- ¿Cuántos años de experiencia tiene navegando o coordinando rutas internacionales?
- ¿Qué tipo de cruceros opera actualmente (turísticos, de lujo, rutas regionales, etc.)?
- ¿Con qué frecuencia transitan por el Mar Rojo o rutas cercanas?
- ¿Qué herramientas o sistemas utilizan para planificar y monitorear rutas en tiempo real?
- ¿Quién toma la decisión final cuando se necesita desviar una ruta por razones de seguridad?
- ¿Cómo acceden a información meteorológica, geopolítica o logística antes de cada travesía?

**Preguntas para el segmento: Exportadores e Importadores de Alta Rotación**
- ¿Cuál es su rol dentro de la agencia naviera?
- ¿Cuántos barcos o rutas supervisa actualmente su agencia?
- ¿Qué tipos de embarcaciones manejan con más frecuencia (mercantes, petroleros, cruceros, etc.)?
- ¿Cómo han afectado las tensiones geopolíticas en el Mar Rojo (por ejemplo, los ataques hutíes) a la planificación de sus rutas?
- ¿Qué decisiones operativas han debido tomar como resultado de los desvíos alrededor del Cabo de Buena Esperanza?
- ¿Han experimentado demoras o incrementos en los costos de transporte en los últimos meses debido a esta situación?
- ¿Qué tan difícil ha sido acceder a información confiable y oportuna sobre riesgos en rutas específicas?



### 2.2.2. Registro de entrevistas 
En el proceso de investigación para nuestro proyecto, se llevaron a cabo entrevistas del público objetivo. Cada entrevista se documentó en video y se registraron los siguientes detalles:

Link de la entrevista: https://upcedupe-my.sharepoint.com/:v:/g/personal/u20221a955_upc_edu_pe/ERshpHqBeD1Btquo46R2npsBg3-ZqoIrr90kLY8Ix_a4qw?e=brkSf8&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

**Segmento 1: Empresas Navieras y Operadoras Logísticas Globales**

#### Entrevista 1:

**Nombre y Apellido:** Patricia Salas

**Edad:** 45 años

**Distrito:** Callao

**Screenshot de la Entrevista:** 
![alt text](<../../assets/img/chapter-II/Captura entrevista 1.1.png>)

**Timelapse:** [Inicio: 14:45, Fin: 20:19]

**Resumen de la Entrevista:**

Patricia ocupa el rol de directora de planificación de rutas en una empresa de cruceros turísticos de alta gama. Cuenta con 22 años de experiencia coordinando rutas internacionales, especialmente en itinerarios de lujo por el Mediterráneo, Caribe y algunas travesías transatlánticas. Actualmente opera cruceros turísticos de lujo que ocasionalmente incluyen tramos por el Mar Rojo, aunque enfatizó que debido a los riesgos geopolíticos actuales, las rutas por esa zona han sido reducidas significativamente.
Para la planificación y monitoreo en tiempo real, su equipo utiliza una combinación de plataformas AIS, mapas satelitales interactivos y un software interno de optimización de rutas que les permite ajustar trayectos en función de condiciones climáticas y alertas de seguridad. En cuanto a decisiones de desvío, Patricia explicó que, aunque el capitán tiene la última palabra a bordo, todas las decisiones importantes se toman en coordinación con el centro de control en tierra, donde ella participa directamente.
El acceso a información crítica antes de cada travesía se realiza a través de briefings diarios, reportes meteorológicos internacionales, alertas geopolíticas emitidas por agencias de seguridad marítima y consultores externos especializados en riesgos marítimos. Patricia resaltó la importancia de mantener un flujo constante de información actualizada para garantizar tanto la seguridad de los pasajeros como la eficiencia de las operaciones.




**Segmento 2: Exportadores e Importadores de Alta Rotación**

#### Entrevista 1:

**Nombre y Apellido:** Arwen Vasquez

**Edad:** 40 años

**Distrito:** Callao

**Screenshot de la Entrevista:** ![alt text](<../../assets/img/chapter-II/Captura entrevista 1.png>)

**Timelapse:** [Inicio: 00:00, Fin: 05:01]

**Resumen de la Entrevista:**

Arwen es capitana de embarcaciones pesqueras industriales. Tiene 20 años de experiencia en navegación de alta mar, en especial en el Pacífico Sur. Actualmente no trabaja con cruceros turísticos; opera embarcaciones de pesca de altura, pero conoce bien la planificación de rutas. No transita por el Mar Rojo, ya que su zona de operación está en aguas sudamericanas, pero comentó que entiende la importancia de esa región para el comercio mundial. Para planificar rutas, se apoya en sonares marinos avanzados, cartografía electrónica y informes de corrientes oceánicas. Ella misma, como capitana, decide cambios de ruta si la seguridad de la tripulación está en riesgo, actuando de forma autónoma en alta mar. Accede a informes meteorológicos de alta frecuencia, alertas de fenómenos climáticos, y a redes de información marina compartida entre capitanes pesqueros.

#### Entrevista 2:

**Nombre y Apellido:** Mariela Sanchez

**Edad:** 40 años

**Distrito:** Callao

**Screenshot de la Entrevista:** ![alt text](<../../assets/img/chapter-II/Captura entrevista 2.png>)

**Timelapse:** [Inicio: 05:01, Fin: 10:45]

**Resumen de la Entrevista:**

Mariela es jefa de operaciones navieras encargada de coordinar rutas para cruceros turísticos regionales. Tiene 16 años de experiencia en logística marítima. Actualmente opera principalmente cruceros turísticos y de lujo, orientados a recorridos en Sudamérica y el Caribe. Aunque su operación no es frecuente en el Mar Rojo, explicó que en temporadas especiales coordinan rutas alternativas que bordean África.
Utiliza plataformas de monitoreo AIS (Automatic Identification System) junto con softwares propios de planificación naviera. En caso de desvíos por riesgos, el capitán del barco tiene la última palabra, pero siempre con el respaldo del equipo de tierra. Mariela recurre a boletines meteorológicos internacionales, reportes de situación política y consultores de riesgos marítimos para cada travesía.

#### Entrevista 3:

**Nombre y Apellido:** Alejandro Rivas

**Edad:** 40

**Distrito:** Callao

**Screenshot de la Entrevista:** ![alt text](<../../assets/img/chapter-II/Captura entrevista 3.png>)

**Timelapse:** [Inicio: 10:45, Fin: 14:45]

**Resumen de la Entrevista:**

Alejandro es capitán de buque de carga internacional. Lleva 18 años navegando rutas tanto regionales como de larga distancia. Actualmente, opera principalmente cruceros de carga pesada, no turísticos. Respecto al Mar Rojo, comentó que transita la zona aproximadamente dos veces al año, y que debido a la situación geopolítica reciente, deben extremar precauciones. Para la planificación y monitoreo de rutas, utiliza sistemas ECDIS (Electronic Chart Display and Information System) combinados con radar de alta precisión. Cuando hay necesidad de desviar la ruta por seguridad, él mismo toma la decisión final, pero siempre consultando previamente con la compañía naviera. Sobre la información previa al viaje, accede a informes meteorológicos satelitales, briefings de inteligencia marítima y actualizaciones de tráfico marítimo en tiempo real.

### 2.2.3. Análisis de entrevistas

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

Patricia Salas, con 22 años de experiencia en la coordinación de rutas internacionales, actualmente se desempeña como directora de planificación de rutas en una empresa de cruceros turísticos de lujo. Su rol consiste en diseñar y supervisar las rutas de los cruceros, asegurando la optimización de los trayectos y la seguridad de los pasajeros. Aunque sus cruceros transitan ocasionalmente por el Mar Rojo, destacó que debido a la situación geopolítica reciente han disminuido considerablemente sus pasos por esa zona. Para planificar y monitorear en tiempo real, Patricia y su equipo utilizan plataformas AIS, mapas satelitales interactivos y un software interno especializado en optimización de rutas, lo que les permite realizar ajustes inmediatos ante cualquier alerta. En cuanto a las decisiones de desvío por seguridad, explicó que, aunque el capitán a bordo tiene la decisión final, todo se coordina estrechamente con el centro de control en tierra, donde ella participa directamente en la evaluación de riesgos. Para mantenerse actualizados antes de cada travesía, acceden a briefings diarios, reportes meteorológicos, alertas geopolíticas de agencias internacionales y consultorías externas de seguridad marítima, demostrando un enfoque sistemático y multidisciplinario en la gestión de riesgos y planificación estratégica.

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

Los capitanes y jefes de embarcaciones entrevistados comparten un perfil de alta experiencia, con entre 16 y 20 años navegando o coordinando rutas internacionales, y todos coinciden en que la decisión final ante un desvío por razones de seguridad siempre recae en el capitán a bordo. También es común el uso de tecnología avanzada para la planificación y monitoreo de rutas, incluyendo sistemas electrónicos como ECDIS, AIS, radares o sonares, así como la consulta regular de información meteorológica y geopolítica antes de cada travesía, aunque las fuentes y herramientas específicas varían según el tipo de operación. A pesar de estos puntos en común, existen diferencias claras: Alejandro opera buques de carga, Mariela coordina cruceros turísticos y de lujo, y Arwen lidera embarcaciones pesqueras industriales. Asimismo, mientras Alejandro transita rutas internacionales incluyendo el Mar Rojo, Mariela solo ocasionalmente se acerca a esta zona y Arwen opera exclusivamente en el Pacífico Sur. En cuanto a la obtención de información crítica, Alejandro depende de informes internos de inteligencia marítima, Mariela trabaja con consultores de riesgos externos, y Arwen se apoya en redes informales entre capitanes. A pesar de las diferencias en el tipo de embarcación y las zonas de operación, todos destacan que la seguridad de la tripulación y la actualización tecnológica constante son elementos fundamentales en su labor diaria.

## 2.3. Needfinding
Posteriormente a las entrevistas, pudimos obtener la información sobre sus deseos, frustraciones, situación y múltiples datos que nos van a servir para satisfacer sus necesidades, mejorando la experiencia a nuestros usuarios. 
Esta información también nos ayudará a realizar los esquemas para las secciones de User Personas, User Task Matrix, User Journey Maps y el Empathy Mapping.

### 2.3.1. User Persona
Para desarrollar Mushroom, hemos entrevistado a estudiantes y usuarios de bicicletas. Estos datos nos permiten crear "User Personas" detalladas, que guiarán el diseño y desarrollo de nuestra plataforma para satisfacer las necesidades específicas de nuestros usuarios, ofreciendo una solución de movilidad eficiente y sostenible.

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

![alt text](<../../assets/img/chapter-II/Diego Bertie-User Persona.png>)

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

![alt text](<../../assets/img/chapter-II/Ronaldinho Luna-user persona.png>)

### 2.3.2. User Task Matrix

Elaboramos los User Task Matrix  del Usuario con el propósito de determinar la frecuencia con la que los usuarios llevan a cabo diversas actividades, lo que nos permite visualizar la importancia de ciertas tareas.

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

| Tareas                                                        |  Importancia   |  Frecuencia               |
|---------------------------------------------------------------|--------------------------|--------------------------
| Evaluar rutas marítimas antes de cada embarque.	                        |Alta                     | Siempre
| Reprogramar rutas en tiempo real	 |Media                 | Siempre                  
| Estimar tiempos de llegada y retrasos potenciales |Alta         | Siempre           
| Coordinar logística con puertos alternos                   |Media                   | A veces                  
| Acceder a reportes de riesgos marítimos |Media            | A veces                  
| Comunicar cambios de ruta con embarcaciones        |Alta                     | Diaria/Semanal                  
| Simular rutas con menor riesgo y costo     |Baja                    | Diaria                 
| Generar informes para clientes o directivos                    |Media                     | Ocasionalmente    

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

| Tareas                                                        |  Importancia   |   Frecuencia               |
|---------------------------------------------------------------|--------------------------|--------------------------
| Planificar rutas seguras antes de cada viaje		                        |Alta                     | Diaria
| Monitorear en tiempo real cambios meteorológicos y riesgos geopolíticos	 |Media                 | Semanal/Mensual                  
| Comunicar emergencias y desvíos con su equipo en tierra |Media         | Diaria/Semanal
| Asegurar cumplimiento del itinerario turístico                 |Alta                 | Diaria               
| Verificar acceso a puertos alternativos en tiempo de crisis	 |Alta            | Semanal                  
| Tomar decisiones de desvío inmediato        |Media                     | Diaria/Semanal                              
| Realizar reportes post-ruta o bitácoras                    |Media                     | Ocasionalmente    

**Analisis y Explicación:**

Las Empresas Navieras y Operadoras Logísticas Globales, al estar centradas en la planificación estratégica y la gestión logística, suelen actuar con un enfoque preventivo: evalúan rutas con antelación, generan reportes para toma de decisiones y necesitan simular escenarios posibles ante amenazas geopolíticas. Son usuarios que valoran la precisión, confiabilidad y anticipación, y que trabajan en horarios más estables pero bajo alta presión institucional. En contraste, los capitanes de crucero y sus jefes de ruta operan en un entorno de alta inmediatez, con necesidad de información clara y decisiones rápidas. Su comportamiento es más reactivo y está marcado por la necesidad de flujo continuo de datos en tiempo real, comunicación ágil con tierra y facilidad para adaptarse en situaciones críticas, como desvíos urgentes o interrupciones portuarias. 

### 2.3.3. User Journey Mapping

Creamos los User Journey Maps con el objetivo de comprender la experiencia de nuestro cliente al utilizar nuestra aplicación. Por ende, cada paso que el cliente realiza se detalla minuciosamente, incluyendo el proceso, los obstáculos encontrados y los pensamientos o emociones que surgen a raíz de ello.

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

![alt text](<../../assets/img/chapter-II/Diego Bertie Journey Map.png>)

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

![alt text](<../../assets/img/chapter-II/Ronaldinho Luna journey map.png>)

### 2.3.4. Empathy Mapping
Para el desarrollo de los Empathy Map hemos utilizado la información recopilada en base a nuestros dos User Personas que representan nuestro segmento.

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

![alt text](<../../assets/img/chapter-II/Diego Bertie - Empathy map.png>)

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

![alt text](<../../assets/img/chapter-II/Ronaldinho Luna - Empathy map.png>)

### 2.3.5. As-is Scenario Mapping
Realizamos una lluvia de ideas e identificamos las fases de acorde a lo propuesto en los User Persona. De tal modo, hemos conseguido realizar los As-Is mapping para los segmentos dados.

**_Segmento 1: Empresas Navieras y Operadoras Logísticas Globales_**

<td><img src="../../assets/img/chapter-II/AS-IS_2.png" style="width:1000px; height:auto;" alt=""></td>

**_Segmento 2: Exportadores e Importadores de Alta Rotación_**

<td><img src="../../assets/img/chapter-II/AS-IS_1.png" style="width:1000px; height:auto;" alt=""></td>

### 2.3.6. Ubiquitous Language

- **Ruta Segura**:	Trayectoria marítima recomendada basada en criterios de seguridad actualizados, incluyendo riesgos geopolíticos.

- **Simulador de Ruta**:	Herramienta que permite visualizar, comparar y proyectar diferentes rutas posibles considerando variables críticas.

- **Alerta en Tiempo**: Real	Notificación automatizada que informa sobre amenazas o cambios relevantes (clima, ataques, cierre de puertos, etc).

- **Capitán**:	Usuario operativo que navega en el mar y requiere decisiones inmediatas sobre navegación y seguridad.

- **Jefe de Ruta**:	Perfil que acompaña o asiste al capitán en la planificación y monitoreo de trayectos marítimos.

- **Agencia Naviera**:	Organización encargada de coordinar, planificar y aprobar rutas y operaciones logísticas de embarcaciones.

- **Punto Crítico**:	Zona geográfica de alto riesgo para embarcaciones, ya sea por conflicto armado, condiciones climáticas o congestión.

- **Panel de Monitoreo**:	Vista centralizada de la ubicación de embarcaciones, rutas activas y condiciones del entorno.

- **Reporte de Ruta**:	Documento generado automáticamente o a solicitud, que resume el estado de una ruta, riesgos y alternativas sugeridas.
