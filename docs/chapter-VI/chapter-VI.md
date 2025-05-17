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

# **CAPÍTULO VI: PRODUCT VERIFICATION & VALIDATION**

## 6.1. Testing Suites & Validation
### 6.1.1. Core Entities Unit Tests

Los Core Entities Unit Tests son esenciales en el desarrollo de software, ya que garantizan la calidad y correcto funcionamiento de las entidades centrales, previniendo errores y facilitando el mantenimiento del código.
### 6.1.2. Core Integration Tests

Las pruebas de integración central (Core Integration Tests) son esenciales para verificar que los controladores se comuniquen de forma adecuada con otros elementos del sistema, como los servicios y las bases de datos. Al analizar situaciones de error, estas pruebas aseguran que el sistema responda correctamente ante eventos imprevistos, utilizando los códigos de estado apropiados. Esto no solo optimiza la experiencia del usuario, sino que también simplifica la depuración y favorece la creación de un software robusto y de calidad.
### 6.1.3. Core Behavior-Driven Development
### 6.1.4. Core System Tests

## 6.2. Static Testing & Verification
### 6.2.1. Static Code Analysis
Esta sección aborda las técnicas de prueba y verificación estática del código, con el objetivo de garantizar que el software cumpla con los criterios de calidad y seguridad antes de su ejecución. Estos métodos permiten detectar fallos desde las primeras etapas del ciclo de desarrollo.

El análisis estático consiste en examinar el código fuente sin necesidad de ejecutarlo, mediante herramientas automáticas y revisiones manuales. Este procedimiento facilita la identificación de errores, vulnerabilidades de seguridad y áreas de mejora, lo que favorece una mayor calidad del software y disminuye los costos asociados a correcciones en fases más avanzadas del proyecto.

<img src="../../assets/img/chapter-VI/StaticCodeAnalysis.png" style="width:500px; height:auto;" alt="static code">

#### 6.2.1.1. Coding Standard & Code Conventions
En el desarrollo de software moderno, mantener un código claro, coherente y alineado con los objetivos del negocio es esencial para asegurar la escalabilidad, la mantenibilidad y la colaboración efectiva entre equipos. Para lograrlo, es indispensable adoptar buenas prácticas de codificación que garanticen tanto la calidad técnica como la comprensión funcional del sistema. Dos enfoques fundamentales que contribuyen a este propósito son Clean Code y Domain-Driven Design (DDD).

- **Clean Code:**

El concepto de Clean Code se basa en escribir código que sea fácil de leer, entender y modificar. Esto implica utilizar nombres claros y significativos para variables, funciones y clases, escribir funciones cortas que cumplan con una única responsabilidad, y eliminar el código muerto y los comentarios innecesarios. Un código limpio no solo facilita el mantenimiento, sino que también mejora la colaboración entre desarrolladores, reduce la probabilidad de errores y acelera los procesos de revisión y depuración.

<img src="../../assets/img/chapter-VI/Clean Code.png" style="width:500px; height:auto;" alt="clean code">

- **Domain-Driven Design (DDD):**

Domain-Driven Design es un enfoque centrado en modelar el software según el dominio del negocio. Para ello, se recomienda el uso de un lenguaje ubicuo que refleje con precisión los términos y conceptos del negocio en el código. El sistema debe dividirse en bounded contexts, lo que permite separar claramente diferentes áreas funcionales y evitar ambigüedades. Dentro de cada contexto, se utilizan entidades y objetos de valor de forma adecuada para representar los conceptos clave del dominio. Además, la lógica del negocio se organiza mediante servicios de dominio y repositorios, promoviendo una arquitectura más estructurada, comprensible y alineada con las necesidades reales del negocio.

<img src="../../assets/img/chapter-VI/DDD.png" style="width:600px; height:auto;" alt="Domain-Driven Design">

#### 6.2.1.2. Code Quality & Code Security
La calidad del código y la seguridad son pilares fundamentales para garantizar el desarrollo de software confiable y sostenible.

- **Calidad del Código:**
La evaluación de la calidad del código debe apoyarse en métricas objetivas como la cobertura de pruebas y la complejidad ciclomática. Para ello, es recomendable emplear herramientas como SonarQube, que permite realizar un monitoreo continuo de la calidad del código. Esta herramienta proporciona un análisis detallado, identifica defectos potenciales y ofrece sugerencias para optimizar el rendimiento y la mantenibilidad del software, asegurando el cumplimiento de los estándares definidos.

- **Seguridad del Código:**
La protección del sistema requiere detectar y prevenir vulnerabilidades comunes, como inyecciones SQL y cross-site scripting (XSS), mediante revisiones constantes del código fuente. Aplicar prácticas de codificación segura y validar correctamente las entradas del usuario son medidas clave para minimizar riesgos y fortalecer la integridad del software.

- **Herramienta de Apoyo – SonarLint:**
Para reforzar el enfoque en calidad y seguridad, se recomienda el uso de SonarLint, una herramienta que realiza análisis de código en tiempo real dentro del entorno de desarrollo. SonarLint se integra con IDEs populares como IntelliJ IDEA, Eclipse y Visual Studio, ayudando a los desarrolladores a detectar errores y vulnerabilidades mientras programan. Ofrece recomendaciones inmediatas, promoviendo una cultura de mejora continua desde las primeras etapas del desarrollo y evitando que los problemas lleguen a fases críticas como revisión o pruebas.

<img src="../../assets/img/chapter-VI/Sonarlint.png" style="width:600px; height:auto;" alt="Sonarlint">

### 6.2.2. Reviews
## 6.3. Validation Interviews
### 6.3.1. Diseño de Entrevistas
### 6.3.2. Registro de Entrevistas
### 6.3.3. Evaluaciones según heurísticas

## 6.4. Auditoría de Experiencias de Usuario
### 6.4.1. Auditoría realizada
#### 6.4.1.1. Información del grupo auditado
#### 6.4.1.2. Cronograma de auditoría realizada
#### 6.4.1.3. Contenido de auditoría realizada
### 6.4.2. Auditoría recibida
#### 6.4.2.1. Información del grupo auditor
#### 6.4.2.2. Cronograma de auditoría recibida
#### 6.4.2.3. Contenido de auditoría recibida
#### 6.4.2.4. Resumen de modificaciones para subsanar hallazgos
