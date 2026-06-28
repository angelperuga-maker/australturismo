# Handoff: Austral Lacustre — Landing de turismo de lujo (Valdivia / zona lacustre)

## Overview
Landing page de una sola página (long-scroll) para un servicio de turismo de lujo en el sur de Chile (Valdivia y la región de los Siete Lagos). Objetivo triple: **inspirar** mostrando destinos, **generar reservas/consultas** y **presentar colecciones con precios**. Público objetivo: viajero internacional de alto poder adquisitivo, turismo nacional premium, familias acomodadas, parejas/luna de miel y aventura exclusiva (pesca y ski privados). Idioma: español.

## About the Design Files
El archivo de este paquete (`Austral Lacustre.dc.html`) es una **referencia de diseño creada en HTML** — un prototipo que muestra el look & feel y el comportamiento previstos, **no código de producción para copiar tal cual**. La tarea es **recrear este diseño en el entorno del codebase destino** (React, Next.js, Vue, Astro, etc.) usando sus patrones y librerías establecidas. Si no existe un entorno aún, elige el framework más apropiado (recomendado: Next.js + React, o Astro para una landing estática) e impleméntalo allí.

Nota técnica: el `.dc.html` usa un runtime propietario ("Design Components"). **No** intentes reutilizar ese runtime; toma de él el markup, los estilos inline, el contenido y la lógica descrita abajo, y reescríbelo en componentes nativos del codebase.

## Fidelity
**Alta fidelidad (hifi).** Colores, tipografía, espaciados e interacciones son finales. Recrear pixel-perfect con la librería/sistema del codebase. Las imágenes son **placeholders** (fondos de rayas con etiqueta monoespaciada) y deben reemplazarse por fotografía real; las posiciones, ratios y overlays sí son definitivos.

## Layout general
- Página única, scroll vertical, `scroll-behavior:smooth`, anclas internas (`#destinos`, `#experiencias`, `#lodges`, `#paquetes`, `#reserva`).
- Ancho de contenido máximo: secciones de contenido `max-width:1320px` (lodges/destinos), texto editorial `max-width:1080px`, centrados con `margin:0 auto`.
- Padding horizontal de sección estándar: `48px`. Padding vertical de sección: `110–120px`.
- Fondo base de página: `#f4f0e9` (papel greige). Secciones alternan con `#1b2a31` (pizarra oscura) y `#ece6db` (greige más cálido).

## Screens / Views (secciones, en orden)

### 1. Nav (fixed)
- `position:fixed; top/left/right:0; z-index:50`. `padding:18px 48px`. Fondo `rgba(244,240,233,.82)` con `backdrop-filter:blur(14px)`, borde inferior `1px solid rgba(36,54,66,.10)`. `display:flex; justify-content:space-between; align-items:center`.
- Izquierda (logo, columna): "Austral Lacustre" en Cormorant Garamond 26px/500, color `#243642`; debajo "Valdivia · Sur de Chile" en Spline Sans Mono 9px, `letter-spacing:.34em`, uppercase, color acento `#a07d54`.
- Derecha: links "Destinos, Experiencias, Lodges, Colecciones" (13px, `letter-spacing:.04em`, color `#3d4f5a`, gap 34px) + botón "Reservar": `padding:11px 22px`, borde `1px solid #a07d54`, texto 11px/600 uppercase `letter-spacing:.12em`; hover → fondo `#a07d54`, texto `#f4f0e9`, `transition:all .3s`.

### 2. Hero (`#top`)
- `position:relative; height:100vh; min-height:680px; overflow:hidden; display:flex; align-items:flex-end`.
- Capa imagen (placeholder): `repeating-linear-gradient(125deg,#c9c3b4 0 3px,#d4cdbd 3px 22px)`, animación `slowzoom` (scale 1 → 1.08 en 24s ease-out forwards). → reemplazar por foto "amanecer sobre lago Panguipulli".
- Overlay de oscurecimiento (gradiente vertical) cuya opacidad escala con la variable `--ov` (default 0.45): `linear-gradient(180deg, rgba(20,30,38,calc(var(--ov)*.6)) 0%, rgba(20,30,38,0) 28%, rgba(18,26,32,calc(var(--ov)*.55)) 62%, rgba(15,22,28,calc(var(--ov)*1.5)) 100%)`.
- Contenido (`z-index:2; padding:0 48px 72px; max-width:1080px; animation:fadeup 1.1s ease-out`):
  - Eyebrow: "Colección de viajes privados", Spline Sans Mono 11px `letter-spacing:.32em` uppercase, color `#e7c98a`.
  - H1: Cormorant Garamond, weight 300, `clamp(52px,7vw,108px)`, `line-height:.96`, color `#f6f2ea`. Dos líneas; la 2ª en itálica color `#efe2c8`: "El sur de Chile, / *a orillas del agua.*"
  - Párrafo: `max-width:540px`, 18px, `line-height:1.6`, `rgba(244,240,233,.86)`, weight 300.
  - Dos CTAs (gap 18px): primario fondo `#a07d54` texto `#f7f3ec` (hover `#8c6b46`); secundario borde `rgba(244,240,233,.55)` texto `#f4f0e9`. Ambos `padding:16px 30px`, 12px/600 uppercase `letter-spacing:.14em`.

### 3. Intro / statement
- `padding:120px 48px; max-width:1080px; margin:auto; text-align:center`.
- Eyebrow "La región de los Siete Lagos" (mono, acento). Párrafo grande Cormorant Garamond weight 300 `clamp(28px,3.6vw,46px)` `line-height:1.32` color `#2b3d48`, `text-wrap:balance`.
- Fila de 3 stats (gap 60px): número en Cormorant Garamond 46px color acento + label 12px uppercase `letter-spacing:.14em` color `#6b7680`. Valores: **7** Lagos cordilleranos · **24/7** Concierge dedicado · **100%** Itinerarios privados.

### 4. Destinos / Los lagos (`#destinos`)
- `padding:30px 48px 110px; max-width:1320px`. Encabezado con borde superior `1px solid rgba(36,54,66,.16)`: H2 "Los lagos" (Cormorant Garamond 300, `clamp(34px,4.4vw,60px)`) + lista mono a la derecha "Calafquén · Panguipulli · Riñihue · Ranco · Pirihueico".
- **Grid superior** `grid-template-columns:1.4fr 1fr; gap:22px`:
  - Tarjeta feature (Calafquén), `min-height:460px`, imagen placeholder + overlay inferior + eyebrow "Aguas turquesa" + H3 40px + descripción.
  - Columna derecha: 2 tarjetas apiladas (`grid-template-rows:1fr 1fr; gap:22px`, cada una `min-height:219px`): Panguipulli, Riñihue.
- **Grid inferior** `repeat(3,1fr); gap:22px; margin-top:22px`, cada tarjeta `min-height:240px`: Ranco, Pirihueico, Río Valdivia.
- Patrón de tarjeta de lago: `position:relative; overflow:hidden; display:flex; align-items:flex-end`; capa placeholder con su `repeating-linear-gradient` (tonos grises levemente distintos por tarjeta), overlay `linear-gradient(180deg,rgba(20,30,38,0) ~45-50%,rgba(18,28,34,.68-.72) 100%)`, etiqueta mono de foto arriba-izquierda, y texto abajo (H3 Cormorant Garamond color `#f6f2ea` + descripción `rgba(244,240,233,.8)` 13px). Toda la tarjeta es `<a href="#reserva">`. Hover en la feature: la capa imagen hace `scale(1.04)`.

  Copys: Calafquén "Playas de arena volcánica y termas a pocos minutos. El corazón termal de la región." · Panguipulli "La puerta a los Siete Lagos y al volcán Mocho-Choshuenco." · Riñihue "Silencio absoluto y el nacimiento del río San Pedro." · Ranco "Islas privadas y casonas patrimoniales frente al agua." · Pirihueico "Bosque virgen y el cruce de lagos hacia Argentina." · Río Valdivia "Navegación, humedales y la ciudad fluvial del sur."

### 5. Experiencias (`#experiencias`) — sección oscura
- Fondo `#1b2a31`, `padding:110px 48px`, interior `max-width:1320px`.
- Encabezado: eyebrow "Cada día, una experiencia" (mono, `#e7c98a`) + H2 "Las experiencias" (`#f4f0e9`) y párrafo de apoyo a la derecha (`rgba(244,240,233,.7)`).
- **Grid de 8 celdas** `grid-template-columns:repeat(4,1fr); gap:1px` sobre fondo `rgba(244,240,233,.12)` con borde igual (efecto líneas hairline). Cada celda: fondo `#1b2a31` (hover `#21333b`), `padding:34px 28px; min-height:280px; flex column; justify-content:space-between`. Número de orden en mono color acento arriba; abajo H3 Cormorant Garamond 28px/400 `#f4f0e9` + descripción 13.5px `rgba(244,240,233,.68)`.
  1. **Pesca con mosca** — "Ríos San Pedro y Enco, truchas fario y arcoíris. Guías de catch & release y lanchas dedicadas."
  2. **Navegación privada** — "Embarcaciones con capitán, picnic a bordo y fondeo en calas que solo se alcanzan por agua."
  3. **Cabalgatas** — "Travesías a caballo por la selva valdiviana con baqueanos locales y almuerzo de campo."
  4. **Trekking & volcán** — "Senderos del Parque Mocho-Choshuenco y bosques de alerces con guía de montaña."
  5. **Termas & spa** — "Termas de Liquiñe y Coñaripe en jornadas privadas, masajes y rituales de bosque."
  6. **Ski Mocho-Choshuenco** — "Nieve de volcán con vistas al lago. Ascensos guiados y descensos fuera de pista en temporada."
  7. **Gastronomía & vinos** — "Mesas de autor, mariscos del sur y cavas de vinos chilenos guiadas por sommelier."
  8. **Bienestar en familia** — "Jornadas a medida para niños y adultos: kayak suave, fogatas y observación de aves."

### 6. Lodges / Casas orilla de lago (`#lodges`)
- `padding:120px 48px; max-width:1320px`. Grid `1fr 1fr; gap:64px; align-items:center`.
- Izquierda: imagen placeholder vertical `min-height:560px` con etiqueta "casa con muelle privado, orilla del lago".
- Derecha: eyebrow "Alojamiento" + H2 "Casas frente al agua, / muelle propio." (Cormorant Garamond 300) + párrafo. Luego lista de 4 filas con borde superior `1px solid rgba(36,54,66,.15)` (`display:flex; justify-content:space-between; padding:18px 0`): texto 15px `#243642` + valor mono 12px acento.
  - "Muelle privado y embarcación" → incluido
  - "Chef y mayordomo" → incluido
  - "Concierge 24/7 y traslados" → incluido
  - "Spa y termas a domicilio" → a pedido (última fila con borde inferior también)

### 7. Paquetes / Colecciones (`#paquetes`) — condicional `showPrices`
- Fondo `#ece6db`, `padding:110px 48px`, interior `max-width:1320px`. Esta sección entera se oculta si el flag `showPrices` es false.
- Encabezado centrado: eyebrow "Colecciones", H2 "Itinerarios curados", subtítulo "Valores referenciales por persona, base doble · 5 noches · todo incluido." (12-14px `#6b7680`).
- **3 tarjetas** `repeat(3,1fr); gap:26px`:
  - **Lago & Bosque** (Esencial): fondo `#f6f2ea`, borde `1px solid rgba(36,54,66,.12)`, `padding:40px 34px`, flex column. Precio "USD 4.200" en Cormorant Garamond 46px + "/ persona". CTA outline acento (hover relleno acento, texto papel). Copy: "Casa frente al lago, navegación privada, cabalgata y una jornada de termas. La introducción perfecta a la región."
  - **Siete Lagos** (Firma, destacada): fondo `#1b2a31`, `transform:translateY(-12px)`, `box-shadow:0 30px 60px -30px rgba(20,30,38,.6)`. Badge "Más elegida" arriba-derecha (fondo `#e7c98a`, texto `#1b2a31`, mono 9px). Texto claro. Precio "USD 7.900". CTA relleno acento. Copy: "Recorrido entre tres lagos, pesca con mosca guiada, trekking al volcán, cena de autor con maridaje y spa privado."
  - **Cumbre & Nieve** (Privé): igual que la 1ª. Precio "USD 12.500". Copy: "Residencia exclusiva, ski guiado en el Mocho-Choshuenco, heli-experiencia opcional y servicio totalmente a medida."
- Nota al pie centrada (mono 12px `#8a8170`): "Cada itinerario se diseña a medida. Temporadas de ski y pesca sujetas a disponibilidad."

### 8. Reserva (`#reserva`) — sección oscura con form
- `position:relative; padding:120px 48px; overflow:hidden`. Fondo placeholder `repeating-linear-gradient(125deg,#2a3b43 0 3px,#2f424b 3px 24px)` + overlay `linear-gradient(120deg,rgba(20,30,38,.85),rgba(20,30,38,.55))` (foto "atardecer en el muelle").
- Interior `max-width:1080px`, grid `1fr 1fr; gap:64px; align-items:center`.
- Izquierda: eyebrow "Reservas & consultas" (`#e7c98a`), H2 "Diseñemos su viaje al sur." (`#f6f2ea`), párrafo, y bloque de contacto mono (`rgba(244,240,233,.7)`): "reservas@australlacustre.cl", "+56 9 0000 0000", "Valdivia · Los Ríos · Chile".
- Derecha: **formulario** sobre `rgba(244,240,233,.97)`, `padding:38px 34px`, flex column gap 16px. Campos: Nombre + Apellido (grid 1fr 1fr, required), Email (required), Select "Experiencia de interés…" (opciones: Lago & Bosque, Siete Lagos, Cumbre & Nieve, Pesca con mosca, A medida), Textarea "Fechas y número de viajeros" (rows 3). Inputs: `padding:13px 14px; border:1px solid rgba(36,54,66,.2); background:transparent; font-size:14px; color:#243642`. Botón submit relleno acento, texto papel, 12px/600 uppercase `letter-spacing:.14em` (hover `#8c6b46`).
- **Comportamiento**: al enviar (`onSubmit`, `preventDefault`) se cambia el estado `sent` a true y el formulario se reemplaza por una tarjeta de agradecimiento (mismo fondo): título "Gracias" (Cormorant Garamond 40px acento) + mensaje "Hemos recibido su solicitud. Un asesor le escribirá muy pronto para comenzar a planear su estadía." En producción, conectar a un endpoint real / email / CRM.

### 9. Footer
- Fondo `#141f24`, `padding:64px 48px 40px`. Fila superior (`max-width:1320px`, `justify-content:space-between`, borde inferior `1px solid rgba(244,240,233,.12)`): marca "Austral Lacustre" (Cormorant Garamond 30px/500 `#f4f0e9`) + sublínea mono acento; a la derecha dos columnas de links (Explorar / Contacto) con encabezado mono 10px `letter-spacing:.2em`.
- Fila inferior mono 11px `rgba(244,240,233,.4)`: "© 2026 Austral Lacustre. Todos los derechos reservados." y "Valdivia · Panguipulli · Lago Ranco".

## Interactions & Behavior
- Navegación por anclas con scroll suave (`html{scroll-behavior:smooth}`). Todos los CTAs de tarjetas apuntan a `#reserva`; los del hero a `#paquetes` y `#experiencias`.
- Hover: botón nav/CTA (relleno↔outline), tarjetas de experiencia (cambio de fondo `#1b2a31`→`#21333b`), feature de lago (zoom `scale(1.04)` de la imagen), links del footer (color → `#f4f0e9`).
- Animaciones de entrada del hero: `fadeup` (opacity 0→1, translateY 18px→0, 1.1s) en el bloque de texto; `slowzoom` (scale 1→1.08, 24s) en la imagen de fondo.
- Formulario: validación nativa HTML (`required`, `type=email`) + estado de éxito en cliente. Sin backend en el prototipo.

## State Management
- `sent: boolean` — controla mostrar el formulario vs. la tarjeta "Gracias". Trigger: submit del form.
- Props configurables (en el prototipo son "tweaks"; en el codebase pueden ser props del componente o variables de tema):
  - `accent` (color, default `#a07d54`; alternativas `#9c7a48`, `#b08d4f`, `#3d5a6c`) — color de acento global, aplicado vía variable CSS `--accent`.
  - `heroOverlay` (number 0.15–0.8, default 0.45) — intensidad del overlay del hero, vía variable CSS `--ov`.
  - `showPrices` (boolean, default true) — muestra/oculta la sección de Paquetes.

## Design Tokens
**Colores**
- Papel base: `#f4f0e9` · Papel alt cálido: `#ece6db` · Papel tarjeta: `#f6f2ea`
- Pizarra oscura (secciones): `#1b2a31` · hover celda: `#21333b` · Footer: `#141f24`
- Tinta/azul pizarra (texto): `#243642` · `#2b3d48` · `#3d4f5a` · `#4a5a64`
- Texto mutado: `#6b7680` · `#5a6770` · `#8a8170`
- Acento bronce (default): `#a07d54` · hover acento: `#8c6b46`
- Dorado claro (eyebrows sobre oscuro): `#e7c98a` · itálica hero: `#efe2c8`
- Texto sobre oscuro: `#f6f2ea` / `#f4f0e9`; con alfa `rgba(244,240,233, .4–.86)`
- Líneas: `rgba(36,54,66,.10–.20)` (sobre claro), `rgba(244,240,233,.12)` (sobre oscuro)

**Tipografía**
- Display/serif: **Cormorant Garamond** (300/400/500; itálicas 300/400). Titulares y precios.
- Sans/UI: **Hanken Grotesk** (300/400/500/600/700). Cuerpo, nav, botones, inputs.
- Mono: **Spline Sans Mono** (400/500). Eyebrows, etiquetas de foto, datos de contacto, pies.
- Escalas clave: H1 `clamp(52px,7vw,108px)`/300; H2 sección `clamp(34px,4.4vw,60px)`/300; statement `clamp(28px,3.6vw,46px)`/300; H3 tarjeta 28–40px/400; cuerpo 14–18px/300–400; eyebrow mono 9–11px uppercase `letter-spacing:.18–.34em`.

**Espaciado**: padding de sección `110–120px` vertical / `48px` horizontal; gaps de grid `22px` (tarjetas), `26px` (paquetes), `64px` (dos columnas); padding de tarjeta `34–40px`.

**Otros**: sin border-radius (estética rectilínea, lujo sobrio) salvo el redondeo nulo intencional. Sombra única usada: `0 30px 60px -30px rgba(20,30,38,.6)` (tarjeta destacada). Transiciones `.3s`.

## Assets
- **Imágenes**: TODAS son placeholders (fondos `repeating-linear-gradient` con etiqueta mono). Reemplazar por fotografía real en estas ubicaciones: hero (amanecer lago Panguipulli), 6 lagos, casa con muelle privado, atardecer en el muelle (sección reserva). Ratios y overlays definidos arriba.
- **Iconos**: no se usan iconos; el diseño es puramente tipográfico. Si el codebase requiere iconos, mantener un set lineal fino y discreto.
- **Fuentes**: Google Fonts (Cormorant Garamond, Hanken Grotesk, Spline Sans Mono). Cargar vía `next/font`, `@fontsource` o `<link>` según el stack.

## Datos a confirmar antes de producción
- Email/teléfono/dirección reales (actualmente placeholders: `reservas@australlacustre.cl`, `+56 9 0000 0000`).
- Precios reales de las colecciones (actualmente referenciales: USD 4.200 / 7.900 / 12.500).
- Endpoint/integración del formulario (email, CRM, etc.).
- Nombre de marca definitivo ("Austral Lacustre" es propuesto).

## Files
- `Austral Lacustre.dc.html` — prototipo de alta fidelidad de la landing completa (incluido en este paquete). El markup está con estilos inline; los colores/medidas/copys de este README son la fuente de verdad.
