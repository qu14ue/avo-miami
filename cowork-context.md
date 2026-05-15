# Contexto del Proyecto — Rediseño avo-miami.com
_Archivo de seguimiento de cambios sobre `index.html`_

---

## Estado actual
Archivo en trabajo activo: `index.html`
Objetivo: reemplazar la homepage de avo-miami.com

---

## Cambios aplicados

### 1. NAV — Estructura Sweetgreen-style
- Logo **centrado** usando grid 3 columnas (`minmax(0,1fr) auto minmax(0,1fr)`)
- Links divididos: izquierda (Our Mission / Rewards / Merch) · derecha (Menu / Locations / Catering / Order Online)
- Toggle mobile con **CSS checkbox puro** — sin JS para abrir/cerrar
- Mobile: panel full-screen oscuro (`--carbon`), links en serif itálica, hamburger anima a ✕
- Eliminado el bottom bar mobile anterior
- Bug fix: `visibility: hidden` en lugar de `display: none` para el left nav en mobile (evita colapso de columna del grid)
- Ajuste de spacing en breakpoint 1024–1280px (`gap: 16px`, `padding: 0 24px`)

### 2. Sección "Build Your Bowl" — Eliminada
- Removido CSS completo de `#build-bowl`, proteínas, bowl types, bases, panel, mobile sticky bar
- Removido HTML `<section id="build-bowl">` con sus 3 pasos y panel lateral
- Removido JS: `selection`, `productsData`, `renderProteins`, `renderBowlTypes`, `renderBases`, `selectProtein`, `selectBowlType`, `selectBase`, `updatePanel`, `showBowlSummary`, mobile bar toggle
- El fetch ahora llama solo a `renderDishes(data)`

### 3. Featured Dishes — Limitado a 4 productos
- `data.featured_dishes.slice(0, 4)` en `renderDishes()`

### 4. Sección "Why Avo" (#beneficios) — Mantenida
- Se intentó eliminar y se restauró a pedido del usuario
- Sección intacta con 6 benefit cards sobre fondo `--verde-bosque`

### 5. Colores — Actualizados
| Variable | Antes | Ahora |
|---|---|---|
| `--verde-bosque` | `#1D6B3E` | `#337A44` |
| `--verde-bosque-dark` | `#155A33` | `#2A6438` |
| `--verde-hoja` | `#3A8A57` | `#599C3A` |
| `--crema` | `#F5F1EB` | `#F5F1EB` _(sin cambio)_ |

Paleta disponible no usada aún: `#8FC43C` · `#599C3A` · `#C5E2B0` · `#FFF` · `#f0f0f0`

### 6. Tipografía — Fuente serif reemplazada
- `'Cormorant Garant'` → **`'Pridi'`** (Google Fonts, pesos 200–700)
- Variable CSS: `--font-serif: 'Pridi', Georgia, serif`
- Google Fonts link actualizado

---

## Estructura de secciones activa

| # | ID | Nombre | Estado |
|---|---|---|---|
| 01 | `#hero` | Hero | ✅ activo |
| 02 | `#strip` | Strip de diferenciales | ✅ activo |
| 03 | `#video-section` | Video | ✅ activo |
| 04 | `#build-bowl` | Build Your Bowl | ❌ eliminado |
| 05 | `#platos` | Featured Dishes (4 items) + banner Chef's Suggestion | ✅ activo |
| 06 | `#que-es` | What We Are / Qué es Avo | ❌ eliminado |
| 07 | `#diferenciales` | Our Commitment | ✅ activo |
| 08 | `#beneficios` | Why Avo | ✅ activo |
| 09 | `#testimonios` | Testimonios | ✅ activo |
| 10 | `#rewards` | Rewards | ✅ activo |
| 11 | `#catering` | Catering CTA | ✅ activo |
| 12 | `#locations` | Locations (3 locales) | ✅ activo |
| 13 | `#footer` | Footer | ✅ activo |

---

### 7. Banner "Chef's Suggestion" — dentro de `#platos`
- Card banner `.chefs-banner` dentro del `.container` de `#platos`, entre el dishes grid y el botón "View Full Menu"
- Layout: imagen izquierda (420px fija) / copy derecha en desktop; stack vertical en mobile
- Imagen: `img/platos_destacados/salmon_poached_egg.jpg`
- Plato destacado: **Salmon & Poached Egg**
- Badges: High Protein · Gluten-Free · Zero Seed Oils · Dietitian-Approved · Dairy-Free
- CTA: "Order Now" → `/menus` con tracking `chefs_suggestion_order_now`
- Scroll reveal en todo el card

---

## Pendiente / próximos pasos
_(completar según avance el proyecto)_
