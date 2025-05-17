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

# **CAPÍTULO IV: PRODUCT DESIGN**

## 4.1. Style Guidelines

En esta seccion definiremos los estilos de diseño frontend que serán la base para dar forma a nuestro producto, utilizando patrones que consideren los aspectos de arquitectura de la información y accesibilidad necesarios para la implementación exitosa de UrProvider tanto en una Landing Page como en una Aplicación Web.

### 4.1.1. General Style Guidelines

**Branding:** El branding del logo de nuestra plataforma “Mushroom” es una combinación de elementos que transmiten una imagen sólida y confiable. Nos enfocamos en la confianza de nuestro clientes al momento de tomar un servicio prestado. El nombre “Mushroom” se presenta en una tipografía elegante y profesional, mientras que la paleta de colores crea un contraste visual claro y transmite una sensación de miminalismo y profesionalismo. En resumen, este logo tiene un enfoque clásico y profesional, y podría ser un elemento distintivo en nuestro sitio web.

<img src="../../assets/img/chapter-IV/Logo Mushroom.png" style="width:300px; height:auto;" alt="logo mushroom">

**Typography:** Al seleccionar la tipografía para nuestro proyecto, hemos optado por utilizar Roboto siguiendo las pautas de estilo general. Ya que ofrece una combinación única de legibilidad, versatilidad y modernidad que se alinea perfectamente con la identidad visual y los objetivos de Mushroom. Su diseño limpio y contemporáneo proporciona una excelente lectura en una amplia gama de dispositivos, lo que garantiza una experiencia de usuario óptima para nuestros clientes, que incluyen tanto agencias de embarcaciones navieras como exportadores e importadores de alta rotacion.

<img src="../../assets/img/chapter-IV/Tipografia.png" style="width:700px; height:auto;" alt="tipography">

**Colors:** Hemos escogido una paleta basada en colores suaves y elegantes, algo fríos para dar sensación de premium . De tal modo, estos generan un ambiente profesional y acogedor para el usuario final.
Los tonos más claros pueden ser utilizados para fondos o elementos de diseño amplios, mientras que los colores más oscuros serán para textos o detalles más específicos asegurando legibilidad y contraste entre ellos.

<img src="../../assets/img/chapter-IV/Styles colors.png" style="width:700px; height:auto;" alt="colors">

### 4.1.2. Web Style Guidelines

Para el Web Style Guidelines del sitio web "Mushroom" se utilizó con mayor presencia los colores pasteles en base a una paleta de colores que genere confianza y un ambiente acogedor para el usuario. El logo genera presencia por la combinación de elementos que transmiten una imagen sólida y confiable. A su vez, se ideó un estilo minimalista en el desarrollo del Landing Page para que el usuario tenga la facilidad de navegar y pueda observar las secciones con mayor orden. El tipo de Roboto combina con los colores anteriormente seleccionados, ya que brinda mayor flexibilidad y versatilidad. Para el desarrollo de los mockups y wireframes se utilizó en base a desarrollo web para pantallas de escritorio.

### 4.1.3. Mobile Style Guidelines

El diseño móvil debe mantener la identidad visual y la experiencia de usuario definidas en la guía de marca. La prioridad en plataformas móviles es la legibilidad, accesibilidad y rendimiento, garantizando una experiencia coherente tanto en iOS como en Android.

Los principios clave incluyen:

- Uso predominante de Roboto en todas las pantallas para una lectura limpia y moderna.

- Aplicación estratégica de la paleta de colores:

  - #10BEAE para elementos interactivos y destacados.

  -  #FFFFFF como fondo principal para asegurar limpieza y claridad.

  -  #000000 para textos principales y detalles de alto contraste.

- Espaciados amplios y márgenes consistentes para facilitar la navegación táctil.

- Iconografía clara y minimalista, preferentemente en línea con los colores definidos

#### 4.1.3.1. iOS Mobile Style Guidelines

En iOS se deben seguir los principios de Apple Human Interface Guidelines adaptados a la marca:

- **Tipografía:** Roboto Regular para cuerpo de texto, Roboto Medium para encabezados.

- **Tamaño de fuente recomendado:**

  - Título: 24 pt

  - Subtítulo: 18 pt

  - Cuerpo: 14-16 pt

- **Colores:**

  - Botones primarios: fondo #10BEAE con texto #FFFFFF.

  - Fondo general: #FFFFFF.

  - Textos: principalmente #000000.

- **Espaciado táctil:**  mínimo de 44x44 pt por elemento interactivo.

- **Esquinas redondeadas:** usar bordes suaves (4-8 pt) para botones y tarjetas, manteniendo la estética moderna.

- **Navegación intuitiva** con barras inferiores o pestañas según jerarquía de contenido.

#### 4.1.3.2. Android Mobile Style Guidelines

En Android se deben seguir las Material Design Guidelines personalizadas con el estilo propuesto por la empresa:


- **Tipografía:** Roboto Regular para cuerpo de texto, Roboto Medium para encabezados.

- **Tamaño de fuente recomendado:**

  - Título: 22-24 sp

  - Subtítulo: 16-18 sp

  - Cuerpo: 14-16 sp

- **Colores:**

  - Botones primarios: fondo #10BEAE con texto #FFFFFF.

  - Fondo general: #FFFFFF.

  - Textos: principalmente #000000.

- **Espaciado táctil:**  mínimo de 44x44 pt por elemento interactivo.

- **Elevaciones y sombras:** utilizar sombras sutiles para elementos flotantes como botones de acción (FAB).

- **Esquinas redondeadas:** usar bordes suaves (4-8 pt) para botones y tarjetas, manteniendo la estética moderna.

- **Navegación intuitiva** con barras inferiores o pestañas según jerarquía de contenido.

- **Seguir patrones de navegación** como Drawer, Bottom Navigation o Tabs dependiendo de la complejidad de la app.

## 4.2. Information Architecture
### 4.2.1. Organization Systems

- Sistemas de Organización Visual:
    - Organización secuencial: Se utilizará para explicar de manera consecutiva, la información sobre la plataforma web. De esta manera, el usuario podrá ir conociendo paso a paso el funcionamiento de la aplicación. Esto conectando desde la introducción de la aplicación web hasta la manera de contactarnos con nosotros mostrando información relevante como los beneficios que proporcionamos a partir de nuestros planes, e incluso una breve explicación del uso de la aplicación con testimonios de usuarios que ya la utilizaron. 
- Esquemas de Categorización de Contenido:
    - Por tópicos: Se utilizará para distribuir los diferentes temas a tratar de nuestra plataforma, presentando cada tópico de manera separada como una sección en donde se explicará de manera más detallada la información necesaria para el uso de la plataforma en diferentes aspectos. Esto permitira que los usuarios solo deban buscar el tópico en el que tienen dudas o directamente buscar la sección donde puede realizar estas mismas consultas con un contacto directo.

### 4.2.2. Labeling Systems

En la Landing Page, se hace uso de etiquetas que son cortas e indican con claridad al usuario la sección que van a ingresar para ver la información. Siendo las siguientes etiquetas:
- Home: Esta etiqueta indica la sección inicial donde está la información introductoria de la plataforma web.
- About: Esta etiqueta indica la sección donde se habla sobre quienes somos, nuestra misión, introducción a las suscripciones y miembros que conforman el startup.
- Subscriptions: Esta etiqueta indica la sección donde se muestra los planes disponibles para el uso de la plataforma web y sus beneficios.
- Customers: Esta etiqueta indica la sección donde se muestra los testimonios que iran haciendo los usuarios con respecto a nuestra aplicación.
- Contact: Esta etiqueta indica la sección donde se informará las maneras en las que nos pueden contactar para el feedback o por el plan Enterprise.
- Log In: Esta etiqueta indica la opción que permitirá a los usuarios ingresar a nuestra plataforma. 

### 4.2.3. SEO Tags and Meta Tags

Para la búsqueda eficiente de nuestra plataforma en los buscadores web se emplearon las siguientes tags:
- Title: Mushroom
- Meta Tags:
    - Description: Plataforma de optimización de rutas marítimas mediante tecnología inteligente.
    - Keywords: rutas marítimas, transporte de carga maritima, viajes maritimos, contenedores en embarcaciones de carga
    - Author: TEEMO-SOLUTIONS

### 4.2.4. Searching Systems

En esta parte, se indicarán los sistemas de búsqueda que se implementaran en la Landing Page, Web Applications y Mobile.

Landing Page:
- Para la búsqueda en esta sección, se utilizan las etiquetas y los sistemas de navegación que permiten la búsqueda de la información que requieren los posibles usuarios para la explicación de la misma. Esto mostrando un texto que redirige a la sección seleccionada facilitando la búsqueda.

Web Applications:
- Para la búsqueda en esta sección, se utilizan:
    - Las etiquetas y los sistemas de navegacion para la busqueda de la sección con la información que necesitan o la característica que necesitan utilizar accediendo a ellos mediante los textos.
    - La búsqueda de rutas utiliza el algoritmo de búsqueda A* para encontrar las rutas más cortas de recorrer en el medio marítimo. Esto se reflejará al momento de utilizar la búsqueda de rutas y mostrar los posibles caminos a recorrer.
    - El historial de rutas utilizadas en la aplicación permitirá llevar un registro de los recorridos que se pueden volver a utilizar. En esta sección, se puede realizar una búsqueda por fechas.

### 4.2.5. Navigation Systems

En esta parte, se indicará los sistemas de navegación que se utilizaron para la búsqueda rápida de las secciones que son de interés para los usuarios para el la landing page y la aplicación web.

Landing Page:
- Home: En esta sección, se lleva al usuario a la presentación de Mushroom.
- About: En esta sección, se lleva al usuario a la presentación del equipo, nuestra misión y una explicación breve de las suscripciones.
- Subscriptions: En esta sección, se lleva al usuario a los planes disponibles para el uso de la aplicación web.
- Customers: En esta sección, se lleva al usuario a los testimonios de usuarios que utilizaron la aplicación web.
- Contact: En esta sección, se lleva al usuario a las maneras en que puede contactarnos.
- Log In: Este botón cumple la función de ser un Call to Action que redirige a la aplicación web.

## 4.3. Landing Page UI Design

El desarrollo del UI Design de la Landing Page está en el siguiente link: https://www.figma.com/design/fRCN5nwxmvlgyTYYHrenag/TEEMOSolutions---Figma?node-id=0-1&p=f&t=xftwdiVWdTtj2j2G-0

### 4.3.1. Landing Page Wireframe

<img src="../../assets/img/chapter-IV/wireframe-landing.jpg" style="width:700px; height:auto;" alt="wireframe landing page">

### 4.3.2. Landing Page Mock-up

<img src="../../assets/img/chapter-IV/mockup-landing.jpg" style="width:700px; height:auto;" alt="mock up landing page">

## 4.4. Mobile Applications UX/UI Design
### 4.4.1. Mobile Applications Wireframes

- **El login y registro de usuarios:**
<img src="../../assets/img/chapter-IV/Mobile Applications Wireframes 1.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Todas los servicios que ofrece nuestra aplicacion:**
<img src="../../assets/img/chapter-IV/Mobile Applications Wireframes 2.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Todos los testimonios de otros usuarios:**
<img src="../../assets/img/chapter-IV/Mobile Applications Wireframes 3.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Seccion de contacto para con los administradores de la aplicacion:**
<img src="../../assets/img/chapter-IV/Mobile Applications Wireframes 4.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

### 4.4.2. Mobile Applications Wireflow Diagrams

- **Usuario que desea saber en tiempo real cual será la mejor ruta para el viaje que desea hacer**
<img src="../../assets/img/chapter-IV/Wireflow diagram1.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Usuario que desea saber algunas predicciones a posibles contratiempos que pueda sufrir la embarcacion:**
    
<img src="../../assets/img/chapter-IV/Wireflow diagram2.png " style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Usuario que desea recibir notificaciones o alertas de tormenta o problemas con el clima:**

<img src="../../assets/img/chapter-IV/Wireflow diagram3.png " style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Usuario que desea saber el costo posible del viaje para optimizar la ruta en base a costos:**

<img src="../../assets/img/chapter-IV/Wireflow diagram4.png " style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Usuario que ademas de la ruta principal desea una ruta alternativa para poder saber cual es el mejor planteamiento de ruta:**

<img src="../../assets/img/chapter-IV/Wireflow diagram5.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Usuario que desea saber datos estadisticos de sus viajes:**

<img src="../../assets/img/chapter-IV/Wireflow diagram6.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

### 4.4.3. Mobile Applications Mock-ups
 
- **El login y registro de usuarios:**
<img src="../../assets/img/chapter-IV/Mobile Mockup1.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Todas los servicios que ofrece nuestra aplicacion:**
<img src="../../assets/img/chapter-IV//Mobile Mockup2.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Todos los testimonios de otros usuarios:**
<img src="../../assets/img/chapter-IV/Mobile Mockup3.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **Seccion de contacto para con los administradores de la aplicacion:**
<img src="../../assets/img/chapter-IV/Mobile Mockup4.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

### 4.4.4. Mobile Applications User Flow Diagrams

- **User Flow Goal 1:** Como capitán, quiero que el sistema sugiera automáticamente la ruta más corta y segura según el algoritmo, para llegar eficientemente al puerto destino.

<img src="../../assets/img/chapter-IV/User flow1.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **User Flow Goal 2:** Como capitán, quiero recibir alertas si una ruta se vuelve no viable, para evitar zonas bloqueadas o peligrosas.

<img src="../../assets/img/chapter-IV/User flow3.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **User Flow Goal 3:** Como capitán, quiero que el sistema recalcule la ruta si hay cambios inesperados durante la navegación.

<img src="../../assets/img/chapter-IV/User flow5.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **User Flow Goal 4:** Como capitán, quiero que se guarden los datos del viaje realizado, para poder revisarlos o reportarlos al finalizar.

<img src="../../assets/img/chapter-IV/User flow5.png" style="width:500px; height:auto;" alt="wireframe mobile 1">

- **User Flow Goal 5:** Como empresario, quiero ver un historial de rutas utilizadas en envíos pasados, para poder tomar decisiones basadas en evidencia. 

<img src="../../assets/img/chapter-IV/User flow2.png" style="width:500px; height:auto;" alt="wireframe mobile 1">



## 4.5. Mobile Applications Prototyping
### 4.5.1. iOS Mobile Applications Prototyping

<a href="https://youtu.be/9WosMPSuCxs" target="_blank">
  <img src="../../assets/img/chapter-IV/Prototyping-Mushroom.png" alt="Haz clic para ver el video en YouTube">
</a>

https://www.figma.com/proto/fRCN5nwxmvlgyTYYHrenag/TEEMOSolutions---Figma?node-id=180-2173&p=f&t=gTWw4q4ijvLKKjSU-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=206%3A40 

## 4.6. Web Applications UX/UI Design

El desarrollo del UI Design del Web Applications está en el siguiente link: https://www.figma.com/design/fRCN5nwxmvlgyTYYHrenag/TEEMOSolutions---Figma?node-id=0-1&p=f&t=xftwdiVWdTtj2j2G-0

### 4.6.1. Web Applications Wireframes

<img src="../../assets/img/chapter-IV/wireframe-web-first.jpg" style="width:700px; height:auto;" alt="mock up web page">

<img src="../../assets/img/chapter-IV/wireframe-web-login.jpg" style="width:700px; height:auto;" alt="mock up web page">

<img src="../../assets/img/chapter-IV/wireframe-web-home.jpg" style="width:700px; height:auto;" alt="mock up web page">


### 4.6.2. Web Applications Wireflow Diagrams

- Inicio de sesión: El usuario debe ingresar a la plataforma, en esa sección se le muestra la opción de inicio de sesión y registrarse, al iniciar sesión ingresa a la plataforma.

<img src="../../assets/img/chapter-IV/wireflow-login.jpg" style="width:700px; height:auto;" alt="mock up web page">

### 4.6.3. Web Applications Mock-ups

<img src="../../assets/img/chapter-IV/mock-up-web-first.jpg" style="width:700px; height:auto;" alt="mock up web page">

<img src="../../assets/img/chapter-IV/mock-up-web-login.jpg" style="width:700px; height:auto;" alt="mock up web page">

<img src="../../assets/img/chapter-IV/mock-up-web-home.jpg" style="width:700px; height:auto;" alt="mock up web page">

### 4.6.4. Web Applications User Flow Diagrams

- Inicio de sesión: El usuario debe ingresar a la plataforma, en esa sección se le muestra la opción de inicio de sesión y registrarse, al iniciar sesión ingresa a la plataforma.

<img src="../../assets/img/chapter-IV/userflow-login.jpg" style="width:700px; height:auto;" alt="mock up web page">

## 4.7. Web Applications Prototyping

## 4.8. Domain-Driven Software Architecture
### 4.8.1. Software Architecture Context Diagram

<img src="../../assets/img/chapter-IV/C4-Context-Diagram.png" style="width:700px; height:auto;" alt="c4 context diagram">

### 4.8.2. Software Architecture Container Diagrams

<img src="../../assets/img/chapter-IV/C4-Container-Diagram.png" style="width:700px; height:auto;" alt="c4 container diagram">

### 4.8.3. Software Architecture Components Diagrams

<img src="../../assets/img/chapter-IV/C4-Component-Diagram.png" style="width:700px; height:auto;" alt="c4 container diagram">

## 4.9. Software Object-Oriented Design
### 4.9.1. Class Diagrams



### 4.9.2. Class Dictionary



## 4.10. Database Design
### 4.10.1. Relational/Non-Relational Database Diagram
