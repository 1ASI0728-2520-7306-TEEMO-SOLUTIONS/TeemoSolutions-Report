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

# **Capítulo V: Tactical-Level Software Design**

En esta sección, el equipo aborda el diseño táctico de la solución siguiendo los principios de Domain‑Driven Design (DDD), traduciendo los Bounded Contexts previamente definidos en patrones y estructuras de código concretos. Cada sección se centra en uno de los contextos, describiendo sus agregados, repositorios, servicios de dominio y fábricas, así como las variantes y contratos que rigen su comportamiento interno. De este modo, se conecta la visión estratégica del dominio con decisiones de implementación precisas, garantizando que el software refleje fielmente las reglas de negocio y mantenga la coherencia del lenguaje ubicuo.

Para cada Bounded Context, se propone una arquitectura modular basada en capas tácticas, modelos de entidad, lógica de dominio, interfaces de infraestructura y adaptadores, y se aplican patrones de diseño. Además, se incluyen diagramas de clases. Este enfoque permite iterar rápidamente sobre el diseño interno sin perder alineación con los objetivos del negocio ni generar acoplamientos indebidos entre contextos (Ford et al., 2021).

### 5.1. Bounded Context: IAM (Identity and Access Management)

En el contexto táctico, el Bounded Context IAM (Identity and Access Management) agrupa toda la funcionalidad relacionada con la identificación, autenticación y autorización de los usuarios de Mushroom. Este módulo centraliza el ciclo de vida de las cuentas: desde el registro y recuperación de credenciales hasta la gestión segura de sesiones. Incluye la generación y validación de JSON Web Tokens (access y refresh tokens) para mantener la persistencia de las sesiones sin comprometer la seguridad. Además, IAM ejerce el control de permisos y roles, definiendo y verificando privilegios de usuario conforme a las políticas establecidas, y expone interfaces limpias para su consumo por otros bounded contexts, garantizando una fuente única de verdad en toda la plataforma.

#### 5.1.1. IAM Bounded Context Domain Layer

En la capa de dominio de IAM se definen las entidades y objetos de valor esenciales junto con sus reglas de negocio. Además, en este nivel residen los Domain Services encargados de orquestar procesos complejos, garantizando la coherencia y la reutilización de toda la lógica central.


---

##  User 

## **AuditableAbstractAggregateRoot** 

###### Tabla 17

## Tabla de AuditableAbstractAggregateRoot en el Domain Layer 

| Propiedad     | Valor                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | AuditableAbstractAggregateRoot<T extends AbstractAggregateRoot<T>>                                                                        |
| **Categoría** | Base Class (Aggregate Root con auditoría)                                                                                                 |
| **Propósito** | Proveer a los aggregate roots campos de identificación y auditoría (**id**, **createdAt**, **updatedAt**) y soporte de eventos de dominio |

###### Tabla 2

## Atributos de AuditableAbstractAggregateRoot

| Nombre    | Tipo de dato | Visibilidad | Descripción                               |
| --------- | ------------ | ----------- | ----------------------------------------- |
| id        | `String`     | private     | Identificador único (`@Id` en MongoDB)    |
| createdAt | `Date`       | private     | Fecha de creación (`@CreatedDate`)        |
| updatedAt | `Date`       | private     | Última modificación (`@LastModifiedDate`) |

---

## **User**

###### Tabla 18

## Tabla de User en el Domain Layer 

| Propiedad     | Valor                                                                                                      |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Nombre**    | User                                                                                                       |
| **Categoría** | Aggregate Root (extiende `AuditableAbstractAggregateRoot<User>`)                                           |
| **Propósito** | Representar a un usuario del sistema con credenciales y roles, con trazabilidad de creación/actualización. |

###### Tabla 19

## Atributos de User

| Nombre    | Tipo de dato | Visibilidad | Descripción                                                               |
| --------- | ------------ | ----------- | ------------------------------------------------------------------------- |
| id        | `String`     | inherited   | Identificador único (heredado de la clase base)                           |
| createdAt | `Date`       | inherited   | Fecha de creación (heredado)                                              |
| updatedAt | `Date`       | inherited   | Fecha de última modificación (heredado)                                   |
| username  | `String`     | private     | Nombre de usuario (`@NotBlank`, `@Size(max=50)`)                          |
| password  | `String`     | private     | Contraseña **codificada/hasheada** (`@NotBlank`, `@Size(max=120)`)        |
| roles     | `Set<Role>`  | private     | Conjunto de roles asociados al usuario (inicializa con `new HashSet<>()`) |

###### Tabla 20

# Métodos de User

| Nombre                                                   | Tipo de retorno | Visibilidad | Descripción                                                                                    |
| -------------------------------------------------------- | --------------- | ----------- | ---------------------------------------------------------------------------------------------- |
| User()                                                   | — (ctor)        | public      | Constructor por defecto. Inicializa `roles` como `HashSet<>`.                                  |
| User(String username, String password)                   | — (ctor)        | public      | Constructor básico con username/password.                                                      |
| User(String username, String password, List<Role> roles) | — (ctor)        | public      | Constructor con roles iniciales (invoca `addRoles`).                                           |
| addRoles(List<Role> roles)                               | `void`          | public      | Valida y agrega roles mediante `Role.validateRoleSet`; asegura set no vacío (rol por defecto). |

---

## Role

###### Tabla 21

## Tabla de Role

| Propiedad     | Valor                                                     |
| ------------- | --------------------------------------------------------- |
| **Nombre**    | Role                                                      |
| **Categoría** | Entity (`@Document(collection = "roles")`)                |
| **Propósito** | Representar un rol del sistema basado en el enum `Roles`. |

###### Tabla 22

## Atributos de Role

| Nombre | Tipo de dato | Visibilidad | Descripción                                  |
| ------ | ------------ | ----------- | -------------------------------------------- |
| id     | `String`     | private     | Identificador único del rol (`@Id`)          |
| name   | `Roles`      | private     | Valor del rol (`ROLE_USER`, `ROLE_ADMIN`, …) |

###### Tabla 23

## Métodos de Role

| Nombre                      | Tipo de retorno | Visibilidad   | Descripción                                                                    |
| --------------------------- | --------------- | ------------- | ------------------------------------------------------------------------------ |
| Role(Roles name)            | — (ctor)        | public        | Crea un rol con el valor del enum.                                             |
| getStringName()             | `String`        | public        | Devuelve el nombre del enum (`name.name()`).                                   |
| getDefaultRole()            | `Role`          | public static | Retorna el rol por defecto (`ROLE_USER`).                                      |
| toRoleFromName(String name) | `Role`          | public static | Convierte el nombre a enum y construye `Role`.                                 |
| validateRoleSet(List<Role>) | `List<Role>`    | public static | Si null/vacía → `[getDefaultRole()]`; en otro caso, retorna la lista provista. |

---

## Roles (enum)

###### Tabla 24

## Tabla de Roles

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | Roles                                                   |
| **Categoría** | Enum                                                    |
| **Propósito** | Definir los valores válidos para los roles del sistema. |

###### Tabla 25

## Valores de Roles

| Valor             | Descripción                               |
| ----------------- | ----------------------------------------- |
| `ROLE_USER`       | Rol por defecto de usuario final.         |
| `ROLE_ADMIN`      | Rol administrativo.                       |
| `ROLE_INSTRUCTOR` | Rol de instructor (si aplica al dominio). |

---


#### 5.1.2. IAM Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de IAM se exponen los endpoints necesarios para interactuar con las funcionalidades de autenticación, autorización y gestión de usuarios. A través de controladores especializados, esta capa actúa como punto de entrada para solicitudes externas, facilitando la comunicación entre clientes (como aplicaciones web o móviles) y la lógica de negocio. Su diseño busca garantizar una separación clara de responsabilidades, manteniendo la simplicidad en la orquestación de comandos y consultas sin comprometer la seguridad ni la escalabilidad del sistema.

**UserController:**

###### Tabla 39

_Tabla de SessionToken en el Interface Layer de IAM_

| Propiedad     | Valor                                      |
|---------------|--------------------------------------------|
| **Nombre**    | UserController                             |
| **Categoría** | Controller                                 |
| **Propósito** | Exponer endpoints para gestión de usuarios |
| **Ruta**      | `/api/users`                               |

###### Tabla 40

_Tabla de métodos de SessionToken en el Interface Layer de IAM_

| Nombre         | Ruta                 | Acción                          | Handle                                                           |
|----------------|----------------------|---------------------------------|------------------------------------------------------------------|
| GetById        | `/{userId}`          | Obtiene los datos de un usuario | `GetUserByIdQuery`                                               |
| ChangeName     | `/{userId}/name`     | Cambia `FullName`               | `ChangeUserNameCommand`                                          |
| ChangeEmail    | `/{userId}/email`    | Cambia `Email`                  | `ChangeUserEmailCommand`                                         |
| ChangePassword | `/{userId}/password` | Cambia `PasswordHash`           | `ChangeUserPasswordCommand`                                      |
| ChangeStatus   | `/{userId}/status`   | Cambia `Status`                 | `ActivateUserCommand`, `SuspendUserCommand`, `DeleteUserCommand` |

**AuthController**

###### Tabla 41

_Tabla de AuthController en el Interface Layer de IAM_

| Propiedad     | Valor                                                                 |
|---------------|-----------------------------------------------------------------------|
| **Nombre**    | AuthController                                                        |
| **Categoría** | Controller                                                            |
| **Propósito** | Encargado de todo lo relacionado con registro y autenticación         |
| **Ruta**      | `/api/auth`                                                           |

###### Tabla 42

_Tabla de métodos de AuthController en el Interface Layer de IAM_

| Nombre   | Ruta         | Acción                                    | Handle                     |
|----------|--------------|-------------------------------------------|----------------------------|
| Register | `/register`  | Crea un nuevo usuario                     | `RegisterUserCommand`      |
| Login    | `/login`     | Valida credenciales y devuelve token      | `LoginUserCommand`         |
| Refresh  | `/refresh`   | Renueva el acceso; nuevo token            | `~`                        |
| Logout   | `/logout`    | Revoca el token activo                    | `RevokeSessionCommand`     |

#### 4.2.1.3. IAM Bounded Context Application Layer 

La capa de aplicación del Bounded Context de IAM coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin mezclar reglas de negocio. Aquí residen los Command Handlers, Query Handlers y Event Handlers, responsables de ejecutar operaciones como el registro, inicio o cierre de sesión, así como la gestión de eventos relacionados con la identidad de los usuarios. Esta capa asegura que las acciones se realicen de manera transaccional, manteniendo la integridad del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según corresponda.

**UserRegisterCommandHandler:**

###### Tabla 43

_Tabla de UserRegisterCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                      |
|---------------|----------------------------|
| **Nombre**    | UserRegisterCommandHandler |
| **Categoría** | Command Handler            |
| **Propósito** | Registrar un usuario       |
| **Comando**   | RegisterUserCommand        |

**UserLoginCommandHandler:**

###### Tabla 44

_Tabla de UserLoginCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                       |
|---------------|-----------------------------|
| **Nombre**    | UserLoginCommandHandler     |
| **Categoría** | Command Handler             |
| **Propósito** | Iniciar sesión a un usuario |
| **Comando**   | LoginUserCommand            |

**UserLogoutCommandHandler:**

###### Tabla 45

_Tabla de UserLogoutCommandHandler en el Application Layer de IAM_

| Propiedad     | Valor                       |
|---------------|-----------------------------|
| **Nombre**    | UserLogoutCommandHandler    |
| **Categoría** | Command Handler             |
| **Propósito** | Cerrar sesión de un usuario |
| **Comando**   | LogoutUserCommand           |

**RegisteredUserEventHandle:r**

###### Tabla 46

_Tabla de RegisteredUserEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | RegisteredUserEventHandler          |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserRegisteredEvent                 |

**UserLoggedInEventHandler:**

###### Tabla 47

_Tabla de UserLoggedInEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | UserLoggedInEventHandler            |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedInEvent                   |

**UserLoggedOutEventHandler:**

###### Tabla 48

_Tabla de UserLoggedOutEventHandler en el Application Layer de IAM_

| Propiedad     | Valor                               |
|---------------|-------------------------------------|
| **Nombre**    | UserLoggedOutEventHandler           |
| **Categoría** | Event Handler                       |
| **Propósito** | Gestionar el registro de un usuario |
| **Evento**    | UserLoggedOutEvent                  |

#### 4.2.1.4. Infrastructure Layer

La capa de infraestructura del Bounded Context de IAM actúa como el puente entre la lógica de negocio y los mecanismos técnicos de persistencia, comunicación y ejecución. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, proveedores de autenticación, mecanismos de almacenamiento de sesiones y otros servicios externos o compartidos.

Esta capa concreta las abstracciones definidas en el dominio mediante implementaciones de repositorios. Su diseño busca mantener el desacoplamiento respecto a la lógica central, permitiendo la evolución tecnológica sin comprometer la integridad del dominio. Además, garantiza la eficiencia, seguridad y confiabilidad en la gestión de identidades, roles y sesiones, alineándose con los objetivos funcionales y no funcionales del sistema.

**UserRepository:**

###### Tabla 49

_Tabla de UserRepository en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | UserRepository                            |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `IUserRepository`                         |

**SessionRepository:**

###### Tabla 50

_Tabla de SessionRepository en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                     |
|---------------|-------------------------------------------|
| **Nombre**    | SessionRepository                         |
| **Categoría** | Repositorio                               |
| **Propósito** | Persistir y consultar entidades de `User` |
| **Interfaz**  | `ISessionRepository`                      |

**AppDbContext:**

###### Tabla 51

_Tabla de AppDbContext en el Infraestructure Layer de IAM_

| Propiedad     | Valor                                          |
|---------------|------------------------------------------------|
| **Nombre**    | AppDbContext                                   |
| **Categoría** | ORM Context                                    |
| **Propósito** | Punto central de acceso a la base de datos     |

#### 4.2.1.5. IAM Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de IAM. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales del contexto de gestión de identidad y acceso.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y seguridad del sistema.

###### Figura 80
*Participación del Bounded Context de IAM con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-MobileComponent.png"></image>

###### Figura 81
*Participación del Bounded Context de IAM con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-WebComponent.png"></image>

###### Figura 82
*Participación del Bounded Context de IAM con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-IAM-APIComponent.png"></image>

#### 4.2.1.6. IAM Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de IAM, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.1.6.1. IAM Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica de dominio, así como sus relaciones fundamentales. El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y su rol dentro del modelo.

Asimismo, se incluyen las relaciones entre elementos del dominio, calificadas con nombres descriptivos, direccionalidad cuando corresponde, y multiplicidad para reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada del diseño táctico favorece la comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación efectiva dentro de la arquitectura de software.

###### Figura 83
*Diagrama de clases de la capa de dominio del Bounded Context de IAM*

<image src="../assets/img/capitulo-4/bounded-context-iam/class-diagram.png"></image>

##### 4.2.1.6.2. IAM Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación permite visualizar de forma estructurada y precisa las clases, interfaces y enumeraciones que conforman la lógica de dominio, junto con sus atributos, métodos y responsabilidades específicas dentro del modelo.

El diagrama incluye detalles esenciales como el tipo de dato y la visibilidad de cada miembro, así como las relaciones entre los distintos elementos del dominio. Estas relaciones están calificadas con nombres descriptivos, indican la dirección cuando aplica, e incorporan multiplicidades para representar con fidelidad la cardinalidad de cada asociación.

Esta visualización detallada contribuye significativamente a la comprensión compartida del modelo conceptual, funcionando como un nexo clave entre el análisis de dominio y su posterior implementación en la arquitectura del sistema.

###### Figura 84
*Diagrama de base de datos del Bounded Context de IAM*

<image src="../assets/img/capitulo-4/bounded-context-iam/database-diagram.png"></image>

---

### 4.2.2. Bounded Context: Profile and Preferences

En el contexto táctico, el Bounded Context Profiles and Preferences concentra toda la funcionalidad relacionada con la gestión personalizada de los perfiles de usuario en la plataforma Mushroom. Este módulo se encarga de almacenar, actualizar y exponer información detallada sobre las preferencias individuales, hábitos de uso, configuraciones personalizadas y características del entorno del usuario. Entre sus responsabilidades se incluyen la edición de datos personales no sensibles y la persistencia de hábitos o preferencias.

Profiles and Preferences permite adaptar la experiencia digital a las necesidades particulares de cada usuario, y lo hace mediante una interfaz limpia e interoperable, disponible para otros bounded contexts. Al ofrecer un punto centralizado para el perfilado y la personalización, garantiza consistencia, reutilización y separación de preocupaciones dentro de la arquitectura de la solución.

#### 4.2.2.1. Profile and Preferences Bounded Context Domain Layer

En la capa de dominio de Profiles and Preferences se modelan las entidades, objetos de valor y reglas de negocio fundamentales asociadas a la gestión de perfiles y preferencias personalizadas. Esta capa encapsula la lógica central vinculada al almacenamiento, validación y actualización de datos relacionados con la configuración del usuario, sus preferencias de uso y hábitos de interacción con la plataforma. Asimismo, se definen los Domain Services responsables de coordinar operaciones complejas que involucran múltiples objetos, asegurando la coherencia del comportamiento del sistema y promoviendo su reutilización en otros contextos.


> **Límite del BC:** Perfil NO gestiona credenciales ni roles; solo datos de cuenta y preferencias ligadas a UX/operación.

## **Profile**

###### Tabla 11

## Tabla de Profile en el Domain Layer 

| Propiedad     | Valor                                                                                 |
| ------------- | ------------------------------------------------------------------------------------- |
| **Nombre**    | Profile                                                                               |
| **Categoría** | Aggregate Root (puede extender la clase base auditable si se desea consistencia)      |
| **Propósito** | Gestionar datos de cuenta y preferencias del usuario (no sensibles de autenticación). |

###### Tabla 12

## Atributos de Profile

| Nombre               | Tipo de dato           | Visibilidad | Descripción                                                    |
| -------------------- | ---------------------- | ----------- | -------------------------------------------------------------- |
| id                   | `String`               | private     | Identificador del perfil (propio del BC Profile).              |
| userId               | `String`               | private     | Identificador del usuario en **User BC** (referencia cruzada). |
| displayName          | `String`               | private     | Nombre mostrado.                                               |
| fullName             | `FullName`             | private     | VO con nombre completo (opcional si usas solo `displayName`).  |
| avatarUrl            | `String`               | private     | URL del avatar.                                                |
| phone                | `String`               | private     | Teléfono de contacto.                                          |
| locale               | `String`               | private     | Idioma preferido (ej. `es-PE`).                                |
| timezone             | `String`               | private     | Zona horaria (ej. `America/Lima`).                             |
| notificationSettings | `NotificationSettings` | private     | Preferencias de notificación (email/push/quiet hours).         |
| createdAt            | `Date`                 | private     | Fecha de creación.                                             |
| updatedAt            | `Date`                 | private     | Última modificación.                                           |

###### Tabla 13

## Métodos de Profile

| Nombre                 | Tipo de retorno | Visibilidad | Descripción                                             |
| ---------------------- | --------------- | ----------- | ------------------------------------------------------- |
| changeDisplayName(...) | `void`          | public      | Actualiza el nombre mostrado.                           |
| updateFullName(...)    | `void`          | public      | Modifica `FullName`.                                    |
| changeAvatarUrl(...)   | `void`          | public      | Actualiza el avatar.                                    |
| updateContactInfo(...) | `void`          | public      | Actualiza teléfono y datos de contacto.                 |
| updatePreferences(...) | `void`          | public      | Actualiza `notificationSettings`, `locale`, `timezone`. |

---

## FullName 

###### Tabla 14

## Tabla de FullName 

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | FullName                                   |
| **Categoría** | Value Object                               |
| **Propósito** | Representar el nombre completo del usuario |

###### Tabla 15

## Atributos de FullName

| Nombre    | Tipo de dato | Visibilidad | Descripción |
| --------- | ------------ | ----------- | ----------- |
| name      | `string`     | private     | Nombres     |
| lastNames | `string`     | private     | Apellidos   |

---

### **NotificationSettings** (VO en Profile)

###### Tabla 16

## Tabla de NotificationSettings

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | NotificationSettings                                   |
| **Categoría** | Value Object                                           |
| **Propósito** | Encapsular preferencias de notificaciones del usuario. |

###### Tabla 17

## Atributos de NotificationSettings

| Nombre     | Tipo de dato | Visibilidad | Descripción                                     |
| ---------- | ------------ | ----------- | ----------------------------------------------- |
| emailOptIn | `boolean`    | private     | Recibir notificaciones por email.               |
| pushOptIn  | `boolean`    | private     | Recibir notificaciones push.                    |
| quietHours | `String`     | private     | Ventanas de silencio (ej. `22:00-07:00` local). |

---



#### 4.2.2.2. Profile and Preferences Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Profiles and Preferences se exponen los endpoints necesarios para gestionar la información de perfil de usuario y sus preferencias personalizadas dentro de la plataforma Macetech. A través de controladores dedicados, esta capa actúa como intermediaria entre las aplicaciones cliente y la lógica de negocio, permitiendo operaciones como la visualización, edición y actualización de datos personales y configuraciones. Su diseño promueve una arquitectura segura, enfocada en mantener una experiencia fluida y adaptable para el usuario sin comprometer la coherencia del sistema.

#### 4.2.2.3. Profile and Preferences Bounded Context Application Layer

La capa de aplicación del Bounded Context de Profiles and Preferences coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se implementan los Command Handlers, Query Handlers y Event Handlers responsables de operaciones como la edición de información personal, actualización de preferencias del usuario y notificación de cambios relevantes. Su rol es garantizar que dichas acciones se ejecuten de forma consistente y transaccional, delegando la lógica central al dominio y apoyándose en la infraestructura cuando sea necesario, manteniendo así la cohesión funcional del sistema.

#### 4.2.2.4. Profile and Preferences Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Profile and Preferences sirve como enlace entre la lógica de negocio y los mecanismos técnicos que permiten la persistencia y comunicación con recursos externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, servicios de almacenamiento y otros módulos relevantes que permiten gestionar la información de perfil y preferencias de los usuarios.

Esta capa materializa las abstracciones definidas en el dominio mediante la implementación de repositorios y adaptadores técnicos. Su diseño favorece el desacoplamiento de la lógica central, facilitando la evolución tecnológica sin afectar la integridad del modelo. Asimismo, asegura una gestión consistente, eficiente y segura de los datos personales, configuraciones y preferencias del usuario, en línea con los objetivos funcionales y no funcionales del sistema.

#### 4.2.2.5. Profile and Preferences Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Profiles and Preferences. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías utilizadas y las interacciones entre ellos. Esta representación es fundamental para comprender en detalle cómo se organiza internamente cada parte del sistema, qué funcionalidades asume cada componente, y de qué manera colaboran para gestionar la información personal, preferencias y configuración personalizada del usuario dentro de Mushroom.

Tal como establece el C4 Model, el nivel de componentes representa el cuarto nivel de abstracción en la visualización de arquitecturas de software, y resulta especialmente útil para desarrolladores y arquitectos al ofrecer una visión clara de las decisiones de diseño adoptadas en cada contenedor (Brown, 2023). Este nivel facilita la trazabilidad entre los elementos de alto nivel y su implementación específica, fortaleciendo la mantenibilidad, extensibilidad y coherencia del sistema.

###### Figura 85
*Participación del Bounded Context de Profile and Preferences con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-MobileComponent.png"></image>

###### Figura 86
*Participación del Bounded Context de Profile and Preferences con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-WebComponent.png"></image>

###### Figura 87
*Participación del Bounded Context de Profile and Preferences con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Profile-APIComponent.png"></image>

#### 4.2.2.6. Profile and Preferences Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Profiles and Preferences, presentando diagramas que permiten visualizar con mayor precisión la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos del sistema que gestionan la configuración del perfil de usuario, sus intereses, preferencias y datos personales.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico y la implementación concreta. Esta aproximación garantiza que las decisiones tomadas a nivel táctico se materialicen en estructuras coherentes, sólidas y alineadas con los objetivos funcionales del contexto, brindando claridad y sostenibilidad al proceso de desarrollo y evolución del sistema.

##### 4.2.2.6.1. Profile and Preferences Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que componen la lógica de dominio relacionada con la gestión del perfil del usuario, sus intereses, configuraciones personalizadas y preferencias de interacción dentro del ecosistema de Macetech.

El nivel de detalle incluye la definición de atributos y métodos para cada clase, especificando sus tipos de datos, visibilidad y rol dentro del modelo, así como las relaciones fundamentales entre los distintos elementos del dominio. Estas relaciones se representan con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, lo que permite reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada facilita una comprensión común del modelo conceptual, sirviendo como puente entre el diseño del dominio y su posterior implementación técnica.

###### Figura 88
*Diagrama de clases de la capa de dominio del Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/class-diagram-profile-and-personal-data.png"></image>

##### 4.2.2.6.2. Profile and Preferences Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las entidades persistentes asociadas a la gestión de perfiles, intereses y preferencias del usuario, junto con sus atributos clave, tipos de datos, claves primarias y foráneas, y restricciones asociadas.

El diagrama refleja las relaciones entre las distintas tablas o entidades, indicando la dirección de las asociaciones, su naturaleza y la cardinalidad, lo que facilita el entendimiento de la estructura lógica que respalda el almacenamiento y la recuperación eficiente de datos dentro de este contexto.

Esta visualización resulta esencial para asegurar la coherencia entre el modelo conceptual y su implementación en la capa de persistencia, contribuyendo a una arquitectura sólida, escalable y alineada con los requerimientos funcionales y no funcionales del sistema.

###### Figura 89
*Diagrama de base de datos del Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/database-diagram-profile-and-personal-data.png"></image>

---

### 4.2.3. Bounded Context: Asset & Resource Management

En el contexto táctico, el Bounded Context Asset & Resource Management agrupa toda la funcionalidad vinculada a la administración de activos físicos y recursos operativos dentro del ecosistema Macetech. Este módulo se encarga del registro, monitoreo y mantenimiento de los dispositivos IoT desplegados (como sensores de humedad, temperatura, pH, entre otros), permitiendo llevar un control detallado de su estado, ubicación, historial de intervenciones y condiciones operativas.

Asset & Resource Management centraliza el ciclo de vida de cada dispositivo, desde su activación inicial hasta su posible retiro o sustitución, asegurando trazabilidad completa y continuidad en la gestión técnica. Asimismo, incorpora mecanismos para la asignación de recursos a usuarios o entornos específicos, facilitando una administración eficiente y contextualizada. Este bounded context expone interfaces estandarizadas para permitir su integración con otros contextos funcionales, y actúa como fuente confiable de verdad sobre los activos tecnológicos desplegados en la plataforma.

#### 4.2.3.1. Asset & Resource Management Bounded Context Domain Layer

En la capa de dominio de Asset & Resource Management se definen las entidades y objetos de valor fundamentales relacionados con los puertos y mapas de navegación presentados en la aplicación. Esta capa encapsula las reglas de negocio desde la definición de cada puerto y su ubicación exacta, la revisión del estado de cada puerto y la selección de un puerto de inicio y uno final. Además, en este nivel se ubican los Domain Services encargados de la entrega de información de cada puerto específico para su visualización por el usuario, asegurando coherencia, integridad y rendimiento.

#### 4.2.3.2. Asset & Resource Management Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Asset & Resource Management se exponen los endpoints necesarios para gestionar la información relacionada a cada puerto integrado en la página de Mushroom. Su diseño promueve una separación clara de responsabilidades, orquestando de forma eficiente comandos y consultas, al tiempo que garantiza trazabilidad, disponibilidad y consistencia de los recursos gestionados.

#### 4.2.3.3. Asset & Resource Management Bounded Context Application Layer

La capa de aplicación del Bounded Context de Asset & Resource Management coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones como el registro, actualización y seguimiento del estado de los puertos de Mushroom, así como el procesamiento de eventos vinculados a sus estados y ubicación exacta. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

#### 4.2.2.4. Asset & Resource Management Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Asset & Resource Management actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, coordenadas y representación de mapas de forma adecuada.

Esta capa concreta las abstracciones del dominio a través de implementaciones de repositorios y componentes técnicos especializados. Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la gestión de los puertos y sus respectivos estados operativos, en línea con los requerimientos estratégicos de la solución.

#### 4.2.3.5. Asset & Resource Management Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Asset & Resource Management. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión de de puertos y sus ubicaciones en mapa dentro de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

###### Figura 90
*Participación del Bounded Context de Asset & Resource Management con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-MobileComponent.png"></image>

###### Figura 91
*Participación del Bounded Context de Asset & Resource Management con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-WebComponent.png"></image>

###### Figura 92
*Participación del Bounded Context de Asset & Resource Management con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-APIComponent.png"></image>

#### 4.2.3.6. Asset & Resource Management Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Asset & Resource Management, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.3.6.1. Asset & Resource Management Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Asset & Resource Management. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión de ubicaciones de puertos y estados en la plataforma de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

###### Figura 93
*Diagrama de clases de la capa de dominio del Bounded Context de Asset & Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/class-diagram-pot-management.png"></image>

##### 4.2.3.6.2. Asset & Resource Management Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Asset & Resource Management. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de puertos y estados en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

###### Figura 94
*Diagrama de base de datos del Bounded Context de Asset & Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

---

