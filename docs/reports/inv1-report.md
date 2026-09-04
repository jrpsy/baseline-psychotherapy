# INV-1 · Auditoría de la capa invisible (Google, Yandex, LLMs)

**Fecha**: 2026-09-04 · **Base auditada**: main `9f0d973` (incluye los 2 commits manuales del dueño sobre pricing) · **Rama**: `inv1-review` · **Modo**: lectura con política de graduación (fixes triviales inequívocos aplicados y documentados; todo lo demás reportado sin tocar). **Alcance**: 73 páginas del sitemap + sitemap.xml, robots.txt, llms.txt, 404.html y los 2 archivos de verificación (Google, Yandex).

## Veredicto ejecutivo

**La capa invisible está limpia en lo estructural**: 0 errores de sintaxis JSON-LD en 73 páginas, 66 de 70 Offers con `price`, 62 con su precio visible en la página (los 4 Offers de $620 de las homes no lo muestran: M11 corregido tras la doble auditoría), 216 preguntas FAQ sin duplicados entre páginas, canónicas autorreferenciales 73/73, hreflang recíproco y sin colgantes, sitemap = 73 canónicas exactas, og:image 73/73 resolviendo en repo y en vivo, sameAs con un único conjunto de 10 URLs todas respondiendo, 0 em dashes, 0 hrefs internos rotos, 0 anclas muertas, 0 `target=_blank` sin noopener, guardarraíles intactos (blockquotes 154, wa.me 479, 75-min 0).

**Deuda registrada para decisión (no bloqueante)**: (1) llms.txt caducado en 5 puntos (sin Sesión Focal, sin Yereván, sección ES incompleta); (2) sitemap sin `x-default` en 36 entradas mientras las páginas sí lo declaran; (3) `twitter:title` solo en 4 de 73 páginas (las 69 restantes caen al fallback og:title); (4) el hub FAQ (EN y ES) lleva en 12+12 respuestas visibles un enlace CTA final que el schema omite; (5) **las 3 ediciones manuales del dueño en /pricing/ no tienen espejo en /es/precios/**; (6) **el objetivo declarado del dueño (Sliding Scale visible en el primer viewport a 1280) NO se cumple: el bloque empieza a 1064px con viewport de 900**; (7) `lastReviewed` de tests/hubs/crisis no se movió con la inserción del banner (regla vs semántica clínica); (8) 17 meta descriptions superan 160 caracteres; (9) **las dos homes declaran en schema dos Offers "Monthly Plan (Couples)" $620 que la página no muestra** (herencia del swap PR-1: la card de parejas salió de la vitrina, el Offer quedó) y 4 Offers de formación laboral sin `price`.

**Bloqueantes: NO.**

## Fixes triviales aplicados en esta rama (3 clases, 4 archivos)

| # | Fix | Archivo(s) | Justificación |
|---|-----|-----------|---------------|
| T1 | `English & Spanish` → `English &amp; Spanish` en la línea meta de la card Couples (edición manual del dueño) | pricing/index.html | Normalización mecánica: la card Individual del mismo archivo ya usa `&amp;`; render idéntico |
| T2 | `lastReviewed` 2026-09-01 → 2026-09-04 en el MedicalWebPage | yerevan/index.html, es/yerevan/index.html | YER-2 (2026-09-04) reestructuró la sección de precios y no bumpeó la fecha; regla vigente: "lastReviewed se actualiza en cada edición de la página" |
| T3 | `lastmod` del sitemap = fecha del último commit git de cada archivo (69 entradas) | sitemap.xml | Regla del comando: "los de las páginas tocadas esta semana al día". Ningún valor futuro. **Nota para el estratega**: 65 entradas pasan a 2026-09-03 porque el banner sitewide (b08f43a) tocó 69 páginas ese día; si se prefiere reservar lastmod para cambios sustantivos, revertir es un `git checkout main -- sitemap.xml` |

Diff total de fixes: 4 archivos, 72 líneas cambiadas (69 lastmod + 1 `&amp;` + 2 lastReviewed). Suite post-fix re-ejecutada: idéntica en verde (abajo).

---

## BATERÍA 1: JSON-LD

```
html files 76 | sitemap urls 73 | no-sitemap html: 404.html, google048156ac86345d67.html, yandex_2274014066491920.html
JSON-LD syntax errors: 0 (73/73 parseados)
pages sin JSON-LD: policies.html, es/politicas.html, privacy-policy.html, politica-privacidad.html (legales: aceptable)
@type inventory (site): Question 216 · Answer 216 · ListItem 173 · Offer 70 · Person 69 · BreadcrumbList 69 · ImageObject 63 ·
  EducationalOrganization 48 · FAQPage 39 · MedicalBusiness 35 · PostalAddress 35 · Organization 32 ·
  EducationalOccupationalCredential 28 · Article 22 · MedicalWebPage 21 · Place 20 · Country 20 · City 18 · Service 18 ·
  ServiceChannel 18 · MedicalCondition 12 · OfferCatalog 6 · Book 4 · AdministrativeArea 2 · WebSite 2 · SpeakableSpecification 2
FAQ total schema questions: 216 · preguntas duplicadas entre páginas: 0
schema=visible (FAQPage): 39 FAQPage · 216 preguntas presentes en el render de su página: 216/216 (pricing 7/7 ×2, yerevan 6/6 ×2,
  9 blogs con FAQ 18/18 como <h3>+<p>, hub FAQ 12/12 ×2, servicios: todas)
  Respuestas byte-idénticas: 192/216. Las 24 restantes (12 faq/index.html + 12 es/preguntas-frecuentes/index.html) difieren SOLO
  por un <a class="faq-link"> final en la versión visible ("Learn more about burnout therapy →" / "Más información sobre…") que el
  schema omite. Desync de fondo: 0. Registrado como M4.
Offers/prices: 70 Offers en 22 páginas (index ×12 [Service.offers + OfferCatalog], es/index ×12, pricing ×6, es/precios ×6, 7 pares de servicio ×3 ó ×2)
  · con `price`: 66/70 (los 4 sin price son "Workplace Mental Health Training"/"Formación en Salud Mental Laboral" ×2 por home: precio a consulta)
  · price ∈ {60,120,170,430,620,1200} USD: 66/66 · precio visible fuera de <script>/<style> en su página: 62/66
  · NO visibles: los 4 Offers "Monthly Plan (Couples)" / "Plan Mensual (Pareja)" $620 de index.html y es/index.html (2 por home).
    Las homes muestran 60/120/170/430/1,200 pero no $620 desde que la card de parejas salió de la vitrina (PR-1). Registrado M11.
  · Corrección de la doble auditoría: el primer pase contó el "620" del color CSS #0C1620 como visible y omitió los 4 Offers sin price.
  AMD: no hay Offers en AMD.
lastReviewed (21 MedicalWebPage): crisis pair 2026-08-22 · tests hubs 2026-08-27 · 5 tests ×2 + tmms-24 2026-08-26 ·
  breathing/emotional-meter pairs 2026-08-27 · yerevan pair 2026-09-01 → FIX T2 → 2026-09-04. Futuros: 0.
tipos prohibidos: LocalBusiness 0 · Review 0 · AggregateRating 0 · Rating 0. MedicalBusiness 35 nodos = la entidad
  @id #organization con address {addressCountry: SG} en TODAS (incl. yerevan pair): sin LocalBusiness de Yereván, doctrina cumplida.
< crudos dentro de JSON-LD: 0
```

## BATERÍA 2: Metas y cabezas

```
titles: únicos 73/73 · ausentes 0 · >65 chars: 0 (min 39 privacy-policy.html · max 61 es/tests/dass-21)
meta description: presentes 73/73 · duplicadas 0 · longitud 99–210 · >160 chars: 17 (registrado M8)
title = og:title: 73/73
twitter:title: presente solo en 4 (index, es/index, pricing, es/precios) y = title en las 4; ausente en 69 (fallback a og:title). Registrado M3.
og:image: 73/73 URL absoluta https://baselinepsychotherapy.com/… · archivo existe en repo 73/73 · 14 imágenes distintas
  (og-home-en.png ×24, og-home-es.png ×25, EI_BOOK.webp ×2, 11 blog-*.webp ×2) · en vivo 200 image/* (LOGO, HERO, og-home-en/es, profile verificadas)
og:url = canonical: 73/73 · charset 73/73 · viewport 73/73
Analítica: GA 73/73 (×1, sin duplicados) · criterio interactivas = tests/* excepto los 2 hubs = 15 páginas
  (5 tests ×2 + tmms-24 ES + breathing/respiracion + emotional-meter/medidor-emocional):
  Clarity 0/15 y Metrika 0/15 en interactivas ✔ · Clarity 58/58 y Metrika 58/58 (script+noscript ×1) en las no interactivas ✔
  Observación fuera del sitemap: 404.html lleva Metrika sin GA ni Clarity (registrado M9, cosmético).
```

## BATERÍA 3: Canónicas y hreflang

```
canonical autorreferencial https con barra final: 73/73 (4 legales .html sin barra por diseño: canonical = URL .html)
hreflang: 72 páginas con bloque en/es/x-default · 1 sin hreflang: es/tests/tmms-24 (solo-ES, limpia por decisión) ✔
recíprocos EN↔ES: 36 pares completos, no recíprocos 0 · autoinclusión 72/72 · colgantes hacia páginas inexistentes: 0
política x-default: →EN en 72/72 (uniforme en páginas)
sitemap <xhtml:link>: 70 urls con hreflang, 3 sin (tmms-24, privacy-policy.html, politica-privacidad.html; las 2 legales SÍ declaran hreflang en página) · x-default presente solo en 34 entradas; en 36 entradas el sitemap
  omite el x-default que la página sí declara (patrón mixto documentado en YER-1). Registrado M2.
```

## BATERÍA 4: Sitemap, robots y llms.txt

```
sitemap: 73 <loc> = 73 canónicas del repo (extras 0, ausentes 0, aliases sin barra 0) · XML bien formado · lastmod 73/73, futuros 0
  ANTES del fix: 69/73 desactualizados frente al último commit git (el banner del 09-03 y las ediciones del 09-04)
  DESPUÉS (T3): 2026-08-25 ×4 (legales) · 2026-09-03 ×65 · 2026-09-04 ×4 (pricing pair, yerevan pair)
robots.txt: "User-agent: *\nAllow: /\nDisallow:\n\nSitemap: https://baselinepsychotherapy.com/sitemap.xml" → sano; en vivo 200 text/plain
llms.txt: 38 líneas · en vivo idéntico al repo (sha1 igual). Línea a línea contra el sitio:
  L03 "founded in New York in 2019, now based in Singapore" → coincide con about/ e index ✔
  L05 "Individual $120 (60 min). Couples $170 (90 min). Free 15-min consultation" → ✔ pero FALTA "Focused Session $60 (30 min)" (canon PR-1) ✘
  L05 "Rated 5.0 on Google Reviews (22 reviews)" → index dice "22 Google Reviews" ✔
  L07 credenciales: 7 items, mismos nombres que los 7 <h3> de about/ y que hasCredential del schema ✔ (única variación: "PDP" entre
      comas en vez de paréntesis: cosmético)
  L11–L20 servicios EN: 10 enlaces, todos existen en repo ✔
  L21 screeners: "PHQ-9, GAD-7, CBI, WHO-5, DASS-21, TMMS-24" = seis ✔ (no dice "four")
  L22 herramientas: "breathing pacer and emotional meter" = dos ✔
  L24–L33 servicios ES: 8 enlaces existen ✔ pero FALTAN tests/herramientas, FAQ y crisis en ES ✘ (asimetría con EN)
  Yereván: AUSENTE en todo el archivo (existe /yerevan/ y /es/yerevan/ desde 2026-09-01) ✘
  Crisis (/crisis/) y Yandex/Mentalzon: ausentes (opcional)
  Afirmaciones falsas: 0 · afirmaciones caducas/incompletas: 3 (Focused, Yereván, sección ES). Registrado M1.
```

## BATERÍA 5: Entidad

```
sameAs: 1 único conjunto de 10 URLs, en 4 nodos (index, es/index, about, es/sobre-mi); las 69 Person restantes son referencias @id sin sameAs ✔
  Verificación en red (UA Chrome/128, -L):
  heallist 200 · internationaltherapistdirectory 200 · mentalzon 200 · share.google 200 (→ google.com/search, perfil GBP) ·
  amazon author 200 · expat.com 200 · psychologytoday 200 (→ /sg/counselling/jesus-hernandez-singapore-sg/1282908) ·
  therapyroute 200 · yandex.ru/profile 200 (→ yandex.com/profile/88929712346) ·
  linkedin 999 con GET / 405 con HEAD (bloqueo anti-bot estándar de LinkedIn: "verificada por existencia en conversación"); amazon 405 con HEAD / 200 con GET
  Inventario esperado cubierto: Google (share.google) ✔ Yandex ✔ Mentalzon ✔ Expat.com ✔ + sociales/directorios preexistentes ✔
Person: name "J.R. Hernandez" (alternateName "Jesus Hernandez" donde aplica) · jobTitle "Psychotherapist" ×43 / "Psicoterapeuta" ×20 (0 variantes) ·
  hasCredential 7 (nomenclatura = about/) en index, es/index, about, es/sobre-mi
Organization/MedicalBusiness: "Baseline Psychotherapy" · address addressCountry SG en 35/35 (Singapur base; Yereván sin address propia) ✔
logo/image: LOGO.webp y HERO.webp existen en repo y responden 200 en vivo ✔
```

## BATERÍA 6: Higiene profunda

```
em dashes: 0 en 76 html (incl. ediciones del dueño) · &amp;amp;: 0 · < crudos en JSON-LD: 0
& crudos en texto (HTML5-válidos, seguidos de espacio): index 15, faq 9, yerevan 2, es/yerevan 1, burnout 1 (CSS), workplace 1 (comentario),
  pricing 1 (edición del dueño) → FIX T1 en pricing; el resto es convención preexistente ("Burnout & Chronic Stress"), registrado M10
apóstrofes: 0 páginas con mezcla curly/straight en texto
hrefs internos rotos: 0 (relativos + absolutos baselinepsychotherapy.com) · anclas referenciadas inexistentes: 0
  (incl. banner → /pricing/#focused: id="focused" existe en pricing, es/precios, index, es/index, yerevan, es/yerevan)
tel:/mailto: 22 variantes, todas bien formadas (mailto:jr@… ×75 + 14 con ?subject= codificado; tel: 11 líneas de crisis)
target=_blank sin rel=noopener: 0 · restos "75 min": 0
blockquotes: 154 (inventario sha1 por página guardado como canon: 8 por cada una de las 7 páginas de servicio ×2 idiomas = 112,
  + 1 por cada uno de los 21 blogs ×2 = 42) · wa.me: 479 (canon post YER-2: 471 + 8)
precios visibles por superficie: coherentes con el canon en las 73 (home/servicios/yerevan: 60/120/430/1,200 (+107.50/100 por sesión);
  parejas: 170/620 (+155); pricing: escalera completa). Cifras ajenas (200/250/350/400, 8,640) son comparativas de mercado en blogs/FAQ.
```

## BATERÍA 7: Red de seguridad de las ediciones del dueño

Commits manuales: `f85dcd9` y `9f0d973` (2026-09-04, "Update index.html"), 1 archivo (pricing/index.html), 3 líneas:

1. Focused `price-desc`: + "one specific topic," → ES NO espejado ("Para identificar lo que estás atravesando, una consulta breve, dirigida a objetivos…" sin "un tema específico").
2. Couples `price-fmt`: "Both partners present" → "English & Spanish" → ES sigue "Ambos miembros presentes"; `&` crudo → FIX T1.
3. Burnout `price-desc`: "…with a written summary after every session and consultation by text." → "…with priority scheduling." → ES sigue "con resumen escrito después de cada sesión y consultas por mensaje de texto".

```
markup: balance <div>/<p>/<section> 0 · JSON-LD 0 err · schema OfferCatalog de pricing sin afectación (las frases editadas no viven en schema)
caracteres problemáticos: 1 (& crudo, corregido T1) · em dashes 0
render CDP (servidor local, chrome headless, viewport 1280×900 y 1280×800, 1440×900):
  /pricing/    @1280: 6 cards UNA línea · alturas 480×6 · ancho 188 · overflowX 0 · texto desbordado 0 · imágenes rotas 0 · banner visible
  /es/precios/ @1280: 6 cards UNA línea · alturas 570×6 · ancho 188 · overflowX 0
  Sliding Scale @1280×900 EN: fila de cards termina en y=978 · sección Sliding Scale top=1064 · h3 top=1092 → NO visible en el primer viewport
    (900 ni 800). ES: top=1181. @1440×900 EN: top=1073 → tampoco.
  Para que el h3 de Sliding Scale entre en 900px harían falta ~200px menos por encima (hero 113→470 + intro) o mover el bloque.
```

Registrado como **M5** (desync EN↔ES de copy: decisión del dueño) y **M6** (objetivo del primer viewport no cumplido: decisión de diseño).

---

## Hallazgos clasificados

**Triviales corregidos (3)**: T1 `&amp;` en pricing · T2 lastReviewed yerevan pair → 2026-09-04 · T3 sitemap lastmod = git (69 entradas, ver nota de reversión).

**Registrados para decisión (11)**:
- **M1 llms.txt caducado**: añadir "Focused Session $60 USD (30 min)" a Key facts; añadir Yereván (presencial con cita) y las páginas ES de tests/herramientas/FAQ/crisis. Propuesta de texto disponible a petición.
- **M2 sitemap x-default**: 36 entradas sin `x-default` que sus páginas sí declaran; uniformar añadiendo la línea (mecánico, 36 inserciones) o documentar el patrón mixto como aceptado.
- **M3 twitter:title** ausente en 69/73 (fallback og:title funciona en X/Twitter; añadirlo es mecánico si se quiere la triple unidad literal).
- **M4 hub FAQ**: 24 respuestas visibles con CTA `faq-link` final no reflejado en schema. Opciones: dejar (el CTA no es contenido de respuesta) o mover el enlace fuera del `faq-answer`.
- **M5 desync EN↔ES en pricing** por las 3 ediciones manuales del dueño (Focused "one specific topic", Couples "English & Spanish", Burnout "priority scheduling"): decidir si ES se espeja.
- **M6 Sliding Scale fuera del primer viewport** a 1280×900 (h3 en y=1092; medido). Reducir el hero/intro ~200px o reubicar el bloque.
- **M7 lastReviewed** de 19 MedicalWebPage (tests, hubs, crisis) no bumpeado por la inserción del banner (09-03): la regla literal lo exige, la semántica clínica no. Definir: ¿lastReviewed sigue a cualquier edición o solo a revisión de contenido clínico?
- **M8 meta descriptions >160**: 17 páginas (máx 210). Google trunca; no penaliza.
- **M9 404.html**: lleva Yandex Metrika pero ni GA ni Clarity (fuera del sitemap).
- **M10 `&` crudos preexistentes** (28 en 6 páginas, HTML5-válidos): normalizar a `&amp;` si se quiere uniformidad.
- **M11 Offers $620 en las homes sin precio visible** (index.html y es/index.html, 2 nodos por home: Service.offers y OfferCatalog). Opciones: retirar el Offer de parejas mensual del schema de la home (coherencia estricta schema=visible, como se hizo con la card) o mostrar el precio en la sección de servicios. Los 4 Offers de formación laboral sin `price` son semánticamente correctos (precio a consulta); opcionalmente añadir `priceSpecification` o dejarlos.

**Bloqueantes: 0.**

## Cánones actualizados (referencia)

wa.me = **479** · blockquotes = **154** (inventario sha1 en el reporte de sesión) · FAQ schema = **216** (39 FAQPage) · Offers = **70** (66 con price, 62 visibles) · sitemap = **73** · páginas interactivas sin Clarity/Metrika = **15** · sameAs = **10 URLs** en 4 nodos · MedicalWebPage con lastReviewed = **21** · precios canon: $60 / $120 / $170 / $430 ($107.50) / $620 ($155) / $1,200 ($100) · og:image = 14 archivos, todos en repo · x-default → EN.

## Método

Scripts Python sobre el árbol (parseo JSON-LD, extracción de FAQ visible por `faq-question`/`faq-answer` y `<h3>+<p>` en blogs, metas por regex, resolución de hrefs relativos/absolutos, inventario sha1 de blockquotes) · red con curl (UA Chrome, -L) · render con Chrome headless 152 vía CDP sobre `python3 -m http.server` (servidor apagado al terminar). Salidas completas pre y post-fix conservadas en el scratchpad de sesión (`inv1/static-out.txt`, `inv1/static-out-postfix.txt`, capturas `b7_*`).

---

## Doble auditoría

**Segundo auditor (agente independiente, solo lectura, cifras recomputadas con scripts propios)**: 14 puntos verificados. CONFIRMADOS 13/14: inventario 73/73, JSON-LD 0 err, Question 216, Offer 70, tipos prohibidos 0/0/0 y MedicalBusiness SG 35/35, FAQ 216/216 visibles con las 24 diferencias reducidas al `faq-link` final, canonical 73/73 y hreflang 72 + tmms-24, sitemap x-default 34/36 y lastmod 4/65/4 (= fecha git 73/73), metas, analítica 15/58, higiene (—0, rotos 0, anclas 0, noopener 0, 75-min 0, blockquotes 154, wa.me 479), los 3 fixes T1–T3 y el diff de 5 archivos, las 3 ediciones del dueño sin espejo ES, llms.txt, sameAs 10 URLs vivas, estructura de pricing (6 cards + sliding-scale). M6 (viewport) no re-medido por el auditor: queda como medición del primer pase.

**DISCREPA (1/14, punto 2)**: la afirmación original "70/70 Offers con precio en el canon y visible" era falsa. Cifras correctas: 66/70 con `price`; 62/66 visibles; los 4 Offers "Monthly Plan (Couples)" $620 de las dos homes no aparecen en la página (el primer pase confundió el color CSS `#0C1620` con el precio). Nota menor: LinkedIn/Amazon responden 405 a HEAD y 999/200 a GET.

**Resolución del primer auditor**: discrepancia aceptada íntegramente; Batería 1, veredicto ejecutivo y cánones corregidos en este mismo reporte; nuevo hallazgo **M11** registrado para decisión (no bloqueante: un Offer sin rich result no afecta la indexación, pero rompe la doctrina schema=visible del sitio). Firma del segundo auditor tras la corrección: ver línea final.

**Firma del segundo auditor tras la corrección (commit 7170966, recomputación propia sobre el árbol actual)**: Batería 1 Offers 70 / 66 con price / 66 en canon / 62 visibles CONFIRMADO · veredicto ejecutivo CONFIRMADO · M11 CONFIRMADO · nota LinkedIn/Amazon CONFIRMADO · sección "Doble auditoría" fiel a su veredicto CONFIRMADO. **FIRMA: CONFORME.** Salvedad mantenida: M6 (Sliding Scale fuera del primer viewport) es medición del primer auditor, no re-medida por el segundo.

**Veredicto propuesto al estratega**: capa invisible LIMPIA en lo estructural · 3 fixes triviales aplicados en esta rama (T1–T3) · 11 hallazgos registrados para decisión (M1–M11) · bloqueantes: 0. Sin merge hasta autorización.
