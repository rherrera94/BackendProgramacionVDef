# Programación de Vanguardia - Universidad de la Ciudad de Buenos Aires.

<br>
<br>

<h1 align="center" style="font-weight: bold;">Backend de la Plataforma de Gestión de Reservas 💻 </h1>

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

- [Spring Validation](https://docs.spring.io/spring-framework/reference/core/validation/beanvalidation.html) - Implementa Bean Validation (Hibernate Validator) para validar datos de entrada mediante anotaciones como @NotNull, @Email, @Size, etc.



