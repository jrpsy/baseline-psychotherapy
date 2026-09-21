# Reporte NOM-1 · "Therapy for Digital Nomads" (par EN/ES)

Fecha: 2026-09-21 · Base: `cb44815` (main) · Rama: `nom1-review` · Estado: vista previa, SIN merge (veredicto del dueño + autorización del estratega).

## Páginas nuevas (2)

/blog/therapy-digital-nomads/ · /es/blog/terapia-nomadas-digitales/ — construidas por sustitución anclada de slots sobre el par de Londres (H-2): chrome byte-idéntico (CSS, author box, footer, scripts; nav idéntico salvo conmutador al par).

| | EN | ES |
|---|---|---|
| Title | Therapy for Digital Nomads: Mental Health Without an Address (60) | Terapia para nómadas digitales: salud mental sin dirección fija (63) |
| Meta description | 154 (texto del estratega, exacto) | 157 (nativa) |
| H1 | Therapy for digital nomads | Terapia para nómadas digitales |
| Byline | By J.R. Hernandez, Psychotherapist · September 21, 2026 · 7 min read | Por J.R. Hernandez, Psicoterapeuta · 21 de septiembre de 2026 · 7 min de lectura |
| Cuerpo | Texto del dueño verbatim: apertura (2 párrafos), 6 H2-pregunta, blockquote citable, enlaces indicados (Half-Life Check, burnout, método, $120 → precios, WHO-5) | Pieza nativa en tú, mismo esqueleto, H2-pregunta con las búsquedas españolas ("¿Por qué se queman los nómadas digitales?", "…burnout en un nómada digital", "¿Cómo funciona la terapia online viajando?"), glosario canónico, enlaces a las versiones ES |
| FAQ | 4 (H3 + P = schema) | 4 espejo reformuladas |
| Cierre | Continue Exploring: expat-burnout · burnout-therapy · method · CTA H2 "Tired in a Way That Doesn't Match the Life?" + consulta gratuita wa.me | Sigue explorando: burnout-expatriados · terapia-burnout · metodo · "¿Cansado de una forma que no cuadra con la vida que llevas?" + wa.me ES |
| Schema | BreadcrumbList (3) · BlogPosting (author @id #jr, datePublished 2026-09-21, inLanguage en) · FAQPage (4) | idem, inLanguage es |

Decisiones documentadas:
- **Imagen del hero**: pre-merge el dueño aportó `~/Desktop/Nomad.png` (1672×941), recortada al 5:3 de la serie (1568×941, sin reescalar hacia arriba) como `blog-therapy-digital-nomads.webp` (q82); hero con atributos 1200×720, og:image 1200×720, twitter:image y BlogPosting.image en ambos artículos; alt EN "Person working on a laptop by a window at dusk, travel backpack nearby" / ES espejo. La imagen provisional del blog quedó sustituida.
- **Blog-cta y CTA final**: textos propios, redactados para no duplicar los del par de Londres ni los de expat-burnout.
- **Blockquote**: el del dueño, único en el cuerpo; guardarraíl de blockquotes 154 → 156.

## Integración

1. Hubs blog/ y es/blog/: card nueva en PRIMERA posición del `.blog-grid`, patrón single-line existente.
2. /blog/expat-burnout/ y /es/blog/burnout-expatriados/: una frase añadida al final del párrafo "Expat burnout is broader…" / "El burnout en expatriados es más amplio…" con enlace al artículo nuevo (EN: "Digital nomads face a related but distinct pattern: our guide to therapy for digital nomads covers it."; ES espejo); dateModified y article:modified_time 2026-09-21. Nada más tocado.
3. llms.txt: línea EN y ES en la sección Blog.
4. sitemap.xml: 82 → **84** `<loc>`; lastmod 2026-09-21 en las dos URLs nuevas, los dos hubs y el par de expat-burnout; alternates recíprocos.

## Verificación

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores en 87 HTML |
| Em dashes / `<em>` / hrefs / imágenes | 0 / 0 / 0 rotos |
| FAQ globales | **266** (258 + 8), 0 duplicadas exactas; similitud difusa máxima 0,66 (preguntas distintas) |
| Schema = visible | 8/8 Q/A por página; headline = title |
| Duplicados >12 palabras (cuerpo) | vs expat-burnout: 0 · vs burnout-therapy: 0 (EN y ES) |
| Cifras canon | $120 (1 por página, enlazado a precios) · "more than 21 countries" / "más de 21 países" · consulta gratuita de 15 minutos |
| Blockquote | 1 por página, texto del dueño; sitio 156 |
| hreflang | recíproco EN↔ES, x-default EN; canonical = og:url |
| Paridad de plantilla | author box, footer y CSS byte-idénticos; nav idéntico salvo conmutador |
| Render | 1280 y 375 (ver abajo) |

Render (Chrome headless): EN y ES a 1280 y 375, imágenes completas, sin overflow horizontal, H1 libre bajo la nav, blockquote único, 3 cards de Continue Exploring, CTA final del artículo. Capturas de página completa revisadas.

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 9/9** (head y byline · cuerpo EN verbatim contra los anclajes del brief: H2, apertura, cuatro mecanismos, blockquote único, cinco enlaces, cierre y FAQ · ES nativa en tú con las señales de búsqueda y sus enlaces ES · cifras canon $120 y "más de 21 países", sin contradicciones · 3 JSON-LD y schema=visible 8/8 por página, 266 FAQ sin duplicados · 0 shingles de 13 palabras frente a expat-burnout y burnout-therapy · paridad byte-idéntica con la plantilla salvo conmutador · reglas de sitio y blockquotes 156 · integraciones acotadas a los 6 archivos).

Residuos señalados y decisión:
- FAQ 3 EN: por indicación del estratega pre-merge, "identical: a stress system that stops switching off: but" pasa a "identical (a stress system that stops switching off), but" en visible y schema; la ES ya usaba punto y seguido, sin cambio.
- "$60" aparece por el banner de anuncio del sitio (PR-1), no por el artículo.
- El texto fuente del dueño no está en el repo; el cotejo verbatim se hizo contra los anclajes del comando.

## Vista previa

- http://localhost:8000/blog/therapy-digital-nomads/
- http://localhost:8000/es/blog/terapia-nomadas-digitales/
- http://localhost:8000/blog/
- http://localhost:8000/es/blog/
