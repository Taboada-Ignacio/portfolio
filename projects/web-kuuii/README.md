# Web Kuuii
### Presencia comercial responsive con React

[Demostración](https://first-web-site-proyect-kuuii.pages.dev/) · [Código público](https://github.com/Taboada-Ignacio/first-web-site-proyect-Kuuii) · [Volver al portafolio](../../README.md)

## Objetivo

Sitio informativo para una distribuidora de agua y hielo de Comodoro Rivadavia. Presenta la oferta comercial y facilita el contacto directo por WhatsApp, con una interfaz adaptable a distintos tamaños de pantalla.

## Funcionalidades verificadas

- Presentación del negocio y tarjetas de productos.
- Navegación por secciones con desplazamiento suave y barra adaptable.
- Información de ubicación y mapa interactivo cargado al solicitarlo.
- Enlaces de contacto y acceso a WhatsApp.
- Metadatos de buscadores, URL canónica, Open Graph, sitemap y recursos de identidad visual.

## Stack y organización

React 19.2, JavaScript, Vite 7, Bootstrap 5.3, React Bootstrap, Bootstrap Icons y CSS. Las versiones provienen de las dependencias declaradas.

La aplicación compone navegación, presentación, productos, ubicación, pie de página y un componente flotante de contacto. Los estilos se organizan junto a componentes y secciones.

## Decisiones técnicas

**Mapa bajo demanda.** Una imagen inicial sustituye al iframe hasta que la persona pulsa el botón. Así se difiere la carga del recurso externo.

**Presentación responsive.** La grilla y los componentes Bootstrap se combinan con CSS propio. Las imágenes de productos y marca declaran dimensiones, y hay recursos WebP.

**Contenido y navegación claros.** Las secciones separan la propuesta comercial, los productos y el contacto. El desplazamiento considera el espacio ocupado por la navegación fija.

## Alcance y calidad

Es un frontend informativo: no implementa un backend propio, base de datos, autenticación ni procesamiento de pedidos. El contacto se deriva a canales externos.

El repositorio incluye scripts de desarrollo, build, preview y lint con ESLint. No se encontró una suite automatizada de tests en la estructura revisada; no se atribuyen métricas Lighthouse ni resultados de pruebas no ejecutadas.

## Demostración y material visual

La [demo pública](https://first-web-site-proyect-kuuii.pages.dev/) corresponde a la URL canónica del proyecto. Las capturas auténticas pendientes se describen en el [plan visual](../../assets/web-kuuii/README.md).

## Aprendizajes y mejoras propuestas

Composición por componentes, diseño responsive e integración controlada de servicios externos. Como próximos pasos: pruebas de navegación, revisión de accesibilidad y mediciones reproducibles de carga. Estas mejoras se presentan como propuestas.

---
[Volver al catálogo](../README.md)
