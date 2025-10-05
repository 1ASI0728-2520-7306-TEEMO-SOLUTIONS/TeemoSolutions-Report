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

¡Perfecto, Fabrizio! Tomé tus controladores y los documenté en el **Interface Layer** con el mismo formato de tablas que mostraste (Nombre, Categoría, Propósito, Ruta + métodos con Ruta, Acción y Handle). Mantengo todo en español y agrego una nota breve por controlador con consideraciones de respuesta/seguridad.

---

## **AuthenticationController**

###### Tabla 26

*Tabla de **AuthenticationController** en el Interface Layer*

| Propiedad         | Valor                                           |
| ----------------- | ----------------------------------------------- |
| **Nombre**        | AuthenticationController                        |
| **Categoría**     | Controller                                      |
| **Propósito**     | Exponer endpoints para registro y autenticación |
| **Ruta**          | `/api/authentication`                           |
| **Tag (OpenAPI)** | `Authentication`                                |

###### Tabla 27

*Tabla de métodos de **AuthenticationController***

| Nombre | Ruta       | Acción                     | Handle                                        |
| ------ | ---------- | -------------------------- | --------------------------------------------- |
| signUp | `/sign-up` | Registrar usuario          | `SignUpCommand` → `userCommandService.handle` |
| signIn | `/sign-in` | Autenticar usuario (login) | `SignInCommand` → `userCommandService.handle` |

> **Notas:**
> * `signUp` devuelve `201 Created` con `UserResource` o `400 Bad Request`.
> * `signIn` devuelve `200 OK` con `AuthenticatedUserResource` o `404 Not Found` si credenciales inválidas.

---

## **RolesController**

###### Tabla 28

*Tabla de **RolesController** en el Interface Layer*

| Propiedad         | Valor                     |
| ----------------- | ------------------------- |
| **Nombre**        | RolesController           |
| **Categoría**     | Controller                |
| **Propósito**     | Exponer catálogo de roles |
| **Ruta**          | `/api/roles`              |
| **Tag (OpenAPI)** | `Roles`                   |

###### Tabla 28

*Tabla de métodos de **RolesController***

| Nombre      | Ruta | Acción                 | Handle                                         |
| ----------- | ---- | ---------------------- | ---------------------------------------------- |
| getAllRoles | `/`  | Listar todos los roles | `GetAllRolesQuery` → `roleQueryService.handle` |

> **Notas:**
>
> * Respuesta: `200 OK` con `List<RoleResource>`.
> * Protección recomendada: solo accesible a `ROLE_ADMIN` si el catálogo no es público.

---

## **UsersController**

###### Tabla 29

*Tabla de **UsersController** en el Interface Layer*

| Propiedad     | Valor                                |
| ------------- | ------------------------------------ |
| **Nombre**    | UsersController                      |
| **Categoría** | Controller                           |
| **Propósito** | Exponer consultas de usuarios (CQRS) |
| **Ruta**      | `/api/v1/users`                      |

###### Tabla 30

*Tabla de métodos de **UsersController***

| Nombre      | Ruta        | Acción                 | Handle                                         |
| ----------- | ----------- | ---------------------- | ---------------------------------------------- |
| getAllUsers | `/`         | Listar usuarios        | `GetAllUsersQuery` → `userQueryService.handle` |
| getUserById | `/{userId}` | Obtener usuario por ID | `GetUserByIdQuery` → `userQueryService.handle` |

> **Notas:**
> * `getAllUsers`: `200 OK` con `List<UserResource>`.
> * `getUserById`: `200 OK` con `UserResource` o `404 Not Found`.


---


#### 4.2.1.3. IAM Bounded Context Application Layer 

La capa de aplicación del Bounded Context de IAM coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin mezclar reglas de negocio. Aquí residen los Command Handlers, Query Handlers y Event Handlers, responsables de ejecutar operaciones como el registro, inicio o cierre de sesión, así como la gestión de eventos relacionados con la identidad de los usuarios. Esta capa asegura que las acciones se realicen de manera transaccional, manteniendo la integridad del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según corresponda.

## SeedRolesCommandHandler
Tabla de SeedRolesCommandHandler en el Application Layer de IAM
| Propiedad        | Valor                                           |
| ---------------- | ----------------------------------------------- |
| **Nombre**       | SeedRolesCommandHandler                         |
| **Categoría**    | Command Handler                                 |
| **Propósito**    | Sembrar (crear si faltan) los roles del sistema |
| **Comando**      | `SeedRolesCommand`                              |
| **Dependencias** | `RoleRepositoryImpl`                            |

## ApplicationReadyEventHandler
Tabla de ApplicationReadyEventHandler en el Application Layer de IAM'
| Propiedad           | Valor                                                 |
| ------------------- | ----------------------------------------------------- |
| **Nombre**          | ApplicationReadyEventHandler                          |
| **Categoría**       | Event Handler (Application Event)                     |
| **Propósito**       | Disparar la siembra de roles al iniciar la aplicación |
| **Comando** | `SeedRolesCommand` → `RoleCommandService.handle`      |

## SignUpCommandHandler
Tabla de SignUpCommandHandler en el Application Layer de IAM
| Propiedad        | Valor                                                |
| ---------------- | ---------------------------------------------------- |
| **Nombre**       | SignUpCommandHandler                                 |
| **Categoría**    | Command Handler                                      |
| **Propósito**    | Registrar un usuario                                 |
| **Comando**      | `SignUpCommand`                                      |
| **Dependencias** | `UserRepository`, `HashingService`, `RoleRepository` |

## SignInCommandHandler
Tabla de SignInCommandHandler en el Application Layer de IAM
| Propiedad        | Valor                                                     |
| ---------------- | --------------------------------------------------------- |
| **Nombre**       | SignInCommandHandler                                      |
| **Categoría**    | Command Handler                                           |
| **Propósito**    | Autenticar usuario y emitir token                         |
| **Comando**      | `SignInCommand`                                           |
| **Dependencias** | `UserRepository`, `HashingService`, `TokenService`        |
| **Retorno**      | `Optional<ImmutablePair<User, String>>` (usuario + token) |

#### 4.2.1.4. Infrastructure Layer

La capa de infraestructura del Bounded Context de IAM actúa como el puente entre la lógica de negocio y los mecanismos técnicos de persistencia, comunicación y ejecución. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, proveedores de autenticación, mecanismos de almacenamiento de sesiones y otros servicios externos o compartidos.

Esta capa concreta las abstracciones definidas en el dominio mediante implementaciones de repositorios. Su diseño busca mantener el desacoplamiento respecto a la lógica central, permitiendo la evolución tecnológica sin comprometer la integridad del dominio. Además, garantiza la eficiencia, seguridad y confiabilidad en la gestión de identidades, roles y sesiones, alineándose con los objetivos funcionales y no funcionales del sistema.

## RoleRepository
Tabla de RoleRepository en el Infrastructure Layer de IAM
| Propiedad          | Valor                                       |
| ------------------ | ------------------------------------------- |
| **Nombre**         | RoleRepository                              |
| **Categoría**      | Repositorio                                 |
| **Propósito**      | Persistir y consultar entidades de `Role`   |
| **Interfaz**       | `RoleRepository`                            |
| **Implementación** | `RoleRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `roles` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)       |

Métodos de RoleRepository / RoleRepositoryImpl

| Método         | Firma                                   | Descripción                               |
| -------------- | --------------------------------------- | ----------------------------------------- |
| `findByName`   | `Optional<Role> findByName(Roles name)` | Busca un rol por nombre (enum).           |
| `findAll`      | `List<Role> findAll()`                  | Retorna todos los roles.                  |
| `saveRole`     | `void saveRole(Role role)`              | Persiste/actualiza un `Role`.             |
| `existsByName` | `boolean existsByName(Roles name)`      | Verifica existencia de un rol por nombre. |


## UserRepository
Tabla de UserRepository en el Infrastructure Layer de IAM
| Propiedad          | Valor                                       |
| ------------------ | ------------------------------------------- |
| **Nombre**         | UserRepository                              |
| **Categoría**      | Repositorio                                 |
| **Propósito**      | Persistir y consultar entidades de `User`   |
| **Interfaz**       | `UserRepository`                            |
| **Implementación** | `UserRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `users` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)       |

Métodos de UserRepository / UserRepositoryImpl
| Método             | Firma                                            | Descripción                         |
| ------------------ | ------------------------------------------------ | ----------------------------------- |
| `findByUsername`   | `Optional<User> findByUsername(String username)` | Busca usuario por `username`.       |
| `findById`         | `Optional<User> findById(String id)`             | Busca usuario por `id`.             |
| `findAll`          | `List<User> findAll()`                           | Lista todos los usuarios.           |
| `saveUser`         | `void saveUser(User user)`                       | Persiste/actualiza un `User`.       |
| `existsByUsername` | `boolean existsByUsername(String username)`      | Verifica existencia por `username`. |

#### 4.2.1.5. IAM Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de IAM. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales del contexto de gestión de identidad y acceso.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y seguridad del sistema.

#### 4.2.1.6. IAM Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de IAM, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.1.6.1. IAM Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica de dominio, así como sus relaciones fundamentales. El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y su rol dentro del modelo.

Asimismo, se incluyen las relaciones entre elementos del dominio, calificadas con nombres descriptivos, direccionalidad cuando corresponde, y multiplicidad para reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada del diseño táctico favorece la comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación efectiva dentro de la arquitectura de software.

![IAM CLASS DIAGRAM](../../assets/img/chapter-V/iam-class-diagram.png)

##### 4.2.1.6.2. IAM Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de IAM. Esta representación permite visualizar de forma estructurada y precisa las clases, interfaces y enumeraciones que conforman la lógica de dominio, junto con sus atributos, métodos y responsabilidades específicas dentro del modelo.

El diagrama incluye detalles esenciales como el tipo de dato y la visibilidad de cada miembro, así como las relaciones entre los distintos elementos del dominio. Estas relaciones están calificadas con nombres descriptivos, indican la dirección cuando aplica, e incorporan multiplicidades para representar con fidelidad la cardinalidad de cada asociación.

Esta visualización detallada contribuye significativamente a la comprensión compartida del modelo conceptual, funcionando como un nexo clave entre el análisis de dominio y su posterior implementación en la arquitectura del sistema.



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


## **ProfileController**

###### Tabla PRF-1

*Tabla de **ProfileController** en el Interface Layer (Profile)*

| Propiedad         | Valor                                                        |
| ----------------- | ------------------------------------------------------------ |
| **Nombre**        | ProfileController                                            |
| **Categoría**     | Controller                                                   |
| **Propósito**     | Exponer endpoints de perfil y preferencias (no credenciales) |
| **Ruta base**     | `/api/v1/profiles`                                           |
| **Tag (OpenAPI)** | `Profiles`                                                   |

###### Tabla PRF-2

*Métodos de **ProfileController***

| Nombre            | Ruta                     | Acción                                           | Handle                                                      |
| ----------------- | ------------------------ | ------------------------------------------------ | ----------------------------------------------------------- |
| getByUserId       | `/{userId}`              | Obtener perfil por `userId`                      | `GetProfileByUserIdQuery` → `profileQueryService.handle`    |
| updateDisplayName | `/{userId}/display-name` | Actualizar nombre mostrado                       | `UpdateDisplayNameCommand` → `profileCommandService.handle` |
| updateFullName    | `/{userId}/full-name`    | Actualizar nombre completo (VO)                  | `UpdateFullNameCommand` → `profileCommandService.handle`    |
| updateAvatar      | `/{userId}/avatar`       | Actualizar avatar                                | `UpdateAvatarCommand` → `profileCommandService.handle`      |
| updateContact     | `/{userId}/contact`      | Actualizar teléfono u otros datos de contacto    | `UpdateContactInfoCommand` → `profileCommandService.handle` |
| updatePreferences | `/{userId}/preferences`  | Actualizar preferencias (notifs/locale/timezone) | `UpdatePreferencesCommand` → `profileCommandService.handle` |



---

#### 4.2.2.3. Profile and Preferences Bounded Context Application Layer

La capa de aplicación del Bounded Context de Profiles and Preferences coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se implementan los Command Handlers, Query Handlers y Event Handlers responsables de operaciones como la edición de información personal, actualización de preferencias del usuario y notificación de cambios relevantes. Su rol es garantizar que dichas acciones se ejecuten de forma consistente y transaccional, delegando la lógica central al dominio y apoyándose en la infraestructura cuando sea necesario, manteniendo así la cohesión funcional del sistema.

## UserCreatedEventHandler
Tabla de UserCreatedEventHandler en el Application Layer de Profile

| Propiedad        | Valor                                            |
| ---------------- | ------------------------------------------------ |
| **Nombre**       | UserCreatedEventHandler                          |
| **Categoría**    | Event Handler                                    |
| **Propósito**    | Crear `Profile` cuando IAM publica `UserCreated` |
| **Evento**       | `UserCreated`                  |
| **Dependencias** | `ProfileRepository` |

## GetProfileByUserIdQueryHandler
Tabla de GetProfileByUserIdQueryHandler en el Application Layer de Profile

| Propiedad        | Valor                                        |
| ---------------- | -------------------------------------------- |
| **Nombre**       | GetProfileByUserIdQueryHandler               |
| **Categoría**    | Query Handler                                |
| **Propósito**    | Obtener `Profile` por `userId`               |
| **Query**        | `GetProfileByUserIdQuery`                    |
| **Dependencias** | `ProfileQueryRepository`/`ProfileRepository` |


## UpdateDisplayNameCommandHandler
Tabla de UpdateDisplayNameCommandHandler en el Application Layer de Profile
| Propiedad        | Valor                               |
| ---------------- | ----------------------------------- |
| **Nombre**       | UpdateDisplayNameCommandHandler     |
| **Categoría**    | Command Handler                     |
| **Propósito**    | Actualizar `displayName` del perfil |
| **Comando**      | `UpdateDisplayNameCommand`          |
| **Dependencias** | `ProfileRepository`                 |

## UpdateFullNameCommandHandler
Tabla de UpdateFullNameCommandHandler en el Application Layer de Profile
| Propiedad        | Valor                        |
| ---------------- | ---------------------------- |
| **Nombre**       | UpdateFullNameCommandHandler |
| **Categoría**    | Command Handler              |
| **Propósito**    | Actualizar `FullName` (VO)   |
| **Comando**      | `UpdateFullNameCommand`      |
| **Dependencias** | `ProfileRepository`          |

## UpdateAvatarCommandHandler
Tabla de UpdateAvatarCommandHandler en el Application Layer de Profile

| Propiedad        | Valor                      |
| ---------------- | -------------------------- |
| **Nombre**       | UpdateAvatarCommandHandler |
| **Categoría**    | Command Handler            |
| **Propósito**    | Actualizar `avatarUrl`     |
| **Comando**      | `UpdateAvatarCommand`      |
| **Dependencias** | `ProfileRepository`        |

## UpdateContactInfoCommandHandler
Tabla de UpdateContactInfoCommandHandler en el Application Layer de Profile

| Propiedad        | Valor                                  |
| ---------------- | -------------------------------------- |
| **Nombre**       | UpdateContactInfoCommandHandler        |
| **Categoría**    | Command Handler                        |
| **Propósito**    | Actualizar datos de contacto (`phone`) |
| **Comando**      | `UpdateContactInfoCommand`             |
| **Dependencias** | `ProfileRepository`                    |

## UpdatePreferencesCommandHandler
Tabla de UpdatePreferencesCommandHandler en el Application Layer de Profile
| Propiedad        | Valor                                                   |
| ---------------- | ------------------------------------------------------- |
| **Nombre**       | UpdatePreferencesCommandHandler                         |
| **Categoría**    | Command Handler                                         |
| **Propósito**    | Actualizar `NotificationSettings`, `locale`, `timezone` |
| **Comando**      | `UpdatePreferencesCommand`                              |
| **Dependencias** | `ProfileRepository`                                     |


#### 4.2.2.4. Profile and Preferences Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Profile and Preferences sirve como enlace entre la lógica de negocio y los mecanismos técnicos que permiten la persistencia y comunicación con recursos externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, servicios de almacenamiento y otros módulos relevantes que permiten gestionar la información de perfil y preferencias de los usuarios.

Esta capa materializa las abstracciones definidas en el dominio mediante la implementación de repositorios y adaptadores técnicos. Su diseño favorece el desacoplamiento de la lógica central, facilitando la evolución tecnológica sin afectar la integridad del modelo. Asimismo, asegura una gestión consistente, eficiente y segura de los datos personales, configuraciones y preferencias del usuario, en línea con los objetivos funcionales y no funcionales del sistema.

## ProfileRepository
Tabla de ProfileRepository en el Infrastructure Layer de Profile

| Propiedad          | Valor                                          |
| ------------------ | ---------------------------------------------- |
| **Nombre**         | ProfileRepository                              |
| **Categoría**      | Repositorio                                    |
| **Propósito**      | Persistir y consultar agregados de `Profile`   |
| **Interfaz**       | `ProfileRepository`                            |
| **Implementación** | `ProfileRepositoryImpl` (Spring `@Repository`) |
| **Colección**      | `profiles` (MongoDB)                           |
| **Tecnología**     | `MongoTemplate` (Spring Data MongoDB)          |

Métodos de ProfileRepository (propuestos)

| Método           | Firma                                           | Descripción                                                         |
| ---------------- | ----------------------------------------------- | ------------------------------------------------------------------- |
| `findByUserId`   | `Optional<Profile> findByUserId(String userId)` | Busca el perfil asociado a un `userId` (clave de relación con IAM). |
| `findById`       | `Optional<Profile> findById(String id)`         | Busca perfil por su `id` propio.                                    |
| `findAll`        | `List<Profile> findAll()`                       | Lista todos los perfiles.                                           |
| `saveProfile`    | `void saveProfile(Profile profile)`             | Persiste/actualiza un `Profile`.                                    |
| `existsByUserId` | `boolean existsByUserId(String userId)`         | Verifica existencia por `userId`.                                   |

#### 4.2.2.5. Profile and Preferences Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Profiles and Preferences. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías utilizadas y las interacciones entre ellos. Esta representación es fundamental para comprender en detalle cómo se organiza internamente cada parte del sistema, qué funcionalidades asume cada componente, y de qué manera colaboran para gestionar la información personal, preferencias y configuración personalizada del usuario dentro de Mushroom.

Tal como establece el C4 Model, el nivel de componentes representa el cuarto nivel de abstracción en la visualización de arquitecturas de software, y resulta especialmente útil para desarrolladores y arquitectos al ofrecer una visión clara de las decisiones de diseño adoptadas en cada contenedor (Brown, 2023). Este nivel facilita la trazabilidad entre los elementos de alto nivel y su implementación específica, fortaleciendo la mantenibilidad, extensibilidad y coherencia del sistema.


#### 4.2.2.6. Profile and Preferences Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Profiles and Preferences, presentando diagramas que permiten visualizar con mayor precisión la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos del sistema que gestionan la configuración del perfil de usuario, sus intereses, preferencias y datos personales.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico y la implementación concreta. Esta aproximación garantiza que las decisiones tomadas a nivel táctico se materialicen en estructuras coherentes, sólidas y alineadas con los objetivos funcionales del contexto, brindando claridad y sostenibilidad al proceso de desarrollo y evolución del sistema.

##### 4.2.2.6.1. Profile and Preferences Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que componen la lógica de dominio relacionada con la gestión del perfil del usuario, sus intereses, configuraciones personalizadas y preferencias de interacción dentro del ecosistema de Macetech.

El nivel de detalle incluye la definición de atributos y métodos para cada clase, especificando sus tipos de datos, visibilidad y rol dentro del modelo, así como las relaciones fundamentales entre los distintos elementos del dominio. Estas relaciones se representan con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, lo que permite reflejar con precisión el grado de asociación entre las entidades. Esta vista detallada facilita una comprensión común del modelo conceptual, sirviendo como puente entre el diseño del dominio y su posterior implementación técnica.



![PROFILE CLASS DIAGRAM](../../assets/img/chapter-V//profile-class-diagram.png)



##### 4.2.2.6.2. Profile and Preferences Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Profiles and Preferences. Esta representación estructurada permite visualizar con claridad las entidades persistentes asociadas a la gestión de perfiles, intereses y preferencias del usuario, junto con sus atributos clave, tipos de datos, claves primarias y foráneas, y restricciones asociadas.

El diagrama refleja las relaciones entre las distintas tablas o entidades, indicando la dirección de las asociaciones, su naturaleza y la cardinalidad, lo que facilita el entendimiento de la estructura lógica que respalda el almacenamiento y la recuperación eficiente de datos dentro de este contexto.

Esta visualización resulta esencial para asegurar la coherencia entre el modelo conceptual y su implementación en la capa de persistencia, contribuyendo a una arquitectura sólida, escalable y alineada con los requerimientos funcionales y no funcionales del sistema.

###### Figura 89
*Diagrama de base de datos del Bounded Context de Profile and Preferences*

<image src="../assets/img/capitulo-4/bounded-context-profile-and-personal-data/database-diagram-profile-and-personal-data.png"></image>

---

### 4.2.3. Bounded Context: Asset and Resource Management

En el contexto táctico, el Bounded Context Asset and Resource Management agrupa toda la funcionalidad vinculada a la administración de activos físicos y recursos operativos dentro del ecosistema Macetech. Este módulo se encarga del registro, monitoreo y mantenimiento de los dispositivos IoT desplegados (como sensores de humedad, temperatura, pH, entre otros), permitiendo llevar un control detallado de su estado, ubicación, historial de intervenciones y condiciones operativas.

Asset and Resource Management centraliza el ciclo de vida de cada dispositivo, desde su activación inicial hasta su posible retiro o sustitución, asegurando trazabilidad completa y continuidad en la gestión técnica. Asimismo, incorpora mecanismos para la asignación de recursos a usuarios o entornos específicos, facilitando una administración eficiente y contextualizada. Este bounded context expone interfaces estandarizadas para permitir su integración con otros contextos funcionales, y actúa como fuente confiable de verdad sobre los activos tecnológicos desplegados en la plataforma.

#### 4.2.3.1. Asset and Resource Management Bounded Context Domain Layer

En la capa de dominio de Asset and Resource Management se modelan las entidades y objetos de valor que encapsulan las reglas de negocio de los puertos, waypoints y activos. Aquí residen los aggregates, value objects, domain services y eventos que garantizan la coherencia e invariantes del dominio.

###### Tabla 
*Descripción de Port en el Domain Layer de Asset and Resource Management*

|Propiedad|Valor|
|-|-|
|Nombre	|Port|
|Categoría|	Aggregate Root (document MongoDB, colección ports)|
|Propósito|	Representar la ficha del puerto con ubicación, capacidades y estado operativo.|

###### Tabla 2
*Atributos de Port en el Domain Layer de Asset and Resource Management*

|Nombre	|Tipo de dato	|Visibilidad|	Descripción|
|-|-|-|-|
|id|	String (ObjectId)|	private	|Identificador único del documento (_id).|
|name	|String|	private|	Nombre descriptivo del puerto.|
|coordinates| Coordinates {type: "Point", coordinates: [lon, lat]}	|private|	Coordenadas geoespaciales para ubicar cada puerto |
|continent | String | private | Continente en el que se encuentra el puerto. |
|status	|String (enum)	|private	|Estado operativo: OPEN, RESTRICTED, CLOSED.|
|createdAt	|Date	|private|	Fecha de creación.|
|updatedAt	|Date|	private	|Fecha de última modificación.|

###### Tabla 3 
*Métodos de Port en el Domain Layer de Asset and Resource Management*

|Nombre	|Tipo de retorno	|Visibilidad	|Descripción|
|-|-|-|-|
|Port	|Constructor |	public|Constructor que valida ubicación.|
|changeStatus(newStatus, reason, actor)|	void|	public|	Valida transición de estados y registra evento PortStatusChanged.|

---

**Location:**

###### Tabla 4
*Value Object de Location en el Domain Layer de Asset and Resource Management*

|Propiedad|Valor|
|-|-|
|Nombre	|Coordinates |
|Categoría|	Value Object|
|Propósito	|Representar y validar coordenadas geoespaciales con precisión de los puertos.|
|Atributos|	latitude, longitude, validación de rango |

###### Tabla 7

*Atributos de Location en el Domain Layer de Asset and Resource Management*

|Nombre	|Tipo de dato	|Visibilidad|	Descripción|
|-|-|-|-|
|latitude	|Double	|private	|Latitud (-90..90) |
|longitude	|Double	|private	|Longitud (-180..180) |

---

**Continent:**

###### Tabla 4
*Value Object de Continent en el Domain Layer de Asset and Resource Management*

|Propiedad|Valor|
|-|-|
|Nombre	|Continent |
|Categoría|	Value Object|
|Propósito	|Presentar los continentes en los que pueden encontrarse los puertos. Útil especialmente para filtros.|
|Atributos|	name, portsNumber |

###### Tabla 7

*Atributos de Location en el Domain Layer de Asset and Resource Management*

|Nombre	|Tipo de dato	|Visibilidad|	Descripción|
|-|-|-|-|
|name | String | private | El nombre del continente indicado |
| portsNumber | int | private | Cantidad de puertos integrados en un continente específico. |

---

**Domain Services:**

###### Tabla 10

*Descripción de PortSelectionService en el Domain Layer de Asset and Resource Management*

|Propiedad | Valor|
|-|-|
| Nombre | PortSelectionService |
| Categoría | Domain Service |
| Propósito | Lógica para seleccionar puertos candidatos en el mapa de la aplicación. Devuelve nombre, ubicación, continente y restricciones. |

###### Tabla 11

*Descripción de PortSyncService en el Domain Layer de Asset and Resource Management*

|Propiedad|Valor|
|-|-|
| Nombre | PortSyncService |
| Categoría | Domain Service |
| Propósito | Aplicar reglas de reconciliación cuando se reciben datos de fuentes externas (normalización).|

---

**Domain Events:**

###### Tabla 11

*Tabla de eventos de dominio en el Domain Layer de Asset and Resource Management*

|Evento	|Descripción|
|-|-|
|PortRegistered	|Se registró nuevo puerto.|
|PortUpdated	|Datos del puerto fueron actualizados.|
|PortStatusChanged|	Cambió el estado operativo del puerto.|

---

#### 4.2.3.2. Asset and Resource Management Bounded Context Interface Layer

En la capa de interfaz del Bounded Context de Asset and Resource Management se exponen los endpoints necesarios para gestionar la información relacionada a cada puerto integrado en la página de Mushroom. Su diseño promueve una separación clara de responsabilidades, orquestando de forma eficiente comandos y consultas, al tiempo que garantiza trazabilidad, disponibilidad y consistencia de los recursos gestionados.

**PortsController:**

###### Tabla 12

*Descripción de PortsController en el Interface Layer de Asset and Resource Management*

|Propiedad	|Valor|
|-|-|
|Nombre	|PortsController|
|Categoría	|Controller (REST)|
|Propósito	|Proveer endpoints para CRUD y consultas geoespaciales sobre puertos. |

###### Tabla 13

*Métodos de PortsController en el Interface Layer de Asset and Resource Management*

|Nombre|Ruta	|Acción	|Handle|
|-|-|-|-|
|getPorts|	GET / |	Listar puertos (filtros: status, country, bbox, near, page)`|	GetPortsQuery -> GetPortsQueryHandler|
|getPortById	|GET /{portId}|	Obtener ficha detallada del puerto|GetPortByIdQuery -> GetPortByIdQueryHandler|
|createPort	|POST /	|Registrar nuevo puerto (solo ROLE_ADMIN)	|RegisterPortCommand -> RegisterPortCommandHandler|
|updatePort	|PUT /{portId}	|Actualizar datos del puerto	|UpdatePortCommand -> UpdatePortCommandHandler|
|changeStatus	|PATCH /{portId}/status	|Cambiar estado operativo del puerto|	ChangePortStatusCommand -> ChangePortStatusCommandHandler|
|getPortsByContinent|	GET /continent/{continentCode}	|Filtrar por continente |	GetPortsByContinentQuery -> GetPortsByContinentQueryHandler|

###### Tabla 14

*Descripción de Eventos asincronos relevantes publicados por Assets and Resource Management*

|Eventos|	Propósito|
|-|-|
|ports.events	|Publica eventos "PortRegistered", "PortUpdated", "PortStatusChanged", consumido para Ruteo y Notification.|

---

#### 4.2.3.3. Asset and Resource Management Bounded Context Application Layer

La capa de aplicación del Bounded Context de Asset and Resource Management coordina el flujo de trabajo entre la interfaz y el dominio, encapsulando la lógica de orquestación sin incorporar reglas de negocio. En esta capa se ubican los Command Handlers, Query Handlers y Event Handlers, encargados de gestionar operaciones como el registro, actualización y seguimiento del estado de los puertos de Mushroom, así como el procesamiento de eventos vinculados a sus estados y ubicación exacta. Esta capa garantiza que las interacciones se realicen de manera segura y transaccional, manteniendo la coherencia del sistema y delegando la lógica específica al dominio o a componentes de infraestructura según sea necesario.

**Command Handlers:**

###### Tabla 15

*Listado de Command Handlers del Application Layer de Assets and Resource Management*

|Nombre	|Categoría	|Propósito	|Comando|
|-|-|-|-|
|RegisterPortCommandHandler	|Command Handler	|Registrar nuevo puerto, validar unicidad y persistir	|RegisterPortCommand|
|UpdatePortCommandHandler	|Command Handler	|Actualizar datos del puerto|	UpdatePortCommand|
|ChangePortStatusCommandHandler|	Command Handler|	Validar transición de estado, persistir y publicar evento	|ChangePortStatusCommand|

---

**Query Handlers:**

###### Tabla 16

**Listado de Query Handlers del Application Layer de Assets and Resource Management*

|Nombre|	Categoría	|Propósito	|Query|
|-|-|-|-|
|GetPortsQueryHandler	|Query Handler|	Retornar lista denormalizada ports_read	|GetPortsQuery|
|GetPortByIdQueryHandler	|Query Handler	|Retornar PortView detallado	|GetPortByIdQuery|

---

**Event Handlers:**

###### Tabla 17

*Listado de Event Handlers del Application Layer de Assets and Resource Management*

|Nombre	|Categoría	|Propósito	|Evento consumido|
|-|-|-|-|
|PortRegisteredEventHandler	|Event Handler|	Construir o actualizar ports_read y limpiar caches|	PortRegistered|
|PortUpdatedEventHandler	|Event Handler	|Actualizar ports_read con cambios	|PortUpdated|
|PortStatusChangedEventHandler	|Event Handler|	Notificar en la página principal con las funciones de ruteo |	PortStatusChanged|

---

#### 4.2.2.4. Asset and Resource Management Bounded Context Infrastructure Layer

La capa de infraestructura del Bounded Context de Asset and Resource Management actúa como el vínculo entre la lógica de negocio y las tecnologías subyacentes que permiten la persistencia, comunicación e integración con sistemas externos. En este nivel se implementan las dependencias necesarias para interactuar con bases de datos, coordenadas y representación de mapas de forma adecuada.

Esta capa concreta las abstracciones del dominio a través de implementaciones de repositorios y componentes técnicos especializados. Su diseño busca preservar el desacoplamiento respecto al núcleo del sistema, facilitando la evolución tecnológica sin afectar la consistencia de las reglas de negocio. Asimismo, garantiza eficiencia y confiabilidad en la gestión de los puertos y sus respectivos estados operativos, en línea con los requerimientos estratégicos de la solución.

**Repositorios:**

###### Tabla 18

*Listado de repositorios en el Infrastructure Layer de Asset and Resource Management*

|Nombre|	Categoría	|Propósito	|Interfaz|
|-|-|-|-|
|PortRepository	|Repositorio	|Persistir y consultar documentos ports|	IPortRepository|

###### Tabla 19

*Métodos de IPortRepository en el Infrastructure Layer de Asset and Resource Management*

|Nombre	|Tipo de retorno|	Descripción|
|-|-|-|
|findById(portId)	|Port|	Recupera port por id.|
|findByCode(code)	|Port|	Recupera por código único.|
|save(port, session?)	|void|	Persiste aggregate (usar session para transacciones).|
|updateStatus(portId, newStatus, actor, session?)|	void|	Actualiza estado con control optimista.|

**Implementaciones MongoDB:**

###### Tabla 20

**Tabla de colecciones y notas de implementación para MongoDB**

|Componente	|Colección|	Notas|
|-|-|-|
|Ports	|ports|	Documento Port. Índice único code. Índice 2dsphere en location. Campos createdAt y updatedAt. version para control optimista.|
|Ports read|	ports_read	|Denormalización con resumen y geometría simplificada para UI; actualizada por event handlers.|

#### 4.2.3.5. Asset and Resource Management Bounded Context Software Architecture Component Level Diagrams

En esta sección se presentan los diagramas de componentes correspondientes a los principales containers definidos dentro del Bounded Context de Asset and Resource Management. Estos diagramas permiten descomponer cada contenedor en sus componentes internos, identificando sus responsabilidades específicas, las tecnologías involucradas y las interacciones entre ellos. Esta representación es clave para comprender con mayor precisión cómo se estructura internamente cada parte del sistema, qué tareas cumple cada componente, y cómo colaboran para satisfacer los requerimientos funcionales y no funcionales relacionados con la gestión de de puertos y sus ubicaciones en mapa dentro de Mushroom.

Tal como lo establece el C4 Model, el nivel de componentes es el cuarto nivel de detalle en la visualización de arquitecturas de software, y resulta útil tanto para desarrolladores como para arquitectos, al proporcionar una perspectiva clara de las decisiones de diseño que se toman dentro de cada contenedor (Brown, 2023). Este nivel permite una mayor trazabilidad entre la arquitectura lógica y la implementación concreta, reforzando así la mantenibilidad, escalabilidad y eficiencia del sistema.

###### Figura 90
*Participación del Bounded Context de Asset and Resource Management con la aplicación móvil mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-MobileComponent.png"></image>

###### Figura 91
*Participación del Bounded Context de Asset and Resource Management con la aplicación web mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-WebComponent.png"></image>

###### Figura 92
*Participación del Bounded Context de Asset and Resource Management con la Cloud API mediante el diagrama de componentes*

<image src="..\assets\img\capitulo-4\c4-model\structurizr-102464-Pot-APIComponent.png"></image>

#### 4.2.3.6. Asset and Resource Management Bounded Context Software Architecture Code Level Diagrams

En esta sección se profundiza en los aspectos internos de implementación del Bounded Context de Asset and Resource Management, presentando diagramas que permiten visualizar con mayor detalle la estructura y composición de sus componentes clave. A través de representaciones estructuradas, como los diagramas de clases de la capa de dominio y el diagrama de base de datos, se facilita la comprensión técnica de cómo se organizan e interrelacionan los elementos dentro del sistema.

Estos recursos visuales permiten identificar entidades, objetos de valor, relaciones, atributos, operaciones, estructuras persistentes y sus vínculos, sirviendo como puente entre el diseño arquitectónico de alto nivel y la implementación concreta. Esta aproximación asegura que las decisiones tomadas a nivel táctico se traduzcan en estructuras sólidas, coherentes y alineadas con los objetivos del dominio, aportando claridad al proceso de desarrollo y mantenimiento del sistema.

##### 4.2.3.6.1. Asset and Resource Management Bounded Context Domain Layer Class Diagrams

En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context de Asset and Resource Management. Esta representación estructurada permite visualizar con claridad las clases, interfaces y enumeraciones que conforman la lógica del dominio, centrada en la gestión de ubicaciones de puertos y estados en la plataforma de Mushroom.

El nivel de detalle abarca la definición de atributos y métodos para cada clase, especificando su tipo de dato, visibilidad y propósito en el modelo. Asimismo, se incluyen las relaciones entre elementos del dominio, cualificadas mediante nombres representativos, dirección cuando aplica y multiplicidad adecuada para reflejar con precisión las asociaciones entre entidades.

Esta vista detallada del diseño táctico facilita una comprensión compartida del modelo conceptual, sirviendo como puente entre el análisis del dominio y su implementación técnica, y asegurando la coherencia estructural en la gestión y trazabilidad de recursos en la plataforma.

###### Figura 93
*Diagrama de clases de la capa de dominio del Bounded Context de Asset and Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/class-diagram-pot-management.png"></image>

##### 4.2.3.6.2. Asset and Resource Management Bounded Context Database Design Diagram

En esta subsección se presenta el diagrama de base de datos correspondiente al bounded context de Asset and Resource Management. Esta representación permite visualizar de forma estructurada y precisa las entidades persistentes que forman parte de la gestión de puertos y estados en Mushroom, así como sus atributos, claves primarias, claves foráneas y relaciones asociadas.

El diagrama incluye detalles fundamentales como los tipos de datos, las restricciones y la cardinalidad de las asociaciones entre tablas, lo que permite entender cómo se organiza la información a nivel de almacenamiento. Asimismo, se especifican las relaciones entre los distintos elementos, con nombres descriptivos, direccionalidad, cuando aplica, y multiplicidad, reflejando de forma fidedigna la estructura lógica del modelo persistente.

Esta visualización detallada contribuye significativamente a la comprensión compartida del diseño de datos, sirviendo como puente entre el modelo de dominio y la implementación técnica de la base de datos, y asegurando que la arquitectura sea coherente, mantenible y alineada con los requerimientos del sistema.

###### Figura 94
*Diagrama de base de datos del Bounded Context de Asset and Resource Management*

<image src="../assets/img/capitulo-4/bounded-context-pot-management/database-diagram-pot-management.png"></image>

### 4.2.4. Bounded Context: A*/AI Process
En el contexto táctico, el Bounded Context A/AI process* concentra la funcionalidad asociada al cálculo de rutas óptimas y a la predicción climática que complementa la experiencia de navegación. Este módulo encapsula la lógica del algoritmo A* para determinar la ruta mínima entre puntos definidos, integrando además un componente de inteligencia artificial orientado a anticipar condiciones meteorológicas que puedan afectar la planificación del trayecto.

El proceso se apoya en datos obtenidos de APIs externas, que pueden proveer información climática en tiempo real o registros históricos especializados, según se defina en etapas posteriores del proyecto. A partir de esta información, el sistema ajusta dinámicamente las rutas propuestas, otorgando a los navegantes un soporte predictivo que incrementa tanto la eficiencia como la seguridad del recorrido.

De esta forma, el bounded context actúa como el núcleo de cálculo y predicción, exponiendo interfaces bien delimitadas para que otros módulos del sistema consuman sus resultados sin acoplarse a la complejidad interna de los algoritmos. Esto asegura independencia, escalabilidad y una fuente única de verdad en lo referente a optimización de trayectorias y análisis del entorno climático.

#### 4.2.4.1. A*/AI Process Bounded Context Domain Layer

Route:
*Tabla de Route en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | Route |
| Categoría | Aggregate Root |
| Propósito | Representar una ruta calculada por el algoritmo A*, incluyendo nodos, distancia y costo total. |

*Tabla de Route en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Id | UUID | private | Identificador único de la ruta |
| Nodes | List<Node> | private | Lista de nodos que conforman el trayecto |
| Distance | double | private | Distancia total de la ruta |
| Cost | double | private | Costo acumulado según heurística A* |
| CreatedAt | DateTime | private | Fecha en que fue calculada la ruta |

*Tabla de métodos de Route en el Domain Layer de A*/AI process*
| Nombre | Tipo de retorno | Visibiilidad | Descripción |
|--------|-----------------|--------------|-------------|
| CalculateCost | void | public | Recalcula el costo total de la ruta |
| AddNode | void | public | Agrega un nodo al trayecto de la ruta |
| Optimize | void | public | Permite optimizar el orden de los nodos |

Node:
*Tabla de Node en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | Node |
| Categoría | Entity |
| Propósito | Representar un punto geográfico o de grafo en el cálculo de rutas. |

*Tabla de atributos de Node en el Domain Layer de A*/AI process*
| Nombre    | Tipo de dato | Visibilidad | Descripción |
|-----------|--------------|-------------|-------------|
| Id        | UUID         | private     | Identificador único del nodo |
| Latitude  | double       | private     | Coordenada de latitud del nodo |
| Longitude | double       | private     | Coordenada de longitud del nodo |
| Cost      | double       | private     | Costo heurístico acumulado en el algoritmo |

WeatherPrediction:
*Tabla de WeatherPrediction en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | WeatherPrediction |
| Categoría | Entity |
| Propósito | Representar una predicción climática asociada a un trayecto en una fecha dada |

*Tabla de atributos de WeatherPrediction en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Id | UUID | private | Identificador único de la predicción |
| RouteId | UUID | private | Identificador de la ruta asociada |
| Date | DateTime | private | Fecha y hora de la predicción |
| Condition | string | private | Condición climática (ej. lluvia, soleado) |
| Confidence | double | private | Nivel de confianza en la predicción |

AStarAlgorithm:
*Tabla de AStarAlgorithm en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | AStarAlgorithm |
| Categoría | Domain Service |
| Propósito | Implementar la lógica de cálculo de rutas mínimas con A* |

*Tabla de métodos de AStarAlgorithm en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| FindShortest | Route | public | Ejecuta el algoritmo A* y devuelve la mejor ruta |
| Heuristic | Double | private | Calcula la heurística (distancia estimada) entre nodos |

WeatherService:
*Tabla de WeatherService en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | WeatherService |
| Categoría | Domain Service |
| Propósito | Centralizar la lógica de predicción de clima consumiendo IA y APIs externas |

*Tabla de métodos de WeatherService en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| PredictCondition | WeatherPrediction | public | Devuelve una predicción climática para una ruta |
| AdjustRoute | Route | public | Ajusta la ruta considerando las predicciones climáticas |

IRouteRepository:
*Tabla de IRouteRepository en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | IRouteRepository |
| Categoría | Repository |
| Propósito | Abstracción para persistencia y consulta de rutas |

*Tabla de métodos de IRouteRepository en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Save | Route | public | Guarda una ruta calculada |
| FindById | Route? | public | Recupera una ruta por su identificador |
| FindAll | List<Route> | public | Lista todas las rutas registradas |

IWeatherRepository:
*Tabla de IWeatherRepository en el Domain Layer de A*/AI process*
| Propiedad   | Valor   |
|-------------|---------|
| Nombre | IWeatherRepository |
| Categoría | Repository |
| Propósito | Abstracción para almacenar y recuperar predicciones climáticas |

*Tabla de métodos de IWeatherRepository en el Domain Layer de A*/AI process*
| Nombre | Tipo de dato | Visibilidad | Descripción |
|--------|--------------|-------------|-------------|
| Save | WeatherPrediction | public | Guarda una predicción de clima |
| FindById | WeatherPrediction? | public | Recupera una predicción por identificador |
| FindByRoute | List<WeatherPrediction> | public | Recupera predicciones asociadas a una ruta |


#### 4.2.4.2. A*/AI Process Bounded Context Interface Layer

La capa de Interface (Presentation) del bounded context A/AI process* contiene los controllers REST que exponen la funcionalidad del core (cálculo de rutas, obtención de datos de puertos, consulta de distancias, listados de rutas). Además expone los DTOs/Resources que representan las peticiones y respuestas de la API, y los assemblers que transforman recursos a comandos del Application Layer (y viceversa). Esta capa no contiene lógica de negocio; su única responsabilidad es traducir HTTP ↔ objetos del dominio/aplicación y manejar respuestas/errores.

RouteController
*Tabla de RouteController en el Interface Layer del A*/AI process*
| Propiedad     | Valor                                                                                     |
|---------------|-------------------------------------------------------------------------------------------|
| Nombre        | RouteController                                                                           |
| Categoría     | Controller                                                                                |
| Propósito     | Exponer endpoints relacionados con operaciones sobre rutas (cálculo, consulta, listados). |
| Base Path     | /api/routes (convención; el controller usa recursos RouteCalculationResource, etc.)       |

*Tabla de métodos (ejemplos relevantes encontrados en el código)*
|Nombre (Método)        | Ruta (ejemplo)        | Acción                                | Handle / Resource utilizado                  |
|--------------------   |-----------------------|---------------------------------------|----------------------------------------------|
| calculateRoute (POST) | /api/routes/calculate | Recibe datos de inicio/destino y solicita cálculo de ruta óptima | RouteCalculationResource / RouteRequestResource |
| getRouteById (GET)    | /api/routes/{routeId} | Recupera una ruta por ID                    | RouteDocument / RouteResource |
| getAllRoutes (GET)    | /api/routes/all-routes| Lista todas las rutas guardadas (historial) | List<RouteDocument> |

PortController
*Tabla de PortController en el Interface Layer del A*/AI process*
| Propiedad     | Valor                                                                                     |
|---------------|-------------------------------------------------------------------------------------------|
| Nombre        | PortController                                                                           |
| Categoría     | Controller                                                                                |
| Propósito     | Exponer endpoints para gestión/consulta de puertos y utilitarios relacionados (ej. distancia entre puertos). |
| Base Path     | /api/ports (convención; el controller usa PortResource, CreatePortResource)      |

*Tabla de métodos (ejemplos relevantes encontrados en el código)*
|Nombre (Método)        | Ruta (ejemplo)        | Acción                                | 
|--------------------   |-----------------------|---------------------------------------|
| createPort (POST) | /api/ports | Crea un nuevo puerto a partir del DTO CreatePortResource | 
| getPortById (GET)    | /api/ports/{portId} | Obtiene información del puerto                   | 
| getDistanceBetweenPorts (GET)    | /api/ports/distance-between-ports | Devuelve distancia/resultado entre dos puertos (usa RouteDistanceResource) | 

Resources / DTOs
*Tabla breve de los recursos encontrados y su propósito*
| Recurso | Propósito/Uso |
|---------|---------------|
| RouteCalculationResource | Representa respuesta con datos de la ruta calculada (nodos, coste). |
| RouteRequestResource | DTO de petición para calcular una ruta (puerto inicio/fin, parámetros). |
| RouteDistanceResource | DTO de respuesta para distancias / mensajes de error relacionados. |
| PortResource | DTO de salida con datos de un puerto. |
| PortResource | DTO de entrada para creación de puerto. |

Assemblers / Transformers
*Tabla de assemblers presentes y su propósito*
| Clase | Propósito |
|-------|-----------|
| CreatePortCommandFromResourceAssembler | Transforma CreatePortResource → CreatePortCommand del Application Layer |
| PortResourceFromEntityAssembler | Transforma Port entity → PortResource para respuesta al cliente |


#### 4.2.4.3. A*/AI Process Bounded Context Application Layer
La capa de Application del bounded context A/AI process* orquesta los flujos de negocio que coordinan el dominio (A*, modelos y repositorios) y la capa de presentación (controllers). En el repositorio actual esta capa está implementada principalmente mediante Application Services (clases *Service y *ServiceImpl) que exponen las capacidades (capabilities) del bounded context: cálculo de rutas, construcción del grafo, provisión de condiciones de navegación y gestión de puertos y rutas persistidas. En este monolito no hay Event Handlers ni Command Handlers explícitos como clases independientes; las responsabilidades de manejo de comandos se realizan desde los servicios de aplicación (simple y apropiado para un entregable académico/monolito).

RouteService
*Tabla de RouteService en el Application Layer*
| Propiedad     | Valor                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteService`                                                                                                      |
| **Categoría** | Application Service                                                                                                 |
| **Propósito** | Orquestar operaciones de negocio relacionadas con rutas: cálculo, persistencia y consultas (historial, existencia). |

*Métodos clave (extraídos del código)*
| Nombre                                                            | Tipo de retorno            | Descripción                                                                                                                                                                 |
| ----------------------------------------------------------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `calculateOptimalRoute(String startPortName, String endPortName)` | `RouteCalculationResource` | Orquesta el cálculo de la ruta óptima entre dos puertos (invoca servicios de dominio como `RouteCalculatorService` y `NavigationConditionsService`, arma la respuesta DTO). |
| `calculateTotalDistance(List<Port> route)`                        | `double`                   | Calcula distancia total para una lista de puertos (utilidad usada en reports/mediciones).                                                                                   |
| `findAllRoutes()`                                                 | `List<RouteDocument>`      | Recupera todas las rutas guardadas (historial).                                                                                                                             |
| `saveAllRoutes(List<RouteDocument> routes)`                       | `void`                     | Persiste una lista de rutas.                                                                                                                                                |
| `existsByHomePortAndDestinationPort(String h, String d)`          | `boolean`                  | Valida existencia de ruta entre puertos (para lógica de “popular routes”).                                                                                                  |
| `deleteAllRoutes()`                                               | `void`                     | Operación administrativa para limpiar rutas.                                                                                                                                |

PortService
*Tabla de PortService en el Application Layer*
| Propiedad     | Valor                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `PortService`                                                                                                           |
| **Categoría** | Application Service                                                                                                     |
| **Propósito** | Operaciones CRUD y consultas sobre puertos; integrador de comandos de creación y de lectura para la capa de interfaces. |

*Métodos clave*
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

RouteCalculatorServiceImpl
*Tabla de RouteCalculatorServiceImpl en el Application Layer*
| Propiedad     | Valor                                                                                                                 |
| ------------- | --------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteCalculatorServiceImpl`                                                                                          |
| **Categoría** | Application / Inbound Service (implementación de la capability de cálculo)                                            |
| **Propósito** | Implementa la orquestación concreta para calcular una ruta óptima: utiliza el grafo, las condiciones y el pathfinder. |

Métodos clave
| Nombre                                        | Tipo de retorno | Descripción                                                                             |
| --------------------------------------------- | --------------- | --------------------------------------------------------------------------------------- |
| `calculateOptimalRoute(Port start, Port end)` | `List<Port>`    | Devuelve la secuencia de puertos que conforman la ruta calculada entre `start` y `end`. |

RouteGraphBuilder
*Tabla de RouteGraphBuilder en el Application Layer*
| Propiedad     | Valor                                                                                                 |
| ------------- | ----------------------------------------------------------------------------------------------------- |
| **Nombre**    | `RouteGraphBuilder`                                                                                   |
| **Categoría** | Application Service / Utility                                                                         |
| **Propósito** | Construir dinámicamente la representación de grafo (`RouteGraph`) que será usada por el algoritmo A*. |

*Métodos clave*
| Nombre                                     | Tipo de retorno | Descripción                                                   |
| ------------------------------------------ | --------------- | ------------------------------------------------------------- |
| `buildDynamicRouteGraph()`                 | `RouteGraph`    | Construye y devuelve el grafo actual (nodos y aristas).       |
| `calculateTotalDistance(List<Port> route)` | `double`        | Calcula la distancia total de una ruta (servicio utilitario). |

NavigationConditionsService
*Tabla de NavigationConditionsService en el Application Layer*
| Propiedad     | Valor                                                                                                                                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**    | `NavigationConditionsService`                                                                                                                                                                                     |
| **Categoría** | Application Service (adapter/inbound)                                                                                                                                                                             |
| **Propósito** | Proveer ajustes y penalizaciones de coste en función de condiciones de navegación (corrientes, clima, peligros). Consume/o prepara datos que vienen de `NavigationConditionsProvider` (Domain) y/o APIs externas. |

*Métodos clave*
| Nombre                                                                           | Tipo de retorno | Descripción                                                          |
| -------------------------------------------------------------------------------- | --------------- | -------------------------------------------------------------------- |
| `getAdjustedCost(Route route, Port homePort, Port destinationPort, Clock clock)` | `double`        | Retorna costo ajustado para una ruta basada en condiciones actuales. |
| `isAlongFavorableCurrent(Port from, Port to)`                                    | `boolean`       | Indica si el tramo cuenta con corrientes favorables.                 |
| `isAgainstStrongCurrent(Port from, Port to)`                                     | `boolean`       | Indica si el tramo va contra corriente fuerte.                       |


Comandos
| Nombre              | Tipo / ubicación                                                | Propósito                                                                                       |
| ------------------- | --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `CreatePortCommand` | `mapping/domain/model/commands/CreatePortCommand.java` (record) | Estructura de datos para la creación de un `Port`. Consumido por `PortService.createPort(...)`. |





#### 4.2.4.4. A*/AI Process Bounded Context Infrastructure Layer
La capa de Infrastructure contiene las implementaciones concretas que interactúan con sistemas externos: la base de datos (MongoDB), mapeadores entre documentos y entidades, y adaptadores para servicios externos. En este proyecto las implementaciones de repositorios (SDMDB documents/repositories), mappers y configuraciones de MongoDB se ubican aquí. Esta capa implementa las interfaces definidas en el Domain Layer y expone adaptadores que la Application Layer consume.

*RouteDocument*
| Propiedad            | Valor                                                                                                                                                                                                                                                     |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `RouteDocument.java`                                                                                                                                                                                                                                      |
| **Categoría**        | Document / Persistence Model                                                                                                                                                                                                                              |
| **Propósito**        | Representar la entidad Route en la capa de persistencia (documento Mongo).                                                                                                                                                                                |
| **Campos típicos**   | `id` (String/UUID), `homePort` (String o subdocument con id/nombre), `destinationPort`, `nodes` (lista de nodos o referencias), `distance` (double), `cost` (double), `createdAt` (DateTime), `metadata` (map con info adicional como emisiones, eventos) |
| **Uso**              | Persistido vía `RouteRepository` para historial y consultas.                                                                                                                                                                                              |
*PortDocument*
| Propiedad            | Valor                                                                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `PortDocument.java`                                                                                                          |
| **Categoría**        | Document / Persistence Model                                                                                                 |
| **Propósito**        | Representar un puerto en la base de datos (documento Mongo).                                                                 |
| **Campos típicos**   | `id` (String/UUID), `name` (String), `coordinates` (lat,long), `continent` (String), `metadata` (capacidad, servicios, etc.) |
| **Uso**              | Persistido vía `PortRepository`, utilizado por `PortService` y para construir el grafo de rutas.                             |

*RouteRepository*
| Propiedad               | Valor                                                                                                                                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)**    | `RouteRepository.java`                                                                                                                                                                                      |
| **Categoría**           | Repository (Infra implementation / Spring Data repository)                                                                                                                                                  |
| **Propósito**           | Persistir y recuperar `RouteDocument` desde MongoDB. Implementa la abstracción definida en Domain (`IRouteRepository` o similar).                                                                           |
| **Operaciones típicas** | `save(RouteDocument)`, `saveAll(List<RouteDocument>)`, `findById(String)`, `findAll()`, `deleteById(String)`, consultas por `homePort` y `destinationPort` (p. ej. `findByHomePortAndDestinationPort(...)`) |
| **Notas**               | En la práctica suele extender `MongoRepository<RouteDocument, String>` o usar `@Repository` con `MongoTemplate` para consultas personalizadas.                                                              |
*RouteRepository*
| Propiedad               | Valor                                                                                                                                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)**    | `RouteRepository.java`                                                                                                                                                                                      |
| **Categoría**           | Repository (Infra implementation / Spring Data repository)                                                                                                                                                  |
| **Propósito**           | Persistir y recuperar `RouteDocument` desde MongoDB. Implementa la abstracción definida en Domain (`IRouteRepository` o similar).                                                                           |
| **Operaciones típicas** | `save(RouteDocument)`, `saveAll(List<RouteDocument>)`, `findById(String)`, `findAll()`, `deleteById(String)`, consultas por `homePort` y `destinationPort` (p. ej. `findByHomePortAndDestinationPort(...)`) |
| **Notas**               | En la práctica suele extender `MongoRepository<RouteDocument, String>` o usar `@Repository` con `MongoTemplate` para consultas personalizadas.                                                              |
*PortRepository*
| Propiedad               | Valor                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)**    | `PortRepository.java`                                                                                                              |
| **Categoría**           | Repository (Infra implementation / Spring Data repository)                                                                         |
| **Propósito**           | Persistir y recuperar `PortDocument` desde MongoDB. Implementa la abstracción definida en Domain (`IPortRepository` o similar).    |
| **Operaciones típicas** | `save(PortDocument)`, `findById(String)`, `findByName(String)`, `findAll()`, `existsByNameAndContinent(...)`, `deleteById(String)` |
| **Notas**               | Soporta las operaciones que `PortService` necesita para crear puertos y construir grafo.                                           |

*Mappers*
| Propiedad           | Valor                                                                                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (ej.)**    | `PortMapper.java`, `RouteMapper.java`                                                                                                                   |
| **Categoría**       | Mapper / Adapter                                                                                                                                        |
| **Propósito**       | Convertir entre documentos de persistencia (`PortDocument`, `RouteDocument`) y entidades/VO del Domain Layer (`Port`, `Route`, `Node`).                 |
| **Métodos típicos** | `toDocument(Port)`, `toEntity(PortDocument)`, `toDocument(Route)`, `toEntity(RouteDocument)`                                                            |
| **Uso**             | Los Application Services y Repositories usan los mappers para no exponer documentos directamente al dominio; mantienen separación de responsabilidades. |


*MongoConfig*
| Propiedad            | Valor                                                                                                                                                                             |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre (archivo)** | `MongoConfig.java` (o configuración en `application.properties`)                                                                                                                  |
| **Categoría**        | Configuration                                                                                                                                                                     |
| **Propósito**        | Configurar conexión a MongoDB (URI, cliente, `MongoTemplate`, serializadores), y parámetros de conexión (pool, timeouts).                                                         |
| **Uso**              | La infraestructura utiliza esta configuración para instanciar repositorios y `MongoTemplate`. En el repo hay referencias a `spring.data.mongodb.uri` en `application.properties`. |


*Adaptadores externos*
| Propiedad               | Valor                                                                                                                                                                                            |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Ejemplos**            | Adaptadores para APIs externas de clima / geopolitica (no necesariamente ya implementados en código).                                                                                            |
| **Categoría**           | External Adapter / HTTP Client                                                                                                                                                                   |
| **Propósito**           | Implementar llamadas HTTP a proveedores externos (weather API, geopolitical API), parsear respuestas y exponer un contrato interno (p. ej. `WeatherApiClient` → `NavigationConditionsProvider`). |
| **Tecnología sugerida** | `WebClient` (Spring WebFlux) o `RestTemplate` (simple) según preferencia del proyecto.                                                                                                           |
| **Consideración**       | Para la entrega del curso es aceptable simular (mocks) o usar un adapter con configuraciones que permitan habilitar/inhabilitar llamadas reales.                                                 |

*Logs / Monitoring*
| Propiedad               | Valor                                                                                                                                          |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nombre**              | `ErrorLog` (modelo de persistencia), `ServiceStatus` (si se implementa)                                                                        |
| **Categoría**           | Observability / Persistence                                                                                                                    |
| **Propósito**           | Guardar registros de errores críticos, estado de servicios externos y alertas; pueden persistirse en MongoDB para auditoría y debugging.       |
| **Operaciones típicas** | `save(ErrorLog)`, `findRecentByService(String)`, `storeServiceStatus(ServiceStatus)`                                                           |
| **Notas**               | No es necesario un stack complejo; un collection simple en MongoDB con timestamp y nivel de severidad es suficiente para el alcance del curso. |


#### 4.2.4.5. A*/AI Process Bounded Context Software Architecture Component Level Diagrams

#### 4.2.4.6. A*/AI Process Bounded Context Software Architecture Code Level Diagrams

##### 4.2.4.6.1. A*/AI Process Bounded Context Domain Layer Class Diagrams
En esta subsección se presenta el diagrama de clases UML correspondiente al Domain Layer del bounded context A/AI Process*. Esta representación estructurada permite visualizar de forma clara los principales componentes que conforman la lógica de dominio asociada al cálculo y optimización de rutas marítimas mediante algoritmos inteligentes, integrando factores como condiciones meteorológicas, distancias geográficas y costos operativos.

El nivel de detalle mostrado abarca la definición de clases, interfaces y servicios de dominio involucrados en el proceso de navegación y planificación óptima de rutas, especificando sus atributos, operaciones y responsabilidades dentro del modelo. Además, se incluyen las relaciones fundamentales entre los distintos elementos del dominio, indicando su multiplicidad y direccionalidad, lo que permite representar con precisión las dependencias entre entidades, servicios y repositorios.

Esta vista detallada facilita una comprensión integral del modelo conceptual del A/AI Process, sirviendo como base para la alineación entre el diseño del dominio y las capas de aplicación e infraestructura que soportan la ejecución del algoritmo de búsqueda A* y la orquestación de servicios inteligentes en el sistema.

![A*/AI CLASS DIAGRAM](../../assets/img/chapter-V/AI-Process-Class-Diagram.jpg)


##### 4.2.4.6.2. A*/AI Process Bounded Context Database Design Diagram

