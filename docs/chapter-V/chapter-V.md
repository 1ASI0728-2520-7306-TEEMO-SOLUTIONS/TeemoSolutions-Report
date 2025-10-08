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

En la capa de dominio de IAM se definen las entidades y objetos de valor esenciales junto con sus reglas de negocio. Además, en este nivel residen los Domain Services encargados de orquestar procesos complejos, garantizando la coherencia y la reutilización de toda la lógica central referente al control de usuarios y permisos.

**AuditableAbstractAggregateRoot:** 

###### Tabla 24

*Descripción de AuditableAbstractAggregateRoot en el Domain Layer de IAM* 

| Propiedad     | Valor                                                                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | AuditableAbstractAggregateRoot<T extends AbstractAggregateRoot<T>>                                                                        |
| **Categoría** | Base Class (Aggregate Root con auditoría)                                                                                                 |
| **Propósito** | Proveer a los aggregate roots campos de identificación y auditoría (id, createdAt, updatedAt) y soporte de eventos de dominio |

###### Tabla 25

*Atributos de AuditableAbstractAggregateRoot en el Domain Layer de IAM*

| Nombre    | Tipo de dato | Visibilidad | Descripción                               |
| --------- | ------------ | ----------- | ----------------------------------------- |
| id        | `String`     | private     | Identificador único (`@Id` en MongoDB)    |
| createdAt | `Date`       | private     | Fecha de creación (`@CreatedDate`)        |
| updatedAt | `Date`       | private     | Última modificación (`@LastModifiedDate`) |

---

**User:**

###### Tabla 26

*Descripción de User en el Domain Layer de IAM*

| Propiedad     | Valor                                                                                                      |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| **Nombre**    | User                                                                                                       |
| **Categoría** | Aggregate Root (extiende `AuditableAbstractAggregateRoot<User>`)                                           |
| **Propósito** | Representar a un usuario del sistema con credenciales y roles, con trazabilidad de creación/actualización. |

###### Tabla 27

*Atributos de User en el Domain Layer de IAM*

| Nombre    | Tipo de dato | Visibilidad | Descripción                                                               |
| --------- | ------------ | ----------- | ------------------------------------------------------------------------- |
| id        | `String`     | inherited   | Identificador único (heredado de la clase base)                           |
| createdAt | `Date`       | inherited   | Fecha de creación (heredado)                                              |
| updatedAt | `Date`       | inherited   | Fecha de última modificación (heredado)                                   |
| username  | `String`     | private     | Nombre de usuario (`@NotBlank`, `@Size(max=50)`)                          |
| password  | `String`     | private     | Contraseña **codificada/hasheada** (`@NotBlank`, `@Size(max=120)`)        |
| roles     | `Set<Role>`  | private     | Conjunto de roles asociados al usuario (inicializa con `new HashSet<>()`) |

###### Tabla 28

*Métodos de User en el Domain Layer de IAM*

| Nombre                                                   | Tipo de retorno | Visibilidad | Descripción                                                                                    |
| -------------------------------------------------------- | --------------- | ----------- | ---------------------------------------------------------------------------------------------- |
| User()                                                   | — (ctor)        | public      | Constructor por defecto. Inicializa `roles` como `HashSet<>`.                                  |
| User(String username, String password)                   | — (ctor)        | public      | Constructor básico con username/password.                                                      |
| User(String username, String password, List<Role> roles) | — (ctor)        | public      | Constructor con roles iniciales (invoca `addRoles`).                                           |
| addRoles(List<Role> roles)                               | `void`          | public      | Valida y agrega roles mediante `Role.validateRoleSet`; asegura set no vacío (rol por defecto). |

---

**Role:**

###### Tabla 29

*Descripción de Role en el Domain Layer de IAM*

| Propiedad     | Valor                                                     |
| ------------- | --------------------------------------------------------- |
| **Nombre**    | Role                                                      |
| **Categoría** | Entity (`@Document(collection = "roles")`)                |
| **Propósito** | Representar un rol del sistema basado en el enum `Roles`. |

###### Tabla 30

*Atributos de Role en el Domain Layer de IAM*

| Nombre | Tipo de dato | Visibilidad | Descripción                                  |
| ------ | ------------ | ----------- | -------------------------------------------- |
| id     | `String`     | private     | Identificador único del rol (`@Id`)          |
| name   | `Roles`      | private     | Valor del rol (`ROLE_USER`, `ROLE_ADMIN`, …) |

###### Tabla 31

*Métodos de Role en el Domain Layer de IAM*

| Nombre                      | Tipo de retorno | Visibilidad   | Descripción                                                                    |
| --------------------------- | --------------- | ------------- | ------------------------------------------------------------------------------ |
| Role(Roles name)            | constructor       | public        | Crea un rol con el valor del enum.                                             |
| getStringName()             | `String`        | public        | Devuelve el nombre del enum (`name.name()`).                                   |
| getDefaultRole()            | `Role`          | public static | Retorna el rol por defecto (`ROLE_USER`).                                      |
| toRoleFromName(String name) | `Role`          | public static | Convierte el nombre a enum y construye `Role`.                                 |
| validateRoleSet(List<Role>) | `List<Role>`    | public static | Si null/vacía → `[getDefaultRole()]`; en otro caso, retorna la lista provista. |

---

**Roles (enum):**

###### Tabla 32

*Descripción de Roles (enum) en el Domain Layer de IAM*

| Propiedad     | Valor                                                   |
| ------------- | ------------------------------------------------------- |
| **Nombre**    | Roles                                                   |
| **Categoría** | Enum                                                    |
| **Propósito** | Definir los valores válidos para los roles del sistema. |

###### Tabla 33

*Listado de valores de Roles (enum) en el Domain Layer de IAM*

| Valor             | Descripción                               |
| ----------------- | ----------------------------------------- |
| `ROLE_USER`       | Rol por defecto de usuario final.         |
| `ROLE_ADMIN`      | Rol administrativo.                       |

---

#### 5.1.2. IAM Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de IAM se exponen los endpoints necesarios para interactuar con las funcionalidades de autenticación, autorización y gestión de usuarios. A través de controladores especializados, esta capa actúa como punto de entrada para solicitudes externas, facilitando la comunicación entre clientes (como aplicaciones web o móviles) y la lógica de negocio. Su diseño busca garantizar una separación clara de responsabilidades, manteniendo la simplicidad en la orquestación de comandos y consultas sin comprometer la seguridad ni la escalabilidad del sistema.

**AuthenticationController:**

###### Tabla 34

*Descripción de AuthenticationController en el Interface Layer de IAM*

| Propiedad         | Valor                                           |
| ----------------- | ----------------------------------------------- |
| **Nombre**        | AuthenticationController                        |
| **Categoría**     | Controller                                      |
| **Propósito**     | Exponer endpoints para registro y autenticación |
| **Ruta**          | `/api/authentication`                           |
| **Tag (OpenAPI)** | `Authentication`                                |

###### Tabla 35

*Métodos de AuthenticationController en el Interface Layer de IAM*

| Nombre | Ruta       | Acción                     | Handle                                        |
| ------ | ---------- | -------------------------- | --------------------------------------------- |
| signUp | `/sign-up` | Registrar usuario          | `SignUpCommand` → `userCommandService.handle` |
| signIn | `/sign-in` | Autenticar usuario (login) | `SignInCommand` → `userCommandService.handle` |

> **Notas:**
> * `signUp` devuelve `201 Created` con `UserResource` o `400 Bad Request`.
> * `signIn` devuelve `200 OK` con `AuthenticatedUserResource` o `404 Not Found` si las credenciales son inválidas.

---

**RolesController:**

###### Tabla 36

*Descripción de RolesController en el Interface Layer de IAM*

| Propiedad         | Valor                     |
| ----------------- | ------------------------- |
| **Nombre**        | RolesController           |
| **Categoría**     | Controller                |
| **Propósito**     | Exponer catálogo de roles |
| **Ruta**          | `/api/roles`              |
| **Tag (OpenAPI)** | `Roles`                   |

###### Tabla 37

*Métodos de RolesController en el Interface Layer de IAM*

| Nombre      | Ruta | Acción                 | Handle                                         |
| ----------- | ---- | ---------------------- | ---------------------------------------------- |
| getAllRoles | `/`  | Listar todos los roles | `GetAllRolesQuery` → `roleQueryService.handle` |

---

**UsersController:**

###### Tabla 38

*Descripción de UsersController en el Interface Layer de IAM*

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | UsersController                      |
| **Categoría** | Controller                           |
| **Propósito** | Exponer consultas de usuarios (CQRS) |
| **Ruta**      | `/api/v1/users`                      |

###### Tabla 39

*Métodos de UsersController en el Interface Layer de IAM*

| Nombre      | Ruta        | Acción                 | Handle                                         |
| ----------- | ----------- | ---------------------- | ---------------------------------------------- |
| getAllUsers | `/`         | Listar usuarios        | `GetAllUsersQuery` → `userQueryService.handle` |
| getUserById | `/{userId}` | Obtener usuario por ID | `GetUserByIdQuery` → `userQueryService.handle` |

> **Notas:**
> * `getAllUsers`: `200 OK` con `List<UserResource>`.
> * `getUserById`: `200 OK` con `UserResource` o `404 Not Found`.

---

#### 5.1.3. IAM Bounded Context Application Layer 

La capa de aplicación del Bounded Context de IAM coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin mezclar reglas de negocio. Aquí residen los Command Handlers, Query Handlers y Event Handlers, responsables de ejecutar operaciones como el registro, inicio o cierre de sesión, así como la gestión de eventos relacionados con la identidad de los usuarios. 

**Command Handlers:**

###### Tabla 40

*Descripción de SeedRolesCommandHandler en el Application Layer de IAM*

| Propiedad        | Valor                                           |
| ---------------- | ----------------------------------------------- |
| **Nombre**       | SeedRolesCommandHandler                         |
| **Categoría**    | Command Handler                                 |
| **Propósito**    | Crear los roles del sistema |
| **Comando**      | `SeedRolesCommand`                              |
| **Dependencias** | `RoleRepositoryImpl`                            |

###### Tabla 41

*Descripción de SignUpCommandHandler en el Application Layer de IAM*

| Propiedad        | Valor                                                |
| ---------------- | ---------------------------------------------------- |
| **Nombre**       | SignUpCommandHandler                                 |
| **Categoría**    | Command Handler                                      |
| **Propósito**    | Registrar un usuario                                 |
| **Comando**      | `SignUpCommand`                                      |
| **Dependencias** | `UserRepository`, `HashingService`, `RoleRepository` |

###### Tabla 42

*Descripción de SignInCommandHandler en el Application Layer de IAM*

| Propiedad        | Valor                                                     |
| ---------------- | --------------------------------------------------------- |
| **Nombre**       | SignInCommandHandler                                      |
| **Categoría**    | Command Handler                                           |
| **Propósito**    | Autenticar usuario y emitir token                         |
| **Comando**      | `SignInCommand`                                           |
| **Dependencias** | `UserRepository`, `HashingService`, `TokenService`        |
| **Retorno**      | `Optional<ImmutablePair<User, String>>` (usuario + token) |

---

**Event Handlers:**

###### Tabla 43

*Descripción de ApplicationReadyEventHandler en el Application Layer de IAM*

| Propiedad           | Valor                                                 |
| ------------------- | ----------------------------------------------------- |
| **Nombre**          | ApplicationReadyEventHandler                          |
| **Categoría**       | Event Handler (Application Event)                     |
| **Propósito**       | Disparar la siembra de roles al iniciar la aplicación |
| **Comando** | `SeedRolesCommand` -> `RoleCommandService.handle`      |

#### 5.1.4. Infrastructure Layer

La capa de infraestructura del Bounded Context de IAM actúa como el puente entre la lógica de negocio y los mecanismos técnicos de persistencia, comunicación y ejecución. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, proveedores de autenticación, mecanismos de almacenamiento de sesiones y otros servicios externos o compartidos.

Esta capa concreta las abstracciones definidas en el dominio mediante implementaciones de repositorios. Su diseño busca mantener el desacoplamiento respecto a la lógica central, permitiendo la evolución tecnológica sin comprometer la integridad del dominio. Además, garantiza la eficiencia, seguridad y confiabilidad en la gestión de identidades, roles y sesiones, alineándose con los objetivos funcionales y no funcionales del sistema.

**Repositorios:**

###### Tabla 44

*Descripción de RoleRepository en el Infrastructure Layer de IAM*

| Propiedad          | Valor                                       |
| ------------------ | ------------------------------------------- |
| **Nombre**         | RoleRepository                              |
| **Categoría**      | Repositorio                                 |
| **Propósito**      | Persistir y consultar entidades de `Role`   |
| **Interfaz**       | `RoleRepository`                            |
| **Implementación** | `RoleRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `roles` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)       |

###### Tabla 45

*Métodos de RoleRepository y RoleRepositoryImpl en el Infrastructure Layer de IAM*

| Método         | Firma                                   | Descripción                               |
| -------------- | --------------------------------------- | ----------------------------------------- |
| `findByName`   | `Optional<Role> findByName(Roles name)` | Busca un rol por nombre (enum).           |
| `findAll`      | `List<Role> findAll()`                  | Retorna todos los roles.                  |
| `saveRole`     | `void saveRole(Role role)`              | Persiste/actualiza un `Role`.             |
| `existsByName` | `boolean existsByName(Roles name)`      | Verifica existencia de un rol por nombre. |

###### Tabla 46

*Descripción de UserRepository en el Infrastructure Layer de IAM*

| Propiedad          | Valor                                       |
| ------------------ | ------------------------------------------- |
| **Nombre**         | UserRepository                              |
| **Categoría**      | Repositorio                                 |
| **Propósito**      | Persistir y consultar entidades de `User`   |
| **Interfaz**       | `UserRepository`                            |
| **Implementación** | `UserRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `users` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)       |

###### Tabla 47

*Métodos de UserRepository y UserRepositoryImpl en el Infrastructure Layer de IAM*

| Método             | Firma                                            | Descripción                         |
| ------------------ | ------------------------------------------------ | ----------------------------------- |
| `findByUsername`   | `Optional<User> findByUsername(String username)` | Busca usuario por `username`.       |
| `findById`         | `Optional<User> findById(String id)`             | Busca usuario por `id`.             |
| `findAll`          | `List<User> findAll()`                           | Lista todos los usuarios.           |
| `saveUser`         | `void saveUser(User user)`                       | Persiste/actualiza un `User`.       |
| `existsByUsername` | `boolean existsByUsername(String username)`      | Verifica existencia por `username`. |

---

#### 5.1.5. IAM Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de IAM. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales del contexto de gestión de identidad y acceso.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y seguridad del sistema.

###### Figura 47

*Diagrama de componentes del Bounded Context de IAM relacionado a ...*

#### 5.1.6. IAM Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de IAM, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.1.6.1. IAM Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica de dominio, así como sus relaciones fundamentales. El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y su rol dentro del modelo.

Asimismo, se incluyen las relaciones entre elementos del dominio, calificadas con nombres descriptivos, direccionalidad cuando corresponde, y multiplicidad para reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada del diseño táctico favorece la comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación efectiva dentro de la arquitectura de software.

###### Figura 48

*Diagrama de clases del Bounded Context de IAM*

![IAM CLASS DIAGRAM](../../assets/img/chapter-V/iam-class-diagram.png)

##### 5.1.6.2. IAM Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación permite visualizar de forma estructurada y precisa las clases, interfaces y enumeraciones que conforman la lógica de dominio, junto con sus atributos, métodos y responsabilidades específicas dentro del modelo.

El diagrama incluye detalles esenciales como el tipo de dato y la visibilidad de cada miembro, así como las relaciones entre los distintos elementos del dominio. Estas relaciones están calificadas con nombres descriptivos, indican la dirección cuando aplica, e incorporan multiplicidades para representar con fidelidad la cardinalidad de cada asociación.

Esta visualización detallada contribuye significativamente a la comprensión compartida del modelo conceptual, funcionando como un nexo clave entre el análisis de dominio y su posterior implementación en la arquitectura del sistema.

###### Figura 49

*Sección del diagrama entidad-relación correspondiente al Bounded Context de IAM*

---

### 5.2. Bounded Context: Profile and Preferences

En el contexto táctico, el Bounded Context Profiles and Preferences concentra toda la funcionalidad relacionada con la gestión personalizada de los perfiles de usuario en la plataforma Mushroom. Este módulo se encarga de almacenar, actualizar y exponer información detallada sobre las preferencias individuales, hábitos de uso, configuraciones personalizadas y características del entorno del usuario. Entre sus responsabilidades se incluyen la edición de datos personales no sensibles y la persistencia de hábitos o preferencias.

Profiles and Preferences permite adaptar la experiencia digital a las necesidades particulares de cada usuario, y lo hace mediante una interfaz limpia e interoperable, disponible para otros bounded contexts. Al ofrecer un punto centralizado para el perfilado y la personalización, garantiza consistencia, reutilización y separación de preocupaciones dentro de la arquitectura de la solución. Este Bounded Context no gestiona credenciales ni roles, solo datos de cuenta y preferencias ligadas a UX/operación.

#### 5.2.1. Profile and Preferences Bounded Context Domain Layer

En la capa de dominio de Profiles and Preferences se modelan las entidades, objetos de valor y reglas de negocio fundamentales asociadas a la gestión de perfiles y preferencias personalizadas. Esta capa encapsula la lógica central vinculada al almacenamiento, validación y actualización de datos relacionados con la configuración del usuario, sus preferencias de uso y hábitos de interacción con la plataforma. Asimismo, se definen los Domain Services responsables de coordinar operaciones complejas que involucran múltiples objetos, asegurando la coherencia del comportamiento del sistema y promoviendo su reutilización en otros contextos.

**Profile:**

###### Tabla 48

*Descripción de Profile en el Domain Layer de Profile and Preferences*

| Propiedad     | Valor                                                                                 |
| ------------- | ------------------------------------------------------------------------------------- |
| **Nombre**    | Profile                                                                               |
| **Categoría** | Aggregate Root (puede extender la clase base auditable si se desea consistencia)      |
| **Propósito** | Gestionar datos de cuenta y preferencias del usuario (no sensibles de autenticación). |

###### Tabla 49

*Atributos de Profile en el Domain Layer de Profile and Preferences*

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

###### Tabla 50

*Métodos de Profile en el Domain Layer de Profile and Preferences*

| Nombre                 | Tipo de retorno | Visibilidad | Descripción                                             |
| ---------------------- | --------------- | ----------- | ------------------------------------------------------- |
| changeDisplayName(...) | `void`          | public      | Actualiza el nombre mostrado.                           |
| updateFullName(...)    | `void`          | public      | Modifica `FullName`.                                    |
| changeAvatarUrl(...)   | `void`          | public      | Actualiza el avatar.                                    |
| updateContactInfo(...) | `void`          | public      | Actualiza teléfono y datos de contacto.                 |
| updatePreferences(...) | `void`          | public      | Actualiza `notificationSettings`, `locale`, `timezone`. |

---

**FullName:**

###### Tabla 51

*Descripción de FullName en el Domain Layer de Profile and Preferences*

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | FullName                                   |
| **Categoría** | Value Object                               |
| **Propósito** | Representar el nombre completo del usuario |

###### Tabla 52

*Atributos de FullName en el Domain Layer de Profile and Preferences*

| Nombre    | Tipo de dato | Visibilidad | Descripción |
| --------- | ------------ | ----------- | ----------- |
| name      | `string`     | private     | Nombres     |
| lastNames | `string`     | private     | Apellidos   |

---

**NotificationSettings:** 

###### Tabla 53

*Descripción de NotificationSettings en el Domain Layer de Profile and Preferences*

| Propiedad     | Valor                                                  |
| ------------- | ------------------------------------------------------ |
| **Nombre**    | NotificationSettings                                   |
| **Categoría** | Value Object                                           |
| **Propósito** | Encapsular preferencias de notificaciones del usuario. |

###### Tabla 54

*Atributos de NotificationSettings en el Domain Layer de Profile and Preferences*

| Nombre     | Tipo de dato | Visibilidad | Descripción                                     |
| ---------- | ------------ | ----------- | ----------------------------------------------- |
| emailOptIn | `boolean`    | private     | Recibir notificaciones por email.               |
| pushOptIn  | `boolean`    | private     | Recibir notificaciones push.                    |
| quietHours | `String`     | private     | Ventanas de silencio (ej. `22:00-07:00` local). |

---

#### 5.2.2. Profile and Preferences Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Profiles and Preferences se exponen los endpoints necesarios para gestionar la información de perfil de usuario y sus preferencias personalizadas dentro de la plataforma de Mushroom. A través de controladores dedicados, esta capa actúa como intermediaria entre las aplicaciones cliente y la lógica de negocio, permitiendo operaciones como la visualización, edición y actualización de datos personales y configuraciones. Su diseño promueve una arquitectura segura, enfocada en mantener una experiencia fluida y adaptable para el usuario sin comprometer la coherencia del sistema.

**ProfileController**

###### Tabla 55

*Descripción de Profile Controller en el Interface Layer de Profile and Preferences*

| Propiedad         | Valor                                                        |
| ----------------- | ------------------------------------------------------------ |
| **Nombre**        | ProfileController                                            |
| **Categoría**     | Controller                                                   |
| **Propósito**     | Exponer endpoints de perfil y preferencias (no credenciales) |
| **Ruta base**     | `/api/v1/profiles`                                           |
| **Tag (OpenAPI)** | `Profiles`                                                   |

###### Tabla 56

*Métodos de Profile Controller en el Interface Layer de Profile and Preferences*

| Nombre            | Ruta                     | Acción                                           | Handle                                                      |
| ----------------- | ------------------------ | ------------------------------------------------ | ----------------------------------------------------------- |
| getByUserId       | `/{userId}`              | Obtener perfil por `userId`                      | `GetProfileByUserIdQuery` -> `profileQueryService.handle`    |
| updateDisplayName | `/{userId}/display-name` | Actualizar nombre mostrado                       | `UpdateDisplayNameCommand` -> `profileCommandService.handle` |
| updateFullName    | `/{userId}/full-name`    | Actualizar nombre completo (VO)                  | `UpdateFullNameCommand` -> `profileCommandService.handle`    |
| updateAvatar      | `/{userId}/avatar`       | Actualizar avatar                                | `UpdateAvatarCommand` -> `profileCommandService.handle`      |
| updateContact     | `/{userId}/contact`      | Actualizar teléfono u otros datos de contacto    | `UpdateContactInfoCommand` -> `profileCommandService.handle` |
| updatePreferences | `/{userId}/preferences`  | Actualizar preferencias (notifs/locale/timezone) | `UpdatePreferencesCommand` -> `profileCommandService.handle` |

---

#### 5.2.3. Profile and Preferences Bounded Context Application Layer

La capa de aplicación del Bounded Context de Profiles and Preferences coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se implementan los Command Handlers, Query Handlers y Event Handlers responsables de operaciones como la edición de información personal, actualización de preferencias del usuario y notificación de cambios relevantes. Su rol es garantizar que dichas acciones se ejecuten de forma consistente y transaccional, delegando la lógica central al dominio y apoyándose en la infraestructura cuando sea necesario, manteniendo así la cohesión funcional del sistema.

**Event Handlers:**

###### Tabla 57

*Descripción de UserCreatedEventHandler en el Aplication Layer de Profile and Preferences*

| Propiedad        | Valor                                            |
| ---------------- | ------------------------------------------------ |
| **Nombre**       | UserCreatedEventHandler                          |
| **Categoría**    | Event Handler                                    |
| **Propósito**    | Crear `Profile` cuando IAM publica `UserCreated` |
| **Evento**       | `UserCreated`                  |
| **Dependencias** | `ProfileRepository` |

---

**Query Handlers:**

###### Tabla 58

*Descripción de GetProfileByUserIdQueryHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                                        |
| ---------------- | -------------------------------------------- |
| **Nombre**       | GetProfileByUserIdQueryHandler               |
| **Categoría**    | Query Handler                                |
| **Propósito**    | Obtener `Profile` por `userId`               |
| **Query**        | `GetProfileByUserIdQuery`                    |
| **Dependencias** | `ProfileQueryRepository`/`ProfileRepository` |

---

**Command Handlers:**

###### Tabla 59

*Descripción de UpdateDisplayNameCommandHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                               |
| ---------------- | ----------------------------------- |
| **Nombre**       | UpdateDisplayNameCommandHandler     |
| **Categoría**    | Command Handler                     |
| **Propósito**    | Actualizar `displayName` del perfil |
| **Comando**      | `UpdateDisplayNameCommand`          |
| **Dependencias** | `ProfileRepository`                 |

###### Tabla 60

*Descripción de UpdateFullNameCommandHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                        |
| ---------------- | ---------------------------- |
| **Nombre**       | UpdateFullNameCommandHandler |
| **Categoría**    | Command Handler              |
| **Propósito**    | Actualizar `FullName`    |
| **Comando**      | `UpdateFullNameCommand`      |
| **Dependencias** | `ProfileRepository`          |

###### Tabla 61

*Descripción de UpdateAvatarCommandHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                      |
| ---------------- | -------------------------- |
| **Nombre**       | UpdateAvatarCommandHandler |
| **Categoría**    | Command Handler            |
| **Propósito**    | Actualizar `avatarUrl`     |
| **Comando**      | `UpdateAvatarCommand`      |
| **Dependencias** | `ProfileRepository`        |

###### Tabla 62

*Descripción de UpdateContactInfoCommandHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                                  |
| ---------------- | -------------------------------------- |
| **Nombre**       | UpdateContactInfoCommandHandler        |
| **Categoría**    | Command Handler                        |
| **Propósito**    | Actualizar datos de contacto (`phone`) |
| **Comando**      | `UpdateContactInfoCommand`             |
| **Dependencias** | `ProfileRepository`                    |

###### Tabla 63

*Descripción de UpdatePreferencesCommandHandler en el Application Layer de Profile and Preferences*

| Propiedad        | Valor                                                   |
| ---------------- | ------------------------------------------------------- |
| **Nombre**       | UpdatePreferencesCommandHandler                         |
| **Categoría**    | Command Handler                                         |
| **Propósito**    | Actualizar `NotificationSettings`, `locale`, `timezone` |
| **Comando**      | `UpdatePreferencesCommand`                              |
| **Dependencias** | `ProfileRepository`                                     |

---

#### 5.2.4. Profile and Preferences Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Profile and Preferences sirve como enlace entre la lógica de negocio y los mecanismos técnicos que permiten la persistencia y comunicación con recursos externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, servicios de almacenamiento y otros módulos relevantes que permiten gestionar la información de perfil y preferencias de los usuarios.

**Repositorios:**

###### Tabla 64

*Descripción de ProfileRepository en el Infrastructure Layer de Profile and Preferences*

| Propiedad          | Valor                                          |
| ------------------ | ---------------------------------------------- |
| **Nombre**         | ProfileRepository                              |
| **Categoría**      | Repositorio                                    |
| **Propósito**      | Persistir y consultar agregados de `Profile`   |
| **Interfaz**       | `ProfileRepository`                            |
| **Implementación** | `ProfileRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `profiles` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)          |

###### Tabla 65

*Métodos de ProfileRepository en el Infrastructure Layer de Profile and Preferences*

| Método           | Firma                                           | Descripción                                                         |
| ---------------- | ----------------------------------------------- | ------------------------------------------------------------------- |
| `findByUserId`   | `Optional<Profile> findByUserId(String userId)` | Busca el perfil asociado a un `userId` (clave de relación con IAM). |
| `findById`       | `Optional<Profile> findById(String id)`         | Busca perfil por su `id` propio.                                    |
| `findAll`        | `List<Profile> findAll()`                       | Lista todos los perfiles.                                           |
| `saveProfile`    | `void saveProfile(Profile profile)`             | Persiste/actualiza un `Profile`.                                    |
| `existsByUserId` | `boolean existsByUserId(String userId)`         | Verifica existencia por `userId`.                                   |

---

#### 5.2.5. Profile and Preferences Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Profiles and Preferences. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías utilizadas y las interacciones entre ellos. Esta representación es fundamental para comprender en detalle cómo se organiza internamente cada parte del sistema, qué funcionalidades asume cada componente, y de qué manera colaboran para gestionar la información personal, preferencias y configuración personalizada del usuario dentro de Mushroom.

Tal como establece el C4 Model, el nivel de componentes representa el cuarto nivel de abstracción en la visualización de arquitecturas de software, y resulta especialmente útil para desarrolladores y arquitectos al ofrecer una visión clara de las decisiones de diseño adoptadas en cada contenedor (Brown, 2023). Este nivel facilita la trazabilidad entre los elementos de alto nivel y su implementación específica, fortaleciendo la mantenibilidad, extensibilidad y coherencia del sistema.

###### Figura 50

*Sección del diagrama de componentes correspondiente al Bounded Context de Profile and Preferences*


#### 5.2.6. Profile and Preferences Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Profiles and Preferences, presentando diagramas que permiten visualizar con mayor precisión la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos del sistema que gestionan la configuración del perfil de usuario, sus intereses, preferencias y datos personales.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico y la implementación concreta. Esta aproximación garantiza que las decisiones tomadas a nivel táctico se materialicen en estructuras coherentes, sólidas y alineadas con los objetivos funcionales del contexto, brindando claridad y sostenibilidad al proceso de desarrollo y evolución del sistema.

##### 5.2.6.1. Profile and Preferences Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que componen la lógica de dominio relacionada con la gestión del perfil del usuario, sus intereses, configuraciones personalizadas y preferencias de interacción dentro del ecosistema de Macetech.

El nivel de detalle incluye la definición de atributos y métodos para cada clase, especificando sus tipos de datos, visibilidad y rol dentro del modelo, así como las relaciones fundamentales entre los distintos elementos del dominio. Estas relaciones se representan con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, lo que permite reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada facilita una comprensión común del modelo conceptual, sirviendo como puente entre el diseño del dominio y su posterior implementación técnica.

###### Figura 51

*Diagrama de clases del Bounded Context de Profile and Preferences*

![PROFILE CLASS DIAGRAM](../../assets/img/chapter-V//profile-class-diagram.png)

##### 5.2.6.2. Profile and Preferences Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las entidades persistentes asociadas a la gestión de perfiles, intereses y preferencias del usuario, junto con sus atributos clave, tipos de datos, claves primarias y foráneas, y restricciones asociadas.

El diagrama refleja las relaciones entre las distintas tablas o entidades, indicando la dirección de las asociaciones, su naturaleza y la cardinalidad, lo que facilita el entendimiento de la estructura lógica que respalda el almacenamiento y la recuperación eficiente de datos dentro de este contexto.

Esta visualización resulta esencial para asegurar la coherencia entre el modelo conceptual y su implementación en la capa de persistencia, contribuyendo a una arquitectura sólida, escalable y alineada con los requerimientos funcionales y no funcionales del sistema.

###### Figura 52

*Sección del diagrama entidad-relación correspondiente al Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/database-diagram-profile-and-personal-data.png"></image>

---

### 5.3. Bounded Context: Asset and Resource Management

En el contexto táctico, el Bounded Context Asset & Resource Management agrupa la funcionalidad asociada al catálogo y selección de puertos dentro de Mushroom. Este módulo expone los puertos con su identidad, nombre, continente y coordenadas, provee endpoints para listar/consultar puertos y habilita la selección de origen/destino (y opcionalmente intermedios) como paso previo a la visualización y cálculo de rutas. De manera complementaria, la interfaz de usuario consume un contrato de puertos cercanos/estado para apoyar la toma de decisiones operativas.  

#### 5.3.1. Asset and Resource Management Bounded Context Domain Layer

En la capa de dominio de Asset & Resource Management se definen las entidades y objetos de valor fundamentales relacionados con los puertos y mapas de navegación presentados en la aplicación. Esta capa encapsula las reglas de negocio desde la definición de cada puerto y su ubicación exacta, la revisión del estado de cada puerto y la selección de un puerto de inicio y uno final. Además, en este nivel se ubican los Domain Services encargados de la entrega de información de cada puerto específico para su visualización por el usuario, asegurando coherencia, integridad y rendimiento.

**Port:**

###### Tabla 66

*Descripción de Port en el Domain Layer de Asset and Resource Management*

| Propiedad     | Valor                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------|
| **Nombre**    | Port                                                                                                    |
| **Categoría** | Entity                                                                                                  |
| **Propósito** | Representa un puerto del catálogo maestro, con datos mínimos para selección y referencia geográfica.   |

###### Tabla 67

*Atributos de Port en el Domain Layer de Asset and Resource Management*

| Nombre                | Tipo de dato | Visibilidad | Descripción                         |
|-----------------------|--------------|-------------|-------------------------------------|
| id                    | `string`     | private     | Identificador único del puerto      |
| name                  | `string`     | private     | Nombre del puerto                   |
| coordinates.latitude  | `number`     | private     | Latitud                             |
| coordinates.longitude | `number`     | private     | Longitud                            |
| continent             | `string`     | private     | Continente                          |

---

**GeoPoint (coordinates):**

###### Tabla 68

*Descripción de GeoPoint en el Domain Layer de Asset and Resource Management*

| Propiedad     | Valor                                 |
|---------------|---------------------------------------|
| **Nombre**    | GeoPoint                              |
| **Categoría** | Value Object                          |
| **Propósito** | Encapsular `latitude` y `longitude`.  |

###### Tabla 69

*Atributos de GeoPoint en el Domain Layer de Asset and Resource Management*

| Nombre    | Tipo de dato | Visibilidad | Descripción |
|-----------|--------------|-------------|-------------|
| latitude  | `number`     | private     | Latitud     |
| longitude | `number`     | private     | Longitud    |

---

**PortStatus:**

La UI utiliza un servicio `NearbyPortService` que espera una lista de puertos cercanos con estado (`open/closed`), distancia y facilidades. Este contrato de front se mapea a entidad de estado/puerto cercano.

###### Tabla 70

*Descripción de PortStatus en el Domain Layer de Asset and Resource Management*

| Propiedad     | Valor                                                                                                   |
|---------------|---------------------------------------------------------------------------------------------------------|
| **Nombre**    | PortStatus (ó NearbyPort)                                                                               |
| **Categoría** | Entity                                                                                                  |
| **Propósito** | Representar el **estado operativo** y metadatos de puertos cercanos a una posición/vessel.              |

###### Tabla 71

*Atributos de PortStatus en el Domain Layer de Asset and Resource Management*

| Nombre       | Tipo de dato                   | Visibilidad | Descripción                                           |
|--------------|--------------------------------|-------------|-------------------------------------------------------|
| id           | `number`                        | private     | Identificador del puerto cercano                      |
| name         | `string`                        | private     | Nombre                                                |
| country      | `string`                        | private     | País/Región                                           |
| latitude     | `number`                        | private     | Latitud                                               |
| longitude    | `number`                        | private     | Longitud                                              |
| distance     | `number`                        | private     | Distancia desde la referencia                         |
| status       | `"open" \| "closed"`            | private     | Estado operativo                                      |
| facilities   | `string[]`                      | private     | Servicios disponibles                                 |
| maxDepth     | `number`                        | private     | Calado máximo                                         |
| contactInfo  | `{ phone,email,vhfChannel }`    | private     | Datos de contacto                                     |

---

**SelectionSession:**

La UI mantiene una sesión de selección de origen/destino e intermedios para iniciar el cálculo y visualización de ruta. Se modela como aggregate para mantener consistencia local.

###### Tabla 72

*Descripción de SelectionSession en el Domain Layer de Asset and Resource Management*

| Propiedad     | Valor                                                                                                                 |
|---------------|-----------------------------------------------------------------------------------------------------------------------|
| **Nombre**    | SelectionSession                                                                                                      |
| **Categoría** | Aggregate Root                                                                                                        |
| **Propósito** | Gestionar la **selección de puertos** (origen/destino/intermedios) del usuario y marcar la sesión lista para ruteo.  |

###### Tabla 73

*Atributos de SelectionSession en el Domain Layer de Asset and Resource Management*

| Nombre                | Tipo de dato   | Visibilidad | Descripción                                                 |
|-----------------------|----------------|-------------|-------------------------------------------------------------|
| sessionId             | `string`       | private     | Identificador de la sesión                                  |
| originPortId          | `string?`      | private     | Puerto de origen                                            |
| destinationPortId     | `string?`      | private     | Puerto de destino                                           |
| intermediatePortIds   | `string[]`     | private     | Puertos intermedios seleccionados                           |
| readyForRouting       | `boolean`      | private     | `true` si la selección es válida/completa                   |
| createdAt             | `DateTime`     | private     | Fecha de creación                                           |
| updatedAt             | `DateTime`     | private     | Última actualización                                        |

###### Tabla 74

*Métodos de SelectionSession en el Domain Layer de Asset and Resource Management*

| Nombre            | Tipo de retorno | Visibilidad | Descripción                                             |
|-------------------|-----------------|-------------|---------------------------------------------------------|
| setOrigin         | `void`          | public      | Define el puerto de origen                              |
| setDestination    | `void`          | public      | Define el puerto de destino                             |
| addIntermediate   | `void`          | public      | Agrega un puerto intermedio                             |
| removeIntermediate| `void`          | public      | Quita un puerto intermedio                              |
| swapPorts         | `void`          | public      | Intercambia origen/destino                              |
| validateReadiness | `boolean`       | public      | Verifica que origen y destino existan y no sean iguales |
| markReady         | `void`          | public      | Establece `readyForRouting = true`                      |

---

**Repositorios (interfaces):**

###### Tabla 75

*Descripción de las Interfaces de los Repositorios en el Domain Layer de Asset and Resource Management*

| Nombre                       | Categoría  | Propósito                                |
|-----------------------------|------------|------------------------------------------|
| PortRepository              | Repository | Persistencia/consulta de `Port`          |
| PortStatusRepository        | Repository | Persistencia/consulta de `PortStatus`    |
| SelectionSessionRepository  | Repository | Persistencia/consulta de `SelectionSession` |

---

**Eventos de dominio:**

###### Tabla 76

*Listado de eventos de dominio en el Domain Layer de Asset and Resource Management*

| Evento                  | Descripción                                         |
|------------------------|-----------------------------------------------------|
| PortCatalogUpdated     | Actualización de catálogo de puertos                |
| PortStatusChanged      | Cambio de estado de un puerto                       |
| PortSelectionCompleted | Selección válida (origen/destino) lista para ruteo  |

---

#### 5.3.2. Asset and Resource Management Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Asset & Resource Management se exponen los endpoints necesarios para gestionar la información relacionada a cada puerto integrado en la página de Mushroom. Su diseño promueve una separación clara de responsabilidades, orquestando de forma eficiente comandos y consultas, al tiempo que garantiza trazabilidad, disponibilidad y consistencia de los recursos gestionados.

**PortController:**

###### Tabla 77

*Descripción de PortController en el Interface Layer de Asset and Resource Management*

| Propiedad     | Valor                                                                                     |
|---------------|-------------------------------------------------------------------------------------------|
| **Nombre**    | `PortController`                                                                          |
| **Categoría** | Controller                                                                                |
| **Ruta base** | `/api/ports`                                                                              |
| **Produces**  | `application/json`                                                                        |
| **Descripción** | Endpoints REST para gestionar el catálogo de puertos.                                    |

###### Tabla 78

*Métodos de PortController en el Interface Layer de Asset and Resource Management*

| Método   | Ruta                         | Acción                                | Request body            | Response / Status                  |
|----------|------------------------------|----------------------------------------|-------------------------|------------------------------------|
| `POST`   | `/api/ports`                 | Crear un nuevo puerto                  | `CreatePortResource`    | `PortResource` — `201 Created`     |
| `GET`    | `/api/ports/{portId}`        | Obtener un puerto por **ID**           | —                       | `PortResource` — `200 OK` / `404`  |
| `GET`    | `/api/ports/name/{name}`     | Obtener un puerto por **nombre**       | —                       | `PortResource` — `200 OK` / `404`  |
| `DELETE` | `/api/ports/{portId}`        | Eliminar un puerto por **ID**          | —                       | `204 No Content`                   |
| `GET`    | `/api/ports/all-ports`       | Listar **todos los puertos**           | —                       | `List<PortResource>` — `200 OK`    |

---

**DTOs:**

###### Tabla 79

*DTO de CreatePortResource en el Interface Layer de Asset and Resource Management*

| Campo        | Tipo               | Obligatorio | Descripción                 |
|--------------|--------------------|-------------|-----------------------------|
| name         | `String`           | Sí          | Nombre del puerto           |
| coordinates  | `CoordinatesResource` | Sí       | Lat/Long                    |
| continent    | `String`           | Sí          | Continente                  |

###### Tabla 80

*DTO de PortResource en el Interface Layer de Asset and Resource Management*

| Campo        | Tipo                  | Descripción                           |
|--------------|-----------------------|---------------------------------------|
| id           | `String`              | Identificador del puerto              |
| name         | `String`              | Nombre del puerto                     |
| coordinates  | `CoordinatesResource` | Lat/Long                              |
| continent    | `String`              | Continente                            |

---

**Nearby Ports:**

En el frontend, `NearbyPortService` consulta `GET {environment.apiUrl}/api/v1/vessels/{vesselId}/nearby-ports` y espera un `NearbyPort[]`. Este es el **contrato consumido por la UI** para estado/puertos cercanos.

###### Tabla 81

*Contrato esperado por la UI de Nearby Ports en el Interface Layer de Asset and Resource Management*

| Método | Ruta (consumida por el front)                        | Acción                                   | Response           |
|--------|-------------------------------------------------------|------------------------------------------|--------------------|
| `GET`  | `/api/v1/vessels/{vesselId}/nearby-ports`            | Puertos cercanos + estado/facilities     | `NearbyPort[]`     |

###### Tabla 82

*DTO de nearbyPort en el Interface Layer de Asset and Resource Management*

| Campo        | Tipo                                                     |
|--------------|----------------------------------------------------------|
| id           | `number`                                                 |
| name         | `string`                                                 |
| country      | `string`                                                 |
| latitude     | `number`                                                 |
| longitude    | `number`                                                 |
| distance     | `number`                                                 |
| status       | `"open" \| "closed"`                                     |
| facilities   | `string[]`                                               |
| maxDepth     | `number`                                                 |
| contactInfo  | `{ phone: string; email: string; vhfChannel: string }`   |

**Selección de Puertos:**

`PortSelectorComponent` consume `PortService.getAllPorts()` para poblar **origen/destino** e **intermedios**, y dispara la visualización/cálculo de rutas mediante `RouteService`.

###### Tabla 83

*Interacciones de PortSelectorComponent en el Interface Layer de Asset and Resource Management*

| UI / Servicio                             | Propósito                                                                 |
|-------------------------------------------|---------------------------------------------------------------------------|
| `PortService.getAllPorts()`               | Poblar listas de puertos (origen/destino/intermedios)                     |
| `NearbyPortService.getNearbyPorts(id)`    | Mostrar puertos cercanos/estado para el vessel                            |
| `RouteService.calculateOptimalRoute(...)` | Visualizar ruta (otro BC; se activa tras la selección ARM)                |

---

#### 5.3.3. Asset and Resource Management Bounded Context Application Layer

La capa de aplicación del Bounded Context de Asset & Resource Management coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones como el registro, actualización y seguimiento del estado de los puertos de Mushroom, así como el procesamiento de eventos vinculados a sus estados y ubicación exacta. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**PortService:**

###### Tabla 84

*Descripción de PortService en el Application Layer de Asset and Resource Management*

| Servicio       | Método(s) en el Controller                                        | Propósito                                   |
|----------------|--------------------------------------------------------------------|---------------------------------------------|
| `PortService`  | `createPort(...)`, `getPortById(...)`, `getPortByName(...)`, `deletePort(...)`, `getAllPorts()` | Orquestar la lógica de gestión de puertos   |

---

#### 5.3.4. Asset and Resource Management Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Asset and Resource Management actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, coordenadas y representación de mapas de forma adecuada.

Esta capa concreta las abstracciones del dominio a través de implementaciones de repositorios y componentes técnicos especializados. Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la gestión de los puertos y sus respectivos estados operativos, en línea con los requerimientos estratégicos de la solución.

**Repositorios:**

###### Tabla 85

*Listado de Repositorios en el Infrastructure Layer de Asset and Resource Management*

|Nombre|	Categoría	|Propósito	|Interfaz|
|-|-|-|-|
|PortRepository	|Repositorio	|Persistir y consultar documentos ports|	IPortRepository|

###### Tabla 86

*Métodos de IPortRepository en el Infrastructure Layer de Asset and Resource Management*

|Nombre	|Tipo de retorno|	Descripción|
|-|-|-|
|findById(portId)	|Port|	Recupera port por id.|
|findByCode(code)	|Port|	Recupera por código único.|
|save(port, session?)	|void|	Persiste aggregate (usar session para transacciones).|
|updateStatus(portId, newStatus, actor, session?)|	void|	Actualiza estado con control optimista.|

---

**Implementaciones MongoDB:**

###### Tabla 87

*Tabla de colecciones y notas de implementación para MongoDB en el Infrastructure Layer de Asset and Resource Management*

|Componente	|Colección|	Notas|
|-|-|-|
|Ports	|ports|	Documento Port. Índice único code. Índice 2dsphere en location. Campos createdAt y updatedAt. version para control optimista.|
|Ports read|	ports_read	|Denormalización con resumen y geometría simplificada para UI; actualizada por event handlers.|

---

#### 5.3.5. Asset and Resource Management Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Asset and Resource Management. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión de de puertos y sus ubicaciones en mapa dentro de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

###### Figura 53

*Sección del diagrama de componentes correspondiente al Bounded Context de Asset and Resource Management*


#### 5.3.6. Asset and Resource Management Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Asset and Resource Management, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.3.6.1. Asset and Resource Management Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Asset and Resource Management. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión de ubicaciones de puertos y estados en la plataforma de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

###### Figura 54

*Diagrama de clases del Bounded Context de Asset and Resource Management*

![DiagramaClasesARM](../../assets/img/chapter-V/DiagramaClasesARM.png)

##### 5.3.6.2. Asset and Resource Management Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Asset and Resource Management. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de puertos y estados en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

###### Figura 55

*Sección del diagrama entidad-relación correspondiente al Bounded Context de Asset and Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

---

### 5.4. Bounded Context: A*/AI Process

En el contexto táctico, el Bounded Context A/AI process* concentra la funcionalidad asociada al cálculo de rutas óptimas y a la predicción climática que complementa la experiencia de navegación. Este módulo encapsula la lógica del algoritmo A* para determinar la ruta mínima entre puntos definidos, integrando además un componente de inteligencia artificial orientado a anticipar condiciones meteorológicas que puedan afectar la planificación del trayecto.

El proceso se apoya en datos obtenidos de APIs externas, que pueden proveer información climática en tiempo real o registros históricos especializados, según se defina en etapas posteriores del proyecto. A partir de esta información, el sistema ajusta dinámicamente las rutas propuestas, otorgando a los navegantes un soporte predictivo que incrementa tanto la eficiencia como la seguridad del recorrido.

De esta forma, el bounded context actúa como el núcleo de cálculo y predicción, exponiendo interfaces bien delimitadas para que otros módulos del sistema consuman sus resultados sin acoplarse a la complejidad interna de los algoritmos. Esto asegura independencia, escalabilidad y una fuente única de verdad en lo referente a optimización de trayectorias y análisis del entorno climático.

#### 5.4.1. A*/AI Process Bounded Context Domain Layer

En la capa de dominio de A*/AI Process se definen las entidades y objetos de valor fundamentales relacionados con las rutas de navegación específicas entre puertos del mapa. Esta capa encapsula las reglas de negocio desde las especificaciones de cada ruta obtenida, los algoritmos utilizados para definir la mejor ruta y la información externa que puede involucrar el análisis de ML.

**Route:**

###### Tabla 88

*Descripción de Route en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | Route |
| Categoría | Aggregate Root |
| Propósito | Representar una ruta calculada por el algoritmo A*, incluyendo nodos, distancia y costo total. |

###### Tabla 89

*Atributos de Route en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Id | UUID | private | Identificador único de la ruta |
| Nodes | List<Node> | private | Lista de nodos que conforman el trayecto |
| Distance | double | private | Distancia total de la ruta |
| Cost | double | private | Costo acumulado según heurística A* |
| CreatedAt | DateTime | private | Fecha en que fue calculada la ruta |

###### Tabla 90

*Métodos de Route en el Domain Layer de A/AI process*

| Nombre | Tipo de retorno | Visibiilidad | Descripción |
|--------|-----------------|--------------|-------------|
| CalculateCost | void | public | Recalcula el costo total de la ruta |
| AddNode | void | public | Agrega un nodo al trayecto de la ruta |
| Optimize | void | public | Permite optimizar el orden de los nodos |

---

**Node:**

###### Tabla 91

*Descripción de Node en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | Node |
| Categoría | Entity |
| Propósito | Representar un punto geográfico o de grafo en el cálculo de rutas. |

###### Tabla 92

*Atributos de Node en el Domain Layer de A/AI process*

| Nombre    | Tipo de dato | Visibilidad | Descripción |
|-----------|--------------|-------------|-------------|
| Id        | UUID         | private     | Identificador único del nodo |
| Latitude  | double       | private     | Coordenada de latitud del nodo |
| Longitude | double       | private     | Coordenada de longitud del nodo |
| Cost      | double       | private     | Costo heurístico acumulado en el algoritmo |

---

**WeatherPrediction:**

###### Tabla 93

*Descripción de WeatherPrediction en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | WeatherPrediction |
| Categoría | Entity |
| Propósito | Representar una predicción climática asociada a un trayecto en una fecha dada |

###### Tabla 94

*Atributos de WeatherPrediction en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Id | UUID | private | Identificador único de la predicción |
| RouteId | UUID | private | Identificador de la ruta asociada |
| Date | DateTime | private | Fecha y hora de la predicción |
| Condition | string | private | Condición climática (ej. lluvia, soleado) |
| Confidence | double | private | Nivel de confianza en la predicción |

---

**AStarAlgorithm:**

###### Tabla 95

*Descripción de AStarAlgorithm en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | AStarAlgorithm |
| Categoría | Domain Service |
| Propósito | Implementar la lógica de cálculo de rutas mínimas con A* |

###### Tabla 96

*Métodos de AStarAlgorithm en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| FindShortest | Route | public | Ejecuta el algoritmo A* y devuelve la mejor ruta |
| Heuristic | Double | private | Calcula la heurística (distancia estimada) entre nodos |

---

**WeatherService:**

###### Tabla 97

*Descripción de WeatherService en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | WeatherService |
| Categoría | Domain Service |
| Propósito | Centralizar la lógica de predicción de clima consumiendo IA y APIs externas |

###### Tabla 98

*Métodos de WeatherService en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| PredictCondition | WeatherPrediction | public | Devuelve una predicción climática para una ruta |
| AdjustRoute | Route | public | Ajusta la ruta considerando las predicciones climáticas |

---

**IRouteRepository:**

###### Tabla 99

*Descripción de IRouteRepository en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | IRouteRepository |
| Categoría | Repository |
| Propósito | Abstracción para persistencia y consulta de rutas |

###### Tabla 100

*Métodos de IRouteRepository en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Save | Route | public | Guarda una ruta calculada |
| FindById | Route? | public | Recupera una ruta por su identificador |
| FindAll | List < Route > | public | Lista todas las rutas registradas |

---

**IWeatherRepository:**

###### Tabla 101

*Descripción de IWeatherRepository en el Domain Layer de A/AI process*

| Propiedad   | Valor   |
|-------------|---------|
| Nombre | IWeatherRepository |
| Categoría | Repository |
| Propósito | Abstracción para almacenar y recuperar predicciones climáticas |

###### Tabla 102

*Métodos de IWeatherRepository en el Domain Layer de A/AI process*

| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Save | WeatherPrediction | public | Guarda una predicción de clima |
| FindById | WeatherPrediction? | public | Recupera una predicción por identificador |
| FindByRoute | List < WeatherPrediction > | public | Recupera predicciones asociadas a una ruta |

---

#### 5.4.2. A*/AI Process Bounded Context Interface Layer

La capa de Interface del bounded context A/AI process* contiene los controllers REST que exponen la funcionalidad del core (cálculo de rutas, obtención de datos de puertos, consulta de distancias, listados de rutas). Además expone los DTOs/Resources que representan las peticiones y respuestas de la API, y los assemblers que transforman recursos a comandos del Application Layer (y viceversa). Esta capa no contiene lógica de negocio; su única responsabilidad es traducir HTTP ↔ objetos del dominio/aplicación y manejar respuestas/errores.

**RouteController:**

###### Tabla 103

*Descripción de RouteController en el Interface Layer de A/AI process*

| Propiedad     | Valor                                                                                     |
|---------------|-------------------------------------------------------------------------------------------|
| Nombre        | RouteController                                                                           |
| Categoría     | Controller                                                                                |
| Propósito     | Exponer endpoints relacionados con operaciones sobre rutas (cálculo, consulta, listados). |
| Base Path     | /api/routes (convención; el controller usa recursos RouteCalculationResource, etc.)       |

###### Tabla 104

*Métodos de RouteController en el Interface Layer de A/AI process*

|Nombre (Método)        | Ruta (ejemplo)        | Acción                                | Handle / Resource utilizado                  |
|--------------------   |-----------------------|---------------------------------------|----------------------------------------------|
| calculateRoute (POST) | /api/routes/calculate | Recibe datos de inicio/destino y solicita cálculo de ruta óptima | RouteCalculationResource / RouteRequestResource |
| getRouteById (GET)    | /api/routes/{routeId} | Recupera una ruta por ID                    | RouteDocument / RouteResource |
| getAllRoutes (GET)    | /api/routes/all-routes| Lista todas las rutas guardadas (historial) | List<RouteDocument> |

---

**PortController:**

###### Tabla 105

*Descripción de PortController en el Interface Layer de A/AI process*

| Propiedad     | Valor                                                                                     |
|---------------|-------------------------------------------------------------------------------------------|
| Nombre        | PortController                                                                           |
| Categoría     | Controller                                                                                |
| Propósito     | Exponer endpoints para gestión/consulta de puertos y utilitarios relacionados (ej. distancia entre puertos). |
| Base Path     | /api/ports (convención; el controller usa PortResource, CreatePortResource)      |

###### Tabla 106

*Métodos de PortController en el Interface Layer de A/AI process*

|Nombre (Método)        | Ruta (ejemplo)        | Acción                                | 
|--------------------   |-----------------------|---------------------------------------|
| createPort (POST) | /api/ports | Crea un nuevo puerto a partir del DTO CreatePortResource | 
| getPortById (GET)    | /api/ports/{portId} | Obtiene información del puerto                   | 
| getDistanceBetweenPorts (GET)    | /api/ports/distance-between-ports | Devuelve distancia/resultado entre dos puertos (usa RouteDistanceResource) | 

---

**Resources / DTOs:**

###### Tabla 107

*Listado de recursos encontrados en el Interface Layer de A/AI process*

| Recurso | Propósito/Uso |
|---------|---------------|
| RouteCalculationResource | Representa respuesta con datos de la ruta calculada (nodos, coste). |
| RouteRequestResource | DTO de petición para calcular una ruta (puerto inicio/fin, parámetros). |
| RouteDistanceResource | DTO de respuesta para distancias / mensajes de error relacionados. |
| PortResource | DTO de salida con datos de un puerto. |
| PortResource | DTO de entrada para creación de puerto. |

---

**Assemblers / Transformers:**

###### Tabla 108

*Listado de assemblers presentes en el Interface Layer de A/AI process*

| Clase | Propósito |
|-------|-----------|
| CreatePortCommandFromResourceAssembler | Transforma CreatePortResource → CreatePortCommand del Application Layer |
| PortResourceFromEntityAssembler | Transforma Port entity → PortResource para respuesta al cliente |

---

#### 5.4.3. A*/AI Process Bounded Context Application Layer
La capa de Application del bounded context A/AI process* orquesta los flujos de negocio que coordinan el dominio (A*, modelos y repositorios) y la capa de presentación (controllers). En el repositorio actual esta capa está implementada principalmente mediante Application Services (clases *Service y *ServiceImpl) que exponen las capacidades del bounded context: cálculo de rutas, construcción del grafo, provisión de condiciones de navegación y gestión de puertos y rutas persistidas. 

**RouteService:**

###### Tabla 109

*Descripción de RouteService en el Application Layer de A/AI process*

| Propiedad     | Valor                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteService`                                                                                                      |
| **Categoría** | Application Service                                                                                                 |
| **Propósito** | Orquestar operaciones de negocio relacionadas con rutas: cálculo, persistencia y consultas (historial, existencia). |

###### Tabla 110

*Métodos de RouteService en el Application Layer de A/AI process*

| Nombre                                                            | Tipo de retorno            | Descripción                                                                                                                                                                 |
| ----------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `calculateOptimalRoute(String startPortName, String endPortName)` | `RouteCalculationResource` | Orquesta el cálculo de la ruta óptima entre dos puertos (invoca servicios de dominio como `RouteCalculatorService` y `NavigationConditionsService`, arma la respuesta DTO). |
| `calculateTotalDistance(List<Port> route)`                        | `double`                   | Calcula distancia total para una lista de puertos (utilidad usada en reports/mediciones).                                                                                   |
| `findAllRoutes()`                                                 | `List<RouteDocument>`      | Recupera todas las rutas guardadas (historial).                                                                                                                             |
| `saveAllRoutes(List<RouteDocument> routes)`                       | `void`                     | Persiste una lista de rutas.                                                                                                                                                |
| `existsByHomePortAndDestinationPort(String h, String d)`          | `boolean`                  | Valida existencia de ruta entre puertos (para lógica de “popular routes”).                                                                                                  |
| `deleteAllRoutes()`                                               | `void`                     | Operación administrativa para limpiar rutas.                                                                                                                                |
---

**PortService:**

###### Tabla 111

*Descripción de PortServices en el Application Layer de A/AI process*

| Propiedad     | Valor                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `PortService`                                                                                                           |
| **Categoría** | Application Service                                                                                                     |
| **Propósito** | Operaciones CRUD y consultas sobre puertos; integrador de comandos de creación y de lectura para la capa de interfaces. |

###### Tabla 112

*Métodos de PortServices en el Application Layer de A/AI process*

| Nombre                                                    | Tipo de retorno          | Descripción                                                                                 |
| --------------------------------------------------------- | ------------------------ | ------------------------------------------------------------------------------------------- |
| `createPort(CreatePortCommand command)`                   | `Port`                   | Crea un nuevo `Port` a partir del comando (se usa el assembler desde la capa de Interface). |
| `saveAllPorts(List<Port> ports)`                          | `void`                   | Persiste una lista de puertos.                                                              |
| `findByNameAndContinent(String name, String continent)`   | `Optional<PortDocument>` | Busca puerto por nombre y continente.                                                       |
| `getPortById(String id)`                                  | `Optional<Port>`         | Recupera puerto por id.                                                                     |
| `getPortByName(String name)`                              | `Optional<Port>`         | Busca puerto por nombre.                                                                    |
| `getAllPorts()`                                           | `List<Port>`             | Recupera todos los puertos.                                                                 |
| `existsByNameAndContinent(String name, String continent)` | `boolean`                | Chequeo de existencia.                                                                      |
| `deletePort(String id)` / `deleteAllPorts()`              | `void`                   | Eliminación (individual/masiva).                                                            |

---

**RouteCalculatorServiceImpl:**

###### Tabla 113

*Descripción de RouteCalculatorServiceImpl en el Application Layer de A/AI process*

| Propiedad     | Valor                                                                                                                 |
| ------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteCalculatorServiceImpl`                                                                                          |
| **Categoría** | Application / Inbound Service (implementación de la capability de cálculo)                                            |
| **Propósito** | Implementa la orquestación concreta para calcular una ruta óptima: utiliza el grafo, las condiciones y el pathfinder. |

###### Tabla 114

*Métodos de RouteCalculatorServiceImpl en el Application Layer de A/AI process*

| Nombre                                        | Tipo de retorno | Descripción                                                                             |
| --------------------------------------------- | --------------- | --------------------------------------------------------------------------------------- |
| `calculateOptimalRoute(Port start, Port end)` | `List<Port>`    | Devuelve la secuencia de puertos que conforman la ruta calculada entre `start` y `end`. |

---

**RouteGraphBuilder:**

###### Tabla 115

*Descripción de RouteGraphBuilder en el Application Layer de A/AI process*

| Propiedad     | Valor                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteGraphBuilder`                                                                                   |
| **Categoría** | Application Service / Utility                                                                         |
| **Propósito** | Construir dinámicamente la representación de grafo (`RouteGraph`) que será usada por el algoritmo A*. |

###### Tabla 116

*Métodos de RouteGraphBuilder en el Application Layer de A/AI process*

| Nombre                                     | Tipo de retorno | Descripción                                                   |
| ------------------------------------------ | --------------- | ------------------------------------------------------------- |
| `buildDynamicRouteGraph()`                 | `RouteGraph`    | Construye y devuelve el grafo actual (nodos y aristas).       |
| `calculateTotalDistance(List<Port> route)` | `double`        | Calcula la distancia total de una ruta (servicio utilitario). |

---

**NavigationConditionsService:**

###### Tabla 117

*Descripción de NavigationConditionsService en el Application Layer de A/AI process*

| Propiedad     | Valor                                                                                                                                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `NavigationConditionsService`                                                                                                                                                                                     |
| **Categoría** | Application Service (adapter/inbound)                                                                                                                                                                             |
| **Propósito** | Proveer ajustes y penalizaciones de coste en función de condiciones de navegación (corrientes, clima, peligros). Consume/o prepara datos que vienen de `NavigationConditionsProvider` (Domain) y/o APIs externas. |

###### Tabla 118

*Métodos de NavigationConditionsService en el Application Layer de A/AI process*

| Nombre                                                                           | Tipo de retorno | Descripción                                                          |
| -------------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------- |
| `getAdjustedCost(Route route, Port homePort, Port destinationPort, Clock clock)` | `double`        | Retorna costo ajustado para una ruta basada en condiciones actuales. |
| `isAlongFavorableCurrent(Port from, Port to)`                                    | `boolean`       | Indica si el tramo cuenta con corrientes favorables.                 |
| `isAgainstStrongCurrent(Port from, Port to)`                                     | `boolean`       | Indica si el tramo va contra corriente fuerte.                       |

---

**Comands:**

###### Tabla 119

*Listado de Comandos en el Application Layer de A/AI process*

| Nombre              | Tipo / ubicación                                                | Propósito                                                                                       |
| ------------------- | --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `CreatePortCommand` | `mapping/domain/model/commands/CreatePortCommand.java` (record) | Estructura de datos para la creación de un `Port`. Consumido por `PortService.createPort(...)`. |

---

#### 5.4.4. A*/AI Process Bounded Context Infrastructure Layer

La capa de infraestructura contiene las implementaciones concretas que interactúan con sistemas externos: la base de datos (MongoDB), mapeadores entre documentos y entidades, y adaptadores para servicios externos. En este proyecto las implementaciones de repositorios (SDMDB documents/repositories), mappers y configuraciones de MongoDB se ubican aquí. Esta capa implementa las interfaces definidas en el Domain Layer y expone adaptadores que la Application Layer consume.

**RouteDocument:**

###### Tabla 120

*Descripción de RouteDocument en el Infrastructure Layer de A/AI process*

| Propiedad            | Valor                                                                                                                                                                                                                                                     |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `RouteDocument.java`                                                                                                                                                                                                                                      |
| **Categoría**        | Document / Persistence Model                                                                                                                                                                                                                              |
| **Propósito**        | Representar la entidad Route en la capa de persistencia (documento Mongo).                                                                                                                                                                                |
| **Campos típicos**   | `id` (String/UUID), `homePort` (String o subdocument con id/nombre), `destinationPort`, `nodes` (lista de nodos o referencias), `distance` (double), `cost` (double), `createdAt` (DateTime), `metadata` (map con info adicional como emisiones, eventos) |
| **Uso**              | Persistido vía `RouteRepository` para historial y consultas.                                                                                                                                                                                              |

---

**PortDocument:**

###### Tabla 121

*Descripción de PortDocument en el Infrastructure Layer de A/AI process*

| Propiedad            | Valor                                                                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `PortDocument.java`                                                                                                          |
| **Categoría**        | Document / Persistence Model                                                                                                 |
| **Propósito**        | Representar un puerto en la base de datos (documento Mongo).                                                                 |
| **Campos típicos**   | `id` (String/UUID), `name` (String), `coordinates` (lat,long), `continent` (String), `metadata` (capacidad, servicios, etc.) |
| **Uso**              | Persistido vía `PortRepository`, utilizado por `PortService` y para construir el grafo de rutas.                             |

---

**Repositorios:**

###### Tabla 122

*Descripción de RouteRepository en el Infrastructure Layer de A/AI process*

| Propiedad               | Valor                                                                                                                                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)**    | `RouteRepository.java`                                                                                                                                                                                      |
| **Categoría**           | Repository (Infra implementation / Spring Data repository)                                                                                                                                                  |
| **Propósito**           | Persistir y recuperar `RouteDocument` desde MongoDB. Implementa la abstracción definida en Domain (`IRouteRepository` o similar).                                                                           |
| **Operaciones típicas** | `save(RouteDocument)`, `saveAll(List<RouteDocument>)`, `findById(String)`, `findAll()`, `deleteById(String)`, consultas por `homePort` y `destinationPort` (p. ej. `findByHomePortAndDestinationPort(...)`) |
| **Notas**               | En la práctica suele extender `MongoRepository<RouteDocument, String>` o usar `@Repository` con `MongoTemplate` para consultas personalizadas.                                                              |

###### Tabla 123

*Descripción de PortRepository en el Infrastructure Layer de A/AI process*


| Propiedad               | Valor                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)**    | `PortRepository.java`                                                                                                              |
| **Categoría**           | Repository (Infra implementation / Spring Data repository)                                                                         |
| **Propósito**           | Persistir y recuperar `PortDocument` desde MongoDB. Implementa la abstracción definida en Domain (`IPortRepository` o similar).    |
| **Operaciones típicas** | `save(PortDocument)`, `findById(String)`, `findByName(String)`, `findAll()`, `existsByNameAndContinent(...)`, `deleteById(String)` |
| **Notas**               | Soporta las operaciones que `PortService` necesita para crear puertos y construir grafo.                                           |

---

**Mappers:**

###### Tabla 124

*Descripción de PortMapper y RouteMapper en el Infrastructure Layer de A/AI process*

| Propiedad           | Valor                                                                                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (ej.)**    | `PortMapper.java`, `RouteMapper.java`                                                                                                                   |
| **Categoría**       | Mapper / Adapter                                                                                                                                        |
| **Propósito**       | Convertir entre documentos de persistencia (`PortDocument`, `RouteDocument`) y entidades/VO del Domain Layer (`Port`, `Route`, `Node`).                 |
| **Métodos típicos** | `toDocument(Port)`, `toEntity(PortDocument)`, `toDocument(Route)`, `toEntity(RouteDocument)`                                                            |
| **Uso**             | Los Application Services y Repositories usan los mappers para no exponer documentos directamente al dominio; mantienen separación de responsabilidades. |

---

**Implementaciones MongoDB:**

###### Tabla 125

*Tabla de colecciones y notas de implementación para MongoDB en el Infrastructure Layer de A/AI process*


| Propiedad            | Valor                                                                                                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `MongoConfig.java` (o configuración en `application.properties`)                                                                                                                  |
| **Categoría**        | Configuration                                                                                                                                                                     |
| **Propósito**        | Configurar conexión a MongoDB (URI, cliente, `MongoTemplate`, serializadores), y parámetros de conexión (pool, timeouts).                                                         |
| **Uso**              | La infraestructura utiliza esta configuración para instanciar repositorios y `MongoTemplate`. En el repo hay referencias a `spring.data.mongodb.uri` en `application.properties`. |

---

**Adaptadores externos:**

###### Tabla 126

*Tabla de adaptadores externos en el Infrastructure Layer de A/AI process*

| Propiedad               | Valor                                                                                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Ejemplos**            | Adaptadores para APIs externas de clima / geopolitica .                                                                                            |
| **Categoría**           | External Adapter / HTTP Client                                                                                                                                                                   |
| **Propósito**           | Implementar llamadas HTTP a proveedores externos (weather API, geopolitical API), parsear respuestas y exponer un contrato interno (p. ej. `WeatherApiClient` → `NavigationConditionsProvider`). |
| **Tecnología sugerida** | `WebClient` (Spring WebFlux) o `RestTemplate`.                                                                                                           |
| **Consideración**       | Para la entrega del curso es aceptable simular (mocks) o usar un adapter con configuraciones que permitan habilitar/inhabilitar llamadas reales.                                                 |

---

**Logs / Monitoring:**


###### Tabla 127

*Tabla de los modelos de monitoreo y reportes en el Infrastructure Layer de A/AI process*

| Propiedad               | Valor                                                                                                                                          |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**              | `ErrorLog` (modelo de persistencia), `ServiceStatus`                                                                       |
| **Categoría**           | Observability / Persistence                                                                                                                    |
| **Propósito**           | Guardar registros de errores críticos, estado de servicios externos y alertas; pueden persistirse en MongoDB para auditoría y debugging.       |
| **Operaciones típicas** | `save(ErrorLog)`, `findRecentByService(String)`, `storeServiceStatus(ServiceStatus)`                                                           |
| **Notas**               | No es necesario un stack complejo; un collection simple en MongoDB con timestamp y nivel de severidad es suficiente para el alcance del curso. |

---

#### 5.4.5. A*/AI Process Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de A*/AI Process. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con el desarrollo y gestión de rutas con distintos algoritmos dentro de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

#### 5.4.6. A*/AI Process Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de A*/AI Process, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.4.6.1. A*/AI Process Bounded Context Domain Layer Class Diagrams
En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de A*/AI Process. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión y desarrollo de rutas en la plataforma de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.


![A*/AI CLASS DIAGRAM](../../assets/img/chapter-V/AI-Process-Class-Diagram.jpg)


##### 5.4.6.2. A*/AI Process Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de A*/AI Process. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión y desarrollo de rutas en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

---

### 5.5. Bounded Context: Service Design and Planning

En el contexto táctico, el Bounded Context de Service Design and Planning Asset agrupa toda la funcionalidad vinculada a la gestión de los Incoterms y mejores opciones para los usuarios dentro de Mushroom. 

Se encarga exclusivamente del cálculo, recomendación y cálculo de precio asociado al Incoterm para una operación dada. Recibe como entrada una vista de ruta (RouteView) y datos de la operación, ejecuta la calculadora de Incoterm (reglas con estimador de coste) y produce una recomendación justificable y un desglose de coste. Publica eventos para Service Operation and Monitoring, A*/AI Process y Notification.

#### 5.5.1. Service Design and Planning Bounded Context Domain Layer

En la capa de dominio de Service Design and Planning se modela la lógica de negocio mínima necesaria para validar los inputs, ejecutar reglas de Incoterm y producir resultados trazables.

**IncotermAssessment:**

###### Tabla 128
*Descripción de IncotermAssessment en el Domain Layer de Service Design and Planning*

|Propiedad|Valor|
|-|-|
|Nombre	|IncotermAssessment|
|Categoría| Aggregate Root (colección incoterm_assessments)|
|Propósito|	Representa un cálculo de Incoterm para una operación (route). Contiene entrada (referencia a RouteView), resultados recomendados, justificación, desglose de precio y metadatos.|

###### Tabla 129
*Atributos de IncotermAssessment en el Domain Layer de Service Design and Planning*

|Nombre	|Tipo de dato	|Visibilidad|	Descripción|
|-|-|-|-|
|id	|UUID|private	|Identificador único.|
|routeId	|String	|private	|Referencia a la ruta y al plan sobre el que se calcula el Incoterm.|
|requestedBy|	String|	private|	Actor que solicitó el cálculo del Incoterm (userId).
|recommendedIncoterm	|String|	private|	Incoterm recomendado según la ruta dada por el usuario.|
|justification|	Array < Object >	|private	|Lista breve de razones cuantitativas para la selección del Incoterm. |
|priceBreakdown|	Object	|private|	Montos de pago dados por el Incoterm que puede revisar el usuario.|
|status|	String|	private	| Estado del proceso de revisión de Incoterms |
|createdAt	|Date	|private|	Fecha de cálculo.|
|updatedAt|	Date	|private	Última actualización.|

###### Tabla 130
*Métodos de IncotermAssessment en el Domain Layer de Service Design and Planning*

|Nombre|	Tipo de retorno|	Visibilidad	|Descripción|
|-|-|-|-|
|IncotermAssessment(...)	|constructor |	public	|Crea con un modelo de input  que valida datos mínimos.|
|markCalculated(incoterm, justification, priceBreakdown, modelVersion, actor)	|void|	public|	Registra resultado, indica que el status es CALCULATED y genera evento IncotermCalculated.
|markFailedInsufficientData(missingFields, actor)	| void|	public|	Marca FAILED_INSUFFICIENT_DATA y genera evento IncotermCalculationFailed.|
|toView()|	IncotermAssessmentView|	public|	DTO para read models/UI.|

---

**IncotermType:**

###### Tabla 131
*Value Object de IncotermType en el Domain Layer de Service Design and Planning*

|Propiedad|Valor|
|-|-|
|Nombre|IncotermType|
|Propósito|	Enum con lista de Incoterms soportados para representarlos al momento de calcular.|
|Valores| FAS (Franco al costado del buque), FOB (Franco a bordo), CFR (Coste y Flete) y CIF (Coste, Seguro y Flete)|

---

**Status:**

###### Tabla 132
*Value Object de Status en el Domain Layer de Service Design and Planning*

|Propiedad|Valor|
|-|-|
|Nombre|Status|
|Propósito| Enum con la lista de valores posibles del estado de evaluación de recomendación de Incoterms en la aplicación.|
|Valores| CALCULATED, FAILED_INSUFFICIENT_DATA|

---

**Domain Services:**

###### Tabla 133

*Descripción de IncotermCalculatorService en el Domain Layer de Service Design and Planning*

|Propiedad | Valor|
|-|-|
| Nombre | IncotermCalculatorService |
| Categoría | Domain Service |
| Propósito | Ejecutar reglas (business rules) que relacionan origen/destino/cargo profile y proponer Incoterm(es). |

###### Tabla 134

*Descripción de CostEstimationService en el Domain Layer de Service Design and Planning*

|Propiedad|Valor|
|-|-|
| Nombre | CostEstimationService |
| Categoría | Domain Service |
| Propósito | Calcular desglose de coste asociado al Incoterm: flete, seguro, aduanas y cargos estimados. |

###### Tabla 135

*Descripción de ValidationService en el Domain Layer de Service Design and Planning*

|Propiedad|Valor|
|-|-|
| Nombre | ValidationService |
| Categoría | Domain Service |
| Propósito | Verificar que RouteView y datos complementarios están completos para cálculo.. |

---

**Domain Events:**

###### Tabla 136

*Tabla de eventos de dominio en el Domain Layer de Service Design and Planning*

|Evento	|Descripción|
|-|-|
|IncotermCalculated	|Assessment completado con Incoterm recomendado y desglose.|
|IncotermCalculationFailed	|Falló cálculo por datos insuficientes (lista de campos faltantes).|

---

#### 5.5.2. Service Design and Planning Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Service Design and Planning se exponen los endpoints REST necesarios para solicitar cálculos y consultar resultados. También se realiza la publicación de eventos asincrónicos "incoterm.events".

**IncotermController:**

###### Tabla 137

*Descripción de IncotermController en el Interface Layer de Service Design and Planning*

|Propiedad	|Valor|
|-|-|
|Nombre	|IncotermController|
|Categoría|	Controller (REST)|
|Propósito|	Endpoints para calcular Incoterm, consultar resultados y simular precio.|
|Ruta base	|/api/v1/incoterms|

###### Tabla 138

*Métodos de IncotermController en el Interface Layer de Service Design and Planning*

|Nombre	|Ruta	|Acción|	Handle|
|-|-|-|-|
|calculateIncoterm|	POST /calculate	|Recibe RouteView y datos de la operación, luego devuelve assessmentId o resultado directo	|CalculateIncotermCommand -> CalculateIncotermCommandHandler|
|getAssessment|	GET /{assessmentId}	|Obtener resultado detallado de Assessment|	GetIncotermAssessmentQuery -> GetIncotermAssessmentQueryHandler|

###### Tabla 139

*Descripción de Eventos asincronos relevantes publicados por el Interface Layer de Service Design and Planning*

|Eventos|	Propósito|
|-|-|
|incoterm.events	|Publica IncotermCalculated e IncotermCalculationFailed para los Bounded Context relacionados|

---

#### 5.5.3. Service Design and Planning Bounded Context Application Layer

La capa de aplicación del Bounded Context de Service Design and Planning coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones relacionadas al Aggregate de Incoterms. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**Command Handlers:**

###### Tabla 140

*Listado de Command Handlers del Application Layer de Assets and Resource Management*

|Nombre	|Categoría	|Propósito	|Comando|
|-|-|-|-|
|CalculateIncotermCommandHandler | Command Handler |Valida input, invoca ValidationService, IncotermCalculatorService y CostEstimationService, persiste IncotermAssessment. |	CalculateIncotermCommand|

---

**Query Handlers:**

###### Tabla 141

*Listado de Query Handlers del Application Layer de Assets and Resource Management*

|Nombre|	Categoría	|Propósito	|Query|
|-|-|-|-|
|GetIncotermAssessmentQueryHandler| Query Handler|	Recuperar IncotermAssessmentView desde incoterm_read.|	GetIncotermAssessmentQuery |

---

**Event Handlers:**

###### Tabla 142

*Listado de Event Handlers del Application Layer de Assets and Resource Management*

|Nombre	|Categoría	|Propósito	|Evento consumido|
|-|-|-|-|
|PortUpdatedEventHandler| Event Handler |Si RouteView cambia por cambio de puerto, marcar assessments relacionados para re-evaluar | PortUpdated (consumido desde Asset & Resource Management)|

---

#### 5.5.4. Service Design and Planning Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Service Design and Planning actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, y modelos de Incoterm necesarios.

Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la obtención de la información necesaria para el cálculo de los Incoterms asociados a cada ruta.

**Repositorios:**

###### Tabla 143

*Listado de repositorios en el Infrastructure Layer de Service Design and Planning*

|Nombre|	Categoría	|Propósito	|Interfaz|
|-|-|-|-|
|IncotermRepository	| Repositorio |Persistir incoterm_assessments	|IIncotermRepository|
|IncotermReadRepository	|Gestionar incoterm_read para consultas rápidas	|IIncotermReadRepository|

###### Tabla 144

*Métodos de IPortRepository en el Infrastructure Layer de Service Design and Planning*

|Nombre	|Tipo de retorno|	Descripción|
|-|-|-|
|findById(assessmentId)|	IncotermAssessment|	Recupera por id.|
|findByRouteId(routeId)|	List<IncotermAssessment>|	Recupera assessments asociados a route.|

---

**Implementaciones MongoDB:**

###### Tabla 145

*Tabla de colecciones y notas de implementación para MongoDB en el Infrastructure Layer de Service Design and Planning*

|Colección	|Propósito	|
|-|-|
|incoterm_assessments	|Persiste documento IncotermAssessment	|
|incoterm_read|	Read-model denormalizado para UI.	|

#### 5.5.5. Service Design and Planning Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Service Design and Planning. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión de de puertos y sus ubicaciones en mapa dentro de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

###### Figura 90
*Participación del Bounded Context de Service Design and Planning con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-MobileComponent.png"></image>

###### Figura 91
*Participación del Bounded Context de Service Design and Planning con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-WebComponent.png"></image>

###### Figura 92
*Participación del Bounded Context de Service Design and Planning con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-APIComponent.png"></image>

#### 5.5.6. Service Design and Planning Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Service Design and Planning, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.5.6.1. Service Design and Planning Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Service Design and Planning. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión de ubicaciones de puertos y estados en la plataforma de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

###### Figura 93
*Diagrama de clases de la capa de dominio del Bounded Context de Service Design and Planning*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/class-diagram-pot-management.png"></image>

##### 5.5.6.2. Service Design and Planning Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Service Design and Planning. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de puertos y estados en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

###### Figura 94
*Diagrama de base de datos del Bounded Context de Service Design and Planning*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

---

### 5.6. Bounded Context: Service Operation and Monitoring
En el contexto táctico, el Bounded Context Service Operation and Monitoring concentra la observabilidad, el monitoreo operativo y el control de las operaciones de Mushroom. Su objetivo es ofrecer una fuente única de verdad sobre el estado del sistema (servicios internos y dependencias externas como IA, clima y geopolítica) y sobre la ejecución de rutas marítimas (cumplimiento de ETA, desvíos, incidencias y cambios de riesgo), habilitando la detección temprana de anomalías y la reacción informada ante eventos.

Este módulo centraliza métricas, logs y eventos operativos, normaliza su semántica y los transforma en señales accionables: estados de servicio (ServiceStatus), alertas críticas (SystemAlert) y registros de error (ErrorLog). Desde allí, expone interfaces claras para que otros bounded contexts—por ejemplo, Report (que genera documentos descargables de desempeño, riesgos y emisiones) y Notification (que comunica fallos, desviaciones y cambios de ETA a usuarios finales)—consuman información consistente y confiable. Además, provee capacidades de control operacional (p. ej., pausar/reanudar monitoreo de una ruta, ajustar umbrales de alerta, forzar revalidaciones) que cierran el ciclo entre la supervisión y la acción.

Los límites de este bounded context están definidos para evitar acoplamientos indebidos: no calcula rutas ni optimiza trayectorias (responsabilidad del Core de Cálculo de Rutas), ni gestiona identidades o permisos (IAM). En su lugar, observa la ejecución, correla eventos de sistema y de operación, evalúa condiciones contra SLO/umbrales, y publica estados/alertas estandarizados. En el monolito con DDD, sus responsabilidades se organizan por capas (Domain, Application, Interface, Infrastructure) y se integran con el resto de la plataforma mediante servicios de aplicación e interfaces explícitas, manteniendo baja complejidad (sin brokers ni event bus) y privilegiando integraciones HTTP sencillas con las APIs externas.

---

#### 5.6.1. Service Operation and Monitoring Bounded Context Domain Layer

En la capa de dominio de Service Operation and Monitoring se modela la lógica de negocio mínima necesaria para validar los inputs, realizar una revisión de estado de los otros Bounded Context, desarrollar reportes y verificar puntajes de rutas con respecto a su popularidad o influencia.

**ServiceStatus:**

###### Tabla 146

*Descripción de ServiceStatus en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                 |
| ------------- | ------------------------------------------------------------------------------------- |
| **Nombre**    | ServiceStatus                                                                         |
| **Categoría** | **Aggregate Root**                                                                    |
| **Propósito** | Representar el estado “vivo” de un servicio (interno/externo) y su última evaluación. |

###### Tabla 147

*Atributos de ServiceStatus en el Domain Layer de Service Operation and Monitoring*

| Nombre      | Tipo                   | Visibilidad | Descripción                                          |
| ----------- | ---------------------- | ----------- | ---------------------------------------------------- |
| id          | `ServiceId`            | private     | Identidad del servicio monitorizado                  |
| name        | `ServiceName`          | private     | Nombre canónico (p. ej. `RouteEngine`, `WeatherAPI`) |
| kind        | `ServiceKind` (enum)   | private     | `INTERNAL` / `EXTERNAL`                              |
| endpoint    | `EndpointUrl?`         | private     | URL base si aplica (servicio externo)                |
| status      | `ServiceHealth` (enum) | private     | `UP` / `DEGRADED` / `DOWN` / `MAINTENANCE`           |
| lastCheck   | `Instant`              | private     | Timestamp de última evaluación                       |
| lastLatency | `Duration?`            | private     | Latencia reciente agregada                           |
| errorRate   | `Double?`              | private     | % de errores reciente (ventana corta)                |
| version     | `long`                 | private     | Versión para control de concurrencia optimista       |

###### Tabla 148

*Métodos de ServiceStatus en el Domain Layer de Service Operation and Monitoring*

| Nombre                       | Retorno          | Visibilidad | Descripción                                                                                  |
| ---------------------------- | ---------------- | ----------- | -------------------------------------------------------------------------------------------- |
| applyHealthCheck             | `void`           | public      | Aplica un `HealthCheckResult` y actualiza `status`, `lastLatency`, `errorRate`, `lastCheck`. |
| markMaintenance              | `void`           | public      | Pone el servicio en `MAINTENANCE`.                                                           |
| markDown                     | `void`           | public      | Pone el servicio en `DOWN`.                                                                  |
| markUp                       | `void`           | public      | Pone el servicio en `UP` y limpia métricas degradadas.                                       |
| toDomainEventIfStatusChanged | `StatusChanged?` | public      | Devuelve evento si cambió el estado desde la última evaluación.                              |

---

**SystemAlert:**

###### Tabla 149

*Descripción de SystemAlert en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------- |
| **Nombre**    | SystemAlert                                                                                           |
| **Categoría** | **Aggregate Root**                                                                                    |
| **Propósito** | Gestionar el ciclo de vida de una alerta (apertura, actualización, resolución) con severidad y causa. |

###### Tabla 150

*Atributos de SystemAlert en el Domain Layer de Service Operation and Monitoring*


| Nombre       | Tipo                     | Visibilidad | Descripción                                             |
| ------------ | ------------------------ | ----------- | ------------------------------------------------------- |
| id           | `AlertId`                | private     | Identificador de alerta                                 |
| serviceId    | `ServiceId`              | private     | Servicio afectado                                       |
| type         | `AlertType` (enum)       | private     | `AVAILABILITY`, `LATENCY`, `ERROR_SPIKE`, `INTEGRATION` |
| severity     | `Severity` (VO)          | private     | Severidad estándar (mapea a OTel)                       |
| status       | `AlertStatus` (enum)     | private     | `OPEN` / `ACKED` / `RESOLVED`                           |
| title        | `String`                 | private     | Resumen                                                 |
| description  | `String`                 | private     | Detalle técnico/negocio                                 |
| openedAt     | `Instant`                | private     | Fecha de apertura                                       |
| lastUpdateAt | `Instant`                | private     | Última actualización                                    |
| resolvedAt   | `Instant?`               | private     | Fecha de resolución si aplica                           |
| evidence     | `List<IncidentEvidence>` | private     | Evidencias adjuntas (latencias, errores, eventos)       |

###### Tabla 151

*Métodos de SystemAlert en el Domain Layer de Service Operation and Monitoring*

| Nombre        | Retorno                       | Visibilidad | Descripción                                         |
| ------------- | ----------------------------- | ----------- | --------------------------------------------------- |
| escalate      | `void`                        | public      | Incrementa severidad (p. ej., de `WARN` a `ERROR`). |
| acknowledge   | `void`                        | public      | Marca como reconocida por operaciones.              |
| addEvidence   | `void`                        | public      | Adjunta `IncidentEvidence`.                         |
| resolve       | `void`                        | public      | Cierra la alerta, set `RESOLVED` y `resolvedAt`.    |
| toDomainEvent | `AlertRaised`/`AlertResolved` | public      | Emite evento de apertura/cierre.                    |

---

**ErrorLog:**

###### Tabla 152

*Descripción de ErrorLog en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                         |
| ------------- | ----------------------------------------------------------------------------- |
| **Nombre**    | ErrorLog                                                                      |
| **Categoría** | **Entity**                                                                    |
| **Propósito** | Registrar errores o eventos inesperados con severidad y trazabilidad opcional |

###### Tabla 153

*Atributos de ErrorLog en el Domain Layer de Service Operation and Monitoring*

| Nombre     | Tipo                  | Visibilidad | Descripción                                        |
| ---------- | --------------------- | ----------- | -------------------------------------------------- |
| id         | `ErrorId`             | private     | Identificador                                      |
| serviceId  | `ServiceId?`          | private     | Servicio asociado (si aplica)                      |
| occurredAt | `Instant`             | private     | Momento de ocurrencia                              |
| severity   | `Severity`            | private     | Nivel de severidad                                 |
| code       | `String?`             | private     | Código o categoría (p. ej., `WEATHER_API_TIMEOUT`) |
| message    | `String`              | private     | Mensaje                                            |
| details    | `Map<String,Object>?` | private     | Datos estructurados (requestId, endpoint, etc.)    |
| traceId    | `String?`             | private     | Correlación con trazas                             |
| spanId     | `String?`             | private     | Correlación con spans                              |

---

**ServiceId:**

###### Tabla 154

*Value Object de ServiceId en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                           |
| ------------- | ------------------------------- |
| **Nombre**    | ServiceId                       |
| **Categoría** | Value Object                    |
| **Propósito** | Encapsular el ID de un servicio |

**ServiceName:**

###### Tabla 155

*Value Object de ServiceName en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | ServiceName                          |
| **Categoría** | Value Object                         |
| **Propósito** | Nombre legible y único en el dominio |

**EndpointUrl:**

###### Tabla 156

*Value Object de EndpintUrl en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                             |
| ------------- | --------------------------------- |
| **Nombre**    | EndpointUrl                       |
| **Categoría** | Value Object                      |
| **Propósito** | URL válida de dependencia externa |

**Severity:**

###### Tabla 157

*Value Object de Severity en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | Severity                                  |
| **Categoría** | Value Object                              |
| **Propósito** | Nivel estándar de severidad interoperable |

**HealthCheckResult:**

###### Tabla 158

*Value Object de HealthCheckResult en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | HealthCheckResult                          |
| **Categoría** | Value Object                               |
| **Propósito** | Resultado inmutable de un chequeo de salud |

**IncidentEvidence:**

###### Tabla 159

*Value Object de IncidentEvidence en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | IncidentEvidence                           |
| **Categoría** | Value Object                               |
| **Propósito** | Evidencia compacta que respalda una alerta |

---

**Enums:**

###### Tabla 160

*Listado de enums en el Domain Layer de Service Operation and Monitoring*

| Nombre | Valores |
|-|-|
|ServiceKind |INTERNAL, EXTERNAL|
|ServiceHealth | 1UP, DEGRADED, DOWN, MAINTENANCE|
|AlertType | AVAILABILITY, LATENCY, ERROR_SPIKE, INTEGRATION
|AlertStatus | OPEN, HACKED, RESOLVED |

---

**HealthAssessmentService:**

###### Tabla 161

*Descripción de HealthAssessmentService en el Domain Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                        |
| ------------- | ---------------------------------------------------------------------------- |
| **Nombre**    | HealthAssessmentService                                                      |
| **Categoría** | Domain Service                                                               |
| **Propósito** | Evaluar un `HealthCheckResult` y decidir `ServiceHealth` + si amerita alerta |

###### Tabla 162

*Métodos de HealthAssessmentService en el Domain Layer de Service Operation and Monitoring*

| Nombre           | Retorno         | Descripción                                                               |
| ---------------- | --------------- | ------------------------------------------------------------------------- |
| assess           | `ServiceHealth` | Aplica reglas (umbral latencia, % error, reachability) y devuelve estado. |
| shouldRaiseAlert | `boolean`       | Determina si se abre/escala alerta según política y estado previo.        |
| buildAlertFor    | `SystemAlert`   | Crea instancia inicial de `SystemAlert` usando `SystemAlertFactory`.      |

---

**SystemAlertFactory:**

###### Tabla 163

*Descripción de SystemAlertFactory en el Domain Layer de Service Operation and Monitoring*

| Propósito | Construir `SystemAlert` válido (ID, timestamps, severidad inicial) a partir de un `ServiceId`, `AlertType` y evidencia. |
| --------- | ----------------------------------------------------------------------------------------------------------------------- |

---

**Repositorios:**

###### Tabla 164

*Métodos de ServiceStatusRepository en el Domain Layer de Service Operation and Monitoring*

| Método     | Retorno               | Descripción                               |
| ---------- | --------------------- | ----------------------------------------- |
| findById   | `ServiceStatus?`      | Busca por `ServiceId`.                    |
| findAll    | `List<ServiceStatus>` | Lista todos.                              |
| save       | `ServiceStatus`       | Persiste (upsert) con control de versión. |
| findByKind | `List<ServiceStatus>` | Filtra por `INTERNAL/EXTERNAL`.           |

###### Tabla 165

*Métodos de SystemAlertRepository en el Domain Layer de Service Operation and Monitoring*

| Método                   | Retorno             | Descripción                        |
| ------------------------ | ------------------- | ---------------------------------- |
| findOpenByServiceAndType | `SystemAlert?`      | Alerta abierta para servicio+tipo. |
| save                     | `SystemAlert`       | Persiste/actualiza.                |
| findOpen                 | `List<SystemAlert>` | Todas abiertas.                    |
| findById                 | `SystemAlert?`      | Por `AlertId`.                     |

###### Tabla 166

*Métodos de ErrorLogRepository en el Domain Layer de Service Operation and Monitoring*

| Método              | Retorno          | Descripción                |
| ------------------- | ---------------- | -------------------------- |
| save                | `ErrorLog`       | Persiste log.              |
| findRecentByService | `List<ErrorLog>` | Últimos N por `serviceId`. |
| findByTraceId       | `List<ErrorLog>` | Útiles para correlación.   |

*Tabla de PopularRoute en el Domain Layer*

| Propiedad     | Valor                                                                                              |
| ------------- | -------------------------------------------------------------------------------------------------- |
| **Nombre**    | PopularRoute                                                                                       |
| **Categoría** | Aggregate Root                                                                                     |
| **Propósito** | Representar una ruta catalogada como “popular”, con métricas de uso y validación periódica por IA. |

*Tabla de atributos de PopularRoute*

| Nombre          | Tipo             | Visibilidad | Descripción                                       |
| --------------- | ---------------- | ----------- | ------------------------------------------------- |
| id              | `PopularRouteId` | private     | Identificador único de la ruta popular            |
| routeId         | `RouteId`        | private     | Identificador de la ruta base calculada por A*/AI |
| origin          | `PortCode`       | private     | Puerto de origen                                  |
| destination     | `PortCode`       | private     | Puerto de destino                                 |
| popularityScore | `double`         | private     | Puntaje compuesto de popularidad                  |
| usageCount      | `long`           | private     | Conteo de usos/selecciones                        |
| lastUsedAt      | `Instant`        | private     | Última vez que fue utilizada                      |
| lastValidatedAt | `Instant?`       | private     | Última fecha en la que fue revalidada por IA      |
| valid           | `boolean`        | private     | Indica si sigue siendo óptima/vigente             |
| safetyScore     | `double?`        | private     | Métrica de seguridad        		       |
| etaReliability  | `double?`        | private     | Confiabilidad de ETA       	               |

*Tabla de métodos de PopularRoute*

| Nombre         | Tipo de retorno | Visibilidad | Descripción                                          |
| -------------- | --------------- | ----------- | ---------------------------------------------------- |
| registerUsage  | `void`          | public      | Incrementa `usageCount` y actualiza `lastUsedAt`     |
| recomputeScore | `void`          | public      | Recalcula `popularityScore` con la política definida |
| markValidated  | `void`          | public      | Marca `valid` y setea `lastValidatedAt`              |

*Tabla de PopularityScore en el Domain Layer*

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | PopularityScore                      |
| **Categoría** | Value Object                         |
| **Propósito** | Encapsular el puntaje de popularidad |

*Tabla de PopularRouteRepository en el Domain Layer*

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | PopularRouteRepository                     |
| **Categoría** | Repository                                 |
| **Propósito** | Interfaz para persistencia de PopularRoute |

*Tabla de métodos de PopularRouteRepository*

| Nombre         | Tipo de retorno      | Visibilidad | Descripción                                         |
| -------------- | -------------------- | ----------- | --------------------------------------------------- |
| findTopN       | `List<PopularRoute>` | public      | Devuelve el top-N por `popularityScore`             |
| findByOD       | `List<PopularRoute>` | public      | Busca por par `origin`–`destination`                |
| save           | `PopularRoute`       | public      | Persiste/actualiza una PopularRoute                 |
| incrementUsage | `void`               | public      | Incrementa `usageCount` de una ruta (por `routeId`) |


---

#### 5.6.2. Service Operation and Monitoring Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Service Operation and Monitoring se exponen los endpoints REST necesarios para solicitar revisiones, revisar estados y consultar resultados tras cada reporte. Esta capa debe preservar un alto rendimiento para asegurar que la solución de problemas en el sistema se resuelva con rapidez y se eviden problemas a corto y largo plazo.

**OpsStatusController:**

###### Tabla 167

*Descripción de OpsStatusController en el Interface Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                         |
| ------------- | --------------------------------------------------------------------------------------------- |
| **Nombre**    | OpsStatusController                                                                           |
| **Categoría** | Controller                                                                                    |
| **Propósito** | Exponer el **estado de servicios** internos/externos del sistema (vista simple de operación). |
| **Ruta base** | `/api/ops/status`                                                                             |

###### Tabla 168

*Endpoints de OpsStatusController en el Interface Layer de Service Operation and Monitoring*

| Nombre           | Ruta                             | Método | Acción                                                        | Handle (Application)             |
| ---------------- | -------------------------------- | ------ | ------------------------------------------------------------- | -------------------------------- |
| GetAll           | `/`                              | GET    | Lista estados con filtros opcionales `kind`, `name`, `health` | `ListServiceStatusQuery`         |
| GetById          | `/{serviceId}`                   | GET    | Obtiene el estado de un servicio por id                       | `GetServiceStatusByIdQuery`      |
| MarkMaintenance  | `/{serviceId}/maintenance`       | POST   | Marca un servicio en **mantenimiento**                        | `MarkServiceMaintenanceCommand`  |
| ClearMaintenance | `/{serviceId}/maintenance/clear` | POST   | Sale de mantenimiento → **UP**                                | `ClearServiceMaintenanceCommand` |

---

**OpsAlertController:**

###### Tabla 169

*Descripción de OpsAlertController en el Interface Layer de Service Operation and Monitoring.*

| Nombre           | Ruta                             | Método | Acción                                                        | Handle (Application)             |
| ---------------- | -------------------------------- | ------ | ------------------------------------------------------------- | -------------------------------- |
| GetAll           | `/`                              | GET    | Lista estados con filtros opcionales `kind`, `name`, `health` | `ListServiceStatusQuery`         |
| GetById          | `/{serviceId}`                   | GET    | Obtiene el estado de un servicio por id                       | `GetServiceStatusByIdQuery`      |
| MarkMaintenance  | `/{serviceId}/maintenance`       | POST   | Marca un servicio en **mantenimiento**                        | `MarkServiceMaintenanceCommand`  |
| ClearMaintenance | `/{serviceId}/maintenance/clear` | POST   | Sale de mantenimiento → **UP**                                | `ClearServiceMaintenanceCommand` |

###### Tabla 170

*Endpoints de OpsAlertController en el Interface Layer de Service Operation and Monitoring*

| Nombre      | Ruta                 | Método | Acción                                                                                      | Handle (Application)      |
| ----------- | -------------------- | ------ | ------------------------------------------------------------------------------------------- | ------------------------- |
| List        | `/`                  | GET    | Lista alertas con filtros `status`, `type`, `serviceId` y paginación simple (`page`,`size`) | `ListAlertsQuery`         |
| GetById     | `/{alertId}`         | GET    | Detalle de una alerta (incluye evidencias)                                                  | `GetAlertByIdQuery`       |
| Open        | `/`                  | POST   | (Opcional) Abrir alerta manual (para pruebas)                                               | `OpenAlertCommand`        |
| Acknowledge | `/{alertId}/ack`     | POST   | Marcar alerta como **reconocida**                                                           | `AcknowledgeAlertCommand` |
| Resolve     | `/{alertId}/resolve` | POST   | Cerrar alerta con mensaje de resolución                                                     | `ResolveAlertCommand`     |

---

**OpsErrorController:**

###### Tabla 171

*Descripción de OpsErrorController en el Interface Layer de Service Operation and Monitoring.*

| Propiedad     | Valor                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------- |
| **Nombre**    | OpsErrorController                                                                        |
| **Categoría** | Controller                                                                                |
| **Propósito** | Consultar **registros de errores** del sistema de manera simple para soporte/diagnóstico. |
| **Ruta base** | `/api/ops/errors`                                                                         |

###### Tabla 172

*Endpoints de OpsErrorController en el Interface Layer de Service Operation and Monitoring*

| Nombre  | Ruta         | Método | Acción                                                                                                               | Handle (Application)   |
| ------- | ------------ | ------ | -------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| Search  | `/`          | GET    | Búsqueda por `serviceId`, rango de tiempo (`from`,`to`) y `severity` (INFO/WARN/ERROR/FATAL). Soporta `page`,`size`. | `SearchErrorLogsQuery` |
| GetById | `/{errorId}` | GET    | Detalle de un error puntual                                                                                          | `GetErrorLogByIdQuery` |

*Tabla de PopularRoutesController en el Interface Layer*

| Propiedad     | Valor                                  |
| ------------- | -------------------------------------- |
| **Nombre**    | PopularRoutesController                |
| **Categoría** | Controller                             |
| **Propósito** | Exponer endpoints para rutas populares |
| **Ruta base** | `/api/routes/popular`                  |

*Tabla de endpoints de PopularRoutesController*

| Nombre   | Ruta                  | Método | Acción                                                | Handle                        |
| -------- | --------------------- | ------ | ----------------------------------------------------- | ----------------------------- |
| List     | `/`                   | GET    | Listar top (filtros `origin`, `destination`, `limit`) | `GetPopularRoutesQuery`       |
| Detail   | `/{routeId}`          | GET    | Ficha detallada                                       | `GetPopularRouteDetailQuery`  |
| Validate | `/{routeId}/validate` | POST   | Revalidar (A*/AI) y marcar vigente                    | `ValidatePopularRouteCommand` |

*Tabla de RouteReportsController en el Interface Layer*

| Propiedad     | Valor                                   |
| ------------- | --------------------------------------- |
| **Nombre**    | RouteReportsController                  |
| **Categoría** | Controller                              |
| **Propósito** | Generar informe descargable de una ruta |
| **Ruta base** | `/api/reports/routes`                   |

*Tabla de endpoints de RouteReportsController*

| Nombre   | Ruta         | Método | Acción                                                                                       | Handle                        |
| -------- | ------------ | ------ | -------------------------------------------------------------------------------------------- | ----------------------------- |
| Generate | `/{routeId}` | POST   | Genera informe (Excel/PDF) con tiempos, eventos, emisiones; usa histórico + métricas de “ops” | `GenerateRouteReportCommand`* |

---

#### 5.6.3. Service Operation and Monitoring Bounded Context Application Layer 

La capa de aplicación del Bounded Context de Service Operation and Monitoring coordina el flujo de revisión de estados y procesos de todo el sistema con el fin de mantener seguridad y rendimiento continuo, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones relacionadas al monitoreo y salud del sistema. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**Command Handlers:**

###### Tabla 173

*Descripción de RecordHealthCheckCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                      |
| ------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | RecordHealthCheckCommandHandler                                                                                            |
| **Categoría** | Command Handler                                                                                                            |
| **Propósito** | Registrar un `HealthCheckResult` y actualizar `ServiceStatus` (UP/DEGRADED/DOWN/MAINTENANCE) usando reglas del dominio.    |
| **Comando**   | `RecordHealthCheckCommand { serviceId, measuredAt, latencyMs?, errorRate?, isReachable, notes? }`                          |
| **Efectos**   | Llama a `HealthAssessmentService` (dominio), `ServiceStatusRepository.save`. Si cambia el estado, publica `StatusChanged`. |

###### Tabla 174

*Descripción de MarkServiceMaintenanceCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                           |
| ------------- | ------------------------------------------------------------------------------- |
| **Nombre**    | MarkServiceMaintenanceCommandHandler                                            |
| **Categoría** | Command Handler                                                                 |
| **Propósito** | Marcar un servicio como `MAINTENANCE`.                                          |
| **Comando**   | `MarkServiceMaintenanceCommand { serviceId, reason? }`                          |
| **Efectos**   | `ServiceStatus.markMaintenance()` + `save` y publica `StatusChanged` si aplica. |

###### Tabla 175

*Descripción de ClearServiceMaintenanceCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | ClearServiceMaintenanceCommandHandler                              |
| **Categoría** | Command Handler                                                    |
| **Propósito** | Salir de mantenimiento → `UP` (si corresponde).                    |
| **Comando**   | `ClearServiceMaintenanceCommand { serviceId }`                     |
| **Efectos**   | `ServiceStatus.markUp()` + `save` y `StatusChanged` si hay cambio. |

###### Tabla 176

*Descripción de OpenAlertCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                             |
| ------------- | --------------------------------------------------------------------------------- |
| **Nombre**    | OpenAlertCommandHandler                                                           |
| **Categoría** | Command Handler                                                                   |
| **Propósito** | Abrir alerta manual (para pruebas o acción operativa).                            |
| **Comando**   | `OpenAlertCommand { serviceId, type, severity, title, description, evidence?[] }` |
| **Efectos**   | Usa `SystemAlertFactory.create(...)`, persiste y publica `AlertRaised`.           |

###### Tabla 177

*Descripción de AcknowledgeAlertCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                        |
| ------------- | -------------------------------------------- |
| **Nombre**    | AcknowledgeAlertCommandHandler               |
| **Categoría** | Command Handler                              |
| **Propósito** | Marcar alerta como **ACKED**.                |
| **Comando**   | `AcknowledgeAlertCommand { alertId, note? }` |
| **Efectos**   | `SystemAlert.acknowledge()`, `save`.         |

###### Tabla 178

*Descripción de ResolveAlertCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                     |
| ------------- | --------------------------------------------------------- |
| **Nombre**    | ResolveAlertCommandHandler                                |
| **Categoría** | Command Handler                                           |
| **Propósito** | Resolver alerta abierta.                                  |
| **Comando**   | `ResolveAlertCommand { alertId, resolutionMessage? }`     |
| **Efectos**   | `SystemAlert.resolve()`, `save`, publica `AlertResolved`. |

###### Tabla 179

*Descripción de LogErrorCommandHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                            |
| ------------- | -------------------------------------------------------------------------------- |
| **Nombre**    | LogErrorCommandHandler                                                           |
| **Categoría** | Command Handler                                                                  |
| **Propósito** | Registrar un `ErrorLog` con severidad/código y detalles.                         |
| **Comando**   | `LogErrorCommand { serviceId?, occurredAt, severity, code?, message, details? }` |
| **Efectos**   | Crea `ErrorLog`, persiste y publica `ErrorLogged`.                               |

---

**Query Handlers:**

###### Tabla 180

*Descripción de ListServiceStatusQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                      |
| ------------- | -------------------------------------------------------------------------- |
| **Nombre**    | ListServiceStatusQueryHandler                                              |
| **Categoría** | Query Handler                                                              |
| **Propósito** | Listar estados con filtros (`kind`, `name`, `health`) y paginación simple. |
| **Query**     | `ListServiceStatusQuery { filters..., page?, size? }`                      |
| **Efectos**   | Lectura en `ServiceStatusRepository`.                                      |

###### Tabla 181

*Descripción de GetServiceStatusByIdQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                     |
| ------------- | ----------------------------------------- |
| **Nombre**    | GetServiceStatusByIdQueryHandler          |
| **Categoría** | Query Handler                             |
| **Propósito** | Obtener estado por `serviceId`.           |
| **Query**     | `GetServiceStatusByIdQuery { serviceId }` |
| **Efectos**   | Lectura en `ServiceStatusRepository`.     |

###### Tabla 182

*Descripción de ListAlertsQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                   |
| ------------- | ----------------------------------------------------------------------- |
| **Nombre**    | ListAlertsQueryHandler                                                  |
| **Categoría** | Query Handler                                                           |
| **Propósito** | Listar alertas por `status`, `type`, `serviceId`, severidad (paginado). |
| **Query**     | `ListAlertsQuery { filters..., page?, size? }`                          |
| **Efectos**   | Lectura en `SystemAlertRepository`.                                     |

###### Tabla 183

*Descripción de GetAlertByIdQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                               |
| ------------- | ----------------------------------- |
| **Nombre**    | GetAlertByIdQueryHandler            |
| **Categoría** | Query Handler                       |
| **Propósito** | Detalle de alerta.                  |
| **Query**     | `GetAlertByIdQuery { alertId }`     |
| **Efectos**   | Lectura en `SystemAlertRepository`. |

###### Tabla 184

*Descripción de SearchErrorLogsQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                 |
| ------------- | ------------------------------------------------------------------------------------- |
| **Nombre**    | SearchErrorLogsQueryHandler                                                           |
| **Categoría** | Query Handler                                                                         |
| **Propósito** | Buscar `ErrorLog` por `serviceId`, rango de tiempo, severidad, `traceId`, paginación. |
| **Query**     | `SearchErrorLogsQuery { criteria..., page?, size? }`                                  |
| **Efectos**   | Lectura en `ErrorLogRepository`.                                                      |

###### Tabla 185

*Descripción de GetErrorLogByIdQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                              |
| ------------- | ---------------------------------- |
| **Nombre**    | GetErrorLogByIdQueryHandler        |
| **Categoría** | Query Handler                      |
| **Propósito** | Detalle de un error.               |
| **Query**     | `GetErrorLogByIdQuery { errorId }` |
| **Efectos**   | Lectura en `ErrorLogRepository`.   |

###### Tabla 186

*Descripción de GetOpsHealthSummaryQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                           |
| ------------- | --------------------------------------------------------------- |
| **Nombre**    | GetOpsHealthSummaryQueryHandler                                 |
| **Categoría** | Query Handler                                                   |
| **Propósito** | Resumen agregado (porcentaje UP/DEGRADED/DOWN, top degradados). |
| **Query**     | `GetOpsHealthSummaryQuery { window? }`                          |
| **Efectos**   | Lee `ServiceStatusRepository` y/o caches simples.               |

###### Tabla 187

*Descripción de GetOpsHealthByServiceQueryHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                       |
| ------------- | ----------------------------------------------------------- |
| **Nombre**    | GetOpsHealthByServiceQueryHandler                           |
| **Categoría** | Query Handler                                               |
| **Propósito** | Vista de salud para un servicio (últimos n chequeos).       |
| **Query**     | `GetOpsHealthByServiceQuery { serviceId, window? }`         |
| **Efectos**   | Lee `ServiceStatusRepository` (+ snapshots si los guardan). |

---

**Event Handlers:**

###### Tabla 188

*Descripción de OnStatusChangedEventHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                           |
| ------------- | --------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | OnStatusChangedEventHandler                                                                                     |
| **Categoría** | Event Handler                                                                                                   |
| **Evento**    | `StatusChanged { serviceId, previous, current, at }`                                                            |
| **Propósito** | Política simple: si `current == DOWN` abrir alerta `AVAILABILITY`; si vuelve a `UP`, resolver alertas abiertas. |
| **Efectos**   | Invoca `OpenAlertCommand` o `ResolveAlertCommand`.                                                              |

###### Tabla 189

*Descripción de OnAlertRaisedEventHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                            |
| ------------- | -------------------------------------------------------------------------------- |
| **Nombre**    | OnAlertRaisedEventHandler                                                        |
| **Categoría** | Event Handler                                                                    |
| **Evento**    | `AlertRaised { alertId, serviceId, type, severity, at }`                         |
| **Propósito** | Auditoría/notificación interna (ej.: persistir un registro de actividad simple). |
| **Efectos**   | Guardar actividad en una colección simple                            |

###### Tabla 190

*Descripción de OnAlertResolvedEventHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                      |
| ------------- | ---------------------------------------------------------- |
| **Nombre**    | OnAlertResolvedEventHandler                                |
| **Categoría** | Event Handler                                              |
| **Evento**    | `AlertResolved { alertId, serviceId, at }`                 |
| **Propósito** | Auditoría al resolver; podría recalcular “score” de salud. |
| **Efectos**   | Actualiza métricas resumidas (si las almacenan).           |

###### Tabla 191

*Descripción de OnErrorLoggedEventHandler en el Application Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                |
| ------------- | ---------------------------------------------------------------------------------------------------- |
| **Nombre**    | OnErrorLoggedEventHandler                                                                            |
| **Categoría** | Event Handler                                                                                        |
| **Evento**    | `ErrorLogged { errorId, serviceId?, severity, at }`                                                  |
| **Propósito** | Correlacionar errores recientes con estado del servicio (si muchos errores → degradar/abrir alerta). |
| **Efectos**   | Podría encadenar `OpenAlertCommand` tipo `ERROR_SPIKE`.                                              |

*Tabla de RegisterRouteUsageCommandHandler en el Application Layer*

| Propiedad     | Valor                                           |
| ------------- | ----------------------------------------------- |
| **Nombre**    | RegisterRouteUsageCommandHandler                |
| **Categoría** | Command Handler                                 |
| **Propósito** | Registrar uso de una ruta popular               |
| **Comando**   | `RegisterRouteUsageCommand { routeId, usedAt }` |

*Tabla de ValidatePopularRouteCommandHandler en el Application Layer*

| Propiedad     | Valor                                                        |
| ------------- | ------------------------------------------------------------ |
| **Nombre**    | ValidatePopularRouteCommandHandler                           |
| **Categoría** | Command Handler                                              |
| **Propósito** | Revalidar una ruta popular contra A*/AI (clima/geo actuales) |
| **Comando**   | `ValidatePopularRouteCommand { routeId }`                    |

*Tabla de GetPopularRoutesQueryHandler en el Application Layer*

| Propiedad     | Valor                          |
| ------------- | ------------------------------ |
| **Nombre**    | GetPopularRoutesQueryHandler   |
| **Categoría** | Query Handler                  |
| **Propósito** | Obtener top de rutas populares |
| **Query**     | `GetPopularRoutesQuery`        |

*Tabla de GetPopularRouteDetailQueryHandler en el Application Layer*

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | GetPopularRouteDetailQueryHandler           |
| **Categoría** | Query Handler                               |
| **Propósito** | Obtener ficha detallada de una ruta popular |
| **Query**     | `GetPopularRouteDetailQuery { routeId }`    |

---

#### 5.6.4. Service Operation and Monitoring Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Service Operation and Monitoring actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración del monitoreo y la gestión de reportes puntuales. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos y desarrollo de reportes necesarios.

Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio.

**MongoConfig:**

###### Tabla 192

*Descripción de Mongo Configuration en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                    |
| ------------- | ------------------------------------------------------------------------ |
| **Nombre**    | `MongoConfig`                                                            |
| **Categoría** | Configuración (DataSource/MongoTemplate)                                 |
| **Propósito** | Exponer `MongoClient` y `MongoTemplate` para el resto de la capa.        |
| **Detalles**  | Lee `spring.data.mongodb.uri` y base de datos; registra `MongoTemplate`. |

---

**ServiceStatusDocument:**

###### Tabla 193

*Descripción de ServiceStatusDocument en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                                                                |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `ServiceStatusDocument`                                                                                                                                              |
| **Colección** | `ops_service_status`                                                                                                                                                 |
| **Campos**    | `id:String`, `name:String` (único), `kind:String`, `endpoint:String?`, `status:String`, `lastCheck:Date`, `lastLatencyMs:Long?`, `errorRate:Double?`, `version:Long` |
| **Índices**   | Único por `name`; secundario por `status` y `kind`                                                                                                                   |

---

**SystemAlertDocument:**

###### Tabla 194

*Descripción de SystemAlertDocument en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                                                                                              |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `SystemAlertDocument`                                                                                                                                                                              |
| **Colección** | `ops_system_alerts`                                                                                                                                                                                |
| **Campos**    | `id:String`, `serviceId:String`, `type:String`, `severity:String`, `status:String`, `title:String`, `description:String`, `openedAt:Date`, `lastUpdateAt:Date`, `resolvedAt:Date?`, `evidence:[…]` |
| **Índices**   | `{ serviceId:1, status:1, openedAt:-1 }` para listar abiertas y por servicio                                                                                                                       |

---

**ErrorLogDocument:**

###### Tabla 195

*Descripción de ErrorLogDocument en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `ErrorLogDocument`                                                                                                                      |
| **Colección** | `ops_error_logs`                                                                                                                        |
| **Campos**    | `id:String`, `serviceId:String?`, `occurredAt:Date`, `severity:String`, `code:String?`, `message:String`, `details:Map<String,Object>?` |
| **Índices**   | **TTL en `occurredAt`** (por ejemplo 30 días) + `{ serviceId:1, occurredAt:-1 }`                                                        |

---

**ServiceStatusDocumentMapper:**

###### Tabla 196

*Descripción de ServiceStatusDocumentMapper en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                                                                                              |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `SystemAlertDocument`                                                                                                                                                                              |
| **Colección** | `ops_system_alerts`                                                                                                                                                                                |
| **Campos**    | `id:String`, `serviceId:String`, `type:String`, `severity:String`, `status:String`, `title:String`, `description:String`, `openedAt:Date`, `lastUpdateAt:Date`, `resolvedAt:Date?`, `evidence:[…]` |
| **Índices**   | `{ serviceId:1, status:1, openedAt:-1 }` para listar abiertas y por servicio                                                                                                                       |

---

**ErrorLogDocument:**

###### Tabla 197

*Descripción de ErrorLogDocument en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `ErrorLogDocument`                                                                                                                      |
| **Colección** | `ops_error_logs`                                                                                                                        |
| **Campos**    | `id:String`, `serviceId:String?`, `occurredAt:Date`, `severity:String`, `code:String?`, `message:String`, `details:Map<String,Object>?` |
| **Índices**   | **TTL en `occurredAt`** + `{ serviceId:1, occurredAt:-1 }`                                                        |

---

**ServiceStatusDocumentMapper:**

###### Tabla 198

*Descripción de ServiceStatusDocumentMapper en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                  |
| ------------- | ---------------------------------------------------------------------- |
| **Nombre**    | `ServiceStatusDocumentMapper`                                          |
| **Categoría** | Mapper                                                                 |
| **Propósito** | Convertir `ServiceStatus` (dominio) <-> `ServiceStatusDocument` (infra). |

---

**SystemAlertDocumentMapper:**

###### Tabla 199

*Descripción de SystemAlertDocumentMapper en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                       |
| ------------- | --------------------------------------------------------------------------- |
| **Nombre**    | `SystemAlertDocumentMapper`                                                 |
| **Categoría** | Mapper                                                                      |
| **Propósito** | Convertir `SystemAlert` <-> `SystemAlertDocument` (incl. `IncidentEvidence`). |

---

**ErrorLogDocumentMapper:**

###### Tabla 200

*Descripción de ErrorLogDocumentMapper en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                      |
| ------------- | ------------------------------------------ |
| **Nombre**    | `ErrorLogDocumentMapper`                   |
| **Categoría** | Mapper                                     |
| **Propósito** | Convertir `ErrorLog` <-> `ErrorLogDocument`. |

---

**ServiceStatusMongoRepository:**

###### Tabla 201

*Descripción de ServiceStatusMongoRepository en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                              |
| ------------- | ------------------------------------------------------------------ |
| **Nombre**    | `ServiceStatusMongoRepository`                                     |
| **Categoría** | Spring Data `MongoRepository<ServiceStatusDocument, String>`       |
| **Propósito** | CRUD y búsquedas por convención                                    |
| **Métodos**   | `findByName(String)`, `findByKind(String)`, `findByStatus(String)` |

---

**SystemAlertMongoRepository:**

###### Tabla 202

*Descripción de SystemAlertMongoRepository en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                                          |
| ------------- | ------------------------------------------------------------------------------ |
| **Nombre**    | `SystemAlertMongoRepository`                                                   |
| **Categoría** | `MongoRepository<SystemAlertDocument, String>`                                 |
| **Propósito** | CRUD y listados                                                                |
| **Métodos**   | `findByStatus(String, PageRequest)`, `findByServiceIdAndStatus(String,String)` |

---

**ErrorLogMongoRepository:**

###### Tabla 203

*Descripción de ErrorLogMongoRepository en el Infrastructure Layer de Service Operation and Monitoring*

| Propiedad     | Valor                                                             |
| ------------- | ----------------------------------------------------------------- |
| **Nombre**    | `ErrorLogMongoRepository`                                         |
| **Categoría** | `MongoRepository<ErrorLogDocument, String>`                       |
| **Propósito** | CRUD y búsquedas con filtros                                      |
| **Métodos**   | `findByServiceIdAndOccurredAtBetween(...)`, `findBySeverity(...)` |


*Tabla de PopularRouteMongoRepository*

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | PopularRouteMongoRepository          |
| **Categoría** | Spring Data Repository               |
| **Propósito** | Persistir y consultar `PopularRoute` |

*Tabla de RouteReportMongoRepository*

| Propiedad     | Valor                                       |
| ------------- | ------------------------------------------- |
| **Nombre**    | RouteReportMongoRepository                  |
| **Categoría** | Spring Data Repository                      |
| **Propósito** | Persistir y consultar documentos de reporte |

*Tabla combinada de componentes de generación de reportes*

| Componente           | Capa           | Propósito                                                         |
| -------------------- | -------------- | ----------------------------------------------------------------- |
| RouteReportGenerator | Application    | Orquesta la construcción del informe                              |
| PdfExporter          | Infrastructure | Exporta/serializa el informe a PDF (y/o Excel) listo para descarga |

#### 5.7.1.5. Service Operation and Monitoring Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Service Operation and Monitoring. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con el monitoreo del rendimiento y salud de los otros Bounded Context de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

#### 5.7.1.6. Service Operation and Monitoring Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Service Operation and Monitoring, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.7.1.6.1. Service Operation and Monitoring Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Service Operation and Monitoring. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en el monitoreo del rendimiento y salud de los Bounded Context de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

##### 5.7.1.6.2. Service Operation and Monitoring Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Service Operation and Monitoring. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de puertos y estados en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

<img src="../..//assets/img/chapter-V/service-operation-and-monitoring-class-diagram.png">

---

### 5.7. Bounded Context: Notifications

El bounded context de Notification cubre dos usos bien acotados dentro de Mushroom, centrandose en las notificaciones de registro exitoso (correo al usuario inmediatamente después del sign-up), y las notificaciones in-app básicas en el Dashboard principal de visualización (listar, marcar como leídas y eliminar). Se mantiene deliberadamente simple y desacoplado del resto de Bounded Context. La capa de infraestructura usa un adaptador de e-mail (SMTP — configurado con Gmail en este MVP) y un repositorio para persistir notificaciones in-app.

#### 5.7.1. Notifications Bounded Context Domain Layer

En la capa de dominio de Notifications se modela la lógica de negocio mínima necesaria para desarrollar notificaciones rápidas y concisas con información pertinente para el usuario, además de su envío a través de los servicios externos conectados, brindando rendimiento y confiabilidad en todo momento con el fin de asegurar que el usuario este siempre informado de los cambios relevantes en la aplicación.

**Notification**

###### Tabla 204

*Descripción de Notification en el Domain Layer de Notifications*

| Propiedad     | Valor                                                                                   |
|---------------|-----------------------------------------------------------------------------------------|
| **Nombre**    | `Notification`                                                                          |
| **Categoría** | Entity                                                                                  |
| **Propósito** | Representar una notificación mostrada en el dashboard o enviada por correo electrónico. |

###### Tabla 205

*Atributos de Notification en el Domain Layer de Notifications*

| Nombre        | Tipo de dato     | Visibilidad | Descripción                                                        |
|---------------|------------------|-------------|--------------------------------------------------------------------|
| id            | `String`         | private     | Identificador único                                                |
| recipientId   | `String`         | private     | Usuario destinatario                                               |
| title         | `String`         | private     | Título breve                                                       |
| message       | `String`         | private     | Contenido                                                          |
| channel       | `Channel` (enum) | private     | `IN_APP` o `EMAIL`                                                 |
| status        | `Status` (enum)  | private     | `UNREAD`, `READ`, `DELETED`                                        |
| createdAt     | `DateTime`       | private     | Fecha/hora de creación                                             |
| readAt        | `DateTime?`      | private     | Fecha de lectura (opcional)                                        |

###### Tabla 206

*Métodos de Notification en el Domain Layer de Notifications*

| Nombre        | Tipo de retorno | Visibilidad | Descripción                               |
|---------------|-----------------|-------------|-------------------------------------------|
| markRead      | `void`          | public      | Cambia `status` a `READ` y setea `readAt` |
| delete        | `void`          | public      | Cambia `status` a `DELETED`               |

---

**Channel (Enum):**

###### Tabla 207

*Valor de Channel (Enum) en el Domain Layer de Notifications*

| Valor     | Descripción                                  |
|-----------|----------------------------------------------|
| `IN_APP`  | Notificación mostrada en dashboard           |
| `EMAIL`   | Notificación enviada por correo electrónico  |

---

**Status (Enum):**

###### Tabla 208

*Valor de Status (Enum) en el Domain Layer de Notifications*

| Valor      | Descripción                 |
|------------|-----------------------------|
| `UNREAD`   | No leída                    |
| `READ`     | Leída                       |
| `DELETED`  | Eliminada (soft-delete)     |

---

**INotificationRepository:**

###### Tabla 209

*Descripción de INotificationRepository en el Domain Layer de Notifications*

| Método                        | Retorno                   | Descripción                                     |
|------------------------------|---------------------------|-------------------------------------------------|
| `save(notification)`         | `Notification`            | Persiste/actualiza                              |
| `findById(id)`               | `Optional<Notification>`  | Busca por id                                    |
| `findByRecipient(recipient)` | `List<Notification>`      | Lista por usuario                               |
| `deleteById(id)`             | `void`                    | Soft-delete (status = `DELETED`)                |

El alcance es pequeño y no se modelan eventos de dominio ni patrones de consistencia cross-servicio. Si más adelante se disparan notificaciones desde otros Bounded Context, puede evolucionar a event-driven y, de requerirse, Transactional Outbox.

---

#### 5.7.2. Notifications Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Notifications se exponen los endpoints REST necesarios para el registro, redacción y envió de notificaciones, tanto por correo como SMS. Esta capa debe preservar un alto rendimiento para asegurar que la solución de problemas en el sistema se resuelva con rapidez y se eviden problemas a corto y largo plazo.

**NotificationController**

###### Tabla 210

*Descripción de NotificationController en el Interface Layer de Notifications*

| Propiedad     | Valor                                   |
|---------------|-----------------------------------------|
| **Nombre**    | `NotificationController`                |
| **Categoría** | Controller                              |
| **Ruta base** | `/api/notifications`                    |
| **Produces**  | `application/json`                      |

###### Tabla 211

*Endpoints de NotificationController en el Interface Layer de Notifications*

| Método | Ruta                                   | Acción                                      | Body / Query                     | Respuesta                       |
|-------:|----------------------------------------|---------------------------------------------|----------------------------------|---------------------------------|
| `GET`  | `/`                                    | Listar notificaciones del usuario           | `recipientId` (query)            | `List<NotificationResource>`    |
| `POST` | `/{id}/read`                           | Marcar notificación como leída              | —                                | `204 No Content`                |
| `DELETE` | `/{id}`                              | Eliminar (soft-delete)                       | —                                | `204 No Content`                |
| `POST` | `/registration-success`                | Crear notificación de registro y (si aplica) enviar e-mail | `RegistrationSuccessResource` | `201 Created` (`NotificationResource`) |

---

**DTOs (Resources):**

###### Tabla 212

*Descripción de NotificationResource en el Interface Layer de Notifications*

| Campo       | Tipo          |
|-------------|---------------|
| id          | `String`      |
| recipientId | `String`      |
| title       | `String`      |
| message     | `String`      |
| channel     | `String` (`IN_APP`/`EMAIL`) |
| status      | `String` (`UNREAD`/`READ`/`DELETED`) |
| createdAt   | `string (ISO)`|
| readAt      | `string (ISO)?`|

###### Tabla 213

*Descripción de RegistrationSuccessResource en el Interface Layer de Notifications*

###### Tabla 10 — `RegistrationSuccessResource`

| Campo        | Tipo      | Descripción                                |
|--------------|-----------|--------------------------------------------|
| recipientId  | `String`  | Usuario registrado                         |
| email        | `String`  | Correo del usuario                         |
| fullName     | `String`  | Nombre para personalizar el e-mail         |

**Assemblers:**

- `NotificationResourceFromEntityAssembler` — `Notification -> NotificationResource`  
- `CreateRegistrationNotificationAssembler` — `RegistrationSuccessResource -> Notification (EMAIL/IN_APP)`

---

#### 5.7.3. Notification Bounded Context **Application Layer**

La capa de aplicación del Bounded Context de Notifications coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones relacionadas al desarrollo y envio de notificaciones. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**Servicios**

###### Tabla 214

*Listado de servicios empleados en el Application Layer de Notifications*

| Servicio              | Responsabilidad                                                                                                   |
|----------------------|---------------------------------------------------------------------------------------------------------------------|
| `NotificationService`| Orquestar notificaciones in-app (listar, marcar como leída, eliminar) y la creación de notificación de registro.   |
| `EmailService`       | Abstracción de envío de e-mails. En esta versión se provee un adapter SMTP (configurado con Gmail).                 |

**Flujo de “Registro exitoso”**

1) El **controller** recibe `RegistrationSuccessResource`.  
2) `NotificationService` crea la notificación **IN_APP** para el usuario.  
3) Si la política indica canal **EMAIL**, delega en `EmailService` → adapter SMTP.  
4) El servicio devuelve estado de entrega para registro/auditoría.

---

#### 5.7.4. Notification Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Notifications actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, y modelos de notificaciones necesarios.

Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la obtención de la información necesarios para el desarrollo y envío de notificaciones.

**Componentes:**

###### Tabla 215

*Componentes de e-mail para el Infrastructure Layer de Notifications*

| Componente                | Tipo            | Propósito                                                                                 |
|--------------------------|-----------------|-------------------------------------------------------------------------------------------|
| `SpringEmailService`     | Service Adapter | Adaptador de infraestructura que encapsula el envío de correos vía SMTP (Gmail).         |
| `EmailProperties`        | Config          | Propiedades de configuración (host, puerto, usuario, TLS/SSL, *timeouts*).                |
| `NotificationRepository` | Repository      | Persistencia de notificaciones in-app (in-memory o relacional).                           |

**Configuración operativa (MVP)**

- SMTP: `smtp.gmail.com` (STARTTLS 587 o SSL 465).  
- Autenticación: **App Password** (cuenta con 2FA).  
- Cuenta dedicada de envío (p. ej., `noreply@mushroom.example`).  
- Variables de entorno / secret manager para credenciales.

**Resiliencia**

- Reintentos transitorios con *backoff* (2–3 intentos).  
- Registro de fallos y posibilidad de reproceso programado.  
- Si el volumen crece: incorporar **Outbox/Queue** y un **Email Worker**.

---

#### 5.7.5. Notification Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Notifications. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión del desarrollo y envío de notificaciones en la aplicación.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

#### 5.7.6. Notification Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Notifications, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 5.7.6.1. Notification Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Notifications. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión del desarrollo y envio de notificaciones de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

![NotificationsClassDiagram](../../assets/img/chapter-V/NotificationsDiagramC.png)

##### 5.7.6.2. Notification Bounded Context Database Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Notifications. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de notificaciones en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.
