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

# **CAPÍTULO V: PRODUCT IMPLEMENTATION**

## 5.1. Software Configuration Management
En la gestión de la configuración del frontend para la aplicación Teemo, nos enfocamos en el desarrollo de una interfaz de usuario moderna, responsiva e intuitiva, utilizando Angular CLI standalone. Esta arquitectura basada en componentes independientes permite construir aplicaciones más livianas, eficientes y fácilmente escalables, optimizando el tiempo de carga y la experiencia de usuario tanto en desktop como en dispositivos móviles.

La estructura del código se organiza mediante componentes standalone, servicios desacoplados y rutas gestionadas de forma modular. Esta metodología facilita la colaboración entre miembros del equipo, acelera el proceso de desarrollo, y permite iteraciones rápidas sobre nuevas funcionalidades. Además, se siguen las mejores prácticas de Angular como el uso de Lazy Loading, Reactive Forms y RxJS para el manejo de datos asíncronos.

El control de versiones se gestiona a través de Git, aplicando flujos de trabajo basados en branches feature, merge requests y revisiones de código para mantener una alta calidad y cohesión entre los cambios. Asimismo, se ha integrado un pipeline de CI/CD (Integración Continua y Despliegue Continuo) que ejecuta automáticamente pruebas unitarias y pruebas de integración antes de cualquier despliegue, asegurando que las nuevas funcionalidades cumplan con los estándares de calidad establecidos.

### 5.1.1. Software Development Environment Configuration
En esta sección, el equipo de desarrollo detallará las herramientas de software esenciales para el frontend de la aplicación web de **Teemo**, especificando el nombre de cada producto, su propósito dentro del proyecto y el método de acceso o instalación. Para las herramientas basadas en SaaS (Software como Servicio), se proporcionará la URL de acceso a sus respectivas páginas web, mientras que para aquellas que requieren instalación local, se indicará la ruta de descarga adecuada.

Las herramientas seleccionadas abarcan actividades críticas para el desarrollo del frontend, incluyendo la gestión de componentes de interfaz de usuario, el control de versiones, el desarrollo y la prueba de aplicaciones. Cada herramienta ha sido cuidadosamente elegida para optimizar el flujo de trabajo del equipo, asegurando una colaboración efectiva y un desarrollo ágil. Estas herramientas no solo facilitan la implementación de una interfaz de usuario atractiva y funcional, sino que también permiten realizar pruebas exhaustivas y automatizar procesos repetitivos, lo que contribuye a una mayor eficiencia en el ciclo de desarrollo.

**Project Management:** Esta sección aborda la planificación y supervisión del proyecto durante todo su ciclo de vida, incluyendo la coordinación del equipo, la gestión de sus tareas y colaboraciones, así como la asignación de responsabilidades previamente establecidas. Para estructurar esta gestión, hemos dividido el enfoque en métodos distintos de comunicación y administración del equipo.

**Reuniones de Trabajo:** Para la coordinación de las tareas del equipo de frontend, utilizamos **Discord** como nuestra plataforma principal de comunicación. Esta elección se fundamenta en la familiaridad del equipo con la herramienta, lo que permite una comunicación ágil y efectiva para la discusión de temas técnicos relacionados con el desarrollo de la interfaz de usuario y la experiencia del usuario. A pesar de que Discord puede no contar con ciertas características avanzadas que ofrecen otras plataformas, su interfaz intuitiva y la posibilidad de realizar reuniones sin restricciones de tiempo nos facilitan la planificación detallada de los componentes de la aplicación y la resolución de problemas complejos relacionados con el frontend. Además, los canales temáticos en Discord permiten organizar conversaciones específicas sobre desarrollo de UI, pruebas de usabilidad, optimización del rendimiento y gestión de bibliotecas y frameworks, lo que mejora significativamente el seguimiento de los temas relevantes al frontend.

- **Página oficial de Discord:** [https://discord.com/](https://discord.com/)

**Control de Versiones:** Para la gestión del control de versiones del frontend, utilizamos las herramientas integradas de **GitHub**. Esta plataforma permite al equipo colaborar de manera eficiente a través de commits y pull requests específicos para el código de la interfaz de usuario. Los commits documentan detalladamente los cambios realizados en la lógica del cliente, así como en los componentes visuales y estilos CSS, proporcionando un historial claro que facilita la revisión y el seguimiento de las modificaciones en el frontend. Los pull requests permiten una revisión exhaustiva y discusión de los cambios propuestos antes de su integración en la rama principal, asegurando que las nuevas funcionalidades y mejoras en la interfaz se implementen de forma controlada y sin comprometer la estabilidad y la usabilidad de la aplicación. Además, el uso de GitHub como herramienta de control de versiones facilita la implementación de estrategias de ramificación, lo que permite a los miembros del equipo trabajar en características individuales o mejoras sin afectar el flujo de trabajo general.

- **Página oficial de GitHub:** [https://github.com/](https://github.com/)

**Requirements Management:** Para asegurar una organización efectiva del trabajo en nuestro equipo de frontend, en esta sección hemos implementado una metodología que utiliza herramientas específicamente diseñadas para la asignación y seguimiento de tareas relacionadas con el desarrollo de la interfaz de usuario. Estas herramientas no solo facilitan la gestión de los requisitos del proyecto, sino que también permiten una comunicación fluida entre los miembros del equipo, asegurando que cada uno esté alineado con los objetivos y plazos establecidos.

**Organización de tareas:** Hemos adoptado **ClickUp** como nuestra herramienta principal para la gestión de tareas del frontend. La plataforma ofrece una interfaz amigable que facilita la división de las actividades relacionadas con el diseño y desarrollo de la interfaz de usuario entre los miembros del equipo. Al crear tableros personalizados y asignar tareas específicas del frontend, podemos establecer plazos, designar responsables y monitorear el progreso de cada tarea técnica de manera eficiente. Esta configuración nos permite evaluar el avance en la implementación de componentes de interfaz, pruebas de usabilidad y optimización del rendimiento, así como analizar el desempeño general del equipo de frontend. ClickUp también proporciona la capacidad de revisar las contribuciones individuales y el trabajo realizado en la parte visual de la aplicación, promoviendo la transparencia y la colaboración efectiva.

- **Página oficial de ClickUp:** [https://clickup.com/](https://clickup.com/)

**Product Architecture Design:** Esta sección se centra en el desarrollo y diseño de las diferentes capas de la arquitectura del producto a lo largo de su ciclo de vida. Las herramientas seleccionadas deben ofrecer una amplia gama de funcionalidades y estilos, permitiendo la creación de diagramas complejos que capturen de manera precisa cada componente de la arquitectura, incluidos los frameworks, IDEs y lenguajes de programación utilizados. La capacidad para diagramar de manera clara y detallada es crucial para identificar cada una de las capas que componen nuestra solución.

**Diagramas C4:** Para la creación de los diagramas C4 relacionados con la arquitectura del producto, el equipo ha optado unánimemente por la plataforma **Visual Paradigm**. Esta elección se fundamenta en varios aspectos clave que consideramos esenciales para un modelado claro, comprensible y efectivo, dirigido tanto a miembros técnicos como no técnicos del proyecto. Visual Paradigm se distingue por ofrecer modelos optimizados y especializados para el desarrollo de diagramas C4, que permiten una representación clara de los sistemas complejos del FrontEnd. Su enfoque en la arquitectura y la visualización facilita la creación de diagramas que no solo son comprensibles para los desarrolladores, sino también para otros stakeholders, lo que es fundamental para alinear a todo el equipo en la evolución del proyecto.

- **Página oficial de Visual Paradigm:** [https://www.visual-paradigm.com/](https://www.visual-paradigm.com/)

**Diagramas UML:** Para abordar el diseño de todos los diagramas UML relacionados con el frontend de nuestro proyecto y asegurar una representación precisa y detallada de la estructura de la interfaz y la interacción entre los componentes, nuestro equipo ha decidido utilizar **LucidChart**. Esta plataforma es reconocida por su especialización en la creación de diagramas UML, lo que la convierte en la herramienta perfecta para nuestras necesidades de modelado de la interfaz de usuario y flujo de datos en el frontend.

- **Página oficial de LucidChart:** [https://lucidchart.com/](https://lucidchart.com/)
**Product UX/UI Design:** Esta sección respecta al desarrollo y diseño de las secciones basadas en el UX y UI correspondientes a nuestro proyecto durante todo su ciclo de vida. Las herramientas utilizadas deben estar compuestas de varias aplicaciones con estilos variados que permitan modificar la estética de todas las páginas que vamos a programar y cómo estas se verían para nuestros clientes finales, siguiendo las historias de usuario y toda metodología de desarrollo web. Asimismo, estas herramientas también deben permitir la estructuración y diagramación de todas las tablas y organizadores necesarios.

**Mapas de guía:** En relación con el diseño de los diagramas necesarios para el frontend de la aplicación, como el Empathy Map, el Journey Map y el Impact Map, hemos llegado a la conclusión unánime de que la plataforma **UXPressia** es la opción más adecuada para llevar a cabo esta tarea. Esta decisión se fundamenta en varios aspectos que consideramos esenciales para un proceso de diseño eficaz y colaborativo en el desarrollo de la interfaz de usuario. UXPressia se destaca por ofrecer un entorno de diseño más cómodo y accesible en comparación con otras soluciones disponibles en el mercado. Su interfaz intuitiva y herramientas integradas simplifican la creación de mapas de experiencia de usuario de manera rápida y precisa, lo cual es clave para el diseño centrado en el usuario. Además, la plataforma soporta un flujo de trabajo colaborativo, lo que permite que nuestro equipo de frontend trabaje de forma coordinada y eficiente en la creación de los mapas.

**User Personas:** En cuanto al diseño de User Personas para cada segmento objetivo identificado en nuestra startup y producto, hemos decidido utilizar también la plataforma **UXPressia**. Aunque somos conscientes de que existen otras herramientas que ofrecen características más avanzadas, consideramos que UXPressia proporciona modelos predefinidos y formatos visualmente atractivos que nos permiten crear User Personas de manera eficaz y comprensible. Si bien reconocemos que la plataforma presenta algunas limitaciones en cuanto al desarrollo de gráficos más grandes y diagramas complejos, las ventajas que ofrece en términos de usabilidad, simplicidad y diseño compensan estos aspectos. Además, su interfaz amigable nos permite trabajar de manera ágil, enfocándonos en la creación de perfiles que reflejen con precisión los comportamientos, necesidades y objetivos de nuestros usuarios, facilitando así el desarrollo de una estrategia más centrada en el usuario.

- **Página oficial de UXPressia:** [https://uxpressia.com/](https://uxpressia.com/)

**Escenarios:** Para la creación de escenarios correspondientes al AS-IS y TO-BE para nuestros segmentos de mercado, hemos seleccionado la plataforma web **Miro** como nuestra herramienta principal. Miro es una solución extremadamente versátil que ofrece una amplia gama de funcionalidades para el modelado de escenarios, tanto del estado actual (AS-IS) como del estado ideal o futuro (TO-BE). La plataforma permite visualizar y mapear fácilmente todos los puntos de contacto y acciones que el cliente realiza, ayudando a identificar las áreas de mejora y potenciales innovaciones en nuestro producto. Asimismo, la usabilidad de las plantillas de Miro permite a los diseñadores concentrarse en el análisis y la resolución de problemas sin tener que preocuparse por las cuestiones técnicas o de diseño que puedan surgir durante el modelado. Además, la función de trabajo colaborativo de Miro ofrece una ventaja significativa. Varios miembros del equipo pueden trabajar de manera simultánea y en tiempo real sobre un mismo tablero, lo que favorece la participación activa.

- **Página oficial de Miro:** [https://miro.com/](https://miro.com/)

**Wireframes, Mock-ups y Prototypes:** Para el desarrollo de wireframes, mock-ups y prototipos relacionados con la landing page de nuestra startup y todas las secciones de la aplicación web orientadas al frontend, hemos decidido utilizar la plataforma **Figma**. Esta herramienta ha sido seleccionada por su especialización en el diseño de interfaces de usuario para aplicaciones móviles y sitios web, ofreciendo un conjunto robusto de características que abordan las necesidades tanto de diseñadores como de desarrolladores de productos digitales. Su capacidad para crear prototipos interactivos y simular experiencias reales de usuario nos permite probar y validar conceptos antes de pasar al desarrollo final. Otra de las razones clave para esta elección es el enfoque colaborativo de Figma, que permite que múltiples miembros del equipo trabajen simultáneamente en un mismo diseño. Otro aspecto importante de Figma es su vasta biblioteca de recursos y modelos predefinidos. Estos recursos proporcionan a nuestro equipo una base sólida sobre la cual construir los wireframes iniciales, mock-ups visuales y prototipos interactivos. Por último, la capacidad de Figma para simular la experiencia del usuario final en dispositivos móviles y navegadores es fundamental para garantizar que la aplicación web y la landing page proporcionen una experiencia de usuario óptima en todos los dispositivos y plataformas.

- **Página oficial de Figma:** [https://figma.com/](https://figma.com/)
### 5.1.2. Source Code Management
En esta sección, se definirá la estrategia para utilizar GitHub como plataforma de control de versiones y colaboración durante el ciclo de vida del desarrollo del frontend. Se emplearán todas las herramientas proporcionadas por GitHub para garantizar una gestión eficaz del código fuente, incluyendo el seguimiento de versiones y la colaboración entre miembros del equipo. Se mantendrá un registro exhaustivo de las versiones del frontend, permitiendo rastrear cambios, identificar nuevos desarrollos y corregir errores de manera precisa.

Se establecerán ramas específicas para diferentes etapas del desarrollo, tales como la integración continua, las pruebas y la producción. Además, se implementarán políticas de pull requests y revisiones de código para asegurar la calidad y coherencia del frontend. Esta metodología permitirá un control riguroso del ciclo de vida del desarrollo, facilitando la colaboración y asegurando que todos los cambios se registren de forma clara y ordenada.

A continuación, se proporciona una lista con los enlaces a la organización de GitHub de WHAI y a los repositorios específicos relacionados con el desarrollo del frontend dentro de esta organización:
# Repositorios en GitHub

- **Organización:** [TEEMO-SOLUTIONS](https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS)

- **Reporte:** [upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-Report](https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-Report)

- **Aplicación Móvil:** [upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-MobileApplication]()

- **Landing Page:** [upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-LandingPage](https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-LandingPage)

- **Front End:** [upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-FrontEnd](https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-Front-End)

-**Back End** [upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-BackEnd](https://github.com/1ASI0732-2510-4441-TEEMO-SOLUTIONS/upc-pre-202501-cc-1asi0732-4441-TeemoSolutions-Back-End)

## Integrantes de la organización

En esta sección, se presentarán todos los usuarios que forman parte de la organización de GitHub del proyecto WHAI, junto con sus nombres de usuario correspondientes. El objetivo es evitar confusiones sobre los autores de los commits en GitHub y facilitar la identificación de los colaboradores al revisar y analizar el reporte y el código desarrollado por nuestro equipo.

# Modelo de integrantes del equipo dentro de la página de organización de Github

| **Nombre de Usuario**  | **Nombre del Integrante del Equipo** |
|------------------------|--------------------------------------|
| JuanPescoran           | Pescorán Angulo, Juan Fabritzzio - U20221C936 |
| JoseRiega              | Riega Salas José Miguel - U202211254 |
| Yair360                | VAru Acevedo, Yair Christofer - U202125984 |
| GuardianDeity          | Lizano Coll Cardenas, Fernando Jesus - U202214522|
| Mathifaa               | Vasquez Requejo, Augusto Mathias Leonardo - u20221a955|

# GitFlow Workflow

En nuestro proyecto, implementaremos el modelo **GitFlow** para el control de versiones, el cual está estructurado en torno a ramas principales y secundarias. Las ramas principales actúan como las bases fundamentales para el desarrollo y la implementación final del frontend. La rama **master** representa la versión estable y en producción, mientras que **develop** se utiliza para integrar todas las características y correcciones que se encuentran en desarrollo.

Las ramas secundarias se utilizan para gestionar desarrollos específicos y modificaciones puntuales. Estas ramas se crean para el desarrollo de nuevas funcionalidades, para abordar errores críticos en producción y para preparar la versión para su liberación final. Cada una de estas ramas se fusiona con **develop** a través de pull requests, los cuales son revisados por el equipo para asegurar la calidad y coherencia del código. Este enfoque asegura que cada cambio se maneje de manera organizada y que los errores críticos se aborden de forma eficiente, manteniendo la estabilidad del proyecto en todo momento.

Esta metodología garantiza una organización efectiva del flujo de trabajo, facilita la colaboración entre los miembros del equipo y optimiza la gestión de versiones del frontend, asegurando que todos los cambios se integren de manera controlada y que el historial del proyecto sea claro y manejable. A continuación, se detallan las convenciones para nombrar las ramas dentro de nuestra organización:

## Ramas Principales

- **master:** Esta rama contiene la versión final y estable del frontend, lista para su despliegue en el entorno de producción. Las integraciones a esta rama deben pasar por una revisión exhaustiva por parte del equipo técnico para asegurar la calidad y estabilidad del código del frontend.
  
- **develop:** Esta rama agrupa los elementos en desarrollo relacionados con el frontend, que han sido aprobados por al menos un miembro del equipo diferente del autor de las modificaciones. Sirve como etapa de integración y prueba de nuevas funcionalidades del frontend antes de ser fusionadas con master.


## Ramas Individuales

Estas ramas se utilizan para desarrollos individuales realizados por los miembros del equipo en el frontend.  
Los cambios se integran a las ramas principales mediante pull requests, que deben ser aprobados por el líder del equipo.  
Una vez que los cambios han sido completados y fusionados, estas ramas se eliminan para mantener un repositorio limpio y organizado.

## Formato de Commit

**Formato Estándar:**

- `"branch"` debe indicar la rama en la que se realizaron los cambios.
- La descripción debe iniciar con un verbo en inglés que refleje el cambio realizado.

## Tabla 25: Modelo de escritura de verbos para todos los commits realizados en el proyecto de GitHub

| **Verbo** | **Traducción** | **Uso en el proyecto de programación** |
|-----------|----------------|----------------------------------------|
| Add       | Añadir          | Para añadir nuevas funcionalidades, componentes o módulos al frontend. |
| Create    | Crear           | Para crear nuevos componentes, estilos o rutas en el frontend. |
| Update    | Actualizar      | Para modificar ligeramente funcionalidades existentes, optimizando o ajustando comportamientos. |
| Modify    | Modificar       | Para cambios significativos en la lógica o arquitectura del frontend. |
| Correct   | Corregir        | Para corregir errores menores sin gran impacto. |
| Fix       | Arreglar        | Para solucionar bugs críticos que afectan la funcionalidad principal. |
| Delete    | Borrar          | Para eliminar código obsoleto o recursos no necesarios. |
| Drop      | Tirar           | Para eliminar rutas, configuraciones o estilos de forma crítica y controlada. |

Esta norma sigue los principios de **Conventional Commits**, permitiendo:

- Un historial de cambios más claro y ordenado.
- Automatización de procesos como el **versionado semántico** y el **seguimiento de cambios**.
- Mayor facilidad en la trazabilidad, revisiones y transparencia en el control de versiones.

## Estructura del Mensaje de Commit
type: description
Donde `type` es uno de los verbos recomendados.

## Versionado Semántico

Se aplicará el **Versionado Semántico 2.0.0** siguiendo la estructura:

Major.Minor.Patch

- **Patch**: Correcciones de errores compatibles con versiones anteriores.
- **Minor**: Nuevas funcionalidades compatibles con versiones anteriores.
- **Major**: Cambios importantes que pueden romper la compatibilidad.

Fuente: (GitHub & Netlify, 2024)



### 5.1.3. Source Code Style Guide & Conventions

En esta sección, nuestro equipo explicará y establecerá las referencias que adoptaremos para nombrar, estructurar, organizar y programar en los lenguajes de programación que se utilizarán en el desarrollo de nuestra solución de software, con un enfoque exclusivo en la implementación del frontend.

Se detallarán las convenciones y mejores prácticas que se seguirán para asegurar un código coherente y eficiente en el uso de **Flutter**, **Dart**, **CSS**, **HTML** y **JavaScript**, principales herramientas del proyecto. Estas convenciones garantizarán la claridad, mantenibilidad y escalabilidad del código, facilitando la colaboración entre los diferentes miembros del equipo de desarrollo frontend.

Asimismo, también investigaremos y presentaremos las directrices para la interacción con las interfaces de usuario y la implementación de una experiencia de usuario fluida y atractiva. Esto incluirá:

- La gestión adecuada de los componentes visuales.
- La optimización del rendimiento en la renderización.
- El manejo efectivo de la interacción del usuario con la aplicación.

---

# Guías de Estilo y Referencias

- [Guía de Estilos y Convenciones de Código para HTML (W3Schools)](https://www.w3schools.com/html/html5_syntax.asp)
- [Guía de Estilos de Google para HTML y CSS](https://google.github.io/styleguide/htmlcssguide.html)
- [Convenciones de Gherkin para especificaciones legibles](https://specflow.org/gherkin/gherkin-conventions-for-readable-specifications/)
- [Guía de Google para el Estilo de JavaScript](https://google.github.io/styleguide/jsguide.html)
- [Guía de Pautas de JavaScript de MDN (Mozilla)](https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide/JavaScript)
- [Guía de Estilos de JavaScript de W3Schools](https://www.w3schools.com/js/js_conventions.asp)
- [Guía Oficial del Framework de Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Conjunto de Datos con Recursos de Aprendizaje de Flutter](https://github.com/rafathefull/flutterverso)
- [Guía Oficial de Dart](https://dart.dev/language)
- [Guía de Librerías Oficiales de Dart](https://dart.dev/libraries)

---

# HTML

**Estructura Semántica**
Al construir una página web, es crucial utilizar etiquetas HTML semánticas como `<header>`, `<footer>`, `<article>`, `<section>`, y `<aside>` para reflejar el significado del contenido. Esto mejora la accesibilidad y optimiza el SEO.

** Uso de Atributos "Alt" en Imágenes**
Cada imagen debe tener un atributo `alt` breve y descriptivo para accesibilidad y SEO.

** Uso Adecuado de Encabezados**
Utilizar jerarquías correctas: `<h1>` para el título principal, seguido por `<h2>`, `<h3>`, etc., sin saltar niveles.
** Validación del Código HTML**
Utilizar el validador de HTML del W3C para detectar errores y garantizar compatibilidad entre navegadores.

** Evitar Inline CSS y JavaScript**
Separar los estilos y scripts en archivos externos para mejorar la organización, mantenibilidad y carga de la página.

** Comentarios Claros y Concisos **
Agregar comentarios que expliquen secciones relevantes del código, sin exceso.

** Uso de Clases e IDs Descriptivos**
Usar nombres descriptivos siguiendo una convención coherente como BEM (Block Element Modifier).

**Mantenimiento de la Accesibilidad**
Aplicar prácticas como uso de etiquetas `<label>`, atributos ARIA y cumplir con WCAG.

**Evitación de Elementos Obsoletos**
Evitar elementos obsoletos como `<font>` y `<center>`, utilizando CSS moderno.

**Minimización de Redundancias**
Evitar duplicaciones usando clases, listas y componentes reutilizables.

---

## CSS

**Estructura Modular y Organizativa**
Dividir los estilos en módulos o componentes específicos para facilitar mantenimiento y reutilización.

**Uso de Nombres Descriptivos en Clases**
Adoptar convenciones como BEM para nombrar clases de manera clara y coherente.

**Uso Eficiente de Selectores**
Preferir clases sobre IDs o selectores descendientes complejos para mantener flexibilidad.

**Incorporación de Comentarios Claros**
Comentar secciones de código complejas para facilitar su comprensión.

**Uso de Variables y Preprocesadores**
Utilizar variables (por ejemplo, en SASS o LESS) para colores, fuentes y tamaños.

**Consistencia en Espaciado y Alineación**
Aplicar un sistema de espaciado coherente utilizando unidades relativas (`rem`, `em`).

**Optimización del Rendimiento CSS**
Minificar archivos y evitar propiedades costosas como `box-shadow` y `opacity` excesivo.

**Evitar el Uso de `!important`**
Estructurar correctamente el CSS para minimizar o eliminar el uso de `!important`.

**Responsividad y Diseño Adaptable**
Utilizar Media Queries y diseño fluido para garantizar compatibilidad en diferentes dispositivos.

**Pruebas y Validación del CSS**
Validar regularmente con herramientas automáticas y realizar pruebas en múltiples navegadores.

---

**JavaScript:**

**Uso de let y const en lugar de var:**  
Es fundamental adoptar el uso de let y const para declarar variables en lugar de var, ya que esto ayuda a evitar confusiones relacionadas con el alcance de las variables y la hoisting (elevación). let permite declarar variables con un alcance de bloque, lo que significa que su visibilidad está limitada al bloque en el que se define, mientras que const se utiliza para declarar constantes que no deben cambiar su valor. Al emplear const para valores que no se reasignarán, y let para aquellos que lo harán, se mejora la claridad del código y se previene la re-declaración accidental de variables. Esta práctica también fomenta un estilo de programación más predecible y controlado, lo cual es vital en proyectos de gran escala.

**Nomenclatura Consistente y Descriptiva:**  
Adoptar una convención de nomenclatura clara y consistente para las variables, funciones y clases es crucial para mantener la legibilidad del código. Los nombres deben ser descriptivos y reflejar claramente la función o el propósito de la variable o función. Esto no solo facilita la comprensión del código, sino que también ayuda a los desarrolladores a identificar rápidamente la funcionalidad sin necesidad de leer toda la implementación. Mantener esta consistencia a lo largo del proyecto asegura que el equipo pueda trabajar de manera más eficiente y reduzca la posibilidad de errores.

**Funciones Puramente Declarativas:**  
Escribir funciones puras que no dependan de estados externos ni causen efectos secundarios facilita la depuración y el mantenimiento. Las funciones puras toman una entrada y producen una salida sin modificar datos externos, lo que las hace predecibles y más fáciles de probar.

**Uso de Promesas y async/await para Manejo de Asincronía:**  
El uso de promesas y la sintaxis async/await mejora la gestión de operaciones asincrónicas en JavaScript. Esto facilita la lectura del código, mejora la captura de errores mediante bloques try/catch, y evita el "callback hell" (infierno de callbacks) que puede ocurrir con funciones anidadas.

**Validación de Datos y Manejo de Errores:**  
Siempre validar los tipos y formatos de datos recibidos antes de operar sobre ellos ayuda a evitar errores de ejecución. Además, implementar un manejo adecuado de errores, como usar bloques try/catch, garantiza que las excepciones se capturen y gestionen de manera controlada, mejorando la robustez de las aplicaciones.

**Modularización del Código:**  
Dividir el código en módulos separados facilita la organización, el mantenimiento y la reutilización. Utilizar ES6 Modules (import/export) o herramientas como Webpack o Rollup para estructurar el código en pequeños componentes hace que el proyecto sea más escalable y permite un trabajo colaborativo más eficiente.

**Uso de Comentarios Efectivos:**  
Los comentarios deben utilizarse para explicar el "por qué" detrás de decisiones complejas en el código, no para describir lo obvio. Comentarios efectivos y bien ubicados mejoran la comprensión y facilitan futuras modificaciones.

**Consistencia en la Formateación del Código:**  
Mantener un estilo de codificación consistente en todo el proyecto es vital. Herramientas como Prettier o configuraciones de ESLint ayudan a aplicar reglas uniformes de estilo de código, como sangrías, uso de comillas, longitud de línea, entre otros.

**Optimización del Rendimiento:**  
Optimizar el rendimiento implica evitar operaciones innecesarias dentro de bucles, minimizar accesos al DOM y usar técnicas como delegación de eventos. También es importante utilizar estructuras de datos adecuadas y escribir código eficiente para tareas intensivas.

**Implementación de Pruebas Automatizadas:**  
Implementar pruebas unitarias e integración utilizando frameworks como Jest o Mocha asegura que el código funcione como se espera y facilita la detección de errores tempranos. Esto también promueve la confianza al realizar cambios o agregar nuevas funcionalidades.

---

**Dart:**

**Uso de final y const:**  
Utilizar final para variables cuyo valor no cambiará después de su asignación inicial y const para valores que son constantes en tiempo de compilación ayuda a mejorar la claridad del código y optimizar el rendimiento.

**Nomenclatura Clara y Descriptiva:**  
Aplicar nombres claros y descriptivos a clases, funciones y variables mejora la legibilidad del código y facilita su mantenimiento. Seguir las convenciones de estilo de Dart, como usar lowerCamelCase para variables y funciones, y UpperCamelCase para clases y enums.

**Evitar el Uso de dynamic:**  
Preferir tipos de datos específicos en lugar de dynamic reduce errores en tiempo de ejecución y facilita la documentación automática del código.

**Organización en Módulos y Paquetes:**  
Organizar el código en módulos y paquetes separados por funcionalidad mejora la estructura del proyecto. En Dart, se acostumbra a usar minúsculas y guiones bajos (_) para los nombres de archivos y carpetas.

**Uso de Métodos y Clases de Extensión:**  
Dart permite crear extensiones que agregan funcionalidades a clases existentes sin modificar su código fuente. Esto mejora la modularidad y la reutilización del código.

**Implementación de Manejo de Errores:**  
Utilizar bloques try-catch para capturar y manejar excepciones asegura que la aplicación pueda responder de manera adecuada ante fallos, mejorando la experiencia de usuario.

**Uso de async y await para Operaciones Asincrónicas:**  
Utilizar async y await proporciona un manejo de asincronía más claro y fácil de leer, evitando el uso excesivo de callbacks anidados.

**Utilización de pubspec.yaml para la Gestión de Dependencias:**  
Mantener actualizado el archivo pubspec.yaml asegurando versiones compatibles de las dependencias y utilizando la sección dev_dependencies para herramientas de desarrollo.

**Implementación de Pruebas Unitarias y de Integración:**  
Desarrollar pruebas unitarias e integraciones utilizando el paquete de pruebas de Dart ayuda a validar la funcionalidad de forma temprana y mejora la calidad del código.

**Documentación Clara y Consistente:**  
Utilizar comentarios de documentación (///) para describir clases, métodos y funciones permite la generación automática de documentación y facilita la comprensión del código.

---

**Flutter:**

**Estructura de Proyecto Modular:**  
Organizar el proyecto en carpetas como lib/models, lib/views, lib/widgets, y lib/services facilita la escalabilidad y el mantenimiento del proyecto. Esto permite una separación clara de responsabilidades y mejora la colaboración en equipo.

**Uso de Widgets Compuestos y Personalizados:**  
Crear widgets reutilizables y configurables permite mantener la DRY principle (Don’t Repeat Yourself) y facilita el mantenimiento del código, ya que los cambios se aplican en un solo lugar.

**Adopción del Patrón BLoC para Gestión de Estado:**  
El patrón BLoC (Business Logic Component) separa la lógica de negocio de la UI utilizando Streams y eventos. Esto resulta en un código más organizado y testeable, además de mejorar la escalabilidad de la aplicación.

**Optimización del Rendimiento con ListViews y Grids:**  
Utilizar ListView.builder y GridView.builder para listas largas permite que solo se rendericen los elementos visibles en pantalla, reduciendo el uso de memoria y mejorando el rendimiento.

**Gestión de Rutas con Navigator y Rutas Nombradas:**  
Centralizar la gestión de rutas utilizando rutas nombradas definidas en el MaterialApp facilita la navegación entre pantallas y el paso de argumentos entre ellas.

**Uso de pubspec.yaml para Gestionar Dependencias:**  
Gestionar correctamente las dependencias declaradas en pubspec.yaml garantiza la compatibilidad y evita conflictos en el proyecto. Es importante documentar el propósito de cada dependencia agregada.

**Implementación de Pruebas de Widget y de Integración:**  
Escribir pruebas para widgets individuales y flujos de interacción asegura la estabilidad y calidad de la aplicación, además de permitir la detección temprana de errores.

**Adopción de Temas Globales para Consistencia Visual:**  
Definir un ThemeData global en el MaterialApp permite mantener una apariencia coherente en toda la aplicación en cuanto a colores, tipografías y estilos de botones.

**Documentación y Comentarios Claros:**  
Utilizar comentarios de documentación ayuda a que otros desarrolladores comprendan fácilmente la lógica detrás de cada widget, función o clase, facilitando el mantenimiento y escalabilidad.

**Adopción de Prácticas de Accesibilidad:**  
Implementar buenas prácticas de accesibilidad, como utilizar widgets Semantics y realizar pruebas de accesibilidad, garantiza que la aplicación pueda ser utilizada por personas con discapacidades.


---
### 5.1.4. Software Deployment Configuration
En esta sección, procederemos a detallar de manera exhaustiva la configuración necesaria para implementar y desplegar nuestra solución, centrándonos específicamente en las áreas del FrontEnd. A lo largo de este análisis, enfatizaremos las mejores prácticas que deben seguirse, así como las herramientas más adecuadas a utilizar y los flujos de trabajo recomendados para garantizar una implementación eficaz y coordinada de ambas partes de nuestra solución. Además, discutiremos cómo cada decisión técnica impacta en la funcionalidad y la experiencia del usuario, proporcionando así un enfoque integral para el desarrollo de nuestras aplicaciones.

**Landing Page:**

## 5.2. Product Implementation & Deployment
A continuación, describimos en detalle el enfoque técnico que adoptaremos para la implementación, pruebas y despliegue de nuestra infraestructura FrontEnd, centrado en la creación y gestión de los componentes de la interfaz de usuario, así como en la integración con los servicios externos y el manejo eficiente de las API necesarias para el correcto funcionamiento de la aplicación. Este proceso abarca el desarrollo de interfaces FrontEnd escalables, el diseño de la Landing Page, la validación exhaustiva mediante pruebas unitarias y de integración, y la optimización del rendimiento antes de cada ciclo de despliegue en el entorno de producción. Durante esta fase, nos aseguraremos de que cada componente se alinee con las mejores prácticas de desarrollo y diseño, garantizando así una experiencia de usuario fluida y atractiva. Además, se prestará especial atención a la accesibilidad y la compatibilidad en diferentes navegadores, asegurando que nuestra aplicación sea inclusiva y utilizable por la mayor cantidad de usuarios posible.

### 5.2.1. Sprint Backlogs
En esta sección se explicarán los detalles presentados y analizados durante la reunión del Sprint Planning para el Sprint número 1 de la implementación del FrontEnd. El objetivo principal de esta reunión es establecer un plan claro y realista que guíe el desarrollo de la interfaz de usuario, identificando las tareas específicas a realizar y comprometiéndose con un conjunto de entregables concretos que contribuyan al avance del proyecto por el lado de las funcionalidades principales de generación y edición de TeemoSolution. Este enfoque permite asegurar que todos los miembros del equipo tengan una comprensión compartida de los objetivos y las expectativas del sprint, lo que resulta esencial para la coordinación y efectividad en el trabajo colaborativo.

Durante esta reunión, se abordarán las características a desarrollar, los plazos para cada tarea y los criterios de aceptación correspondientes. Además, se fomentará un diálogo abierto entre los integrantes del equipo para identificar posibles desafíos y oportunidades de mejora, asegurando que cada aspecto del desarrollo del FrontEnd esté alineado con las metas del proyecto. 

<table>
        <tr>
            <td colspan="1">Sprint #</td>
            <td colspan="1">Sprint 1</td>
        </tr>
        <tr>
            <td colspan="2">Sprint Planning Background</td>
        </tr>
        <tr>
            <td>Date</td>
            <td>2025-04-24</td>
        </tr>
          <tr>
            <td>Time</td>
            <td>16:34</td>
        </tr>
            <tr>
            <td>Location</td>
            <td>Discord</td>
        </tr>
            <tr>
            <td>Prepared by</td>
            <td>Riega Salas, José Miguel</td>
        </tr>
            <tr>
            <td>Attendees (to planning meeting)</td>
            <td>Pescorán Angulo, Juan Fabritzzio; Riega Salas, José Miguel; Lizano Coll Cardenas, Fernando Jesus; Vasquez Requejo, Augusto Mathias Leonardo</td>
        </tr>
            <tr>
            <td>Sprint 1 Review Summary</td>
            <td>Al finalizar el Sprint 1, se llevó a cabo la reunión de Sprint Review para evaluar el avance logrado en el desarrollo del FrontEnd de nuestra aplicación. Durante este sprint, el trabajo se enfocó principalmente en la creación de la Landing Page del proyecto, así como en funciones clave de la aplicación, incluyendo la generación y edición de TeemoSolutions y las secciones de inicio de sesión y registro.

La reunión fue productiva tanto en términos de progreso en el software como de colaboración del equipo. Se presentaron las funcionalidades implementadas, se realizaron demostraciones de la interfaz y se recogieron aportes constructivos de los miembros del equipo y otros interesados. Estos comentarios fueron fundamentales para detectar oportunidades de mejora y ajustar la planificación para el siguiente sprint. La comunicación efectiva y el trabajo en equipo durante la revisión fortalecieron la cohesión del grupo y aseguraron que el desarrollo del FrontEnd siguiera alineado con los objetivos del proyecto.</td> 
        </tr>
            <tr>
            <td>Sprint 1 Retrospective Summary</td>
            <td>Durante la Sprint Retrospective del Sprint 1, el equipo se enfocó en analizar a fondo toda la retroalimentación obtenida tras la finalización de este primer sprint. Esta evaluación detallada del rendimiento tanto grupal como individual nos ayudó a identificar áreas clave de mejora, fundamentales para perfeccionar nuestra aplicación móvil desde el enfoque del FrontEnd.

En este espacio de reflexión, surgieron varias estrategias orientadas a mejorar la calidad del trabajo entregado y asegurar que el producto final cumpla con las expectativas de los usuarios. Se abordaron temas como la usabilidad de la interfaz, la coherencia en el diseño y la adopción de mejores prácticas en el desarrollo FrontEnd. Este intercambio de ideas no solo fortaleció la colaboración entre los miembros del equipo, sino que también estableció una base sólida para un enfoque más eficiente en los próximos sprints, garantizando que nuestro producto sea funcional, intuitivo y atractivo para nuestros clientes. </td>
        </tr>
            <tr>
            <td colspan="2">Sprint Goal & User Stories</td>
        </tr>
              <tr>
            <td>Sprint 1 Goal</td>
            <td>Alcanzar una métrica de cumplimiento del 100%, lo que indicará que se ha logrado todos los objetivos del sprint 1 con todas las historias de usuario y otros materiales necesarios.</td>
        </tr>
              <tr>
            <td>Sprint 1 Velocity</td>
            <td>Con el equipo para este sprint 1 decidimos aceptar 3 Story Points</td>
        </tr>
              <tr>
            <td>Sum of Story Points</td>
            <td>La suma de los Story Points para los User Stories que se están incluyendo en este Sprint 1 es 21</td>
        </tr>
    </table>
### 5.2.2. Implemented Landing Page Evidence
### 5.2.3. Implemented Frontend-Web Application Evidence
### 5.2.4. Implemented Native-Mobile Application Evidence
### 5.2.5. Implemented RESTful API and/or Serverless Backend Evidence
### 5.2.6. RESTful API Documentation
### 5.2.7. Team Collaboration Insights

## 5.3. Video About-the-Product
