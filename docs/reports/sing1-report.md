# Reporte SING-1 · Página de servicio de Singapur (par EN/ES)

Fecha: 2026-09-27 · Base: `2c661e1` (main) · Rama: `sing1-review` · Estado: vista previa, SIN merge (ronda visual del dueño + revisión de repo del estratega).

## Páginas nuevas (2)

/therapy-singapore/ · /es/terapia-singapur/ — gemelas estructurales del par de expat-therapy: mismo head, nav (salvo conmutador), footer, CSS base y scripts; anatomía hero → 5 secciones H2 → FAQ → CTA final. CSS propio añadido al final del `<style>` (bloque `.sg-*`: hero en dos columnas con foto, franja de credenciales, prosa de sección).

| | EN | ES |
|---|---|---|
| Title | Psychotherapist in Singapore \| Online Therapy, Book This Week (61) | Psicólogo Español en Singapur \| Terapia Online en Español (57) |
| Meta description | Texto del dueño exacto (153) | 160: la fija del dueño medía 165; recorte mínimo "Psicoterapeuta hispanohablante" → "Psicólogo hispanohablante" (alineado con title y H1); el resto verbatim |
| H1 | Psychotherapist in Singapore, online | Psicólogo español en Singapur, online |
| Hero | Foto del dueño (`/HERO.webp`, la del par de Ereván) + kicker + subline del dueño + botón wa.me "Book a free 15-minute consultation" + microcopy "I answer personally within 24 hours." Botón sobre el pliegue a 1280 y a 375 | Espejo nativo: "Reserva una consulta gratuita de 15 minutos" + "Respondo personalmente en menos de 24 horas." |
| Franja de confianza | 4 ítems del dueño (Duke · APA · Autor del Protocolo · más de 21 países desde 2019) | Espejo ES |
| H2 (orden) | Therapy for burnout… · How much does therapy cost in Singapore? · Start this week: no waitlist · An expat who treats expats · A published, measurable method · FAQ · Ready to stop performing well-being? | Terapia en español para burnout, ansiedad y depresión · ¿Cuánto cuesta un psicólogo en Singapur? · Empieza esta semana, sin lista de espera · Un expatriado que atiende expatriados · Un método publicado y medible · FAQ · ¿Listo para dejar de aparentar que estás bien? |
| Cuerpo | Texto EN del dueño verbatim, con los 11 enlaces indicados | Pieza nativa en tú, mismo esqueleto, glosario canónico; sección expat con el ángulo hispano en Singapur (pareja profesional trasladada, cónyuge que acompañó el traslado, directivo de multinacional) y la línea de la casa en formulación propia ("La terapia profunda ocurre en el idioma en el que piensas, no en el que usas para trabajar") |
| FAQ | 7 (6 del dueño + confidencialidad de la enmienda) | 8 (espejo + confidencialidad + "¿Atiendes a hispanohablantes de cualquier país desde Singapur?") |
| Schema | Service (provider Person `#jr` por referencia, `areaServed` Country Singapore, `availableChannel.availableLanguage` ["English","Spanish"], offer 120 USD) · FAQPage · BreadcrumbList (2) · MedicalBusiness `#organization` | idem, inLanguage es |

### Enmienda SING-1

1. **Moneda local**: USD→SGD 1,2778 (open.er-api.com, 2026-09-27 00:02 UTC; contraste Frankfurter/BCE 1,2771 al 2026-09-25). $120 = S$153,3 → redondeo a múltiplo de 5: "**$120 USD (about S$155)**" en EN y "**120 USD (unos 155 dólares de Singapur)**" en ES. También en las dos líneas de llms.txt.
2. **FAQ de confidencialidad**: el sitio ya responde "Is online therapy confidential?" en /faq/ (y "¿Es confidencial la terapia online?" en /es/preguntas-frecuentes/). La nueva pregunta va en el ángulo del estratega (empleadores, aseguradoras, registro) con el texto EN de la enmienda íntegro, más una frase final que enlaza la FAQ general; similitud difusa con la existente 0,60 (pregunta) / 0,31 (respuesta). ES espejo nativo con enlace a /es/preguntas-frecuentes/.

### Decisiones documentadas

- **FAQ 5 EN**: la pregunta del dueño "Is online therapy as effective as in-person?" colisionaba al 0,92 con la global "Is online therapy as effective as in-person therapy?" (/faq/). Por la regla anti-dup se reformula a "**Does online therapy work as well as in-person?**" (0,71); la respuesta del dueño queda intacta. Reversible si el dueño prefiere el literal. ES: "¿Se pierde algo por hacer la terapia online en vez de presencial?" (0,62 frente a la global ES).
- FAQ de seguro y de reserva EN (0,85 frente a "Does insurance cover online therapy in Singapore?" del artículo de costos y a "How do I book a first session in Yerevan?"): preguntas del dueño mantenidas; son variantes locales del patrón ya aceptado en las páginas de Ereván, y las respuestas son distintas (≤0,44).
- **Barra móvil fija** (heredada de la plantilla, tras el footer): "Free 15-Min Expat Consultation" → "Free 15-Min Consultation"; en ES ya era genérica.
- **Footer**: la lista "Specializations"/"Especializaciones" existe en 82 páginas (dos formatos, una línea y multilínea); se añade "Therapy in Singapore" / "Terapia en Singapur" tras Expat en todas, sin tocar la nav (el dropdown de Servicios no lleva la página, como manda el comando).
- ES escribe "120 USD" (0 apariciones de "$120"); EN "$120 USD".
- **Estilo de enlaces**: las páginas de servicio no definen estilo para enlaces en prosa (`a{color:inherit;text-decoration:none}`), así que los 4 enlaces añadidos en expat/burnout llevan el estilo inline oro subrayado que la plantilla usa en sus enlaces de texto; en las páginas nuevas lo dan las reglas `.sg-prose a` y `.faq-answer a` del bloque propio. En el par de costos rige `.article-content a`.

## Integración

1. hreflang recíproco, canonical propio, og:url = canonical; sitemap 84 → **86** `<loc>`, dos bloques nuevos con alternates recíprocos y lastmod 2026-09-27.
2. Enlaces contextuales (una frase, anclada por contenido):
   - /blog/therapy-cost-singapore/: "If you are looking for the session itself rather than the market map, my therapy in Singapore page has the details." (cierre de la intro) · ES: "Si buscas la sesión en sí y no el mapa del mercado, mi página de terapia en Singapur tiene los detalles." dateModified y article:modified_time 2026-09-27.
   - /expat-therapy/: "Singapore is my base today, and there is a dedicated page on therapy in Singapore." tras la frase de los seis países · ES: "Hoy mi base es Singapur, y hay una página propia sobre terapia en Singapur."
   - /burnout-therapy/: "If you are in Singapore, evening slots on local time are available: see therapy in Singapore." tras "no commute, no waitlist, no geographic limitation." · ES espejo tras "sin limitación geográfica." Esa es la única frase de disponibilidad en ambas páginas y vive en el segundo párrafo descriptivo del hero (`hero-sub`), igual en EN y ES; el enlace se ve en oro subrayado (render verificado a 1280 y 375).
   - lastmod 2026-09-27 en el sitemap para las 6 páginas (las de servicio no llevan dateModified/lastReviewed en página).
3. Nav intacta. Footer: ver decisiones.
4. llms.txt: línea EN en Services y línea ES en Servicios (Español) con la frase de servicio local, precio y conversión.

## Verificación

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores en 89 HTML |
| Em dashes / `<em>` / dos puntos consecutivos | 0 / 0 / 0 en las 2 páginas nuevas y en las frases añadidas (las 4 páginas de expat/burnout conservan su frase de credenciales preexistente con dos ":", no tocada) |
| Hrefs / imágenes internas | 0 rotos |
| FAQ globales | **281** (266 + 15), 0 duplicadas exactas; similitud difusa máxima de pregunta 0,87 (variantes locales, ver decisiones), de respuesta 0,61 |
| Schema = visible | 15/15 (EN) · 17/17 (ES) |
| Duplicados >12 palabras (cuerpo) | 0 frente a expat-therapy, burnout-therapy y artículo de costos (EN y ES) |
| Canon | $120 USD + S$155 (EN) · 120 USD + 155 dólares de Singapur (ES) · more than 21 countries / más de 21 países · 0 URLs de Amazon con "?" |
| CTAs | wa.me con verbo book/reserva en hero y CTA final; 6 wa.me por página (nav, hero, CTA, footer, barra móvil, botón flotante) |
| Paridad de plantilla | footer byte-idéntico; nav idéntica salvo conmutador; CSS = plantilla + bloque `.sg-*` |
| Blockquotes | sitio 156 (sin cambio) |
| Render | 1280 y 375, EN y ES: sin overflow horizontal, 0 imágenes rotas, H1 libre bajo la nav, botón WhatsApp del hero dentro del pliegue en ambos anchos, foto 240 px (escritorio) / 180 px centrada (móvil), franja de credenciales separada del microcopy |

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 9/10** en primera pasada (head EN/ES exactos · cuerpo EN verbatim con 13 enlaces · FAQ EN 7/7 schema=visible · ES nativa sin anglicismos ni errores de ortografía, 8/8 schema=visible · JSON-LD 256 bloques en 89 HTML, 0 errores · integraciones acotadas a los 8 archivos de contenido + 74 footers, 0 dropdowns con Singapur · paridad de plantilla · 281 FAQ únicas y 0 shingles de 13 palabras · 0 hrefs rotos, alt en todas las imágenes). El punto NO CONFORME (menor) y los residuos, aplicados así:

- **Botón flotante y barra móvil** (heredados tras el footer) llevaban el texto prellenado de WhatsApp de expatriados ("discuss expat therapy" / "hablar sobre terapia para expatriados"): sustituidos por el prellenado canónico de reserva; ahora los 6 wa.me de cada página usan "book a free 15-minute consultation" / "reservar una consulta gratuita de 15 minutos". Re-verificado.
- FAQ ES de hispanohablantes: "trabajo con hispanohablantes de más de 21 países" inflaba el dato canónico; pasa a "atiendo a clientes de más de 21 países, hispanohablantes entre ellos".
- Regla `.sg-price` sin uso: eliminada. `.faq-answer a` se mantiene (es lo que hace visibles los enlaces de las respuestas; solo afecta a las dos páginas nuevas).
- Kicker ES "Español e Inglés" con mayúsculas: estilo heredado de los kickers del sitio (versalitas), sin cambio.
- Coherencia de ubicación: el par de Ereván dice "Now in Yerevan" / "Ahora en Ereván" mientras home, about y ahora expat dicen base en Singapur. Preexistente; queda señalado para el estratega.
- "$60" en el cuerpo procede del banner de anuncio sitewide (PR-1), no de la página.

## FIX SING-1-H (veredicto del dueño: se hereda el diseño de la casa)

- **Hero**: eliminado el bloque `.sg-*` (dos columnas con foto). Reconstruido con el componente exacto de las páginas de servicio (`page-hero` › `page-hero-content` › `kicker` · `h1` · `hero-sub` · `hero-markers` con la línea de Google Reviews heredada · `hero-actions` con `btn btn-primary` · `hero-markers` con el microcopy), fuente byte-a-byte el par de expat-therapy; cero clases nuevas. Copy conservado: eyebrow "Singapore · Online · English & Spanish" / "Singapur · Online · Español e Inglés", H1, sublínea, CTA "Book a free 15-minute consultation" / "Reserva una consulta gratuita de 15 minutos", microcopy "I answer personally within 24 hours." / "Respondo personalmente en menos de 24 horas.". Sin foto (el componente no la lleva). Sin botón secundario "#process" (la página no tiene esa sección).
- **Credenciales**: la franja `.sg-trust` se sustituye por la sección `about#about` de la home (EN desde `index.html`, ES desde `es/index.html`) tal cual: mismo componente, mismas clases, mismo contenido (bio, 6 tarjetas de credenciales desplegables, aviso de idioma). Única adaptación: la ruta del fondo pasa de relativa a absoluta (`/ABOUT_BG.webp`) para que resuelva desde el subdirectorio. Sus reglas CSS (`.about*`, `.credential*`, 22 reglas incluidas las `@media`) se copian del `<style>` de la home del mismo idioma al final del `<style>` de la plantilla.
- **Reseñas**: sección `reviews` de la home tal cual (8 reseñas, agregado 5.0 · 22 Google Reviews, enlace "Leave a review"), con `/REVIEW_BG.webp` absoluto; regla `.reviews-aggregate` copiada de la home. Posición análoga a la home: tras las secciones de servicio y antes de la FAQ.
- **Prosa de las 5 secciones**: la clase `.sg-prose` se sustituye por `content-narrow` de la plantilla. Único CSS propio restante: `.content-narrow a,.faq-answer a` (estilo de enlace oro subrayado; sin clases nuevas). 0 apariciones de `sg-` en ambas páginas.
- Verificación: hero con la secuencia de clases del componente de expat (sin el segundo `hero-sub` ni el botón outline); `about` y `reviews` con secuencia de clases, secuencia de etiquetas y texto idénticos a la home de su idioma (solo difiere la URL del fondo). Suite estándar: JSON-LD 0 errores, em dashes 0, dos puntos consecutivos 0, hrefs 0 rotos, schema=visible 15/15 y 17/17, FAQ 281, 0 shingles de 13 palabras frente a expat/burnout/costos excluyendo los dos componentes heredados de la home (que por diseño se repiten en todo el sitio). Render 1280 y 375: CTA del hero sobre el pliegue en ambos anchos, credenciales y reseñas con fondo, sin overflow.
- Efectos colaterales documentados: la frase canónica "more than 21 countries" ya no aparece en la página EN (iba en la franja eliminada; la bio heredada no la contiene); en ES sigue en la FAQ de hispanohablantes. Guardarraíl de blockquotes 156 → **172** (8 reseñas heredadas × 2 páginas).

## Vista previa

- http://localhost:8000/therapy-singapore/
- http://localhost:8000/es/terapia-singapur/
- http://localhost:8000/blog/therapy-cost-singapore/
- http://localhost:8000/es/blog/costo-terapia-singapur/
