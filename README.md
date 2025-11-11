# Programación de Vanguardia - Universidad de la Ciudad de Buenos Aires.

<br>
<br>

<h1 align="center" style="font-weight: bold;">Backend de la Plataforma de Gestión de Reservas 💻 </h1>

![GitHub repo size](https://img.shields.io/github/repo-size/rherrera94/BackendProgramacionVDef?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/rherrera94/BackendProgramacionVDef?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/rherrera94/BackendProgramacionVDef?style=for-the-badge)

<br>
<br>

## Tabla de contenidos
<br>

- [Resumen del Proyecto](#Resumen-del-Proyecto)
- [Instalación](#Instalación)
   - [Clonar](#Clonar-el-repositorio)
   - [Crear ejecutable](#Crear-ejecutable)
   - [Iniciar localmente](#Iniciar-el-proyecto-de-manera-local)
- [Caracteristicas principales](#Características-principales)
   - [Documentación Postman](#Documentación-Postman)
   - [Dependencias utilizadas](#Dependencias-utilizadas)
   - [Estructura del Proyecto](#Estructura)
   - [Base de datos](#Base-de-Datos)
      - [Entidades Principales](#Entidades-principales)
      - [Relaciones destacadas](#Relaciones-destacadas)
- [Rutas](#Rutas)
   - [Seguridad y Autenticación](#Seguridad-y-Autenticación)
      - [Roles](#Roles)
      - [Login](#Login)
      - [Archivos para seguridad](#Funcion-de-los-archivos)
      - [Rutas de libre acceso](#Rutas-sin-autenticación)
      - [Convenciones](#Convenciones)
   - [Rutas usuarios](#Rutas-usuarios)
   - [Rutas artículos](#Rutas-artículos)
   - [Rutas personas](#Rutas-personas)
   - [Rutas reservas](#Rutas-reservas)
   - [Rutas salas](#Rutas-salas)
   - [Rutas públicas](#Rutas-públicas)

<br>

## Resumen del Proyecto

Este backend corresponde a una **Plataforma de Gestión de Reservas**, desarrollada en Java y Spring Boot.  
Descripción del proyecto:

Se desea migrar una plataforma existente en el cual se quiere utilizar una herramienta para poder llevar las reservas de recursos en la organización. Por cuestiones de compliance se debe hacer la migración para poder seguir operando antes de los cambios de plataformas.
Se desea además agregar un módulo de predicción de reservas para hacer uso eficiente de los recursos.
El sistema a migrar está desarrollado en Java 8, con una base de datos Sql Server, donde los Dao 's estaban desarrollados con jdbc. Y varias configuraciones estaban estáticas en el código fuente.

El objetivo principal de éste trabajo:

* Seleccionar tecnologías adecuadas para el desarrollo del proyecto.
* Realizar una MVP(una propuesta mínima viable posible).
* Elegir una base de datos que se adapte mejor a los requisitos del proyecto.
* Crear mocks de pantallas.
* Definir modelo de pruebas para garantizar la calidad del código.
* Plantear la plataforma donde se realizará el despliegue de la aplicación.

Funcionalidades que se solicitan:

* Registro y autenticación de usuarios por roles.
* Ingreso y actualización de datos manual y vía api que se pueden reservar.
* Monitor de predicción de reservas.


Toda la API está asegurada mediante **Spring Security**, implementando autenticación y autorización por roles.  
La persistencia se gestiona mediante **Spring Data JPA + Hibernate** y la información se almacena en una base de datos MySQL.

> [!NOTE] 
> **Para poder ver todo el historial de cambios que se realizaron antes de estas últimas versiones del backend, ingresar a
> [Repositorio anterior](https://github.com/CandelaQuintana/TrabajoPracticoPV)**  

# Instalación

![Java](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)

El proyecto necesita para funcionar:
- [Java SE 17.0.12](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) 
- [Maven](https://maven.apache.org/download.cgi) 

## Clonar el repositorio

   ```sh
    git clone https://github.com/rherrera94/BackendProgramacionVDef
    cd BackendProgramacionVDef
   ```
#### Crear ejecutable

```sh
$ mvn clean install
```

#### Iniciar el proyecto de manera local

```sh
$ java -jar target/demo-0.0.1-SNAPSHOT.jar
```
<br>
<br>

> [!NOTE] 
> **Para comenzar a utilizar el sistema se debe crear la base de datos base_de_datos (de no estar creada la base de datos EL SISTEMA
> ARROJARA ERROR) y configurar las variables de entorno correspondientes en el archivo application.properties. Posteriormente al iniciar
> por primera vez el sistema lo que sucedera es que el mismo creara las tablas iniciales y conformara los primeros usuarios (Admin y
> user) con sus respectivas contraseñas 1234 y permisos.**

# Características principales

#### Documentación Postman

[Documentacion Postman](https://documenter.getpostman.com/view/17357164/2sB3WttKXN)


####  Dependencias utilizadas

Para poder operar el Backend utiliza diferentes librerías que se detallan a continuación

- [Spring Security](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#web.security) - Proporciona autenticación, autorización y mecanismos de seguridad para proteger rutas y gestionar roles.

- [Spring Data JPA](https://spring.io/projects/spring-data-jpa) - Implementa la capa de persistencia usando Hibernate, permitiendo mapear entidades y realizar consultas a la base de datos de forma sencilla.

- [Spring Web](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#web) - Permite construir controladores REST y manejar solicitudes HTTP. Incluye un servidor Tomcat embebido.

- [Spring DevTools](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using.devtools) - Proporciona recarga automática, reinicio rápido y utilidades que facilitan el desarrollo.

- [MySQL Connector/J](https://dev.mysql.com/doc/connector-j/en/) - Driver JDBC utilizado para conectar y operar con bases de datos MySQL.

- [Lombok](https://projectlombok.org/) - Genera automáticamente getters, setters, constructores y otros métodos para reducir código repetitivo.

- [Spring Boot Test](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#features.testing) - Incluye JUnit, Mockito y herramientas de testing para realizar pruebas unitarias e integración.

- [Spring Validation](https://docs.spring.io/spring-framework/reference/core/validation/beanvalidation.html) - Implementa Bean Validation (Hibernate Validator) para validar datos de entrada mediante anotaciones.


#### Estructura

```
BackendProgramacionVDEF/
├── .mvn/                        # Archivos internos de Maven
├── src/
│   └── main/
│       ├── java/com/example/demo/
│       │   ├── conf/            # Configuraciones generales del proyecto
│       │   │   └── SegurityConf.java
│       │   │
│       │   ├── controller/      # Controladores REST (manejan las rutas de la API)
│       │   │   ├── ArticulosRestController.java
│       │   │   ├── AuthController.java
│       │   │   ├── PersonaRestController.java
│       │   │   ├── ReservaRestController.java
│       │   │   ├── SalaRestController.java
│       │   │   └── UsuarioController.java
│       │   │
│       │   ├── model/           # Entidades JPA (mapeo a base de datos)
│       │   │   ├── Articulos.java
│       │   │   ├── Persona.java
│       │   │   ├── Reserva.java
│       │   │   ├── Rol.java
│       │   │   ├── Sala.java
│       │   │   └── Usuario.java
│       │   │
│       │   ├── repository/      # Repositorios (DAO/JPA)
│       │   │   ├── Articulos_Repositorio.java
│       │   │   ├── Persona_Repositorio.java
│       │   │   ├── Reserva_Repositorio.java
│       │   │   ├── Rol_Repositorio.java
│       │   │   ├── Sala_Repositorio.java
│       │   │   └── UsuarioRepository.java
│       │   │
│       │   ├── security/        # Lógica de seguridad personalizada
│       │   │   └── CustomUserDetailsService.java
│       │   │
│       │   └── service/         # Servicios de negocio
│       │       ├── ArticulosService.java
│       │       ├── PersonaService.java
│       │       ├── ReservaService.java
│       │       ├── SalaService.java
│       │       └── DemoApplication.java  # Clase principal de Spring Boot
│       │
│       └── resources/           # Configuraciones y recursos del proyecto
│           └── application.properties
│
└── target/                      # Archivos generados por Maven (compilados)
    └── classes/
```

#### Base de Datos

El sistema utiliza **MySQL** como motor de base de datos.  
Al iniciar por primera vez, Spring Boot crea automáticamente las tablas basadas en las entidades del paquete `model/`.

##### Entidades principales
- **usuarios** → representa los usuarios del sistema (conectado a Rol)
- **roles** → define los roles de usuario (ADMIN / USER)
- **persona** → Informacion de las personas cargadas en el sistema
- **salas** → salas del edificio
- **articulos** → elementos disponibles para su utilizacion.
- **reservas** → registro de las reservas realizadas por los usuarios

##### Relaciones destacadas
- Un **Usuario** tiene un **Rol**
- Una **Reserva** se relaciona con:
  - Persona
  - Sala
  - Artículo

# Rutas
## Seguridad y Autenticación

El sistema implementa **Spring Security**, que protege todos los endpoints exceptuando `/auth/login` y `/error`.

### Roles
- **ADMIN**
- **USER**

### Login
1. El usuario envía un usuario y contraseña a `/auth/login`.
2. Spring Security valida las credenciales en la BBDD usando **CustomUserDetailsService**.
3. Si el usuario y contraseña son correctas:
   - El sistema crea una sesión y asigna el rol correspondiente.
4. El rol determina a qué rutas se puede acceder.

### Funcion de los archivos
- `conf/SegurityConf.java` – configuración principal de seguridad.
- `security/CustomUserDetailsService.java` – carga usuarios desde la BD.

### Rutas sin autenticación
- `/auth/login` (POST y GET)
- `/error`

Todas las demás rutas requieren autenticación.

### Convenciones
- **ADMIN** → acceso total.
- **USER** → acceso a ciertas rutas.
- **PUBLIC** → no requiere autenticación.

## Rutas usuarios 
#### Rutas usuario (/api/usuario/):
**Solo ADMIN**
* `POST` | localhost:8080/api/usuario/add -> crea un nuevo usuario.

**ADMIN y USER**
* `GET`  | localhost:8080/api/usuario/listar -> genera un listado generalizado de los usuarios registrados.

## Rutas artículos
#### Rutas artículo (/api/articulo/):

**Solo ADMIN**
* `POST`   | localhost:8080/api/articulo/add -> crea un nuevo artículo.

* `PUT`    | localhost:8080/api/articulo/update -> actualiza un artículo existente.

* `DELETE` | localhost:8080/api/articulo/delete/{id} -> elimina un artículo por id.

**ADMIN y USER**
* `GET` | localhost:8080/api/articulo/listar -> lista todos los artículos.

* `GET` | localhost:8080/api/articulo/listar/{id} -> obtiene un artículo por id.

* `GET` | localhost:8080/api/articulo/buscar/nombre/{nombre} -> busca artículos por nombre.

## Rutas personas
#### Rutas persona (/api/persona/):

**Solo ADMIN**
* `POST`   | localhost:8080/api/persona/add -> crea una nueva persona.

* `PUT`    | localhost:8080/api/persona/actualizar -> actualiza datos de una persona.

* `DELETE` | localhost:8080/api/persona/eliminar/{id} -> elimina una persona por id.

**ADMIN y USER**
* `GET` | localhost:8080/api/persona/listar -> lista todas las personas.

* `GET` | localhost:8080/api/persona/listarporid/{id} -> obtiene una persona por id.

* `GET` | localhost:8080/api/persona/buscar/email/{email} -> busca persona por email.

* `GET` | localhost:8080/api/persona/buscar/nombre/{nombre} -> busca persona por nombre.

## Rutas reservas
#### Rutas reserva (/api/reservas/):

**Solo ADMIN**
* `PUT`    | localhost:8080/api/reservas/actualizar/{id} -> actualiza una reserva existente.

* `DELETE` | localhost:8080/api/reservas/borrar/{id} -> elimina una reserva por id.

**ADMIN y USER**
* `GET`  | localhost:8080/api/reservas/listar -> lista todas las reservas.

* `GET`  | localhost:8080/api/reservas/listar/{id} -> obtiene una reserva por id.

* `POST` | localhost:8080/api/reservas/crear -> crea una nueva reserva.

## Rutas salas
#### Rutas sala (/api/salas/):

**Solo ADMIN**
* `GET` | localhost:8080/api/salas/crear -> crea una nueva sala.

* `GET` | localhost:8080/api/salas/actualizar -> actualiza una sala.

* `GET` | localhost:8080/api/salas/borrar/{id} -> elimina una sala por id.

**ADMIN y USER**
* `POST` | localhost:8080/api/salas/listar -> lista todas las salas.

## Rutas públicas
#### Rutas auth y sistema (/auth/):

**Públicas**
* `POST` | localhost:8080/auth/login -> login hacia la API.

* `GET`  | localhost:8080/auth/login -> login hacia la API(en modo GET).

* `GET`  | localhost:8080/error -> endpoint de error manejado por Spring.


