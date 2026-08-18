# ACTA DE GRADUACIÓN · Auditoría maestra de las 52 páginas
## baselinepsychotherapy.com

Fecha: 2026-08-18 · Base: `2ed0b4c` (main, verificado contra el hash mandado) · Rama: `graduation-review`

## RESUMEN EJECUTIVO

**¿El sitio está a prueba de balas? Técnicamente, sí; editorialmente, está graduado con registro.** La batería scriptada da CERO defectos en las ocho familias: estructura (126 JSON-LD válidos, HTML balanceado 52/52, hreflang recíproco 25/25, sitemap exacto), schema=visible (163/163 en sync por render real), anti-duplicación (0 FAQ repetidas, 0 encabezados de contenido repetidos), citas (0 sobre-atribuciones en las 28 frases, kit verificado), guardarraíles (em 0, wa.me 387, reseñas byte-idénticas, precios y conteo 22 exactos), enlaces (0 rotos entre ~todos los href del sitio, 479 externos correctos), entidad (0 regresiones, complementariedad 0) y encabezados/titles (0 defectos reales). La lectura humana de las 52 páginas encontró **cero bloqueantes**, una cosecha de **triviales inequívocos que quedaron corregidos en esta rama (92 líneas modificadas, 88 hunks, 37 archivos)** y una cola de **menores registrados sin tocar** cuyos tres frentes de mayor rendimiento son: (1) tres contradicciones factuales entre páginas (cifras de terapia por ciudad en Precios vs blogs, doctrina gestión-vs-regulación entre dos FAQs, TEPT mencionado sin página de servicio); (2) el clúster de diferenciación con filo (la afirmación absoluta "superará a una sesión presencial sin estructura... en cada medida de resultado" ×6 EN/ES y las pullas a apps/directorios/talleres genéricos, en tensión con la regla de diferenciación positiva); (3) repetición intra-página de tríadas clínicas en las páginas de servicio (regulación emocional y burnout las más cargadas). Nada de esto impide operar ni contradice puerta técnica alguna: son decisiones editoriales del dueño, listadas abajo con ubicación exacta. **La página protegida es/blog/burnout-expatriados se leyó (veredicto APROBADA, "estructura y flujo ejemplares"), recibió CERO ediciones y su diff contra main es vacío.**

**Veredicto propuesto: GRADUADO.** Bloqueantes: 0 · Triviales corregidos: 92 líneas modificadas en 37 archivos · Menores registrados: 58 entradas agrupadas en 8 familias.

## PARTE 1 · Batería scriptada (salida literal resumida; logs completos en la sesión)

**1. Integridad estructural**
```
JSON-LD: 126 bloques, 0 errores
HTML balanceado (parser, void-tags excluidos): desbalanceadas 0/52
hreflang: 50 páginas con bloque en/es/x-default · 25 pares únicos · autoinclusión y reciprocidad: 0 errores
canonical autorreferencial: 0 errores en 50 · sin canonical: 404.html y google048156ac86345d67.html (esperado: no indexables)
sitemap: 50 URLs = exactamente las 50 canónicas · extra 0 · faltantes 0 · duplicadas 0
lastmod: 0 fechas fuera de [2026-08-10, 2026-08-18] (ni futuras ni anteriores)
```

**2. Schema=visible (render real: HTMLParser con script/style excluidos, unescape, normalización de espacios)**
```
entradas FAQPage: 163 · desincronizadas: 0
```

**3. Anti-duplicación**
```
preguntas FAQ: 163 · duplicadas entre páginas: 0
H2/H3 idénticos entre páginas del mismo idioma: 61-64 coincidencias según normalización de <br>/entidades, TODAS de clases de plantilla legítimas:
  (a) títulos de posts/servicios repetidos como tarjetas de enlace ("Continue Exploring"/"Sigue Explorando",
      tarjetas de servicios relacionados, cards del índice del blog); (b) tarjetas de precios ("Individual
      Session", "Monthly Plan", "12-Session Program" y espejos ES); (c) pasos del proceso clínico ("Clinical
      Assessment", "Targeted Intervention", "Sustained Recovery/Integration" y espejos); (d) H3 "J.R. Hernandez" ×18 por idioma (10 author boxes + 8 bloques de credenciales/bio de servicios y libros); (e) H2 de secciones funcionales ("Online Psychotherapy Reviews" ×8,
      "Frequently Asked Questions" ×3, "Start Your Process" ×3 y espejos ES); (f) título del libro "Toto's
      Journey Through Emotions" ×2 (páginas de libros). Cero H2/H3 de CONTENIDO repetidos: los encabezados
      buscables de F2/F3 son únicos todos.
```

**4. Citas académicas**
```
S1 PMC10168168: 200 · S3 WHO: 200 · S5 nature nn.3093: 200 (UA navegador)
S2 29215315, S4 17576282, S6 30713811 (PubMed): 203 + interstitial de cookies (gating anti-bot de NLM a
  clientes no-navegador; los PMID son permalinks estables). Verificación de identidad vía Europe PMC REST:
  29215315 = Carlbring 2018 "Internet-based vs. face-to-face CBT..." · 17576282 = Lieberman 2007 "Putting
  feelings into words..." · 30713811 = Hofmann & Hayes 2019 "The Future of Intervention Science: PBT". ✓
enlaces de cita en el sitio: 28 · páginas con >2: ninguna
sobre-atribuciones: 0. Muestreo completo de las 28 frases: equivalencia (nunca superioridad) en S1/S2;
  ansiedad→"anxiety disorders", depresión→"depressive disorders"; regulación emocional cita SOLO el hallazgo
  general sin extenderlo a su condición; burnout/PTSD/parejas formulados como claims de práctica ("at this
  practice"); S3 solo fenómeno ocupacional OMS; S4 solo labeling/amígdala; S5 solo neuroplasticidad adulta;
  S6 solo formalización de PBT (Hayes & Hofmann 2018/2019).
```

**5. Guardarraíles de marca**
```
em dashes (— y entidades): 0 · wa.me/6593729100: 387 · blockquotes: 146
blockquotes byte-idénticos vs 959f8ec (pre F3-C/G; rondas previas verificadas en su día): 0 archivos alterados
precios: pricing y es/precios con $120, $170, $430, $620, $1,200 exactamente 1 vez en la tarjeta de precio (`<span class="price">`) de cada superficie (las menciones de $120/$170 en title/meta/og son las esperadas)
conteo de reseñas: 17/17 menciones en 22 · menciones con otro número: 0 · aggregateRating en schema: 0
duración del taller en horas: 0 menciones (homes + taller EN/ES)
```

**6. Enlaces**
```
internos rotos: 0 · variantes sin barra final: 0 · anclas (#) rotas: 0
mailtos mal codificados: 0 · externos: 479, todos con target="_blank" + noopener: 0 problemas
enlaces de rating: 36, todos a https://share.google/dQE0CvnGhGx0mbjZq · desviados: 0
```

**7. Entidad**
```
regresiones de nomenclatura de credenciales (vs canon docs/credential-inventory-baseline.md): 0
cargo canónico: 18 EN + 18 ES · desviaciones: 0
author box: 20/20 posts · texto renderizado ÚNICO por idioma (1 EN, 1 ES)
  (cosmética de fuente sin efecto visual en 4 posts: indentación distinta en el par de parejas;
   &rarr; en vez de → literal en el par de profesionales — registrado, no tocado)
llms.txt: $120 ✓ · (22 reviews) ✓ · credenciales canónicas ✓ · sin horas de taller ✓ · sin aggregateRating ✓ · sin em dash ✓
complementariedad (FAQ marca, hero About, author box, llms.txt; prosa, n-gramas de 13): 0 colisiones
```

**8. Encabezados y titles**
```
pareamiento ¿? en ES (conteo interno por encabezado): 0 defectos (el patrón "¿Pregunta? Resto" es válido)
preguntas invertidas EN sin "?": 0 (las formas "What/How/Why + declarativa" son indirectas, no interrogativas)
title == og:title: 50/50 idénticos (unescape) · twitter:title explícito: solo 4 páginas (homes, pricing,
  es/precios), idéntico donde existe; en las otras 46 Twitter cae a og:title == title (menor registrable)
titles >65 caracteres: 0
```

## PARTE 2 · Registro de veredictos: las 52 páginas

Checks scriptados: ✓ en las 52 (la batería es global y dio cero defectos; las columnas por página serían todas idénticas). Veredicto = lectura humana completa (dos auditores independientes, EN y ES). "corr." = los triviales de esa página quedaron corregidos en esta rama; lo demás de la nota queda registrado sin tocar.

| # | ruta | veredicto | notas |
|---|---|---|---|
| 1 | 404.html | FUERTE | Bilingüe, funcional; matiz: contracciones EN contra la voz del sitio. |
| 2 | index.html | APROBADA con registro | "three continents" es no-defecto (modelo continental de 6, coherente con "tres continentes" ES); FAQ comparte redacción con Approach 03; "with expert guidance throughout" filler; trust bar 10,000+/5,000+ horas invita escepticismo. |
| 3 | about/index.html | APROBADA con registro | Fundación NY-2019 enunciada 3 veces (intro, PBT, "Why This Practice Exists"); "three continents" ídem no-defecto. |
| 4 | anxiety-therapy-online | APROBADA (corr.) | corr.: "start of the process". Registro: tríada TCC/exposición/sistema nervioso 2 veces casi literal (cuerpo vs fase 02). |
| 5 | blog/index.html | APROBADA con registro | Tarjeta de depresión titula distinto que el H1 destino (tres títulos para un artículo, con la related-card). |
| 6 | blog/burnout-vs-depression | APROBADA (corr.) | corr.: serial comma author box. Registro: marcadores 1 y 5 son el mismo discriminador; cierre reformula la tesis 3 veces. |
| 7 | blog/does-online-therapy-work | APROBADA (corr.) | corr.: serie de expats; serial comma. Registro: equivalencia 3 veces en el primer tercio; "on every outcome measure" absoluto sin cita; checklist prometida como párrafo corrido. |
| 8 | blog/emotional-intelligence-mental-health | APROBADA (corr.) | corr.: "data... improve". Registro: lista de condiciones 3 veces; "the research is unambiguous" sin cita. |
| 9 | blog/emotional-regulation-techniques | APROBADA (corr.) | corr.: serial comma. Registro: contradicción respiración/amígdala; Nivel 3 re-lista técnicas 1, 3, 4. |
| 10 | blog/expat-burnout | APROBADA (corr.) | corr.: serial comma. Registro: cápsula-snippet de los 6 signos fusionada dentro del h3 del signo 1 (colocación del Comando E; mover requiere decisión). |
| 11 | blog/expat-couples-therapy | APROBADA (corr.) | corr.: coma serial del author box. Registro: H2 entero "Why Regular Couples Therapy Misses This" atribuye fallo a terceros; evidencia de parejas extendida sin cita; lista prometida como párrafo. |
| 12 | blog/high-functioning-anxiety-finance | APROBADA (corr.) | corr.: serial comma. Registro: "tax on every unit of performance" repetido; tríada de costos 3 veces. |
| 13 | blog/how-to-know-if-you-need-therapy | APROBADA (corr.) | corr.: serial comma. Registro: 5 superlativos sin cita; signo 7 calcado de la FAQ de numbness del hub. |
| 14 | blog/online-depression-treatment | APROBADA (corr.) | corr.: puntuación AmE ×2, h2 "The". Registro: las 3 FAQ reformulan el cuerpo con redacción compartida; claim de activación conductual 4 veces. |
| 15 | blog/online-therapy-high-performers | APROBADA (corr.) | corr.: 5 apóstrofos, serial comma. Registro: metaanálisis+cláusula de práctica 2 veces; 4 pullas; cifras de ciudad vs Precios. |
| 16 | burnout-therapy | APROBADA (corr.) | corr.: guiones-raya, coma, vacation, "the process". Registro: HPA/prefrontal repetidos; "rest does not repair" ×4. |
| 17 | couples-therapy-online | APROBADA (corr.) | corr.: artículo, 3 comas seriales, ojal. Registro: "Both partners must be present" literal ×2 (la 2ª no responde su FAQ); "structured neutrality" ×4. |
| 18 | depression-therapy-online | APROBADA (corr.) | corr.: "the process". Registro: tríada fase 02 duplicada; "thoughts of death" sin línea de crisis (propagar la de blog/odt). |
| 19 | emotional-intelligence-books | APROBADA con registro | Capitalización EI inconsistente; masterclass del cierre no existe en Precios. |
| 20 | emotional-regulation-therapy | APROBADA (corr.) | corr.: "the process". Registro: la página más repetitiva del sitio (2 tríadas ×3 veces); tarjeta de terminología dentro del grid de síntomas. |
| 21 | expat-therapy | APROBADA (corr.) | corr.: apositivo, serial comma, vacations, "the process". Registro: lista ansiedad/depresión/burnout literal en tarjeta y FAQ; beat bilingüe ×2. |
| 22 | faq/index.html | APROBADA (corr.) | corr.: serial comma. Registro: "six time zones" es defendible (distribución real de clientes) pero convive mal con "21+ países"; ratio de respiración contradictorio entre 2 respuestas; claim absoluto "outperform". |
| 23 | google048156ac86345d67.html | APROBADA | Token de verificación; sin superficie editorial. |
| 24 | policies.html | APROBADA (corr.) | corr.: counseling ×2. Registro: Setmore contradice WhatsApp-only del resto; sin recursos de crisis pese a excluir intervención en crisis. |
| 25 | pricing/index.html | APROBADA (corr.) | corr.: "between sessions", "60- or 75-minute" (visible+schema), afterward. Registro: tríada antes/durante/después ×4; 3 pullas; sin breadcrumb; cifras de ciudad vs blog. |
| 26 | privacy-policy.html | FUERTE | Ejemplar: cada encabezado entrega, tabla de cookies = banner, retenciones concretas, cero repetición. |
| 27 | workplace-mental-health-training | APROBADA (corr.) | corr.: "It needs regulation.". Registro: H2 de costos sin cifra; doble puntero "the patterns below"; 6 desmarques anti-wellness. |
| 28 | politica-privacidad.html | APROBADA (corr.) | corr.: "junio de 2026". Registro: © 2019–2026 vs © 2019 del resto (las 2 privacidad+políticas EN igual: decisión de plantilla); registro de "usted" (convención legal, coherente). |
| 29 | es/index.html | APROBADA (corr.) | corr.: guion-raya, footer "Políticas de Servicio y Reembolso". Registro: FAQ "evaluación primero"/"fase final" repiten secciones; "garantiza" ×3 (de proceso, roza el borde); 6 credenciales vs 7 del About (decisión Comando D, documentada). |
| 30 | es/sobre-mi | APROBADA con registro | "Libros e Investigación" no entrega investigación; vídeo/postgrado/imaginería divergen del léxico mayoritario. |
| 31 | es/precios | APROBADA (corr.) | corr.: pericia, Ir al contenido, Sin derivación. Registro: badges repetidos en "La Diferencia" y FAQ; 3 pasivas encadenadas; cifras de ciudad vs blog. |
| 32 | es/preguntas-frecuentes | APROBADA (corr.) | corr.: 11 tildes (visible+schema), aplanamiento ×2, Ir al contenido. Registro: "desregular el sistema nervioso" como objetivo invierte el sentido (FAQ, requiere resync si se toca); "abrumamiento" ×3; "entregar" ×5. |
| 33 | es/politicas.html | APROBADA con registro | Reembolsos repite la negativa 2 veces seguidas; "Agenda" como encabezado; © coherencia con la de privacidad. |
| 34 | es/libros-inteligencia-emocional | APROBADA (corr.) | corr.: punto fuera de comillas. Registro: TREC usada antes de definirse; masterclass sin página. |
| 35 | es/formacion-salud-mental-laboral | APROBADA (corr.) | corr.: comillas ES, "Tu Organización". Registro: H2 de costos sin cifra; ojal "Qué se cubre" sobre problemas; encabezado idéntico a su FAQ. |
| 36 | es/regulacion-emocional | APROBADA (corr.) | corr.: estímulo, sereno. Registro: 2 tríadas ×3 veces; contradice a Preguntas Frecuentes en gestión-vs-regulación (elegir doctrina). |
| 37 | es/terapia-ansiedad | APROBADA (corr.) | corr.: estado por defecto. Registro: cierre de "Por Qué" anticipa fase 02 casi literal; "corre"/"un estimado de" calcos. |
| 38 | es/terapia-burnout | APROBADA (corr.) | corr.: no solo, estas, guiones-raya (visible+schema). Registro: "corteza prefrontal... déficit crónico" literal ×2; "el descanso no repara" ×5. |
| 39 | es/terapia-depresion | APROBADA con registro | Criterios DSM-5 casi calcados sección↔FAQ; tríada fase 02 duplicada; "no se levanta" ×3. |
| 40 | es/terapia-expatriados | APROBADA (corr.) | corr.: "En su lugar,...". Registro: lista de 3 condiciones literal tarjeta↔FAQ (la duplicación más flagrante ES); párrafo bilingüe casi calcado; "disrupción" ×5; 2 niveles vs 3 del post protegido. |
| 41 | es/terapia-parejas | APROBADA (corr.) | corr.: "Inglés o Ambos" en markers ×2 y en el H1 (este último por ORDEN EXPLÍCITA del estratega, 2026-08-18, tras su pasada independiente). Registro: tú/ustedes/nosotros mezclados; "participantes en un sistema" en 2 FAQ contiguas. |
| 42 | es/blog/index.html | APROBADA con registro | 3 tarjetas titulan distinto que el H1 destino (incluida la del post protegido; la tarjeta es editable con orden). |
| 43 | es/blog/ansiedad-alto-funcionamiento-finanzas | APROBADA con registro | Voz excelente; "el impuesto que hoy pagas" repetido literal; "pre-viviendo" registrado como neologismo deliberado (voz del post, conservado). |
| 44 | es/blog/burnout-expatriados | APROBADA · PROTEGIDA | Leída completa: estructura y flujo ejemplares, sin duplicaciones internas. CERO ediciones; diff vs main = 0 bytes. Calcos menores solo registrados ("sobremarcha adaptativa", "el estresante", "meses o años después de la experiencia"). |
| 45 | es/blog/burnout-vs-depresion | APROBADA (corr.) | corr.: "desactivarse eficazmente". Registro: "el estresante" como sustantivo ×3; cierre reformula tesis 3 veces. |
| 46 | es/blog/como-saber-si-necesitas-terapia | APROBADA con registro | "ir por los movimientos" ×2 y "corriendo por debajo" ×2 (calcos); §7 calcada de Preguntas Frecuentes; H1 vs tarjeta del índice. |
| 47 | es/blog/funciona-la-terapia-online | APROBADA (corr.) | corr.: "se equiparan". Registro: equivalencia 3 veces en 3 párrafos; giro "la pregunta correcta" repetido. |
| 48 | es/blog/inteligencia-emocional-salud-mental | APROBADA (corr.) | corr.: Ir al contenido. Registro: anuncia "las otras tres ramas" y cita dos; "no es correlacional, es mecanicista" sobredeclara sin cita. |
| 49 | es/blog/tecnicas-regulacion-emocional | APROBADA (corr.) | corr.: aplanamiento ×2, Dialéctico-Conductual. Registro: Nivel 3 re-describe técnicas ya enumeradas. |
| 50 | es/blog/terapia-online-profesionales | APROBADA (corr.) | corr.: Ir al contenido, Sin derivación. Registro: metaanálisis citado 2 veces en 2 párrafos; cifras vs Precios; calcos ("los últimos vapores", "la matemática es directa"). |
| 51 | es/blog/terapia-parejas-expatriados | APROBADA con registro | Atribuye fracaso a otros terapeutas (rubro c); extiende evidencia individual a parejas sin cita; única página con comillas angulares «» (correctas per RAE; decidir estándar). |
| 52 | es/blog/tratamiento-depresion-online | APROBADA (corr.) | corr.: cognitivo-conductual. Registro: las 3 FAQ reformulan el cuerpo con redacción compartida. |

## PARTE 3 · Hallazgos clasificados

### Bloqueantes: NINGUNO

### Triviales corregidos en esta rama (92 líneas modificadas / 88 hunks en 37 archivos por git diff; todas las ocurrencias visible+schema para preservar el sync)

**EN**: 7 reparaciones de gramática/texto roto (artículo faltante en couples, fragmento "It needs regulation.", concordancia "data... improve", apositivo de expat-therapy, "availability between sessions", serie de expats en does-online-therapy-work, "at the start of the process" ×5 páginas); 17 de puntuación (guiones-raya de burnout-therapy ×2 visible+schema, serial commas en couples ×3 + expat + does-online + el author box de los 10 posts y faq ×11, comillas AmE ×2 y h2 "The" en online-depression-treatment, "60- or 75-minute" ×2 visible+schema); 5 de inglés americano (counseling ×2 en policies con BACP/SAC intactos, vacation/vacations, afterward); 5 apóstrofos tipográficos (&#8217;→' en high-performers). **ES**: 11 tildes en preguntas-frecuentes (cada una ×2, visible+JSON-LD, resync automático por reemplazo total); léxico no-nativo con equivalente inequívoco (el default→el estado por defecto, input→estímulo, compuesto→sereno, expertise→pericia, planitud/planeidad→aplanamiento ×3, desregularse→desactivarse en burnout-vs-depresion, equiparan→se equiparan, "En su lugar," reordenado); puntuación española (comillas de formacion y libros, "Inglés o Ambos/ambos" ×2 en markers, guiones-raya de es/index y es/terapia-burnout ×2 v+s, cognitivo-conductual y Dialéctico-Conductual); plantilla ("Ir al contenido" ×4, "Sin derivación" ×2, footer de es/index a la convención de 24 páginas, "Tu Organización" en el CTA de formacion, "junio de 2026").

**Excepción aplicada, revertida y luego ordenada**: la coma del H1 de es/terapia-parejas ("Español, Inglés, o Ambos") entró en el lote y se REVIRTIÓ de inmediato (la regla permanente "H1s y titles intactos salvo orden explícita" manda sobre la excepción de typos). Tras la pasada independiente del estratega llegó la ORDEN EXPLÍCITA (2026-08-18) y el H1 quedó corregido a "Español, Inglés o Ambos". El title de la página nunca tuvo la coma.

### Menores registrados sin tocar (58 entradas, 8 familias)

**1. Contradicciones factuales entre páginas (prioridad alta)**: cifras de terapia por ciudad: pricing/es-precios dicen NY $300-400, Londres £150-250, Singapur $200-300; los blogs de profesionales dicen NY $250-400, Londres £100-200, Singapur $200-350 SGD (además del cambio de divisa). Cuatro cifras en conflicto entre las dos superficies EN y sus espejos ES (el reencuadre del Comando G tocó los blogs; Precios conserva sus rangos previos). · Doctrina gestión-vs-regulación: es/regulacion-emocional y emotional-regulation-therapy responden "es lo mismo"; es/preguntas-frecuentes responde que son procesos distintos. Elegir una (ambos lados son FAQ: resync obligatorio al tocar). · TEPT/PTSD citado como condición tratada en faq, does-online-therapy-work, online-therapy-high-performers y espejos ES, sin página de servicio ni mención en nav. · policies.html ofrece pago "credit card (via Setmore)" mientras todo el sitio es WhatsApp-only sin formulario. · faq afirma plataformas "encrypted... comply with professional telehealth standards" sin el matiz de policies ("no online platform can guarantee absolute security"). · Intervención en 2 niveles (es/terapia-expatriados) vs 3 niveles (post protegido; el lado ajustable es la página de servicio).

**2. Diferenciación con filo (rubro c, tensión con la regla de diferenciación positiva)**: "A well-structured online session with a specialized therapist will outperform an unstructured in-person session with a generalist on every outcome measure" en faq + 2 blogs EN y sus 3 espejos ES: absoluto, sin cita, no testado por los metaanálisis citados. · Pullas a categorías de competidores: "therapist who lists twenty-five specialties" (pricing + high-performers + espejos), "$60/week therapy app" (pricing), "moved their practice online when the pandemic hit and never moved it back" (high-performers), 6 desmarques anti-wellness-workshop (workplace + formacion), H2 completo "Why Regular Couples Therapy Misses This" (expat-couples + espejo). · "Park Avenue rent" reutilizado en 2 posts EN + 2 ES.

**3. Repetición intra-página con redacción compartida (violaciones de la doctrina cápsula→referencia)**: emotional-regulation-therapy / es/regulacion-emocional (2 tríadas ×3 veces cada una: la página más cargada); es/terapia-expatriados (lista de 3 condiciones literal tarjeta↔FAQ + beat bilingüe); couples ("Both partners must be present" ×2, la 2ª fuera de lugar); es/terapia-depresion y depression-therapy-online (tríada fase 02); es/terapia-burnout / burnout-therapy (frases HPA/prefrontal, "el descanso no repara" ×4-5); tratamiento-depresion-online / online-depression-treatment (las 3 FAQ reformulan el cuerpo); formacion (2 literales sección↔FAQ); precios (badges ×3 superficies); anxiety/es-ansiedad (cierre anticipa fase 02).

**4. Duplicación entre páginas fuera de plantilla**: párrafo de numbness/vacío compartido palabra por palabra entre faq/preguntas-frecuentes y el post de señales (§7, ambos idiomas); bloque "¿Regulación o gestión?" casi calcado entre página de servicio y post de técnicas.

**5. Seguridad/deber de cuidado**: la línea de crisis de blog/online-depression-treatment ("Contact your country's emergency services...") no existe en depression-therapy-online ni en faq, que sí listan "thoughts of death". Propagar.

**6. Superficies y claims**: trust bar "10,000+ Hours of Professional Training" junto a "5,000+ Therapy Hours"; superlativos sin cita (5 en how-to-know, "unambiguous"/"mecanicista"/"consenso establecido"/equivalencia extendida a parejas en 4 posts); "with expert guidance throughout" y "Es una disrupción funcional respaldada por la ciencia" como filler firmable; masterclass mencionada solo en las 2 páginas de libros; workplace/formacion H2 de costos sin cifra.

**7. Léxico y notación**: calcos ES recurrentes registrados sin tocar (entrega/deliver ×6, correr/run ×5, abrumamiento ×3, "el estresante" ×3 —1 en protegida—, "una mecha más corta", "llamada de alcance", etc.); vídeo/video, postgrado/posgrado, conciencia/consciencia, online/en línea, imaginería/imaginación guiada; comillas angulares «» solo en 1 post (correctas per RAE: decidir estándar); notación 5/5 vs 5.0; coma serial ES anglicada en 4 páginas; contracciones EN solo en 404; títulos de libros en inglés vs traducidos según página; "Agenda" como encabezado en es/politicas.

**8. Estructura**: cápsula-snippet de expat-burnout fusionada dentro del h3 del signo 1 (colocación del Comando E: mover pide decisión); 2 listas prometidas entregadas como párrafo corrido (expat-couples, does-online-therapy); tarjeta de terminología dentro del grid de síntomas (emotional-regulation + es/regulacion); ojal "Qué esperar" sobre síntomas en 6 servicios ES colisionando con su sección real de "¿Qué Esperar...?"; ojal "Online Therapy Services" sobre "What Conditions..." en 5 servicios EN; pricing sin breadcrumb; twitter:title explícito solo en 4 páginas (las 46 restantes caen a og:title==title: comportamiento correcto); tarjetas de índice vs H1 destino (3 casos por idioma); FAQ hub con 5 prompts de contacto asimétricos; footers © 2019 vs © 2019–2026 en legales.

**No-defectos explicados (para que nadie los "corrija")**: "six countries on three continents" es correcto bajo el modelo continental de América unificada (coherente con "tres continentes" en los espejos ES: decisión de voz del dueño); "six time zones" en faq es distribución real de clientes, no cobertura geográfica; "22" consistente en las 17 superficies; "the documented piece of that investment" funciona con artículo definido en su contexto de compliance; "pre-viviendo" es neologismo deliberado de la voz del post de finanzas; "vía Google Meet" en servicios ES es convención de familia documentada.

## Reglas permanentes vigentes (inventario para futuros comandos)

1. Cero em dashes (—) en todo el sitio, incluidas entidades.
2. Precio $120 y CTAs de WhatsApp intocables en presencia y destino; los bugs de parámetros sí se corrigen (doctrina F3-A/B4).
3. Schema = texto visible carácter a carácter; resync del FAQPage en el mismo cambio que toque texto visible de FAQ.
4. Ninguna pregunta FAQ duplicada entre páginas (hoy: 163 únicas).
5. Complementariedad: sin secuencias >12 palabras entre superficies de entidad (FAQ de marca, hub, hero del About, author box, llms.txt); bloques funcionales compartidos exentos.
6. Doctrina cápsula→referencia: las FAQ son cápsulas autocontenidas; cápsula y sección dicen los mismos hechos con PALABRAS DISTINTAS.
7. Diferenciación positiva: no atribuir fallas a terceros.
8. Reseñas de clientes byte-intocables (146 blockquotes).
9. H1s y titles intactos salvo orden explícita (ejercida hoy en ambos sentidos: reversión preventiva de la coma del H1 de es/terapia-parejas y corrección posterior por orden explícita).
10. Inglés americano; español nativo sin calcos.
11. sitemap lastmod actualizado en el mismo commit que toque la página.
12. Kit de citas cerrado S1-S6; máximo 2 enlaces de cita por página; S1 solo ansiedad/depresión (burnout/TEPT/parejas como claims de práctica, "at this practice").
13. Protocolo de rama: `<comando>-review` + docs/reports/<comando>-report.md; main intacta hasta autorización; merge con merge commit conservando historia; deploy poll ≤5 min + verificaciones en vivo.
14. Puerta de punta de rama (2026-08-18): imprimir y comparar el hash de la punta contra el último reportado antes de todo merge; si difieren, detenerse.
15. es/blog/burnout-expatriados: PROTEGIDA, cero ediciones (posición 4, CTR 12.5%).
16. Conteo de reseñas: actualizar solo vía docs/update-review-count.md (17 superficies, hoy 22).
17. Sin duración del taller en horas; oferta "Focused Session/Full Program" ("Sesión Esencial/Programa Completo").
18. Credenciales y cargo según docs/credential-inventory-baseline.md (formas cortas solo en los h4 de las homes; credencial 7 fuera de homes).
19. Voz de marca conservada por decisión: "running on fumes", jerga financiera (after-hours, P&L), "pre-viviendo".
20. Sin aggregateRating en el schema (el rating vive como texto visible enlazado a share.google/dQE0CvnGhGx0mbjZq).
21. Enlaces de rating con target="_blank" rel="noopener" y display:contents.

## Cierre

Batería: 8/8 familias en cero defectos · Lectura: 52/52 páginas con veredicto (2 FUERTES, 50 APROBADAS de las cuales 37 con triviales corregidos) · Bloqueantes: 0 · Página protegida: intacta (diff 0 bytes). Hashes: base main `2ed0b4c` · rama `graduation-review` (commit del acta en el propio historial de la rama). Doble auditoría del acta: el tercer auditor reprodujo independientemente la batería completa (8/8), los 10 triviales muestreados, la página protegida (0 bytes), la reversión del H1 y 3 menores al azar; discrepó ÚNICAMENTE en 6 asientos contables del propio documento (conteo de filas corr., métrica de reemplazos, redacción del check de precios, un ×3 que era ×2, la etiqueta del H3 ×18 y el estado untracked del acta), todos corregidos en esta versión. Con esas correcciones aplicadas: **FIRMADO** (condición del auditor cumplida; cero defectos de sitio, cero bloqueantes, cero violaciones de regla permanente).

