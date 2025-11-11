# Programación de Vanguardia - Universidad de la Ciudad de Buenos Aires.

<br>
<br>

<h1 align="center" style="font-weight: bold;">Backend de la Plataforma de Gestión de Reservas 💻 </h1>

<br>
<br>

# Instalación

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

**Nota: para comenzar a utilizar el sistema se debe crear la base de datos base_de_datos (de no estar creada la base de datos EL SISTEMA ARROJARA ERROR) y configurar las variables de entorno correspondientes en el archivo application.properties. Posteriormente al iniciar por primera vez el sistema lo que sucedera es que el mismo creara las tablas iniciales y conformara los primeros usuarios (Admin y user) con sus respectivas contraseñas 1234 y permisos.**

#  Dependencias utilizadas

Para poder operar el Backend utiliza diferentes librerías que se detallan a continuación

- [Spring Security](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#web.security) - Proporciona autenticación, autorización y mecanismos de seguridad para proteger rutas y gestionar roles.

- [Spring Data JPA](https://spring.io/projects/spring-data-jpa) - Implementa la capa de persistencia usando Hibernate, permitiendo mapear entidades y realizar consultas a la base de datos de forma sencilla.

- [Spring Web](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#web) - Permite construir controladores REST y manejar solicitudes HTTP. Incluye un servidor Tomcat embebido.

- [Spring DevTools](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#using.devtools) - Proporciona recarga automática, reinicio rápido y utilidades que facilitan el desarrollo.

- [MySQL Connector/J](https://dev.mysql.com/doc/connector-j/en/) - Driver JDBC utilizado para conectar y operar con bases de datos MySQL.

- [Lombok](https://projectlombok.org/) - Genera automáticamente getters, setters, constructores y otros métodos para reducir código repetitivo.

- [Spring Boot Test](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#features.testing) - Incluye JUnit, Mockito y herramientas de testing para realizar pruebas unitarias e integración.

- [Spring Validation](https://docs.spring.io/spring-framework/reference/core/validation/beanvalidation.html) - Implementa Bean Validation (Hibernate Validator) para validar datos de entrada mediante anotaciones.

<br>
<br>

## Rutas usuarios 
#### Rutas usuario (/api/usuario/):
**Nota: Esta sección es solo alcanzable a usuarios de rol admin, excepto el listado.**

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
#### Rutas reservas (/api/reservas/):

**Solo ADMIN**
* `PUT`    | localhost:8080/api/reservas/actualizar/{id} -> actualiza una reserva existente.

* `DELETE` | localhost:8080/api/reservas/borrar/{id} -> elimina una reserva por id.

**ADMIN y USER**
* `GET`  | localhost:8080/api/reservas/listar -> lista todas las reservas.

* `GET`  | localhost:8080/api/reservas/listar/{id} -> obtiene una reserva por id.

* `POST` | localhost:8080/api/reservas/crear -> crea una nueva reserva.

## Rutas salas
#### Rutas salas (/api/salas/):

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


