# Reporte PAR-1a v2 · FAQ de precio en el par de parejas

Fecha: 2026-09-28 · Base: `490c78a` (main) · Rama: `par1-review` · Estado: vista previa, SIN merge.

## Anti-dup previo (gate)

Inventario global de FAQPage antes del cambio: 281 preguntas. Búsqueda de FAQ de precio de parejas en cualquier idioma (pareja/couple + coste/precio/$170): **ninguna existe**. Las únicas menciones de "$170" en FAQ están dentro de las preguntas genéricas de precio local del par de Ereván ("How much does a psychotherapy session cost in Yerevan?" / ES), que enumeran las tres tarifas; no son FAQ de precio de parejas y no bloquean. Solape de 8 palabras de las dos preguntas nuevas (pregunta + respuesta) contra las 281: **0**. Similitud difusa máxima de pregunta: 0,73 (EN, frente a "How does online depression therapy work?") y 0,76 (ES, frente a "¿Cuánto tiempo dura la terapia de pareja?"). Gate superado.

## Cambios

| | /couples-therapy-online/ | /es/terapia-parejas/ |
|---|---|---|
| FAQ nueva (posición 2) | "How much does online couples therapy cost?" → texto del estratega verbatim; "a monthly plan exists for ongoing work" enlaza /pricing/ | "¿Cuánto cuesta la terapia de pareja online?" → texto del estratega verbatim; "existe un plan mensual para procesos continuos" enlaza /es/precios/ |
| Bloque FAQ | 6 → 7 ítems, mismo markup `faq-item` | 6 → 7 ítems |
| Schema FAQPage | ítem insertado en posición 2, texto = visible (schema=visible 15/15) | idem (15/15) |
| Canon | "$170" en la FAQ (el bloque de precios de la página ya lo mostraba) | "170 USD" en la FAQ (la card de precios heredada muestra "$170", componente del sitio) |
| Frescura | La página lleva Service + FAQPage sin clave `dateModified`/`lastReviewed` (patrón de las páginas de servicio); no se inventa una clave. lastmod del sitemap 2026-09-03 → **2026-09-28** | idem |
| hreflang | en/es/x-default intactos, recíprocos | intactos |

Enlace del plan mensual con el estilo inline oro subrayado de la casa (las páginas de servicio no definen estilo de enlace en prosa).

## Verificación

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores en 89 HTML |
| Em dashes / `<em>` / dos puntos consecutivos | 0 / 0 / 0 en lo añadido (la frase de credenciales preexistente de ambas páginas conserva sus dos ":", no tocada) |
| Hrefs | 0 rotos (/pricing/ y /es/precios/ existen) |
| FAQ globales | **283** (281 + 2), 0 duplicadas exactas, 0 solapes de 8 palabras |
| Schema = visible | 15/15 en ambas |
| Sitemap | 86 `<loc>`, lastmod 2026-09-28 en las dos URLs |
| Render | 1280 y 375 en ambas, sin overflow ni imágenes rotas; FAQ 2 desplegada en la captura con el enlace al plan mensual visible |

## Vista previa

- http://localhost:8000/couples-therapy-online/
- http://localhost:8000/es/terapia-parejas/
