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
- Estado: Situación actual (ABIERTA o CERRADA).
- Fecha de creación: Registro temporal que toma SYSDATE por defecto.

El proyecto utiliza una instancia de Oracle DB desplegada en un contenedor Docker, y los scripts han sido desarrollados utilizando la extensión Oracle SQL Developer para VS Code.
