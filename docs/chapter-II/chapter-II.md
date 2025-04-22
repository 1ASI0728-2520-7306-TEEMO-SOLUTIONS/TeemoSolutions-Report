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
    <td colspan="2">(En la cabecera colocar por cada competidor nombre y logo)</td>
    <td>Gogo Biking<br><img src="../assets/imgs/gogobikinglogo.png" alt="Gogo Biking"></td>
    <td>City Bike Lima<br><img src="../assets/imgs/citybikelimalogo.png" alt="City Bike Lima"></td>
    <td>Tembici<br><img src="../assets/imgs/tembici-logo.png" alt="Tembici"></td>
</tr>
  <tr>
    <td rowspan="2">Perfil</td>
    <td>Overview</td>
    <td>GogoBiking es una empresa de alquiler de bicicletas y tours guiados en bicicleta ubicada en Lima, con un enfoque principal en las zonas turísticas de Miraflores y Barranco. Ofrecen una variedad de bicicletas para alquilar, incluyendo bicicletas de ciudad, bicicletas de montaña y bicicletas eléctricas, así como tours guiados en bicicleta por la ciudad y alrededores.</td>
    <td>CityBikeLima es un sistema de bicicletas compartidas que opera en Lima, con estaciones de autoservicio ubicadas en diferentes puntos de la ciudad. Los usuarios pueden alquilar bicicletas por períodos cortos o largos, utilizando una aplicación móvil o una tarjeta de membresía.</td>
    <td>Tembici es una empresa líder en sistemas de bicicletas compartidas en Latinoamérica, con presencia en países como Brasil, Chile, y recientemente en Perú. Ofrecen un servicio de bicicletas compartidas con estaciones en diferentes puntos de la ciudad.
  </td>
  </tr>
  <tr>
  <td>Ventaja Competitiva</td>
  <td>Su principal ventaja competitiva radica en su enfoque en el turismo y la experiencia, ofreciendo tours guiados de alta calidad con guías expertos y conocedores de la ciudad. Además, cuentan con bicicletas en excelente estado y ofrecen servicios adicionales como alquiler de cascos, candados y mapas.</td>
    <td>Su principal ventaja es la conveniencia y accesibilidad que ofrece su sistema de autoservicio, permitiendo a los usuarios alquilar y devolver bicicletas en diferentes puntos de la ciudad de manera rápida y sencilla.</td>
    <td>Su mayor ventaja es su infraestructura sólida y experiencia en la gestión de sistemas de bicicletas compartidas a gran escala en varias ciudades latinoamericanas. Además, trabajan en alianza con grandes empresas como Itaú, lo que les permite ofrecer un servicio con altos estándares de calidad.</td>
    </tr>
<tr>
    <td rowspan="2">Perfil de Marketing</td>
    <td>Mercado Objetivo</td>
    <td>Su mercado objetivo principal son los turistas que visitan Lima y buscan explorar la ciudad de una manera activa y divertida. También atienden a locales que desean disfrutar de un paseo en bicicleta o participar en un tour guiado.</td>
    <td>Su mercado objetivo son los residentes de Lima que buscan una opción de transporte sostenible y conveniente para desplazamientos cortos dentro de la ciudad. También atienden a turistas que desean explorar la ciudad en bicicleta.</td>
    <td>Tembici está dirigido a usuarios urbanos que buscan una opción de transporte ecológica y rápida para desplazamientos dentro de la ciudad. Atraen tanto a residentes como a turistas que buscan alternativas de transporte en las ciudades donde operan.</td>
  </tr>
  <tr>
  <td>Estrategias de Marketing</td>
  <td>GogoBiking utiliza una combinación de estrategias de marketing online y offline. Tienen una fuerte presencia en línea a través de su sitio web y redes sociales, donde promocionan sus servicios y tours. También trabajan con agencias de viajes y hoteles para llegar a un público más amplio.</td>
    <td>CityBikeLima se enfoca en el marketing digital a través de su sitio web, redes sociales y aplicación móvil. También realizan campañas de publicidad en medios de transporte público y espacios públicos.</td>
    <td>Utilizan una combinación de marketing digital y alianzas estratégicas con instituciones públicas y privadas para expandir su red de bicicletas compartidas. Además, realizan campañas en redes sociales y promociones para incentivar el uso del servicio.</td>
    </tr>
<tr>
    <td rowspan="3">Perfil de Producto</td>
    <td>Productos y Servicios</td>
    <td>- Alquiler de bicicletas por hora o día.<br>
    - Tours guiados en bicicleta por Lima y alrededores.<br>
    - Alquiler de equipos de seguridad (cascos, candados).<br>
    - Mapas y guías de la ciudad.</td>
    <td>- Alquiler de bicicletas por períodos cortos (30 minutos, 1 hora) o largos (día, semana, mes, año). <br>
- Membresías mensuales y anuales. <br>
- Aplicación móvil para localizar estaciones y alquilar bicicletas.
</td>
    <td>Tembici ofrece alquiler de bicicletas por períodos cortos y largos, a través de estaciones autoservicio ubicadas en puntos clave de las ciudades. También cuentan con bicicletas eléctricas y aplicaciones móviles para la gestión de las reservas y la ubicación de estaciones.</td>
  </tr>
  <tr>
  <td>Precios y Costos</td>
  <td>- Alquiler de bicicletas: desde S/ 15 por hora hasta S/ 40 por día.<br>
- Tours guiados: desde S/ 60 por persona.<br>
- Equipos de seguridad: S/ 5 por artículo.</td>
    <td>-Alquiler por viaje corto: desde S/ 5 por 30 minutos.<br>
-Membresías: desde S/ 15 por mes hasta S/ 120 por año.</td>
    <td>Los precios de Tembici varían según la ciudad y el tipo de suscripción, pero generalmente ofrecen planes por viaje, mensualidades y anualidades a precios competitivos.</td>
    </tr>
<td>Canales de distribución (Web y/o Móvil)</td>
  <td>Sitio web: https://www.gogobiking.pe/</td>
    <td>Sitio web: https://www.citybikelima.com/</td>
    <td>Sitio web: https://www.tembici.com.br/es/</td>
    </tr>
<tr>
    <td rowspan="4">Análisis SWOT</td>
    <td>Fortalezas</td>
    <td>- Buena reputación, tours de calidad, bicicletas en buen estado, ubicación conveniente.</td>
    <td>- Conveniencia, accesibilidad, sistema de autoservicio.</td>
    <td>- Gran red de estaciones en diversas ciudades y sólida experiencia en el mercado latinoamericano.</td>
  </tr>
  <tr>
  <td>Debilidades</td>
  <td>- Enfoque limitado en el mercado local, precios pueden ser elevados para algunos segmentos.</td>
    <td>- Disponibilidad limitada de bicicletas en horas pico, sistema de autoservicio puede ser confuso para algunos usuarios.</td>
    <td>- A veces, disponibilidad limitada de bicicletas en horas pico y estaciones más congestionadas.</td>
    </tr>
<td>Oportunidades</td>
  <td>- Expandir su oferta de tours, desarrollar alianzas con más hoteles y agencias, ofrecer alquileres a largo plazo.</td>
    <td>- Expandir la red de estaciones, mejorar la aplicación móvil, ofrecer servicios adicionales como tours guiados o alquiler de bicicletas eléctricas.</td>
    <td>- Expansión a nuevas ciudades y mayor integración con otros servicios de transporte público.</td>
    </tr>
<td>Amenazas</td>
  <td>- Competencia de otras empresas de alquiler de bicicletas y tours, cambios en la demanda turística.</td>
    <td>- Competencia de otras empresas de alquiler de bicicletas y servicios de transporte compartido, vandalismo o robo de bicicletas.</td>
    <td>- Competencia con otros servicios de transporte como scooters eléctricos y taxis compartidos.</td>
</table>

### 2.1.2. Estrategias y tácticas frente a competidores.
Para posicionar BiciBreeze frente a competidores, se pueden implementar estrategias como alianzas con universidades para ofrecer descuentos exclusivos a estudiantes, programas de referidos para incentivar la recomendación entre amigos, y campañas de marketing digital enfocadas en resaltar la conveniencia y accesibilidad sobre el modelo de suscripción mensual. Además, se pueden organizar eventos y actividades en campus universitarios para generar comunidad y fidelizar a nuestros clientes. También, podemos considerar ofrecer servicios adicionales como talleres de mantenimiento de bicicletas o rutas guiadas para estudiantes, diferenciándonos aún más de la competencia.

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
    - Vamos relacionandonos un poco mas al tema tecnologico ¿Cuál es la herramienta tecnologica que mas usa? Entre PC y/o Celular, especificar si es Windows, Mac, Android o Iphone.
    - ¿Cuales son los navegadores de internet que mas usa a dia de hoy? (Edge, Chrome, Firefox, Opera o Safari)
    - ¿Qué canal de comunicación prefiere usar: Reuniones presenciales, llamadas telefónicas o mensajes de texto (WhatsApp, SMS, Redes Sociales)?
    -¿Qué marcas y/o influencias han tenido mayor impacto en usted?

**Preguntas para Estudiantes Universitarios**
- ¿Cuáles son los principales desafíos que enfrentas al desplazarte a la universidad? (tráfico, costo, tiempo, etc.)
- ¿Qué tan frecuentemente utilizas medios de transporte alternativos como bicicletas o scooters?
- ¿Estarías dispuesto a considerar un servicio de suscripción de bicicletas para tus desplazamientos diarios a la universidad? ¿Por qué o por qué no?
- ¿Qué características consideras más importantes en un servicio de suscripción de bicicletas? (precio, ubicación de estaciones, tipo de bicicletas, etc.)
- ¿Qué precio mensual estarías dispuesto a pagar por un servicio de suscripción de bicicletas que te permita desplazarte a la universidad y a otros lugares de interés?
- ¿Qué tipo de promociones o beneficios te gustaría recibir como estudiante universitario suscrito a BiciBreeze?

**Preguntas para Publico General**
- ¿Con qué frecuencia utilizas la bicicleta como medio de transporte en tu vida diaria?
- ¿Qué factores influyen en tu decisión de utilizar la bicicleta en lugar de otros medios de transporte?
- ¿Qué barreras o desafíos encuentras al utilizar la bicicleta en la ciudad?
- ¿Qué te atraería de un servicio de alquiler de bicicletas por horas o días?
- ¿Qué características o servicios adicionales valorarías en un servicio de alquiler de bicicletas? (seguros, asistencia en carretera, rutas guiadas, etc.)
- ¿Qué precio por hora o por día consideras razonable para alquilar una bicicleta en buen estado?

### 2.2.2. Registro de entrevistas 
En el proceso de investigación para nuestro proyecto, se llevaron a cabo entrevistas del público objetivo. Cada entrevista se documentó en video y se registraron los siguientes detalles:

Link de la entrevista: https://upcedupe-my.sharepoint.com/:v:/g/personal/u201922146_upc_edu_pe/ET-wXZaUgZ5Bri_hw1N7cTgBe26622tOUkysmrLFjecIRA?e=5WUtQU&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D

**Segmento 1: Universitarios**

#### Entrevista 1:

**Nombre y Apellido:** Gabriel Garcia

**Edad:** 21 años

**Distrito:** Carabayllo

**Screenshot de la Entrevista:**

![alt text](<../assets/imgs/Entrevista Gabo.png>)

**Timelapse:** [Inicio: 00:00, Fin: 06:53]

**Resumen de la Entrevista:**
El entrevistado es Gabriel García, un estudiante de 21 años que vive en Carabayllo. Usa principalmente su iPhone y prefiere navegadores como Safari, Opera y Chrome. Para comunicarse, prefiere llamadas telefónicas y redes sociales como Instagram, Facebook y WhatsApp. Sus marcas que han influenciado en el son Adidas y Apple ya que han tenido un gran impacto en él.

Entre los desafíos para ir a la universidad menciona el tráfico excesivo, que retrasa su llegada. Aunque no usa bicicletas frecuentemente, estaría dispuesto a suscribirse a un servicio de alquiler de bicicletas para ahorrar tiempo y contribuir al medio ambiente. Considera importantes la calidad de las bicicletas, estaciones bien ubicadas y un precio accesible. Estaría dispuesto a pagar 30 soles al mes por el servicio y valora promociones en alimentos, descuentos en ropa y conexiones con servicios como gimnasios.


#### Entrevista 2:

**Nombre y Apellido:** Diego Flores

**Edad:** 20 años

**Distrito:** Barranco

**Screenshot de la Entrevista:**

![alt text](<../assets/imgs/Entrevista Diego.png>)

**Timelapse:** [Inicio: 06:53, Fin: 10:28]

**Resumen de la Entrevista:**
Diego Flores, un estudiante de 20 años que vive en Barranco, utiliza principalmente un iPhone y una PC con Windows, y prefiere navegadores como Chrome y Opera GX. Para comunicarse, opta por redes sociales y encuentros presenciales. Las marcas que más influyen en él son Adidas, Apple y Microsoft. En cuanto a transporte, enfrenta problemas de tráfico y tiempo al desplazarse a la universidad, lo que lo motiva a usar medios alternativos como bicicletas y scooters. Le interesa un servicio de suscripción de bicicletas, considerando cruciales las ubicaciones de las estaciones y un precio accesible, estando dispuesto a pagar 10 soles mensuales. También valora promociones como viajes gratuitos tras un número determinado de viajes, lo que lo haría más atractivo para estudiantes como él.

#### Entrevista 3:

**Nombre y Apellido:** Joseph Ulises Yacho Peralta

**Edad:** 20 años

**Distrito:** Rimac 

**Screenshot de la Entrevista:**

![alt text](<../assets/imgs/Entrevista Mathifa.png>)

**Timelapse:** [Inicio: 10:28, Fin: 16:46]

**Resumen de la Entrevista:**
Joseph Ulises Yacho Peralta, de 20 años y estudiante de ingeniería de software en su sexto ciclo, utiliza principalmente su laptop para sus actividades diarias, llevándola consigo a la universidad y otros lugares. Prefiere navegar con Chrome y Edge y para comunicarse opta por llamadas virtuales a través de Zoom o Meet. En cuanto a transporte, su principal preocupación es el riesgo de robo al llevar su laptop en el transporte público, por lo que usa su carnet universitario para reducir costos. Aunque no tiene bicicleta propia, ocasionalmente utiliza la de su hermano para moverse por su zona. Está interesado en un servicio de suscripción de bicicletas, siempre que las estaciones estén a una distancia conveniente. Le gustan las bicicletas clásicas como las BMX, y estaría dispuesto a pagar entre 20 y 30 soles al mes, ya que actualmente gasta unos 60 soles en pasajes. Además, le gustaría ver promociones como descuentos por meses de uso o sorteos para suscriptores recurrentes, lo cual haría el servicio más atractivo para él y otros estudiantes.


**Segmento 2: Profesionales Urbanos**

#### Entrevista 1:

**Nombre y Apellido:** Jeremy Morales

**Edad:** 24 años

**Distrito:** Surquillo

**Screenshot de la Entrevista:**

![Entrevista Jeremy](<../assets/imgs/Entrevista Jeremy.png>)

**Timelapse:** [Inicio: 16:46, Fin: 24:38]

**Resumen de la Entrevista:**
El entrevistado es un joven de 24 años que vive en el distrito de Surquillo. Es soltero pero tiene pareja actualmente. Terminó la universidad hace un par de años y trabaja como analista de datos en Culqui.

En cuanto a herramientas tecnológicas, utiliza una PC con sistema operativo Windows en su trabajo debido a los programas que emplea, como SQL, Visual Code y Trino. Para su uso personal, utiliza un celular con sistema operativo Android. Prefiere el navegador Brave por su eficiencia y menor consumo de datos, aunque en su trabajo usa Google Chrome. Para comunicarse, prefiere los mensajes por WhatsApp porque le permite responder en su propio tiempo.

Las marcas que han tenido mayor impacto en él son Samsung, Microsoft, Xbox y Sennheiser. Estas marcas están relacionadas con sus intereses en tecnología, trabajo y entretenimiento.

Sobre el uso de la bicicleta, la utiliza como medio de transporte dos veces por semana para ir al trabajo, ya que le toma aproximadamente media hora y es más eficiente y económico que otros medios de transporte como el Metropolitano. Las principales barreras que encuentra al usar la bicicleta en la ciudad son la falta de ciclovías y la poca consideración de los conductores hacia los ciclistas.

Le atrae la idea de un servicio de alquiler de bicicletas que permita tomar una bicicleta en un punto y dejarla en otro, con múltiples estaciones disponibles. De igual modo, valora especialmente los descuentos, promociones y planes de suscripción mensual o anual que ofrezcan precios más atractivos. A la vez, considera razonable pagar cinco soles por hora o entre cuarenta y sesenta soles por día para alquilar una bicicleta en buen estado.

#### Entrevista 2:

**Nombre y Apellido:**Mariela Sanchez

**Edad:** 39 años

**Distrito:** Callao

**Screenshot de la Entrevista:**

![Entrevista Mariela](<../assets/imgs/Entrevista Mathifa2.png>)

**Timelapse:** [Inicio: 24:38, Fin: 29:22]

**Resumen de la Entrevista:**
Mariela Sánchez, una mujer de 39 años que vive en el Callao y está casada, nos comenta que trabaja actualmente y usa principalmente su celular Android y una laptop con Windows. Prefiere el navegador Chrome y las reuniones presenciales para comunicarse con sus amistades y en temas de trabajo.

En cuanto a su uso de la bicicleta, Mariela la utiliza 2-3 veces por semana. Prefiere este medio de transporte por su rapidez, los beneficios para la salud y su contribución al medio ambiente. Sin embargo, enfrenta desafíos como la falta de respeto a las ciclovías por parte de algunos conductores y el mal mantenimiento de estas vías.

Respecto al servicio de alquiler de bicicletas, Mariela prefiere alquilar por días y valora la asistencia en caso de problemas mecánicos, como llantas ponchadas o fallos en los cambios. Considera razonable un precio de 5-6 soles por día y sugiere promociones para uso frecuente de lunes a viernes, con la posibilidad de dejar la bicicleta el sábado para mantenimiento.

De tal modo, la entrevista se realizó para entender mejor las preferencias y necesidades de los usuarios y así mejorar el servicio. A su vez, se destacó la importancia de contar con asistencia técnica y precios competitivos, lo cual ayudará a la startup a ofrecer un servicio más atractivo y eficiente para sus clientes.

#### Entrevista 3:

**Nombre y Apellido:** Miguel Polo

**Edad:** 19 años

**Distrito:** Centro de Lima

**Screenshot de la Entrevista:**

![Entrevista Miguel](<../assets/imgs/Entrevista Mathifa3.png>)

**Timelapse:** [Inicio: 29:22, Fin: 33:41]

**Resumen de la Entrevista:**
Miguel Polo es un joven de 19 años que trabaja en Tailoy y está soltero. Vive en Lima y, a pesar de su juventud, muestra una gran responsabilidad y organización en su vida diaria. Utiliza principalmente una computadora con Windows para sus actividades tecnológicas y prefiere los navegadores Opera y Chrome para navegar por Internet. En cuanto a la comunicación, Miguel se inclina por usar WhatsApp para mensajes de texto y Google Meet para videoconferencias, lo que indica su comodidad tanto con la tecnología como con la interacción digital.

Miguel es un usuario frecuente de la bicicleta, utilizándola todos los días para ir y volver del trabajo. Esta elección refleja su preferencia por la eficiencia y la rapidez, ya que considera que la bicicleta es un medio de transporte más rápido y sencillo en comparación con el microbús. Sin embargo, también enfrenta desafíos significativos, como la inseguridad vial y la falta de respeto hacia las ciclovías por parte de algunos conductores, lo que demuestra su conciencia sobre los problemas de infraestructura y seguridad en la ciudad.

En su tiempo libre, es probable que Miguel disfrute de actividades al aire libre, dado su uso diario de la bicicleta. Su elección de herramientas tecnológicas y su preferencia por la comunicación digital sugieren que es una persona adaptada a las nuevas tecnologías y que valora la eficiencia en su vida cotidiana. Además, su disposición a participar en la entrevista y compartir sus opiniones indica que es una persona colaborativa y abierta a contribuir con ideas para mejorar servicios que beneficien a la comunidad.


### 2.2.3. Análisis de entrevistas

**_Segmento 1: Jovenes Universitarios_**

**Edad:**

21 años: 1, 33.3%
20 años: 2, 66.6%

De esto, se puede notar que la mayoría de los entrevistados (66.6%) tiene 20 años, mientras que solo el 33.3% tiene 21 años.

**Distrito:**

Carabayllo: 1, 33.3%
Barranco: 1, 33.3%
Rímac: 1, 33.3%

Se observa que todos los entrevistados viven en distritos diferentes. Carabayllo y Rímac están más alejados del centro, mientras que Barranco está en una zona más céntrica de Lima.

**Estado Civil:**

Soltero: 3, 100%

De esto, se determina que el 100% de los entrevistados es soltero.

**Dispositivos:**
iPhone: 2, 66.6% en celulares, 33.3% en general
PC Windows: 2, 66.6% en computadoras, 33.3% en general
Laptop Windows: 1, 33.3% en computadoras, 16.67% en general

De esto, se puede notar que la mayoría (66.6%) utiliza iPhone como celular, y el 66.6% usa una PC con Windows, aunque el 33.3% también usa una laptop con Windows.

**Navegadores:**

Google Chrome: 3, 100%
Opera (Opera GX): 2, 66.6%
Safari: 1, 33.3%
Edge: 1, 33.3%

El 100% de los entrevistados usa Google Chrome. Además, el 66.6% utiliza Opera (incluyendo Opera GX), y Safari y Edge son usados por el 33.3% de los entrevistados, respectivamente.

**Canales de Comunicación:**

Redes sociales: 2, 66.6%
Llamadas (telefónicas o virtuales): 2, 66.6%
Encuentros presenciales: 1, 33.3%

La mayoría de los entrevistados (66.6%) prefiere comunicarse mediante redes sociales o llamadas telefónicas o virtuales, mientras que un 33.3% prefiere los encuentros presenciales.

**Marcas que le influencian:**

Adidas: 2, 66.6%
Apple: 2, 66.6%
Microsoft: 1, 33.3%

El 66.6% de los entrevistados está influenciado por marcas como Adidas y Apple. Solo un 33.3% menciona a Microsoft como marca influyente.

**_Segmento 2: Profesionales Urbanos_**

**Edad:**

19 años: 1, 33.3%
20 años: 1, 33.3%
24 años: 1, 33.3%

De esto, se puede notar que todos los entrevistados tienen edades distintas, representando cada uno un tercio del grupo.

**Distrito:**

Callao: 1, 33.3%
Lima: 1, 33.3%
Surquillo: 1, 33.3%

Todos los entrevistados viven en distritos diferentes, lo que muestra una diversidad en la ubicación geográfica dentro de Lima y el Callao.

**Estado Civil:**

Soltero: 2, 66.6%
Casado: 1, 33.3%

De esto, se puede observar que la mayoría (66.6%) de los entrevistados es soltero, mientras que un tercio está casado.

**Ocupación:**

Trabaja: 3, 100%

Todos los entrevistados están trabajando actualmente, a diferencia de los anteriores que eran estudiantes.

**Dispositivos:**

Celular Android: 2, 66.6%
Celular (no especificado): 1, 33.3%
Computadora con Windows: 3, 100%

Todos los entrevistados usan una computadora con Windows. Además, la mayoría usa un celular Android.

**Navegadores:**

Chrome: 2, 66.6%
Opera: 1, 33.3%
Brave: 1, 33.3%

De esto, se observa que Chrome es el navegador más utilizado, seguido por Opera y Brave, que son usados por un tercio de los entrevistados.

**Canales de Comunicación:**

WhatsApp: 2, 66.6%
Google Meet: 1, 33.3%
Reuniones presenciales: 1, 33.3%

La mayoría de los entrevistados prefiere WhatsApp, mientras que Google Meet y las reuniones presenciales son utilizados por un tercio de los entrevistados.

## 2.3. Needfinding
Posteriormente a las entrevistas, pudimos obtener la información sobre sus deseos, frustraciones, situación y múltiples datos que nos van a servir para satisfacer sus necesidades, mejorando la experiencia a nuestros usuarios. 
Esta información también nos ayudará a realizar los esquemas para las secciones de User Personas, User Task Matrix, User Journey Maps y el Empathy Mapping.

### 2.3.1. User Persona
Para desarrollar BiciBreeze, hemos entrevistado a estudiantes y usuarios de bicicletas. Estos datos nos permiten crear "User Personas" detalladas, que guiarán el diseño y desarrollo de nuestra plataforma para satisfacer las necesidades específicas de nuestros usuarios, ofreciendo una solución de movilidad eficiente y sostenible.

**_Segmento 1: Estudiantes Universitarios_**

![alt text](<../assets/imgs/Jorge Diaz Malca - User Persona.png>)

**_Segmento 2: Profesional urbano_**

![alt text](<../assets/imgs/Alex Brocca.png>)

### 2.3.2. User Task Matrix

Elaboramos los User Task Matrix  del Usuario con el propósito de determinar la frecuencia con la que los usuarios llevan a cabo diversas actividades, lo que nos permite visualizar la importancia de ciertas tareas.

**_Segmento 1: Estudiantes Universitarios_**

| Tareas                                                        | Universitario/a Importancia   | Universitario/a  Frecuencia               |
|---------------------------------------------------------------|--------------------------|--------------------------
| Movilizarse a la universidad y otros lugares de interés	                        |Alta                     | Siempre
| Buscar rutas eficientes y seguras en bicicleta	 |Alta                 | Siempre                  
| Comparar precios y opciones de transporte |Media         | A veces           
| Asistir a conferencias y eventos académicos                   |Media                   | A veces                  
| Acceder a información sobre promociones y descuentos |Media            | A veces                  
| Gestionar su tiempo y organizar su agenda        |Media                     | Diaria/Semanal                  
| Lidiar con el tráfico y la congestión	     |Alta                    | Diaria                 
| Preocuparse por la seguridad al viajar de noche                    |Media                     | Ocasionalmente    

**_Segmento 2: Profesional urbano_**

| Tareas                                                        | Profesional Importancia   | Profesional  Frecuencia               |
|---------------------------------------------------------------|--------------------------|--------------------------
| Desplazarse al trabajo		                        |Alta                     | Diaria
| Ir a citas médicas, reuniones o eventos sociales	 |Media                 | Semanal/Mensual                  
| Comparar precios y opciones de transporte |Media         | Diaria/Semanal
| Evitar el tráfico y la congestión en horas pico                  |Alta                 | Diaria               
| Reducir gastos en transporte	 |Alta            | Semanal                  
| Gestionar su tiempo y organizar su agenda        |Media                     | Diaria/Semanal                              
| Preocuparse por la seguridad al viajar de noche                    |Media                     | Ocasionalmente    

**Analisis y Explicación:**

-Los estudiantes universitarios buscan transporte diario eficiente y económico, con seguridad y opciones flexibles.

-El público general busca alternativas al tráfico y al transporte público, con opciones recreativas y familiares.

-BiciBreeze puede ofrecer soluciones a ambos segmentos, destacando la conveniencia, el ahorro y la sostenibilidad.

### 2.3.3. User Journey Mapping

Creamos los User Journey Maps con el objetivo de comprender la experiencia de nuestro cliente al utilizar nuestra aplicación. Por ende, cada paso que el cliente realiza se detalla minuciosamente, incluyendo el proceso, los obstáculos encontrados y los pensamientos o emociones que surgen a raíz de ello.

**_Segmento 1: Estudiantes Universitarios_**

![alt text](<../assets/imgs/Jorge Diaz Malca - Journey.png>)

**_Segmento 2: Profesional urbano_**

![alt text](<../assets/imgs/Alex Brocca - Journey.png>)

### 2.3.4. Empathy Mapping
Para el desarrollo de los Empathy Map hemos utilizado la información recopilada en base a nuestros dos User Personas que representan nuestro segmento.

**_Segmento 1: Estudiantes Universitarios_**

![alt text](<../assets/imgs/Jorge Diaz Malca - Empathy.png>)

**_Segmento 2: Profesional urbano_**

![alt text](<../assets/imgs/Alex Brocca - empathy.png>)

### 2.3.5. As-is Scenario Mapping
Realizamos una lluvia de ideas e identificamos las fases de acorde a lo propuesto en los User Persona. De tal modo, hemos conseguido realizar los As-Is mapping para los segmentos dados.

**_Segmento 1: Estudiantes Universitarios_**

![alt text](<../assets/imgs/as-is estudiantes.jpg>)

**_Segmento 2: Profesional urbano_**

![alt text](<../assets/imgs/as-is publico.jpg>)

### 2.3.6. Ubiquitous Language

- **Estación de bicicletas:** Punto físico donde las bicicletas se encuentran disponibles para alquilar o devolver.

- **Suscripción:** Modelo de pago en el que un usuario paga de manera anticipada por el uso del servicio por un período de tiempo.

- **Mantenimiento:** Estado o proceso en el que una bicicleta está siendo revisada o reparada.

- **App:** Plataforma móvil que los usuarios utilizan para gestionar sus alquileres, reservas y suscripciones.

- **Alquiler:** Acción en la que un usuario toma una bicicleta para su uso temporal.
