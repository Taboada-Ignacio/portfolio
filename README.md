# Ignacio Taboada
### Desarrollo Backend Java · Full Stack Junior

Estudiante de **Ingeniería en Sistemas de Información en UTN, Facultad Regional Córdoba**, orientado a oportunidades como **Desarrollador Backend Java o Full Stack Junior**.

Desarrollo aplicaciones web con foco en APIs REST, arquitectura, persistencia, integración de servicios y calidad. Destaco **TPAI-Bolsines**, una aplicación Full Stack de seguimiento de envíos con tres proveedores GPS, mapa interactivo y patrón Adapter, y **Cuestion.me**, una plataforma con backend Spring Boot y servicios cloud.

**[Conocer TPAI-Bolsines](https://github.com/Taboada-Ignacio/TPAI-Bolsines)** · **[Caso de estudio](projects/tpai-bolsines/README.md)** · **[GitHub](https://github.com/Taboada-Ignacio)**

---

## Proyectos destacados

### 01 · TPAI-Bolsines
**Aplicación Full Stack de seguimiento GPS con arquitectura por capas, mapa interactivo y tres adaptadores.**

Trabajo académico grupal de Diseño de Sistemas de Información (UTN FRC). La versión final está en la rama **`main`** del repositorio. Implementa el **CU 36** para consultar bolsines enviados desde la comisión médica del empleado autenticado, ubicar cada envío y visualizar su recorrido entre origen y destino.

- **Backend y datos:** Next.js 16 (Route Handlers), TypeScript, Prisma ORM 7 y PostgreSQL 17; sesiones, permisos por rol y reglas de negocio en gestores y entidades de dominio.
- **Integración:** API GPS oficial de la cátedra; patrón Adapter con **XTR-4500L, QX-7A y MTR-900**, normalizando respuestas JSON, CSV y matrices.
- **Dos recorridos:** el CU 36 original utiliza **XTR-4500L** fijo; una pantalla adicional permite elegir el modelo GPS mediante un gestor independiente, sin alterar el flujo evaluado.
- **Experiencia:** React 19, MapLibre GL JS + OpenFreeMap, rutas de seguimiento, filtros y detalle de bolsines; interfaz responsive, animaciones GSAP y elementos 3D.
- **Flujo complementario:** confirmación opcional de notificación por correo al gerente de la comisión de destino mediante **CU 31**; entorno local con Docker Compose y Mailpit.

**Alcance:** prototipo académico ejecutable localmente, con código público y sin demo de producción verificada.

[Caso de estudio](projects/tpai-bolsines/README.md) · [Código fuente (rama main)](https://github.com/Taboada-Ignacio/TPAI-Bolsines/tree/main)

### 02 · SYZA · Estética integral
**Landing comercial mobile-first para una marca de estética y bienestar.**

Sitio web de presentación para SYZA, con identidad visual cálida, secciones de servicios, origen de la marca y contacto. El proyecto combina fotografía, animación y recursos 3D, con especial atención al diseño responsive y la experiencia en teléfonos.

- **Frontend:** React, TypeScript, Vite y Tailwind CSS v4.
- **Experiencia visual:** GSAP, Three.js, React Three Fiber, Drei y Lucide React.
- **Alcance:** web estática preparada para Render; la gestión privada de turnos y la integración con Google Drive son etapas futuras, no funcionalidades disponibles en esta landing.

[Caso de estudio](projects/syza/README.md)

### 03 · Cuestion.me
**Plataforma Full Stack de cuestionarios y autoevaluación académica.**

Permite organizar bancos de preguntas por contexto académico, publicar cuestionarios, practicar y revisar resultados. Integra creación manual, paquetes ZIP con Excel e imágenes, corrección automática y conservación del historial de evaluaciones.

- **Backend:** Java 25, Spring Boot 4.1.1, Spring Security, JPA/Hibernate y PostgreSQL.
- **Decisiones técnicas:** autorización por propietario y roles, snapshots de intentos, importación transaccional con compensación multimedia y pruebas de integración.
- **Optimización demostrable:** el flujo local de guardado de metadatos de un cuestionario de 300 preguntas pasó de **1.809 a 5 sentencias SQL**. Es una medición de servicios y transacciones, sin HTTP ni red; no representa rendimiento de producción.

[Demostración](https://www.cuestion-me.app) · [Arquitectura y caso de estudio](projects/cuestionme/README.md)

> El código de Cuestion.me permanece privado. Este portafolio presenta su diseño y decisiones técnicas sin distribuir código fuente ni configuraciones sensibles.

### 04 · Web Kuuii
**Sitio comercial responsive para una distribuidora de agua y hielo.**

Presenta productos, ubicación y vías de contacto por WhatsApp. Desarrollado con React, JavaScript, Bootstrap y CSS, con navegación por secciones y carga del mapa interactivo bajo demanda.

[Demostración](https://first-web-site-proyect-kuuii.pages.dev/) · [Caso de estudio](projects/web-kuuii/README.md) · [Código público](https://github.com/Taboada-Ignacio/first-web-site-proyect-Kuuii)

## Tecnologías aplicadas

| Área | Tecnologías |
| --- | --- |
| Backend | Java 25 · Spring Boot 4.1.1 · Spring Web MVC · Spring Security · Next.js 16 Route Handlers |
| Persistencia | PostgreSQL 17 · JPA/Hibernate · Flyway · Prisma ORM 7 · SQL |
| Frontend | React 19 · JavaScript · TypeScript · Next.js 16 · Vite 7 · Tailwind CSS 4 · Bootstrap 5 · GSAP · Three.js · React Three Fiber · Drei · Lucide React · MapLibre GL JS · OpenFreeMap |
| Seguridad | Sesiones · CSRF · Autorización por roles y recursos · Google OpenID Connect |
| Calidad | JUnit 5 · Mockito · Testcontainers · Vitest · Pruebas del cliente con Node.js |
| Cloud y entrega | Docker · Docker Compose · Nginx · GitHub Actions · Azure Container Apps · Azure Container Registry · Vercel · Render · Neon · Cloudinary |

Las tecnologías se vinculan a los proyectos documentados; las versiones corresponden a las dependencias declaradas y configuraciones revisadas.

## Competencias demostradas

- **Arquitectura:** separar interfaz, API, reglas de negocio y persistencia; integrar servicios externos mediante interfaces y el patrón Adapter.
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
