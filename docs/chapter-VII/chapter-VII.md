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

## 7.3. Continuous Deployment
### 7.3.1. Tools and Practices
### 7.3.2. Production Deployment Pipeline Components

## 7.4. Continuous Monitoring
### 7.4.1. Tools and Practices
### 7.4.2. Monitoring Pipeline Components
### 7.4.3. Alerting Pipeline Components
### 7.4.4. Notification Pipeline Components
