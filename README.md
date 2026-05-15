# Proyecto Cowork - Instrucciones de Uso

## Estructura del Proyecto
```
proyecto/
├── imagenes/
├── logos/
├── referencias/
├── ofertas/
├── reviews/
├── datasheets/
├── seo/
└── .cowork-instructions (← IMPORTANTE)
└── README.md (← IMPORTANTE)
```

## Usando Claude Cowork con Optimización de Tokens

### Prefijos para Respuestas Concisas

| Prefijo | Uso | Ejemplo |
|---------|-----|---------|
| `[BUSCAR]` | Encontrar contenido | `[BUSCAR] textos de marketing` |
| `[REFACTOR]` | Cambiar/mejorar | `[REFACTOR] título de oferta #3` |
| `[REVISAR]` | Feedback rápido | `[REVISAR] reviews - tono` |
| `[CONCISO]` | Respuesta corta | `[CONCISO] ¿Está listo esto?` |
| `[CODIGO]` | Solo codigo | `[CODIGO] Audita y mejora el tiempo de carga de las imagenes de index.html` |
| `[EXPLICAR]` | Respuesta mas larga cuando necesite contexto | `[EXPLICAR] explica la clase .hero y como se adapta en responsive` |
| `[RAPIDO]` | 1 sola linea de respuesta | `[Rapido] cuanto es el 10% de 588` |
| `[FIX]` | Solo la correccion | `[FIX] linea 500 de Index.html` |

### Ahorro de Tokens

**Sin prefijo:** 250-350 tokens por respuesta
**Con prefijo:** 50-100 tokens por respuesta
**Ahorro:** ~70%

### Ejemplos Reales

#### ✅ BIEN (Respuesta en 15 tokens)
```
[REVISAR] ofertas/premium.txt - ¿Falta algo?
```
Respuesta: "Sí. Falta precio final y garantía."

#### ❌ MAL (Respuesta en 200 tokens)
```
Hola, necesito que revises los textos de mis ofertas premium.
Me gustaría saber si están completos, si tienen todo lo necesario
para una buena conversión, si el tono es el correcto...
```

## Patrones de Uso

### Para obtener lo que necesitas rápido:

1. **Sé específico:**
   - ✅ `[REVISAR] ofertas/black-friday.txt`
   - ❌ `[REVISAR] ofertas` (muy vago)

2. **Usa prefijos:**
   - ✅ `[BUSCAR] testimonios negativos`
   - ❌ `Busca testimonios negativos` (sin prefijo)

3. **Una pregunta por línea:**
   - ✅ `[REVISAR] logo - ¿Es reconocible?`
   - ❌ `[REVISAR] logo. ¿Reconocible? ¿Moderno? ¿Profesional?`

## Notas Importantes

- El archivo `.cowork-instructions` debe estar en la **raíz del proyecto**
- Claude lee automáticamente este archivo cuando lo abres
- No necesitas mencionar "modo conciso" en cada pregunta
- Los prefijos son opcionales pero muy recomendados

## Casos de Uso

### Marketing/Ofertas
```
[REVISAR] ofertas/verano.txt - ¿Call to action claro?
[REFACTOR] descripción - Más corta (máx 50 palabras)
[BUSCAR] mejores reviews de clientes
```

### Branding/Logos
```
[REVISAR] logo - ¿Funciona en blanco y negro?
[BUSCAR] logos competidores que encontramos
[REFACTOR] color principal - Más vibrante
```

### Revisión General
```
[REVISAR] proyecto - ¿Está listo?
[BUSCAR] errores o inconsistencias
[CONCISO] ¿Qué falta?
```
