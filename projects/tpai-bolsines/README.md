# TPAI-Bolsines
### Seguimiento de bolsines con mapa interactivo e integración GPS

[Código público](https://github.com/Taboada-Ignacio/TPAI-Bolsines) · [Volver al portafolio](../../README.md)

## Resumen y contexto

Proyecto académico grupal del Trabajo Práctico de Aplicación de Diseño de Sistemas de Información (3.er año de Ingeniería en Sistemas de Información, UTN Facultad Regional Córdoba). Implementa, entre otros flujos, el **CU 36: Consultar seguimiento de bolsines**.

Un encargado de bolsines puede consultar los envíos en tránsito asociados a su comisión médica de origen, conocer su última posición GPS sobre un mapa y, si lo desea, notificar esa ubicación a la comisión médica de destino. El sistema integra una API GPS de la cátedra y servicios locales de persistencia y correo.

**Alcance:** prototipo académico ejecutable en entorno local. No se presenta como producto de rastreo en producción ni como un sistema de seguridad empresarial.

## Mi participación y trabajo en equipo

Participé en el diseño e implementación del flujo de seguimiento (CU 36), la aplicación del patrón Adapter para los modelos GPS y la integración de los datos de localización con la interfaz de mapa. La implementación se realizó en colaboración con el equipo del TPAI; el repositorio público contiene el trabajo compartido.

## Funcionalidades

- Inicio y cierre de sesión académico para acceder a las pantallas protegidas.
- Consulta de bolsines en estado **Enviado** cuyo origen corresponde a la comisión médica del empleado que inició sesión.
- Presentación de posiciones GPS y fecha de última actualización en un mapa interactivo.
- Selección de un bolsín para consultar su información, comisión de origen, ubicación y comisión de destino; filtros por precinto y destino.
- Consulta del proveedor GPS a través de una interfaz común y adaptadores concretos.
- Confirmación opcional de notificación al gerente de la comisión médica de destino mediante correo electrónico; Mailpit permite inspeccionar los envíos en desarrollo.
- CRUD y catálogos técnicos de usuarios/empleados, comisiones, roles, estados y bolsines para respaldar el flujo académico.

## Tecnologías utilizadas

| Área | Tecnologías |
| --- | --- |
| Aplicación web | Next.js 16 (App Router y Route Handlers) · React 19 · TypeScript estricto |
| Persistencia | PostgreSQL 17 · Prisma ORM 7 · @prisma/adapter-pg · migraciones y datos de ejemplo |
| Interfaz y cartografía | Tailwind CSS 4 · MapLibre GL JS · OpenFreeMap |
| Integraciones | API GPS oficial de la cátedra · servicios HTTP · Nodemailer · Mailpit |
| Calidad | Vitest · Zod · ESLint · Prettier |
| Entorno | Node.js 24 · Docker · Docker Compose |

Las versiones son las declaradas en el repositorio revisado; no implican una auditoría de los servicios en ejecución.

## Arquitectura y decisiones de diseño

El frontend y los endpoints HTTP conviven en Next.js. Los Route Handlers funcionan como controladores; los gestores implementan el caso de uso; el dominio representa bolsines, estados, empleados y comisiones médicas; Prisma encapsula el acceso a PostgreSQL. Los DTO y las validaciones delimitan los datos intercambiados.

**Patrón Adapter para GPS.** La frontera `InterfazGPSTracker` selecciona un adaptador concreto de acuerdo con el modelo. Se implementaron `AdaptadorXTR4500L`, `AdaptadorQX7A` y `AdaptadorMTR900`, cada uno conectado a su servicio de integración. Los formatos externos difieren (JSON, CSV y matriz), pero se normalizan a número de bolsín, latitud, longitud y fecha ISO 8601 UTC. El CU 36 principal utiliza el modelo **XTR-4500L** y los códigos de comisión médica de origen. La presencia de los otros adaptadores permite reutilizar la integración para otros flujos.

**Fuente de las ubicaciones.** La API GPS oficial de la cátedra entrega las coordenadas. **MapLibre GL JS** representa los marcadores e interacciones; **OpenFreeMap** aporta el mapa base. No se usa la API ni el SDK de Google Maps para renderizar la pantalla de seguimiento. Las clases con nombres heredados del UML relacionadas con Google Maps conservan esos nombres por trazabilidad del diseño académico.

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

El repositorio incluye pruebas con Vitest para dominio, autenticación, catálogos, Adapter GPS, seguimiento, notificación e integración de componentes. También proporciona comandos para validación Prisma, análisis de tipos TypeScript, lint, formato y compilación.

**Esta incorporación al portafolio se basa en la documentación y los archivos del repositorio. No se ejecutó nuevamente la suite de pruebas ni un despliegue de la aplicación como parte de esta actualización.** Las pruebas HTTP externas del GPS requieren configurar y levantar el entorno de desarrollo.

## Material visual

El [plan de capturas](../../assets/tpai-bolsines/README.md) identifica imágenes que pueden incorporarse del sistema con datos ficticios. No se atribuyen aquí capturas ni métricas visuales no verificadas.

## Aprendizajes y mejoras posibles

- Traducción de casos de uso y diagramas UML a responsabilidades y contratos TypeScript.
- Integración desacoplada de proveedores con formatos de respuesta heterogéneos.
- Diseño de un mapa que asocia el dato de negocio con una posición geográfica y su instante de actualización.
- Coordinación de frontend, dominio, servicios, persistencia y contenedores dentro de un trabajo grupal.

Como evolución, sería útil ampliar las pruebas end-to-end con los servicios GPS activos, fortalecer los controles de acceso para un entorno real y preparar una demo pública con datos y claves exclusivamente ficticios. Estas son **mejoras propuestas**, no capacidades productivas verificadas.

---
[Volver al catálogo](../README.md)
