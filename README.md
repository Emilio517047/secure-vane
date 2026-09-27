# secure-vane

Una API para registrar, clasificar y rastrear vulnerabilidades de software

---

# Base de datos

## Tablas

### Vulnerabilidades

Esta tabla almecenará los datos de las vulnerabilidades reportadas por los usuarios. Cada registro incluye:

- ID: Identificador único y clave primaria de la tabla.
- Título: Nombre de la vulnerabilidad (ej. 'Inyección SQL').
- Descripción: Breve explicación del hallazgo.
- Severidad: Nivel de riesgo (ej. CRÍTICA).
- Estado: Situación actual (ej. ABIERTA, EN REVISIÓN, MITIGADA).
- Fecha de creación: Registro temporal que toma SYSDATE por defecto.

El proyecto utiliza una instancia de Oracle DB desplegada en un contenedor Docker, y los scripts han sido desarrollados utilizando la extensión Oracle SQL Developer para VS Code.

---

# Backend

## Tecnólogias usadas:

- Java 25
- Spring Boot 4.1.1
- Maven 4.0.0

### Dependencias

- Spring Web
- Spring JPA
- Spring Security
- Lombok

## Entidades

### Vulnerabilidad

Quería crear una entidad que usa Hibernate para representar una entrada desde el base de datos. La entidad que es `Vulnerabilidad` representa una entrada desde la table Vulnerabilidades. Las variables consisten:

- id
- titulo
- descripcion
- severidad
- estado
- fechaCreacion

`id` va a auto-incrementar con cada entrada que se añade a la tabla de Vulnerabilidades. `fechaCreacion` está añadido cuanto antes de que una entrada se añada al base de datos.
Ningunos de las propiedades pueden ser `null`.

Desde esta parte del proyecto aprendí sobre crear una entidad que implementa las anotaciones para usar Hibernate. También aprendí sobre Lombok, lo cual nunca antes he usado y que me deja utilizar las anotaciones para getters y setters, además de utilizar anotaciones para inyectar los constructores.

## Componente: Entidad Vulnerabilidad (Hibernate)

En esta sección del proyecto, creé la entidad `Vulnerabilidad` utilizando **Hibernate** para representar y mapear los registros de la tabla `Vulnerabilidades` de la base de datos.

### Propiedades de la Entidad

Ninguno de los siguientes atributos puede ser nulo (`nullable = false`):

- **id**: Clave primaria que se autoincrementa de forma automática con cada nuevo registro.
- **titulo**: El título descriptivo de la vulnerabilidad.
- **descripcion**: Detalle técnico del fallo encontrado.
- **severidad**: Nivel de impacto (ej. Alta, Media, Baja).
- **estado**: Estado actual de la vulnerabilidad (ej. ABIERTA, EN REVISIÓN, MITIGADA).
- **fechaCreacion**: Fecha y hora exactas del registro, la cual se genera automáticamente justo antes de insertar la entrada en la base de datos.

### Aprendizajes Clave

- **Mapeo Object-Relational (ORM) con Hibernate:** Aprendí a estructurar una entidad implementando las anotaciones nativas de JPA/Hibernate para la persistencia de datos y la automatización de campos (como el autoincremento y ganchos de ciclo de vida para la fecha).
- **Lombok:** Implementé esta librería por primera vez. Utilicé sus anotaciones para generar automáticamente los métodos _getters_, _setters_ y la inyección de constructores, lo que reduce drásticamente el código repetitivo (_boilerplate code_).
