# Ignacio Taboada
### Desarrollo Backend Java · Full Stack Junior

Estudiante de **Ingeniería en Sistemas de Información en UTN, Facultad Regional Córdoba**, orientado a oportunidades como **Desarrollador Backend Java o Full Stack Junior**.

Desarrollo aplicaciones web con foco en APIs REST, persistencia, seguridad y calidad. Mi proyecto principal, **Cuestion.me**, integra un frontend React con un backend Spring Boot y servicios cloud para crear cuestionarios y acompañar la práctica académica.

**[Conocer Cuestion.me](https://www.cuestion-me.app)** · **[Caso de estudio](projects/cuestionme/README.md)** · **[GitHub](https://github.com/Taboada-Ignacio)**

---

## Proyectos destacados

### 01 · Cuestion.me
**Plataforma Full Stack de cuestionarios y autoevaluación académica.**

Permite organizar bancos de preguntas por contexto académico, publicar cuestionarios, practicar y revisar resultados. Integra creación manual, paquetes ZIP con Excel e imágenes, corrección automática y conservación del historial de evaluaciones.

- **Backend:** Java 25, Spring Boot 4.1.1, Spring Security, JPA/Hibernate y PostgreSQL.
- **Decisiones técnicas:** autorización por propietario y roles, snapshots de intentos, importación transaccional con compensación multimedia y pruebas de integración.
- **Optimización demostrable:** el flujo local de guardado de metadatos de un cuestionario de 300 preguntas pasó de **1.809 a 5 sentencias SQL**. Es una medición de servicios y transacciones, sin HTTP ni red; no representa rendimiento de producción.

[Demostración](https://www.cuestion-me.app) · [Arquitectura y caso de estudio](projects/cuestionme/README.md)

> El código de Cuestion.me permanece privado. Este portafolio presenta su diseño y decisiones técnicas sin distribuir código fuente ni configuraciones sensibles.

### 02 · Web Kuuii
**Sitio comercial responsive para una distribuidora de agua y hielo.**

Presenta productos, ubicación y vías de contacto por WhatsApp. Desarrollado con React, JavaScript, Bootstrap y CSS, con navegación por secciones y carga del mapa interactivo bajo demanda.

[Demostración](https://first-web-site-proyect-kuuii.pages.dev/) · [Caso de estudio](projects/web-kuuii/README.md) · [Código público](https://github.com/Taboada-Ignacio/first-web-site-proyect-Kuuii)

## Tecnologías aplicadas

| Área | Tecnologías |
| --- | --- |
| Backend | Java 25 · Spring Boot 4.1.1 · Spring Web MVC · Spring Security |
| Persistencia | PostgreSQL 17 · JPA/Hibernate · Flyway · SQL |
| Frontend | React 19 · JavaScript · Vite 7 · Tailwind CSS 4 · Bootstrap 5 |
| Seguridad | Sesiones · CSRF · Autorización por roles y recursos · Google OpenID Connect |
| Calidad | JUnit 5 · Mockito · Testcontainers · Pruebas del cliente con Node.js |
| Cloud y entrega | Docker · Docker Compose · Nginx · GitHub Actions · Azure Container Apps · Azure Container Registry · Vercel · Neon · Cloudinary |

Las tecnologías se vinculan a los proyectos documentados; las versiones corresponden a las dependencias declaradas y configuraciones revisadas.

## Competencias demostradas

- **Arquitectura:** separar interfaz, API, reglas de negocio y persistencia; integrar servicios externos.
- **Datos:** diseñar transacciones y migraciones, conservar resultados históricos y controlar escrituras concurrentes.
- **Seguridad:** validar permisos en el servidor, proteger escrituras con CSRF y validar archivos antes de persistirlos.
- **Testing:** cubrir reglas, autorización, importación, historial y costos SQL con pruebas específicas.
- **DevOps:** contenerizar aplicaciones y automatizar verificación, construcción y despliegue del backend.
- **Rendimiento:** identificar trabajo redundante, medir consultas y agregar regresiones que controlen su crecimiento.

## Formación y contacto

**Ingeniería en Sistemas de Información — UTN Facultad Regional Córdoba.** Formación en curso.

**GitHub:** [Taboada-Ignacio](https://github.com/Taboada-Ignacio). Canal público de contacto y consulta de proyectos.

## Explorar el portafolio

[Catálogo de proyectos](projects/README.md) · [Plantilla de documentación](docs/project-template.md) · [Material visual](assets/README.md)
