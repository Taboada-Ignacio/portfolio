# SYZA · Estética integral
### Identidad digital responsive para una marca de estética y bienestar

[Volver al portafolio](../../README.md) · [Catálogo de proyectos](../README.md)

## Contexto y objetivo

SYZA es una marca de estética integral impulsada por dos profesionales, Abigail Macedo y Dafne Vasconi. La landing presenta su identidad, filosofía, servicios y canales de consulta con una estética contemporánea y cálida. El nombre se inspira en *Sisa*, palabra de origen quechua vinculada a la belleza según el concepto de marca.

El objetivo de esta etapa es construir una presencia digital profesional, accesible y adaptable a teléfonos. El sitio no se presenta como una plataforma de reservas en línea.

## Mi participación

Desarrollo del frontend y de la experiencia visual, organización de secciones y componentes reutilizables, adaptación responsive, integración de recursos de identidad, animaciones e interacciones 3D. También se preparó el proyecto para un despliegue estático.

## Tecnologías

| Área | Tecnologías |
| --- | --- |
| Aplicación | React 19 · TypeScript · Vite |
| Estilos | Tailwind CSS v4 · tokens semánticos · Playfair Display e Inter |
| Animación | GSAP · @gsap/react |
| 3D | Three.js · React Three Fiber · Drei |
| Interfaz | Lucide React |
| Calidad y configuración | ESLint · Vitest · Testing Library · Zod |
| Despliegue previsto | Render Static Site |

Las tecnologías se basan en la configuración y documentación del repositorio. No se atribuyen métricas de rendimiento ni resultados de pruebas que no se hayan verificado expresamente.

## Alcance de la landing

- Presentación de la marca, su origen y filosofía de cuidado integral.
- Secciones de servicios y contenido comercial estructurado.
- Diseño mobile-first con navegación por anclas y transiciones.
- Uso de fotografía de tratamientos e imágenes WebP responsivas.
- Elementos visuales con animación GSAP y un motivo 3D procedural integrado con Three.js.
- Información configurable y recursos SEO, favicon y manifest para la presencia pública.

## Decisiones de implementación

**Separación entre contenido y presentación.** Textos, datos comerciales y metadatos se organizan en una configuración tipada y validada con Zod, lo que facilita actualizaciones sin modificar la composición de cada sección.

**Identidad visual consistente.** La paleta chocolate, cacao, arena, beige y marfil se implementa mediante tokens, junto con tipografías locales y una presentación editorial.

**Rendimiento y accesibilidad.** Las imágenes del Hero y las tarjetas emplean variantes WebP y encuadres responsivos; el componente 3D dispone de una alternativa estática y considera movimiento reducido y fallos de WebGL, según la implementación documentada.

**Despliegue estático.** La aplicación se compila con Vite y genera `dist/`, con configuración para Render. No requiere un backend para la presentación pública.

## Estado actual y próximos pasos

El alcance documentado corresponde a la landing pública. La autenticación con Google, el control de acceso, la persistencia individual en Drive y la gestión de turnos son una **etapa futura**; no se presentan como funcionalidades implementadas o disponibles en producción.

El repositorio de trabajo es privado. La URL pública de la demostración se añadirá al portafolio cuando esté confirmada y verificada.

Para el material visual se priorizan capturas auténticas del sitio y fotografías con autorización de uso, sin exponer información privada de pacientes o clientas.

---

[Volver al catálogo](../README.md)
