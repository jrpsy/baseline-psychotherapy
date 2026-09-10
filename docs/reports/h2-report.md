# Reporte Comando H-2 · "Spanish-Speaking Therapist in London" (par EN/ES)

Fecha: 2026-09-10 · Base: `bfd2d4b` (main) · Rama: `h2-review` · Estado: vista previa, SIN merge (pendiente veredicto del dueño y autorización del estratega).

## T0 · Verificaciones previas (fuentes literales)

### T0.1 Tarifas privadas en Londres

| Fuente | Cita literal | Alcance |
|---|---|---|
| BACP (asociación), "How to get therapy", sección Private therapists, bacp.co.uk/about-therapy/how-to-get-therapy/ | "More than half of the therapist listings on our directory advertise costs of between £40 to £60 per session." | Reino Unido, todo tipo de terapeutas |
| UK Therapy Guide (directorio), "How Much is Therapy in London? (2026 Cost Guide)", uktherapyguide.com/how-much-is-therapy-london | "Most private therapists in London charge between £60 and £150 per session, with the average sitting around £70-£90 for individual therapy." · "Individual psychotherapy: £80-£150" | Londres |
| Psychology Today UK (directorio), psychologytoday.com/gb/basics/therapy/how-much-does-therapy-cost | "Estimates of a therapy session there range from £50-£150." | Reino Unido |

Redondeo honesto aplicado en el texto: sesiones privadas presenciales en Londres **£60-150**; psicoterapia especializada **£80-150** (FAQ 2 EN/ES). Counselling Directory devolvió 403 y la página de tarifas de UKCP no existe (404); no se usan.

### T0.2 Conversión USD→GBP

| Fuente | USD→GBP | Fecha |
|---|---|---|
| open.er-api.com/v6/latest/USD | 0.738041 | 2026-09-10 00:02 UTC |
| api.frankfurter.dev (BCE) | 0.7372 | 2026-09-09 |

$120 × 0.738 = £88.6 → **"about £90" / "unas £90"**.

### T0.3 Procesamiento emocional bilingüe (Crossref, título carácter a carácter)

| Referencia | DOI | Verificación |
|---|---|---|
| Caldwell-Harris, C. L. (2014). Emotionality differences between a native and foreign language: theoretical implications. *Frontiers in Psychology*, 5, 1055. | 10.3389/fpsyg.2014.01055 | Título idéntico; revista y año coinciden. **Usada en el texto** |
| Santiago-Rivera, A. L., & Altarriba, J. (2002). The role of language in therapy with the Spanish-English bilingual client. *Professional Psychology: Research and Practice*, 33(1). | 10.1037/0735-7028.33.1.30 | Título idéntico. Respaldo específico hispano-inglés, no enlazada |
| Harris, Ayçiçeği & Gleason (2003), *Applied Psycholinguistics* · Pavlenko (2012), *International Journal of Psychology* | 10.1017/s0142716403000286 · 10.1080/00207594.2012.743665 | Títulos idénticos. Respaldo adicional |

Resultado: VERIFICA. El párrafo 2 conserva la frase del dueño y añade la atribución sobria entre paréntesis con enlace: "(Caldwell-Harris, 2014)" → https://doi.org/10.3389/fpsyg.2014.01055. Mismo tratamiento en ES.

## Páginas nuevas (2)

/blog/spanish-speaking-therapist-london/ · /es/blog/psicologo-espanol-londres/ — construidas por sustitución anclada de slots sobre las plantillas H-1 de cada idioma (chrome byte-idéntico por construcción: CSS, author box, footer y scripts; nav idéntico salvo el conmutador de idioma, que apunta al par).

| | EN | ES |
|---|---|---|
| Title | Spanish-Speaking Therapist in London: The Honest Guide (54) | Psicólogo en español en Londres: la guía honesta (48) |
| Meta description | 160 (texto del estratega; se retiró una coma para entrar en ≤160) | 155 (nativa) |
| H1 | Finding a Spanish-speaking therapist in London | Encontrar un psicólogo en español en Londres |
| Byline | By J.R. Hernandez, Psychotherapist · September 10, 2026 · 4 min read | Por J.R. Hernandez, Psicoterapeuta · 10 de septiembre de 2026 · 4 min de lectura |
| Cuerpo | Apertura 3 párrafos + 4 H2 del dueño, verbatim, con T0 integrado | Pieza nativa en tú, mismo esqueleto, primera persona conservada, señales "psicólogo en español", "terapia en español en Londres", "terapia de pareja bilingüe" |
| FAQ | 4 (H3 + P = schema) | 4 espejo reformuladas |
| Schema | BreadcrumbList (3) · BlogPosting (author @id #jr, datePublished 2026-09-10, inLanguage en) · FAQPage (4) | idem, inLanguage es |

Decisiones documentadas:
- **Apertura en 3 párrafos**: el texto del dueño llegó en dos bloques; el segundo se parte tras la atribución ("…feeling in (Caldwell-Harris, 2014).") para cumplir los "tres párrafos aprobados". Cero palabras alteradas.
- **Enlace de parejas**: en el cuerpo, "Bilingual couples sessions" → /couples-therapy-online/ (ES: "terapia de pareja bilingüe" → /es/terapia-parejas/); en la FAQ 3 la misma frase lleva el enlace (visible) y el schema conserva el texto plano idéntico.
- **Sin blockquote de cierre**: el texto del dueño no trae "Cierre"; el slot queda vacío. Guardarraíl blockquotes = 154 intacto.
- **CTA**: wa.me estándar del idioma (no el mensaje personalizado de la guía de costos); texto del blog-cta y del CTA final propios, redactados para no duplicar el artículo de costos.
- **Imagen del hero**: `~/Desktop/London.png` (1672×941) recortada al 5:3 de los heroes del blog (centro, 1568×941, sin reescalar hacia arriba para no inventar píxeles), webp q82 = 123 KB, `blog-spanish-speaking-therapist-london.webp`. Atributos width="1200" height="720" como el H-1; 1568 px ≥ 2× de la caja de 760 px (retina). Alt EN/ES del dueño. Misma imagen en og:image y BlogPosting.image.

## Integración

1. Hubs blog/ y es/blog/: card nueva en PRIMERA posición del `.blog-grid`, patrón single-line de las cards existentes.
2. /expat-therapy/ y /es/terapia-expatriados/: una frase añadida al final del párrafo sobre expatriados hispanohablantes (EN: "Spanish-speaking Londoners can start with our honest guide to therapy in Spanish in London." con enlace; ES espejo). Nada más tocado (diff limitado a esa línea).
3. llms.txt: línea EN y línea ES del artículo bajo la sección Blog, con cifras T0.
4. sitemap.xml: 75 → **77** `<loc>`; lastmod 2026-09-10 en las dos URLs nuevas, en los dos hubs y en las dos páginas de expatriados; alternates recíprocos.

## Coherencia de cifras (puerta dura)

| Cifra | Canon / origen | Veredicto |
|---|---|---|
| USD $120 (about £90) por 60 min | canon $120 · T0.2 | IDÉNTICO |
| 90 minutos (parejas) | canon 90min | IDÉNTICO |
| £60-150 y £80-150 | T0.1 (dos fuentes de mercado UK) | Verificado |
| Consulta gratuita 15 min | canon | IDÉNTICO |
| $170 | no se menciona; no contradicho | OK |
| Cifras divergentes (S$, £150 fijo, $300/$400) | 0 en los posts | OK |

## Suite global (80 HTML)

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores |
| Em dashes / `<em>` | 0 / 0 |
| hrefs internos / imágenes rotos | 0 |
| FAQ globales | **238** (230 + 8), 0 duplicadas exactas; similitud difusa > 0.7: ninguna |
| Schema = visible | FAQ Q/A verbatim; headline = title; autor y fecha visibles en byline; imagen visible |
| hreflang | recíproco EN↔ES, x-default EN, canonical = og:url |
| Paridad de plantilla | author box, footer+scripts y CSS byte-idénticos al H-1; nav idéntico salvo conmutador |
| Duplicados >12 palabras (cuerpo del artículo) | vs guía de costos: 0 · vs expat-therapy: 0 (EN y ES) |
| Guardarraíles | blockquotes 154 · wa.me 505 (493 + 12 de las dos páginas nuevas) · Amazon con `?` 0 |

## Render (Chrome headless, CDP)

| Página | 1280 | 375 |
|---|---|---|
| EN | 3/3 imágenes OK (hero 1568 px natural en caja 760×340) · sin overflow · H1 libre · 5 H2 de cuerpo · 4 FAQ | 3/3 OK · caja 335×200 · sin overflow |
| ES | idem | idem |
| Hubs | primera card = artículo nuevo (544 px, sin overflow), EN y ES | |

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 10/10** (metas/canonical/hreflang/og · 3 bloques JSON-LD y schema=visible 16/16 por página · copy EN idéntico al texto del dueño · calidad ES · canon de cifras · paridad byte-idéntica con la plantilla · duplicados 0 · 238 FAQ sin duplicados, similitud máxima 0.64 · integraciones y diff acotado a los seis archivos · imagen 5:3 ≥1520 px con alts del dueño).

Residuos señalados y decisión:
- Estilo ES: aplicados los retoques ("profesionales excelentes", "terapeutas privados presenciales (pocos con español nativo)", "se formó el profesional"); "clínico/clínica" queda solo como adjetivo (evaluación clínica). Suite re-ejecutada en verde.
- Meta description EN en 160 exactos: es el texto del estratega con una coma retirada; se deja.
- og:locale en_US heredado de la plantilla en un artículo dirigido a Londres: se mantiene por paridad de plantilla; decisión del estratega si quiere en_GB para este par.
- Breadcrumb corto frente al H1 largo: convención del sitio, sin cambio.
- llms.txt EN "£60 to £150 per session": coherente con los rangos T0; se deja.

## Vista previa

- http://localhost:8000/blog/spanish-speaking-therapist-london/
- http://localhost:8000/es/blog/psicologo-espanol-londres/
- http://localhost:8000/blog/
- http://localhost:8000/es/blog/
