# MET-1 · Página del Protocolo (/method/ + /es/metodo/)

Fecha: 2026-09-09 · Rama: `met1-review` · Estado: vista previa, SIN merge (pendiente veredicto del dueño y autorización del estratega).

## Alcance ejecutado

**Páginas nuevas (2)**, fuera de nav y footer, par hreflang recíproco (x-default = EN), canonical propio, og:url = canonical, og:image `og-books.png` 1200×630.

| | EN `/method/` | ES `/es/metodo/` |
|---|---|---|
| Title | The Baseline Psychotherapy Protocol \| Method & Book (51) | El Protocolo Baseline Psychotherapy \| Método y libro (52) |
| Meta description | 156 chars (texto del estratega) | 156 chars (espejo, recortado a ≤160) |
| H1 | 1 | 1 |
| Bloques | Hero doble CTA · Qué es · Mapa · Origen + autor · Libro · Protocolo y terapia · FAQ (7) · CTA + línea a libros | espejo |
| Schema | BreadcrumbList · MedicalWebPage (lastReviewed 2026-09-09, reviewedBy #jr) · FAQPage (7) · Book (inLanguage en) | idem, Book inLanguage es |

Plantilla: chrome del par de páginas de libros (nav, banner, footer, cookies, scripts byte-idénticos), secciones `content-section` con eyebrow + H2 centrados y prosa a 760px, mapa clínico centrado como componente propio (pills serif + flechas doradas; en móvil se apila en columna con flechas giradas), bloque de autor compacto con `profile.webp` y enlace a About, card del libro con `PROTOCOL_COVER.webp` y botón canónico de Amazon. Textos EN finales del dueño sin alterar. ES en tú, primera persona conservada ("Lo construí…", "Creé el Protocolo en sesión…"), glosario del libro (defusión, valoración, anclaje no aparece en el original EN).

Convención de la casa: el título del libro en el Bloque 4 va en texto plano (regla `<em>` = 0), no en cursiva como sugería el borrador.

## Integración

1. Páginas de libros (par): línea con enlace bajo la disponibilidad del Protocolo. EN `Learn more about the Protocol as a working tool →` → /method/ · ES `Más sobre el Protocolo como herramienta de trabajo →` → /es/metodo/.
2. About y Sobre-mí: la mención del Protocolo en la frase de los tres libros enlaza a /method/ y /es/metodo/.
3. llms.txt: línea EN y línea ES del método (qué es, creado por J.R. Hernandez, integra CBT/TCC, ACT, inteligencia emocional, somático, URL de la página y canónico de Amazon).
4. Nav y footer intactos en todo el sitio. Home no tocada (la card sigue a la página de libros).
5. sitemap.xml: +2 URLs (75 `<loc>`), lastmod 2026-09-09, alternates recíprocos.

## Suite global (78 HTML)

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores |
| Em dashes | 0 |
| `<em>` | 0 |
| hrefs internos / imágenes locales rotos | 0 |
| FAQ globales | 230 (216 + 14), 0 duplicadas exactas |
| FAQ similitud difusa | 5 pares > 0.7 frente a "What is Baseline Psychotherapy?" / "¿En qué idiomas están disponibles las sesiones?"; preguntas distintas, no duplicados |
| Amazon con `?` | 0 (canónico único B0CZ9S1983) |
| Guardarraíles | blockquotes 154 · wa.me 493 (479 + 14 de las dos páginas nuevas: hero, bloque 5, CTA, footer, flotante, barra móvil, cookie/gtag) |
| Schema = visible | FAQ Q/A verbatim en HTML; Book name, autor, 2026, tapa blanda/Kindle y URL Amazon visibles; MedicalWebPage.name = title |
| hreflang | recíproco EN↔ES, x-default EN, canonical propio |
| Nav / footer | byte-idénticos a las páginas de libros del mismo idioma; 0 enlaces a /method/ o /es/metodo/ en nav o footer |
| Duplicados >12 palabras vs libros y About | EN vs About 0 · ES vs Sobre-mí 0 · vs páginas de libros: únicamente el título propio del libro con subtítulo (14 palabras), inevitable por spec (entidad Book completa y texto del dueño). Ningún párrafo duplicado. |

## Render (Chrome headless, CDP)

| Página | 1280 | 375 |
|---|---|---|
| /method/ | 3/3 imágenes OK · sin overflow · mapa centrado (960px) · H1 no ocluido · FAQ 7 y acordeón funcional | 3/3 OK · sin overflow · mapa centrado (335px) apilado · CTAs a ancho completo |
| /es/metodo/ | idem | idem |

Capturas de página completa y de hero revisadas: banner, nav, breadcrumb, hero con doble CTA, mapa, bloque de autor, card del libro, FAQ y CTA navy con línea discreta a la página de libros.

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 9/9** (títulos/metas/canonical/hreflang · 4 bloques JSON-LD válidos y schema=visible 14/14 por página · reglas de sitio en 78 HTML · nav y footer byte-idénticos, 0 enlaces en menús · 230 FAQ sin duplicados · duplicados >12 palabras solo el título propio del libro · sitemap y llms.txt · calidad ES · copy EN idéntico al spec).

Residuos señalados y decisión:
- Estilo ES (bloques 1 y 3): aplicados los cuatro retoques sugeridos ("una lectura, fundamentada en la TCC, de la historia que construye la mente"; "la atención al cuerpo propia de los enfoques somáticos"; "la conciencia somática, que empieza por el cuerpo"; "de forma automática"). Suite re-ejecutada en verde tras el cambio.
- Conmutador de idioma del nav heredado (EN → /es/, ES → /emotional-intelligence-books/): no aterriza en la página gemela del método. Se deja así porque el spec exige nav byte-intacto; decisión del estratega si quiere excepción (About sí usa conmutador gemelo).
- Breadcrumb visible "The Protocol" / "El Protocolo" frente a BreadcrumbList "The Baseline Psychotherapy Protocol": sigue la convención existente de la página de libros ("Books" vs "Emotional Intelligence Books"). Sin cambio.
- Este informe se incluye en el commit de la rama.

## Vista previa

- http://localhost:8000/method/
- http://localhost:8000/es/metodo/
- http://localhost:8000/emotional-intelligence-books/
- http://localhost:8000/es/libros-inteligencia-emocional/
