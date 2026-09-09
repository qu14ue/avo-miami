# Avo Miami — Homepage SEO / GEO / AEO
## Listado de tareas de implementación

**Archivo objetivo:** `webflow-build/index.html`
**Destino final:** importación a Webflow
**Regla general:** no tocar CSS ni la lógica de los carruseles salvo donde se indique explícitamente. Todos los cambios son de contenido, marcado semántico y `<head>`.

**Datos que faltan y deben pedirse al cliente antes de cerrar** (marcados como `[[PENDIENTE: ...]]` en las tareas):
teléfonos por sede, ZIP codes, horarios reales por sede, URLs de Google Business Profile, handles reales de redes, URL del sistema de pedidos, URL de la app (App Store / Google Play), URLs de delivery partners.
Donde falte el dato, dejar el placeholder literal `[[PENDIENTE: xxx]]` en el HTML como comentario, NO inventarlo.

---

## BLOQUE A — `<head>` y metadatos

### A1. Reemplazar el `<title>`
Actual:
```html
<title>Avo Miami — Meet Miami's Cleanest Menu (Webflow build — Sección 1: Nav + Hero)</title>
```
Nuevo:
```html
<title>Avo Miami | Healthy Restaurant in Miami Beach, Coconut Grove & South Miami</title>
```

### A2. Reemplazar la meta description
Actual:
```html
<meta name="description" content="Whole food meals, made fresh to order in our open kitchens to nourish body and soul. Seed oil free, dietitian-designed, protein-packed.">
```
Nuevo (155 chars aprox.):
```html
<meta name="description" content="Seed oil free, dietitian-designed whole food meals made to order. Three Avo locations in Miami Beach, Coconut Grove and South Miami. Order online or pick up.">
```

### A3. Agregar canonical
Insertar después de la meta description:
```html
<link rel="canonical" href="https://avo-miami.com/">
```

### A4. Agregar Open Graph + Twitter Card
Insertar a continuación del canonical:
```html
<meta property="og:type" content="website">
<meta property="og:site_name" content="Avo Miami">
<meta property="og:url" content="https://avo-miami.com/">
<meta property="og:title" content="Avo Miami | Healthy Restaurant in Miami">
<meta property="og:description" content="Seed oil free, dietitian-designed whole food meals made to order. Three locations across Miami.">
<meta property="og:image" content="https://avo-miami.com/img/heros/hero-img.webp">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:locale" content="en_US">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Avo Miami | Healthy Restaurant in Miami">
<meta name="twitter:description" content="Seed oil free, dietitian-designed whole food meals made to order. Three locations across Miami.">
<meta name="twitter:image" content="https://avo-miami.com/img/heros/hero-img.webp">
```
> Nota: la imagen OG debe ser 1200x630. Si `hero-img.webp` no tiene esa proporción, crear `img/og/og-avo-miami.jpg` y apuntar ahí. Dejar comentario si se generó pendiente.

### A5. Agregar `theme-color` y robots explícito
```html
<meta name="robots" content="index,follow,max-image-preview:large,max-snippet:-1">
<meta name="theme-color" content="#4F5E4A">
```

---

## BLOQUE B — Corrección de typos y textos

### B1. Hero — corregir claim
En `.hero-checks`, cambiar `Dietitian-Design` → `Dietitian-Designed`.

### B2. Classics intro — corregir ortografía y reescribir
Actual:
```html
<p class="classics-intro">We are commited to bring the cleanest ingredients as grass-fed meats, wild-caught fish, cooking with olive oil only. <strong>Just how we will make it for our family!</strong></p>
```
Nuevo:
```html
<p class="classics-intro">We are committed to bringing you the cleanest ingredients — grass-fed meats, wild-caught fish and olive oil only, never seed oils. <strong>Just how we'd make it for our own family.</strong></p>
```

### B3. Footer — corregir horario
Actual: `<p>Open from 7am to 22pm</p>`
Nuevo: `<p>Open daily 7:00 AM – 10:00 PM</p>` — **verificar con `[[PENDIENTE: horarios reales por sede]]`**. Si difieren entre sedes, mover el horario dentro de cada `.footer-place`.

### B4. Alt del hero
Actual: `alt="Fresh bowls styled tablescape at Avo Miami"`
Nuevo: `alt="Seed oil free bowls and fresh dishes served at Avo Miami"`

### B5. Alts de las tarjetas de producto
Las 5 tarjetas `.p-card` usan la MISMA imagen (`img/heros/hero-img.webp`) con alts distintos → alt engañoso.
- Si existen fotos reales por plato, reemplazar cada `src`.
- Si NO existen, dejar el `src` y cambiar todos los alts a `alt=""` + agregar comentario HTML `<!-- [[PENDIENTE: foto real de <nombre del plato>]] -->` encima de cada `<img>`.
- Cuando lleguen las fotos, el alt debe ser descriptivo: `alt="Protein breakfast bowl with poached free-range eggs and avocado at Avo Miami"`.

---

## BLOQUE C — Nuevo contenido (AEO)

### C1. Párrafo de entidad
Insertar **al inicio de la sección `#classics`**, dentro del `.container`, ANTES de `.classics-intro`, un párrafo nuevo:
```html
<p class="entity-line">Avo Miami is a whole-food restaurant with three locations in Miami Beach, Coconut Grove and South Miami, serving seed-oil-free, dietitian-designed meals made fresh to order in open kitchens.</p>
```
CSS a agregar en el bloque `#classics`:
```css
.entity-line{font-size:16px;line-height:1.6;color:var(--crema);opacity:.9;max-width:760px;margin-bottom:20px;}
@media (min-width:1024px){.entity-line{font-size:17px;}}
```

### C2. Nueva sección FAQ
Insertar una sección **entre `#join-app` y `#cta-band`**, con `id="faq"`, fondo `var(--crema)`, un `<h2>Frequently asked questions</h2>` y 8 pares pregunta/respuesta usando `<details>`/`<summary>` (accesible y nativo, se importa bien a Webflow).

Contenido exacto de las 8 FAQ (respuestas autocontenidas, cada una debe poder citarse sola):

1. **Is Avo Miami seed oil free?** — Yes. Every dish at Avo Miami is cooked with olive oil only. We never use canola, sunflower, soybean or other seed oils, in any preparation.
2. **Where is Avo Miami located?** — Avo Miami has three locations: Miami Beach (1834 Bay Rd), Coconut Grove (2911 Grand Ave #400D) and South Miami (5958 S Dixie Hwy).
3. **What are Avo Miami's opening hours?** — `[[PENDIENTE: horarios reales]]`
4. **Does Avo Miami deliver?** — `[[PENDIENTE: confirmar delivery propio y/o partners: Uber Eats, DoorDash]]`
5. **Are the nutrition facts available?** — Yes. Calories and protein are listed for every menu item, and our menu is designed with a registered dietitian to keep a balanced macronutrient profile.
6. **Does Avo Miami have gluten-free or vegan options?** — `[[PENDIENTE: confirmar con el cliente]]`
7. **Does Avo Miami offer catering?** — `[[PENDIENTE: confirmar alcance, mínimos y zona de cobertura]]`
8. **How does the Avo rewards program work?** — Order through the Avo app and earn 1 point for every $1 spent. New members get 50 welcome points and free delivery on their first order.

> Importante: las respuestas con `[[PENDIENTE]]` NO deben publicarse con texto inventado. Dejarlas comentadas o con el placeholder visible hasta tener el dato.

### C3. Bloque "Why seed oil free?"
Agregar dentro de la sección `#classics`, debajo de `.classics-aside`, o como bloque propio antes de "What's new": un párrafo corto (60-90 palabras) explicando el diferencial + link `<a href="/blog/why-seed-oil-free">Read more</a>`.
`[[PENDIENTE: confirmar si va a existir el blog. Si no, dejar el párrafo sin link.]]`

### C4. Sección Locations real
Actualmente `id="locations"` está colgado de una columna del footer — todos los CTA "Find Nearest Avo" aterrizan ahí. Crear una **sección propia** `<section id="locations">` antes del `#cta-band`, y **quitar el `id="locations"` del `div.footer-col`**.

Cada una de las 3 sedes debe incluir:
- `<h3>` con el nombre de la sede
- dirección completa con ciudad, estado y ZIP `[[PENDIENTE: ZIPs]]`
- teléfono con `<a href="tel:...">` `[[PENDIENTE: teléfonos]]`
- horarios `[[PENDIENTE]]`
- link "Get directions" a Google Maps `[[PENDIENTE: URL de GBP/Maps por sede]]`
- CTA "Order from this location" `[[PENDIENTE: URL]]`

Marcado semántico sugerido por sede: `<address>` con microdatos o simplemente HTML limpio (el JSON-LD del bloque D cubre lo estructurado).

### C5. Bloque de prueba social
Agregar un bloque de reseñas/testimonios reales.
`[[PENDIENTE: reseñas reales de Google. NO usar AggregateRating en JSON-LD con reseñas auto-declaradas o inventadas — Google lo penaliza.]]`
Si no hay reseñas disponibles, dejar la sección fuera y anotarlo como tarea abierta.

---

## BLOQUE D — Datos estructurados (JSON-LD)

Agregar **al final del `<head>`** (o justo antes de `</body>`) los siguientes bloques. En Webflow van en *Page Settings → Custom Code → Head*.

### D1. Organization + WebSite
```html
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@graph":[
    {
      "@type":"Organization",
      "@id":"https://avo-miami.com/#organization",
      "name":"Avo Miami",
      "url":"https://avo-miami.com/",
      "logo":"https://avo-miami.com/img/logos/logo-verde-2026.svg",
      "sameAs":[
        "https://www.instagram.com/[[PENDIENTE]]",
        "https://www.tiktok.com/@[[PENDIENTE]]",
        "https://www.facebook.com/[[PENDIENTE]]"
      ]
    },
    {
      "@type":"WebSite",
      "@id":"https://avo-miami.com/#website",
      "url":"https://avo-miami.com/",
      "name":"Avo Miami",
      "publisher":{"@id":"https://avo-miami.com/#organization"},
      "inLanguage":"en-US"
    }
  ]
}
</script>
```

### D2. Restaurant — un bloque por sede (3 en total)
Plantilla (repetir 3 veces cambiando los datos):
```html
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"Restaurant",
  "@id":"https://avo-miami.com/#miami-beach",
  "name":"Avo Miami — Miami Beach",
  "parentOrganization":{"@id":"https://avo-miami.com/#organization"},
  "url":"https://avo-miami.com/",
  "image":"https://avo-miami.com/img/heros/hero-img.webp",
  "servesCuisine":["Healthy","Bowls","Breakfast","Mediterranean"],
  "priceRange":"$$",
  "telephone":"[[PENDIENTE]]",
  "address":{
    "@type":"PostalAddress",
    "streetAddress":"1834 Bay Rd",
    "addressLocality":"Miami Beach",
    "addressRegion":"FL",
    "postalCode":"[[PENDIENTE]]",
    "addressCountry":"US"
  },
  "geo":{"@type":"GeoCoordinates","latitude":"[[PENDIENTE]]","longitude":"[[PENDIENTE]]"},
  "openingHoursSpecification":[{
    "@type":"OpeningHoursSpecification",
    "dayOfWeek":["Monday","Tuesday","Wednesday","Thursday","Friday","Saturday","Sunday"],
    "opens":"07:00","closes":"22:00"
  }],
  "hasMenu":{"@id":"https://avo-miami.com/#menu"},
  "acceptsReservations":"[[PENDIENTE: True/False]]",
  "sameAs":["[[PENDIENTE: URL Google Business Profile]]"],
  "potentialAction":{
    "@type":"OrderAction",
    "target":{"@type":"EntryPoint","urlTemplate":"[[PENDIENTE: URL de pedidos]]"},
    "deliveryMethod":["http://purl.org/goodrelations/v1#DeliveryModePickUp","http://purl.org/goodrelations/v1#DeliveryModeOwnFleet"]
  }
}
</script>
```
Repetir para:
- **Coconut Grove** — 2911 Grand Ave #400D, Miami, FL. Ojo: en el HTML actual dice "Grande Ave" → **verificar, lo correcto es "Grand Ave"**.
- **South Miami** — 5958 S Dixie Hwy, South Miami, FL.

### D3. Menu + MenuItem
Un solo bloque con los 5 platos del carrusel + los 3 ítems de "What's new". Usar los datos ya presentes en el HTML:

| Ítem | kcal | Proteína | Precio |
|---|---|---|---|
| Protein breakfast bowl | 620 | 38g | 16 |
| Beet Salad | 410 | 14g | 14 |
| Avo Signature Bowl | 720 | 46g | 19 |
| Wild Salmon Plate | 580 | 42g | 21 |
| Green Power Bowl | 520 | 40g | 17 |
| Melon Matcha / Blue Coco Açaí / Pitaya Sunrise | — | — | `[[PENDIENTE: precios]]` |

Plantilla por ítem:
```json
{
  "@type":"MenuItem",
  "name":"Protein breakfast bowl",
  "description":"Slow-roasted sweet potato, poached free-range eggs, avocado and feta over greens.",
  "offers":{"@type":"Offer","price":"16.00","priceCurrency":"USD"},
  "nutrition":{"@type":"NutritionInformation","calories":"620 calories","proteinContent":"38 g"},
  "suitableForDiet":"[[PENDIENTE si aplica: https://schema.org/GlutenFreeDiet etc.]]"
}
```
Agruparlos en `Menu` → `hasMenuSection` (por ejemplo "Menu Classics" y "What's New") con `@id":"https://avo-miami.com/#menu"`.

### D4. FAQPage
Generar el JSON-LD `FAQPage` con **exactamente** las preguntas y respuestas de la tarea C2, una vez resueltos los `[[PENDIENTE]]`. **No incluir en el schema ninguna FAQ cuya respuesta siga con placeholder.**

### D5. Validación
Tras implementar, validar los bloques en el Rich Results Test de Google y en el validador de Schema.org. Corregir errores antes de dar por cerrada la tarea.

---

## BLOQUE E — Marcado semántico y accesibilidad

### E1. Jerarquía de encabezados
Verificar tras los cambios que quede: un solo `<h1>` (hero) → `<h2>` por sección (Classics, What's new, Join app, FAQ, Locations, CTA band) → `<h3>` en tarjetas y columnas del footer. Hoy `.classics-musts` ("Our MUST'S") y `.joinapp-copy .eyebrow` son divs — está bien, **no convertirlos en headings**, pero confirmar que ninguna sección quede sin su `<h2>`.

### E2. Metadatos de producto legibles
En `.p-card-meta` los valores están sueltos (`620 kcal`, `38g protein`, `$16`). Envolverlos para que sean autoexplicativos fuera de contexto, por ejemplo:
```html
<span><span class="visually-hidden">Calories: </span>620 kcal</span>
```
Agregar la clase utilitaria:
```css
.visually-hidden{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap;border:0;}
```

### E3. `<address>` en el footer
Envolver cada `.footer-place` en `<address>` y quitar el `text-transform:uppercase` del teléfono si se agrega (los números leídos por lectores de pantalla no deben depender del CSS).

---

## BLOQUE F — Performance y assets (impacto SEO)

### F1. Lazy loading + dimensiones
- Hero (`img/heros/hero-img.webp`): agregar `fetchpriority="high"` y `width`/`height` reales. **NO** ponerle `loading="lazy"`.
- Todas las demás `<img>` (tarjetas de producto, what's new, app, logos del footer): agregar `loading="lazy"` `decoding="async"` + `width` y `height` reales para evitar CLS.
- Los dos SVG decorativos (`avo-shape.svg`) ya tienen `alt=""` y `aria-hidden` — correcto, dejarlos así y agregarles `loading="lazy"`.

### F2. Video
En `<video id="avo-video">`:
- agregar `preload="none"` (hoy no tiene, y descarga el mp4 completo en la carga inicial).
- confirmar que el `poster` sea una imagen propia del video, no el hero reutilizado. `[[PENDIENTE: poster del video]]`
- agregar un `<track kind="captions">` o, si el video no tiene voz, un texto descriptivo cercano. `[[PENDIENTE]]`

### F3. Fuente
Se cargan **18 variantes de Poppins** (`100..900` + italics). En la página se usan solo 400, 500, 600 y 700, y ninguna itálica. Reducir el link a:
```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## BLOQUE G — Enlaces

### G1. Resolver los `href="#"`
Hay 12 links placeholder. Listado y destino requerido:

| Ubicación | Texto | Destino |
|---|---|---|
| Nav | Merch | `[[PENDIENTE]]` |
| Nav | About Us | `/about` |
| Nav | Catering | `/catering` |
| Nav + mobile panel | Order Now | `[[PENDIENTE: URL de pedidos]]` |
| Hero | Order Now | idem |
| 5x tarjetas Classics | Order Now | idem (o deep link al ítem) |
| 3x tarjetas What's new | Order Now | idem |
| Join app | Download Now | `[[PENDIENTE: App Store / Google Play]]` |
| CTA band | Order Now | idem pedidos |
| Footer | About Us / Catering / Blog / Merch | idem nav |

Si un destino no existe todavía, **quitar el link** o dejarlo como `<span>` en lugar de dejar `href="#"` — un link a `#` diluye el crawl y es mala señal de UX.

### G2. Redes sociales del footer
Apuntan a `instagram.com`, `tiktok.com`, `facebook.com` genéricos. Reemplazar por los perfiles reales de Avo Miami `[[PENDIENTE]]` y mantener `rel="noopener"`.

---

## BLOQUE H — Post-import en Webflow

Estas no se aplican al HTML sino al proyecto Webflow, dejarlas anotadas:

1. Cargar title / description / OG en **Page Settings**, no en el Embed.
2. JSON-LD en **Page Settings → Custom Code → Head**.
3. Los `alt` deben cargarse en el **Asset Manager** de Webflow, no como atributo suelto.
4. Activar `robots.txt` y sitemap automático en **Site Settings → SEO**.
5. Configurar el dominio canónico (con/sin www) y forzar HTTPS.
6. Verificar que la sección FAQ (`<details>`) se importe correctamente; si Webflow la rompe, reconstruirla con interacciones nativas manteniendo el texto en el DOM (no cargarlo por JS).
7. Crear las páginas por sede (`/locations/miami-beach`, `/locations/coconut-grove`, `/locations/south-miami`) — son las que van a competir por búsquedas "near me" en cada barrio. La homepage sola no las gana.

---

## Orden de ejecución sugerido

1. Bloque A (head) — rápido, alto impacto
2. Bloque B (typos)
3. Bloque G (links)
4. Bloque C (contenido nuevo: entidad, FAQ, locations)
5. Bloque D (JSON-LD, depende de C4 y C2)
6. Bloque E + F
7. Bloque H tras la importación

## Criterio de cierre
- Sin `[[PENDIENTE]]` visibles en el HTML publicado.
- Rich Results Test sin errores para Restaurant, Menu y FAQPage.
- Sin `href="#"` en el documento.
- Un solo `<h1>`, todas las secciones con `<h2>`.
