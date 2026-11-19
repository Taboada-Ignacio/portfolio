# TPAI-Bolsines
### Seguimiento de bolsines con mapa interactivo e integración GPS

[Código final en main](https://github.com/Taboada-Ignacio/TPAI-Bolsines/tree/main) · [Volver al portafolio](../../README.md)

## Resumen y contexto

Proyecto académico grupal del Trabajo Práctico de Aplicación de Diseño de Sistemas de Información (3.er año de Ingeniería en Sistemas de Información, UTN Facultad Regional Córdoba). Implementa, entre otros flujos, el **CU 36: Consultar seguimiento de bolsines**.

Un encargado de bolsines puede consultar los envíos en tránsito asociados a su comisión médica de origen, conocer su última posición GPS sobre un mapa, explorar su recorrido hasta la comisión de destino y, si lo desea, notificar esa ubicación al gerente de destino. El sistema integra una API GPS de la cátedra y servicios locales de persistencia y correo.

**Versión de referencia:** rama [`main`](https://github.com/Taboada-Ignacio/TPAI-Bolsines/tree/main) del repositorio público, que contiene la integración final de frontend y backend y un recorrido adicional con selección del proveedor GPS.

**Alcance:** prototipo académico ejecutable en entorno local. No se presenta como producto de rastreo en producción ni como un sistema de seguridad empresarial.

## Mi participación y trabajo en equipo

Participé en el diseño e implementación del flujo de seguimiento (CU 36), la aplicación del patrón Adapter para los modelos GPS y la integración de los datos de localización con la interfaz de mapa. El proyecto se desarrolló en equipo y el repositorio público reúne el trabajo compartido. La extensión con selección de tracker está implementada en un gestor y una ruta propios para conservar el recorrido original exigido por la cátedra.

## Funcionalidades

- Inicio y cierre de sesión, identificación del empleado y control de acceso al seguimiento según su rol.
- Consulta de bolsines en estado **Enviado** cuya comisión médica de origen coincide con la del empleado autenticado.
- Visualización de la última ubicación GPS y su fecha de actualización sobre un mapa; representación del recorrido **origen → ubicación actual → destino**.
- Selección de un bolsín para consultar sus datos, precinto, origen y destino; filtros por precinto y comisión de destino.
- **`/seguimiento`:** CU 36 original, que consulta exclusivamente el proveedor **XTR-4500L** con número de bolsín y código de comisión de origen.
- **`/seguimiento/con-opcion-a-elegir`:** variante independiente con selector de **XTR-4500L, QX-7A o MTR-900** y un gestor propio, sin modificar el recorrido original.
- Normalización de datos de GPS heterogéneos a un contrato común para el mapa y manejo de bolsines cuya ubicación no está disponible.
- Confirmación opcional de notificación al gerente de la comisión médica de destino a través del caso de uso **CU 31**; Mailpit permite inspeccionar correos en desarrollo.
- ABM y catálogos técnicos de empleados, comisiones, roles, estados y bolsines para respaldar el escenario académico.
- Interfaz responsive con temas claro/oscuro, animaciones GSAP y representación 3D interactiva de un bolsín en el inicio de sesión.

## Tecnologías utilizadas

| Área | Tecnologías |
| --- | --- |
| Aplicación web | Next.js 16 (App Router y Route Handlers) · React 19 · TypeScript estricto |
| Persistencia | PostgreSQL 17 · Prisma ORM 7 · @prisma/adapter-pg · migraciones y datos de ejemplo |
| Interfaz y cartografía | Tailwind CSS 4 · MapLibre GL JS · OpenFreeMap · GSAP · Three.js · React Three Fiber · Drei |
| Integraciones | API GPS oficial de la cátedra · servicios HTTP · Nodemailer · Mailpit |
| Calidad | Vitest · Zod · ESLint · Prettier |
| Entorno | Node.js 24 · Docker · Docker Compose |

Las versiones son las declaradas en el repositorio revisado; no implican una auditoría de los servicios en ejecución.

## Arquitectura y decisiones de diseño

El frontend y los endpoints HTTP conviven en Next.js. Los Route Handlers funcionan como controladores; los gestores implementan el caso de uso; el dominio representa bolsines, estados, empleados y comisiones médicas; Prisma encapsula el acceso a PostgreSQL. Los DTO y las validaciones delimitan los datos intercambiados.

**Patrón Adapter para GPS.** La frontera `InterfazGPSTracker` selecciona un adaptador concreto según el modelo. Se implementaron `AdaptadorXTR4500L`, `AdaptadorQX7A` y `AdaptadorMTR900`, cada uno conectado a su servicio HTTP de integración. Los formatos externos difieren (JSON, CSV y matriz), pero se normalizan a número de bolsín, latitud, longitud y fecha ISO 8601 UTC. XTR-4500L consulta con el código de CM de origen, QX-7A con el código de CM de destino y MTR-900 con el número de bolsín.

**Dos gestores, sin alterar el CU evaluado.** `GestorConsultarUbicacionDeBolsin` mantiene **XTR-4500L** como constante y consulta por CM de origen. `GestorConsultarUbicacionesDeBolsinConSeleccion` implementa por separado la elección del proveedor y se expone en `/seguimiento/con-opcion-a-elegir`. Ambas pantallas reutilizan componentes de mapa y seguimiento, pero poseen rutas y gestores de consulta independientes.

**Fuente de las ubicaciones.** La API GPS oficial de la cátedra entrega las coordenadas. **MapLibre GL JS** representa los marcadores, trazados e interacciones; **OpenFreeMap** aporta el mapa base. No se usa la API ni el SDK de Google Maps para renderizar la pantalla de seguimiento. Las clases con nombres heredados del UML relacionadas con Google Maps conservan esos nombres por trazabilidad del diseño académico.

**Separación de responsabilidades.** La consulta del CU 36 obtiene y visualiza posiciones; la notificación por correo se delega a otro caso de uso y no ocurre hasta que la persona confirma la acción. La comisión de destino se emplea para mostrar el recorrido y localizar al destinatario del aviso, no para filtrar los bolsines del CU 36.

**Persistencia.** La base relacional guarda usuarios, sesiones, empleados, comisiones médicas, bolsines, estados e historial de cambios. Prisma modela las relaciones y las migraciones; Docker Compose coordina la base, la aplicación, el simulador/API GPS y el correo de desarrollo.

## Ejecución local

Se requiere Node.js 24, Docker con contenedores Linux y Docker Compose. El repositorio incluye `.env.example` con configuración de desarrollo; no deben utilizarse esos valores en un entorno público.

1. Clonar [TPAI-Bolsines](https://github.com/Taboada-Ignacio/TPAI-Bolsines).
2. Revisar `.env.example` y crear el archivo `.env` local según las indicaciones del repositorio.
3. Ejecutar `docker compose up --build -d` desde la raíz.
4. Verificar los servicios con `docker compose ps -a` y el endpoint `http://localhost:3000/api/health`.
5. Acceder a `http://localhost:3000/seguimiento` con la cuenta de demostración configurada en la base local. Para examinar correos, abrir Mailpit en `http://localhost:8025`.

Los recorridos GPS dependen de que los identificadores y comisiones del conjunto de datos sean compatibles con la API oficial; el README del proyecto explica los fixtures disponibles. No hay una demostración pública de la aplicación verificada para enlazar desde este portafolio.

## Pruebas y evidencia

El repositorio incluye pruebas con Vitest para dominio, autenticación, catálogos, Adapter GPS, seguimiento original y con selección de proveedor, notificación e integración de componentes. También proporciona comandos para validación Prisma, análisis de tipos TypeScript, lint, formato y compilación.

**Esta incorporación al portafolio se basa en la documentación y los archivos del repositorio. No se ejecutó nuevamente la suite de pruebas ni un despliegue de la aplicación como parte de esta actualización.** Las pruebas HTTP externas del GPS requieren configurar y levantar el entorno de desarrollo.

## Material visual

El [plan de capturas](../../assets/tpai-bolsines/README.md) identifica imágenes que pueden incorporarse del sistema con datos ficticios. No se atribuyen aquí capturas ni métricas visuales no verificadas.

## Aprendizajes y mejoras posibles

- Traducción de casos de uso y diagramas UML a responsabilidades y contratos TypeScript.
- Integración desacoplada de proveedores con formatos de respuesta heterogéneos.
- Extensión de un caso de uso mediante un gestor independiente, preservando los contratos y el flujo de la evaluación.
- Diseño de un mapa que asocia el dato de negocio con una posición geográfica y su instante de actualización.
- Coordinación de frontend, dominio, servicios, persistencia y contenedores dentro de un trabajo grupal.

Como evolución, sería útil ampliar las pruebas end-to-end con los servicios GPS activos, fortalecer los controles de acceso para un entorno real y preparar una demo pública con datos y claves exclusivamente ficticios. Estas son **mejoras propuestas**, no capacidades productivas verificadas.

---
[Volver al catálogo](../README.md)
