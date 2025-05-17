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

# **CAPÍTULO VII: DEVOPS PRACTICES**

## 7.1. Continuous Integration
### 7.1.1. Tools and Practices

En el contexto del desarrollo y las pruebas de software, resulta fundamental disponer de herramientas y enfoques que garanticen tanto la calidad del código como la eficiencia del equipo de trabajo. Dentro de nuestro flujo de desarrollo, utilizamos diversas herramientas que facilitan la construcción, verificación y validación del funcionamiento esperado de la aplicación. Estas soluciones cubren múltiples etapas del ciclo de vida del software, desde la codificación hasta la ejecución de pruebas automatizadas.

Adoptamos metodologías como el Desarrollo Guiado por Pruebas (TDD) y el Desarrollo Basado en Comportamiento (BDD), lo que nos permite asegurar que nuestros productos no solo respondan a los requerimientos funcionales del cliente, sino que también mantengan estándares elevados de calidad técnica. A continuación, se detallan algunas de las herramientas clave que empleamos:

| Herramienta | Tipo                              | Descripción                                                                                          | Propósito                                                                                          |
|-------------|-----------------------------------|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| J Unit      | Herramienta para pruebas (TDD)    | Es un programa que ayuda a probar pequeñas partes de aplicaciones en Java.                          | Hace más fácil crear y ejecutar pruebas para asegurarse de que las funciones de los componentes funcionen como deberían. |
| Mockito     | Herramienta de simulaciones (TDD) | Permite crear versiones simuladas de otros componentes para hacer pruebas sin usar las versiones reales. | Imitar cómo se comportan objetos externos, lo cual es útil para hacer pruebas de forma efectiva.   |
| Cucumber    | Herramienta de BDD                | Ayuda a desarrollar programas centrándose en el comportamiento, usando un lenguaje simple llamado Gherkin para escribir ejemplos que todos entienden. | Crea y prueba ejemplos basados en cómo debería comportarse el sistema, asegurando que el desarrollo esté alineado con lo que necesita el negocio. |

### 7.1.2. Build & Test Suite Pipeline Components
## 7.2. Continuous Delivery
Su propósito es automatizar la integración y validación del código, asegurando que el sistema esté siempre en condiciones óptimas para ser desplegado en cualquier momento.

### 7.2.1. Tools and Practices

**Tools**:

  - *GitHub Actions / GitLab CLI:*
    - Permiten automatizar todo el flujo de trabajo del pipeline CI/CD. En el caso de Continuous Delivery, es posible configurar una etapa de despliegue final que se ejecute solo tras una intervención manual. Esto garantiza que el software esté listo para producción, pero sin que se despliegue automáticamente, ya que esa acción corresponde al enfoque de Continuous Deployment.

  - *Trello:*
    - Se utiliza como sistema de gestión para controlar la aprobación de despliegues. Puede integrarse de forma que, luego de la validación del pipeline, un gerente de proyecto o administrador deba revisar y autorizar el paso a producción.

  - *Docker:*
    - Al igual que en Continuous Deployment, Docker se emplea para contenerizar la aplicación y asegurar entornos consistentes entre desarrollo, staging y producción. Esto simplifica la validación previa y reduce errores durante los cambios de ambiente.

**Prácticas**

- *Feature Branching y Merge Requests:*
  - Las nuevas funciones se desarrollan en ramas independientes. En Continuous Delivery, dichas ramas se integran a una versión estable una vez que superan las pruebas automatizadas, aunque el despliegue a producción queda sujeto a aprobación manual.

- *Pipeline de Validación en Staging:*
  - Antes de pasar a producción, los cambios son desplegados en un entorno de staging, lo cual permite validar su funcionamiento bajo condiciones similares a las reales. Este entorno puede utilizarse para ejecutar pruebas manuales o recibir comentarios de usuarios clave.

- *Despliegue Semiautomático:*
  - El pipeline deja la aplicación lista para producción, pero el despliegue solo se realiza si un miembro del equipo lo aprueba explícitamente. Esto otorga mayor control y reduce la posibilidad de errores en entornos críticos.

- *Aprobación Manual:*
  - Previo al despliegue final, es necesario que un responsable revise los resultados de las pruebas y dé el visto bueno para avanzar. Esta etapa es crucial para prevenir la liberación de código inadecuado.

- *Rollback Manual:*
  - Aunque algunos pipelines permiten realizar reversiones automáticas ante fallos graves, en Continuous Delivery los rollbacks suelen ser gestionados manualmente por el equipo de desarrollo u operaciones, brindando mayor control sobre las acciones correctivas.

### 7.2.2. Stages Deployment Pipeline Components

**Integración Continua (CI):**
  - Cada vez que se realiza un commit en una rama de desarrollo, se activa el pipeline para ejecutar pruebas automáticas que verifican la estabilidad y funcionamiento del código. Este proceso asegura que el código esté siempre en condiciones óptimas para un eventual despliegue.

**Validación en Staging:**

  - Antes de llevar el código a producción, se valida en un entorno de staging que simula condiciones reales. Esta etapa permite ejecutar pruebas adicionales —como pruebas manuales, de carga o seguridad— para detectar posibles fallos antes del lanzamiento.

**Despliegue Manual:**

  - Aunque el sistema puede dejar el código listo para su liberación, el despliegue final requiere una acción humana. Esta aprobación manual brinda un mayor nivel de control y evita errores que puedan impactar a los usuarios finales.

**Monitoreo y Retroalimentación:**

  - El pipeline incorpora herramientas de observabilidad que permiten analizar el comportamiento del sistema con los nuevos cambios. Esto incluye métricas de rendimiento, estabilidad y errores, lo cual permite tomar decisiones informadas antes de activar el despliegue completo.

**Aprobación del Despliegue:**

  - En este punto, el pipeline queda en pausa hasta que un miembro del equipo (como un desarrollador, administrador o responsable de operaciones) valide los resultados previos y autorice el paso final hacia producción.

## 7.3. Continuous Deployment

El propósito de Continuous Deployment (CD) es permitir que los cambios en el código, una vez validados, se publiquen automáticamente en producción sin requerir intervención manual. Siempre que el código supere todas las pruebas establecidas, cada nueva versión puede ser desplegada de forma continua y confiable desde el entorno de desarrollo hasta el usuario final.

### 7.3.1. Tools and Practices
En esta sección se describen las herramientas y metodologías implementadas para asegurar un despliegue continuo, automatizado y confiable hacia entornos productivos.

- **Tools (Herramientas):**
  - GitHub Actions / GitLab CI:
Se utilizan para automatizar el pipeline completo de CI/CD. Permiten definir workflows que ejecutan pruebas, construyen la aplicación y gestionan el despliegue automático en entornos como desarrollo, staging y producción.

  - Docker:
Se emplea para contenerizar el backend desarrollado en Spring Boot, empaquetando la aplicación junto con sus dependencias. Esto asegura que los entornos de desarrollo, pruebas y producción sean uniformes y reproducibles.

  - Railway:
Es la plataforma usada para alojar y automatizar la base de datos MySQL. Ofrece soporte para migraciones de esquema y backups automáticos, simplificando la gestión del entorno de datos.

  - Render:
Plataforma destinada al despliegue automático del backend en Spring Boot. Brinda capacidades de monitoreo, escalabilidad y administración del entorno de ejecución con mínima intervención manual.

  - Firebase Hosting:
Se encarga del despliegue del frontend construido en Angular. Esta herramienta facilita un despliegue rápido, seguro y automatizado de la aplicación web.
<br>

- **Prácticas**
  - Feature Branching:
Los desarrolladores trabajan en nuevas funcionalidades dentro de ramas específicas. Una vez que se completan y validan, estas se integran a la rama develop, la cual está configurada para gestionar los despliegues hacia producción.

  - Despliegue basado en commits:
Cada vez que se realiza un commit en la rama develop, se activa automáticamente el pipeline de CI/CD, que ejecuta los procesos de construcción, validación y despliegue. Este flujo garantiza que los cambios pasen de forma continua y eficiente al entorno productivo.

  - Rollback automático:
En caso de detectar fallos luego del despliegue en producción, el sistema está configurado para revertir automáticamente a la versión estable anterior. Además, se notifica al equipo sobre el incidente, permitiendo una rápida respuesta y asegurando la estabilidad del sistema.

### 7.3.2. Production Deployment Pipeline Components
En esta sección se detallan los elementos que componen el pipeline de despliegue hacia producción, así como la forma en que se interconectan para lograr una automatización completa del proceso.

**Componentes del Pipeline de la Base de Datos (Railway)**
En esta sección se explican los elementos clave que integran el pipeline de despliegue a producción de la base de datos MySQL, administrada mediante la plataforma Railway.

1. **Migraciones Automáticas:**
Cada vez que se realizan modificaciones en las entidades del backend (desarrollado con Spring Boot), el sistema aplica automáticamente los cambios al esquema de la base de datos en Railway. Esto garantiza que la estructura de datos se mantenga alineada con la lógica del código fuente.

2. **Copias de Seguridad Previas:**
Railway genera backups automáticos de la base de datos antes de ejecutar cualquier migración relevante. Esta medida preventiva permite restaurar el estado anterior en caso de que la migración cause errores o pérdida de información.

3. **Supervisión Activa del Estado de la Base de Datos:**
La plataforma ofrece herramientas de monitoreo que permiten analizar el comportamiento de la base de datos tras cada migración. Si se detectan fallos o caídas en el rendimiento, se generan alertas automáticas para que el equipo pueda intervenir oportunamente.

4. **Validación del Esquema Migrado:**
Una vez aplicadas las migraciones, es recomendable ejecutar pruebas automatizadas que verifiquen la integridad del nuevo esquema. Esto incluye la validación de tablas, relaciones y campos recientemente añadidos o modificados mediante scripts específicos.

5. **Despliegue Automatizado a Producción:**
Tras confirmar que todas las migraciones han sido aplicadas y validadas correctamente, los cambios se actualizan automáticamente en el entorno productivo, lo cual favorece un flujo de desarrollo y entrega continuo, estable y eficiente.

<img src="../../assets/img/chapter-VII/Railway Logo.png" style="width:500px; height:auto;" alt="">

**Componentes del Pipeline del Backend (Render para Spring Boot):**
A continuación, se detallan los pasos que conforman el pipeline de despliegue automatizado del backend desarrollado con Spring Boot, utilizando la plataforma Render.

1. **Integración continua:**
Cada vez que se realiza un commit en la rama develop, Render detecta los cambios y obtiene el código actualizado. A continuación, inicia el proceso de construcción del proyecto utilizando Maven.

2. **Generación de Imagen Docker:**
Render crea automáticamente una imagen Docker del backend, incluyendo todas las dependencias necesarias para su ejecución. Esto garantiza que el entorno de producción sea consistente y replicable.

3. **Despliegue Automatizado:**
Una vez construida la imagen, Render despliega la nueva versión del backend directamente en el servidor de producción, asegurando una actualización fluida y sin intervención manual.

4. **Monitoreo y Alertas:**
Tras el despliegue, Render activa sus herramientas de monitoreo para supervisar el estado y rendimiento de la aplicación. Si se detectan errores o anomalías, el sistema emite alertas automáticas al equipo técnico para una pronta respuesta.

<img src="../../assets/img/chapter-VII/Render Logo.png" style="width:500px; height:auto;" alt="">

<br>

**Componentes del Pipeline del Frontend (Firebase para Angular):**
A continuación, se describen los pasos clave que conforman el pipeline automatizado para el despliegue del frontend desarrollado en Angular, utilizando Firebase Hosting.

1. **Compilación del Proyecto:**
Al detectar un nuevo commit, Firebase CLI inicia automáticamente el proceso de compilación de la aplicación Angular en modo producción, optimizando los recursos para su ejecución en entornos reales.

2. **Ejecución de Pruebas Automatizadas:**
Se llevan a cabo pruebas unitarias y de extremo a extremo (E2E) con el objetivo de verificar que la interfaz funcione correctamente y cumpla con los requisitos funcionales establecidos.

3. **Despliegue en Producción:**
Si todas las pruebas se completan con éxito, Firebase realiza el despliegue automático de la nueva versión del frontend en Firebase Hosting, distribuyéndola a través de una red CDN global para garantizar alta disponibilidad y rendimiento.

4. **Actualización de Caché:**
Una vez desplegada la nueva versión, Firebase invalida la caché anterior para asegurar que todos los usuarios accedan de inmediato a la versión más reciente de la aplicación web.


<img src="../../assets/img/chapter-VII/Firebase Logo.png" style="width:500px; height:auto;" alt="">


## Conclusiones

- La aplicación estructurada del enfoque Lean UX en nuestro proyecto Mushroom ha sido clave para definir con claridad los segmentos de usuarios, los competidores directos y las principales demandas del mercado. Desde los problem statements iniciales hasta los hypothesis statements y el desarrollo del Lean UX canvas, cada fase ha fortalecido tanto la agilidad como la precisión en el diseño y evolución de nuestra solución.
<br>
- A lo largo del capítulo II se llevó a cabo un análisis integral del entorno competitivo, junto con entrevistas y actividades de needfinding, lo cual permitió una comprensión profunda de los usuarios. Esta investigación fundamentó la propuesta de valor de Mushroom, asegurando que la solución responda directamente a necesidades reales del público objetivo.
<br>
- La identificación temprana de los requisitos del proyecto resultó esencial para cimentar una base sólida sobre la cual construir Mushroom. Herramientas como los empathy mappings, impact mappings, user personas, así como los As-Is y To-Be Scenario Mappings, ayudaron a visualizar y comprender los procesos del usuario antes y después de la implementación de nuestra aplicación. A su vez, las user stories detallaron cómo se espera que interactúen los usuarios con la solución, mientras que el product backlog permitió priorizar funcionalidades clave, optimizando el uso de recursos durante el desarrollo.
<br>
- La implementación del backend utilizando Spring Boot, junto con la alineación de los bounded contexts bajo la arquitectura DDD, permitió establecer una estructura técnica robusta y escalable. La documentación generada en Swagger fue fundamental para facilitar la comprensión de los distintos módulos del sistema y mejorar la colaboración entre los miembros del equipo. Además, las entrevistas de validación con usuarios proporcionaron retroalimentación valiosa: destacaron aspectos positivos como la utilidad de la Landing Page y la facilidad de navegación en la Web App, pero también señalaron oportunidades de mejora en aspectos como el diseño, la presentación de información y la navegación general. Estos aprendizajes ofrecen una base sólida para futuras iteraciones centradas en elevar la experiencia del usuario y la eficacia del producto final.

## Bibliografia

1. Lean UX, diseño centrado en el usuario y validación:

- Gothelf, J., & Seiden, J. (2021). Lean UX: Designing Great Products with Agile Teams (3rd ed.). O’Reilly Media.
- Norman, D. A. (2023). The Design of Everyday Things: Revised and Expanded Edition. Basic Books.
- Nielsen Norman Group. (2020-2024). UX Research & User-Centered Design.

2. Arquitectura backend, Spring Boot y DDD
- Evans, E. (2021). Domain-Driven Design: Tackling Complexity in the Heart of Software. Addison-Wesley.
- Walls, C. (2022). Spring in Action (6th ed.). Manning Publications.
- Richardson, C. (2019). Microservices Patterns: With examples in Java. Manning Publications.

3. Documentación de APIs y Swagger
- SmartBear Software. (2023). OpenAPI Specification (Swagger). https://swagger.io/specification/

4. UX y herramientas de diseño
- Interaction Design Foundation. (2023). User Personas, Journey Mapping, As-Is & To-Be Scenarios. https://www.interaction-design.org

5. Informacion de nuestra problematica:

India Briefing. (2024, enero 10). La actual crisis del Mar Rojo obliga al transporte marítimo mundial a buscar nuevas rutas. https://www.india-briefing.com/news/la-actual-crisis-del-mar-rojo-obliga-al-transporte-maritimo-mundial-a-buscar-nuevas-rutas-31590.html

- El Economista. (2024, enero 12). Tesla y Volvo frenan su producción de autos por la crisis del transporte marítimo en el mar Rojo. https://www.eleconomista.com.mx/empresas/Tesla-y-Volvo-frenan-su-produccion-de-autos-por-la-crisis-del-transporte-maritimo-en-el-mar-Rojo-20240112-0042.html


