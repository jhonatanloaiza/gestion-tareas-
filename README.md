# Taskly — Una Idea. Tres Estilos. Un Producto.

> **Comparativa visual, técnica y de rendimiento entre corrientes del diseño de interfaces web.**

##  Descripción General
**Taskly** es una aplicación web de gestión de tareas (Task Management App) desarrollada como el proyecto final para la evaluación de diseño de interfaces y arquitectura front-end de vanguardia. La premisa fundamental de este proyecto es demostrar que **el diseño es una capa de decisión completamente abstracta y separada de la funcionalidad y la lógica de negocio**.

El producto parte de una **arquitectura de software inmutable**: compartiendo estrictamente el mismo HTML5 semántico, la misma nomenclatura de clases bajo la metodología BEM, los mismos breakpoints responsive y la misma organización de componentes. La transformación radical de su carácter, estética, atmósfera y accesibilidad se logra de manera exclusiva mediante la redefinición de un archivo central de **Design Tokens** (CSS Custom Properties).

---

##  Arquitectura de Software y Estándares Base

La estructura común e inamovible de la aplicación se ha diseñado bajo los más estrictos estándares de la industria para garantizar un control experimental exacto entre variantes:

* **HTML5 Semántico Estricto:** Uso exclusivo de etiquetas estructurales nativas (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`, `<button>`) para garantizar una base accesible e indexable de forma óptima.
* **Metodología BEM (Block, Element, Modifier):** Nomenclatura modular y altamente predecible para todas las clases CSS (ej. `.task-card`, `.task-card__title`, `.task-card--completed`), evitando colisiones de especificidad.
***Atomic Design (Brad Frost):** Organización modular dividida en componentes reutilizables independientes:
    1.  `Navegación`: Barra con filtros cronológicos, contadores dinámicos y perfil de usuario.
    2.  `Tarjetas (Cards)`: Visualización atómica de tareas con título, descripción, tag de prioridad, fecha límite y checkbox de estado.
    3.  `Formulario`: Módulo de captura de datos con validaciones nativas para la creación de nuevas tareas.
    4.  `Footer`: Pie de página técnico con selector de entorno e información de versión.
  **Gestión de Ramas en Git:** Flujo de trabajo basado en una rama común (`main`) y tres ramas paralelas aisladas (`estilo-material`, `estilo-glass`, `estilo-clay-dark`) para encapsular las mutaciones de diseño sin contaminar la lógica de la aplicación.

---

## 🎨 Corrientes Visuales Implementadas (Design Systems)

### 1. Rama `estilo-material` — Material Design 3 (Grupo Clásico)
Inspirado por las directrices oficiales de diseño de **Google (M3)**. Representa la evolución del diseño plano hacia la física lógica del software, donde las sombras indican elevaciones reales y jerarquía.
* **Accesibilidad (WCAG 2.2):** Máximo cumplimiento (Ratio > 7:1 en textos principales), garantizando un contraste nítido y descansado para el usuario.

### 2. Rama `estilo-glass` — Glassmorfismo (Grupo Contemporáneo)
Corriente moderna basada en el efecto de vidrio esmerilado, popularizada por **Apple (macOS Big Sur)** y adaptada por **Microsoft en Windows 11 (Fluent Design)**.
* **Foco Técnico:** Uso extensivo de la propiedad avanzada `backdrop-filter: blur() saturate();` , superficies translúcidas con canales Alpha (`rgba()`), bordes milimétricos simulando la refracción del cristal y fondos con gradientes orgánicos vibrantes que se traslucen debajo de los componentes.
* **Desafío de Ingeniería:** Optimización del rendimiento ante el costo de renderizado gráfico por hardware en el navegador y calibración fina de contrastes para evitar barreras de accesibilidad.

### 3. Rama `estilo-clay-dark` — Claymorfismo Neo-Dark (Grupo Experimental)
Variante lúdica que rompe la severidad geométrica tradicional mediante un aspecto táctil, blando e inflado en 3D (Soft UI), fusionado nativamente con un **Modo Oscuro Adaptativo**.
* **Foco Técnico:** Respuesta automática al entorno del usuario mediante la media query `@media (prefers-color-scheme: dark)`. Estructuración de volumen 3D simulado en el navegador mediante la combinación matemática de múltiples sombras externas difusas y sombras internas (`box-shadow: inset ...`).
* **Foco Estético:** Bordes masivos y redondeados con acentos de color neón y luces internas coordinadas sobre un fondo oscuro calibrado para evitar la fatiga visual.

---

## 📊 Suite de Tokens CSS (API Abstracta)

Toda la atmósfera visual se altera modificando exclusivamente el diccionario de variables declarado en el ámbito global (`:root`). El archivo base abstrae las siguientes propiedades:

```css
:root {
  /* Tokens Semánticos de Color */
  --bg-application:       /* Fondo principal de la app */;
  --bg-surface:           /* Superficie de tarjetas y contenedores */;
  --bg-surface-variant:   /* Variación de fondo para inputs/headers */;
  --text-primary:         /* Texto de alto contraste para títulos */;
  --text-secondary:       /* Texto de contraste medio para descripciones */;
  --color-primary:        /* Color de marca principal */;
  --color-accent:         /* Color de énfasis para estados urgentes */;
  --border-color:         /* Tono base para separadores y bordes */;

  /* Tokens de Geometría y Espaciado */
  --radius-card:          /* Radio de redondeo para tarjetas */;
  --radius-button:        /* Radio de redondeo para botones */;
  --spacing-unit:         /* Multiplicador base para padding/margin */;

  /* Tokens de Profundidad y Efectos */
  --shadow-elevation-1:   /* Sombras proyectadas externas */;
  --shadow-inner-1:       /* Sombras internas para efectos táctiles */;
  --backdrop-blur:        /* Desenfoque para corrientes translúcidas */;
  --backdrop-saturate:    /* Saturación de fondo para efectos de cristal */;
  --transition-speed:     /* Constante de tiempo para micro-interacciones */;
}
