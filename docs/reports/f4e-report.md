# Reporte Comando F4-E · Recovery Half-Life Check + Thought Record (par EN/ES cada una)

Fecha: 2026-09-10 · Base: `2c90904` (main) · Rama: `f4e-review` · Estado: vista previa para VEREDICTO DOBLE, SIN merge.

Las dos herramientas se construyen como unidades independientes (script de montaje propio, integraciones propias, commits separados) para que el dueño pueda aprobar una y descartar o ajustar la otra con separación limpia.

## Estado por unidad

| Unidad | Estado |
|---|---|
| **Herramienta 2 · Thought Record** | COMPLETA en la rama: par EN/ES, integraciones, suite, render, prueba funcional, segunda auditoría |
| **Herramienta 1 · Recovery Half-Life Check** | BLOQUEADA por contenido: el comando remite al bloque del estratega (intro, 8 preguntas con opciones a-d, 3 bandas) "provisto en la conversación", pero ese bloque no está en la conversación ni en el repo. Mecánica lista para montarse al recibirlo (ver abajo) |

---

## Herramienta 2 · Thought Record

/tests/thought-record/ · /es/tests/registro-pensamientos/ — construidas por sustitución anclada sobre las plantillas de herramienta (emotional-meter / medidor-emocional): nav idéntico salvo conmutador al par, banner, cookies, footer y scripts de chrome byte-idénticos; CSS de la plantilla íntegro más reglas `.tr-*` propias.

| | EN | ES |
|---|---|---|
| Title | Thought Record: Separate Facts From Interpretation \| CBT Tool (61; el propuesto excedía 65 y se recortó "Free") | Registro de pensamientos: separa hechos de interpretación (57) |
| Meta description | 157 | 160 |
| Intro | Empieza con la frase aprobada ("A thought record is one of the oldest and best-tested tools in cognitive-behavioral therapy…") y completa la promesa de privacidad y la descarga local. La TCC nombrada como origen, sin reclamo de originalidad | Espejo nativo en tú |
| Schema | MedicalWebPage (lastReviewed 2026-09-10, reviewedBy #jr) · BreadcrumbList · MedicalBusiness · FAQPage (4). Sin Quiz | idem |

Nota: del "intro aprobado" solo constaba en el comando la primera frase; el resto se redactó con los elementos que el spec exige (privacidad, descarga, origen TCC). Revisable por el dueño.

**Anatomía de la herramienta**: progreso visible de 8 segmentos (1, 2, 3, 3b, 4, 5, 6, 7) con `role="progressbar"`, contador "Step n of 7" con aria-live, un panel por paso (`role="group"` + aria-labelledby), botones Atrás/Siguiente/Ver mi registro, resumen final con Antes/Después y botón de descarga, "Empezar de nuevo", puente al método y nota de privacidad.

**Los 7 pasos + 3b (cambios del dueño aplicados)**:
- Escala **0-10** en pasos 2 y 7: `input type=range min=0 max=10 step=1` con `<output>` grande visible y extremos etiquetados.
- **Ejemplo guía visible en cada paso** (`<details>` nativo "Example", en gris bajo el campo) con el caso conductor coherente: P1 hechos de cámara (martes 16:40, presentación, jefa mira el teléfono dos veces y sale sin comentar) · P2 "Ashamed, 7." / "Vergüenza, 7." · P3 pensamiento automático · P3b "Mind reading + fortune telling" · P4 evidencia a favor · P5 evidencia en contra · P6 pensamiento equilibrado con la fórmula desplegable "It is true that X, and also true that Y." / "Es cierto que X, y también es cierto que Y." · P7 "Ashamed: from 7 to 4." con la lectura honesta en el resumen: "The goal was never zero: a thought record does not delete emotions, it right-sizes them." / "El objetivo nunca fue cero: un registro de pensamientos no borra las emociones, las pone en su tamaño real."
- **Paso 3b (opcional)** "Does your thought wear one of these disguises?": 11 distorsiones, cada una con definición de una línea y micro-ejemplo del caso. ES con nombres establecidos: lectura de la mente, catastrofización, pensamiento todo o nada, sobregeneralización, filtro mental, descalificar lo positivo, adivinación del futuro, razonamiento emocional, los "debería", personalización, etiquetado.
- **Afinación del paso 5**: ayuda base siempre; líneas adicionales para mind reading ("what do you actually know about their thoughts, versus assume?"), catastrophizing, all-or-nothing y fortune telling (4 afinaciones); el resto usa la ayuda genérica. Se recalcula al marcar y al entrar al paso 5.
- **Re-medición**: resumen con Antes/Después; si Después ≥ Antes aparece la nota honesta adicional ("If the number did not move, that is information too…").
- **Descarga local**: "Download my record" / "Descargar mi registro" genera un .txt con Blob + URL.createObjectURL (cero red): título, fecha, los 7 pasos, "3b. Disguises marked" con la lista, y "Change: 7 → 4" + lectura honesta. Nombre `thought-record-AAAA-MM-DD.txt` / `registro-pensamientos-…`.
- **Cierre**: "This is the practical form of a distinction explored in depth in The Baseline Psychotherapy Protocol: separating data from interpretation." (enlace a /method/) / ES espejo (a /es/metodo/) + CTA estándar wa.me.

**FAQs (4)**: qué es y de dónde viene (TCC, Beck; "not an invention of this practice") · si sirve por tu cuenta · qué pasa si la emoción no baja · privacidad (nada se guarda ni se envía; la descarga es un archivo local tuyo).

**Reglas de páginas interactivas** (auditoría de código): Clarity 0 · Metrika 0 · GA solo tras consentimiento (bootstrap de la plantilla) · en el script de la herramienta: localStorage 0, sessionStorage 0, fetch 0, XMLHttpRequest 0, sendBeacon 0, WebSocket 0 (los únicos `sessionStorage` de la página son los del banner de anuncio heredado del chrome) · sin `<form>` · auditoría de red en tiempo de ejecución (CDP Network, carga + recorrido completo de los 7 pasos): único host contactado `localhost:8000`. Criterio de interactivas: 15 → 17 páginas sin Clarity/Metrika (las 15 previas + este par).

**Accesibilidad**: labels asociados en todos los campos, rangos con aria-valuemin/max/now, `<details>` nativo para ejemplos, botones reales, sin tabindex positivo, sin captura de Tab; foco al título del paso al avanzar. Reduced motion: reglas de la plantilla + desactivación de transiciones `.tr-*`. Móvil primero: paneles a ancho completo, botones a 48 px de alto y ancho completo en ≤768.

### Prueba funcional (Chrome headless, EN y ES, 1280 y 375)

| Comprobación | Resultado |
|---|---|
| Inicio en paso 1, un solo panel visible, Atrás y Descargar ocultos (display none) | OK |
| Rangos 0-10 en pasos 2 y 7; `<output>` sigue al slider | OK |
| 3b: 11 casillas; marcar mind + fortune → ayuda del paso 5 con base + 2 líneas afinadas, sin catastrofización | OK |
| Paso 7 muestra "Ashamed: Before 7"; botón "See my record" | OK |
| Resumen: Before 7 · After 4 + lectura honesta; texto de descarga 31 líneas con lista 3b y "Change: 7 → 4" | OK |
| Ruta sin mejora (After 8 ≥ Before 7): nota adicional visible | OK |
| Reset: paso 1, campos vacíos, sliders a 5, casillas desmarcadas | OK |
| Imágenes completas, sin overflow horizontal, H1 libre | OK |

Corrección detectada en el render y aplicada: los botones con `hidden` se mostraban igualmente porque `.btn{display:inline-flex}` vence al `[hidden]` del navegador; añadida `.tr-nav .btn[hidden],.tr-panel[hidden]{display:none}` y re-verificado por computed style.

### Integración (unidad Thought Record)
1. Hub /tests/ y /es/tests/: card tras el Medidor Emocional con el patrón existente (h3, tipo, meta "7 steps · ~10 minutes", enlace), `transition-delay:.18s` reservando el .12s para la card del Check (que irá tercera).
2. /method/ y /es/metodo/: en el bloque del libro, "The thought record on this site is the practical companion to that chapter." / "El registro de pensamientos de este sitio es el compañero práctico de ese capítulo." con enlace; lastReviewed 2026-09-09 → 2026-09-10 por edición de contenido.
3. llms.txt: línea EN y ES (qué es, origen TCC, 7 pasos, 11 distorsiones, descarga local, nada se guarda).
4. sitemap.xml: 77 → **79** `<loc>` (81 cuando entre el Check); lastmod 2026-09-10 en las dos URLs nuevas, hubs de tests y páginas del método.

### Suite global (82 HTML)
JSON-LD 0 errores · em dashes 0 · `<em>` 0 · hrefs e imágenes 0 rotos · FAQ **246** (238 + 8; objetivo 254 al entrar el Check), 0 duplicadas · schema=visible 8/8 Q/A por página · hreflang recíproco, canonical = og:url · blockquotes 154 · wa.me 511 (505 + 6).

### Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 11/11** (metas/canonical/hreflang/conmutador · reglas de interactivas: Clarity 0, Metrika 0, GA tras consentimiento, script sin almacenamiento ni red · accesibilidad y sin trampa de teclado · 7 pasos + 3b según spec · lógica JS verificada en Node con stub de DOM (afinaciones, nota sin mejora, texto de descarga, reset) · 4 JSON-LD y schema=visible 8/8 · puente al método · reglas de sitio y 246 FAQ sin duplicados (similitud máxima 0.56) · integraciones acotadas a los 6 archivos · paridad de plantilla · calidad ES). Re-verificó las dos correcciones aplicadas durante la auditoría (CSS `[hidden]` y "tiñe").

Residuos señalados y decisión:
- Auto-scroll y robo de foco al cargar (el primer `show()` enfocaba el h3 del paso 1): corregido, el render inicial ya no enfoca; al avanzar de paso sí se enfoca el título (comprobado: scrollY 0 y foco en body al cargar; foco en el h3 del paso 2 tras "Next").
- `role="group"` duplicado en la lista de distorsiones (ya lo tiene el panel): eliminado.
- `transition-delay:.18s` en la card del hub: intencional, reserva el .12s para la card del Half-Life Check que irá tercera.
- Ejemplos ES en masculino ("no estoy listo", "Soy un aficionado"): se dejan; el caso conductor tiene un protagonista y el EN es neutro por gramática, no por decisión.
- docs/reports/f4e-report.md: es este informe, se incluye en el commit.

---

## Herramienta 1 · Recovery Half-Life Check (pendiente de contenido)

Diseño listo para montar sobre la misma plantilla en cuanto llegue el bloque del estratega:
- Páginas /tests/recovery-half-life/ + /es/tests/vida-media-recuperacion/; titles del comando; atribución literal del dueño bajo el título.
- 8 preguntas con 4 opciones a-d como cards/radios grandes (`fieldset` + `radio`), progreso visible, resultado en la misma página.
- **Lógica de bandas** (determinista, documentada): a=0, b=1, c=2, d=3; suma 0-24 → banda 1 (0-8) "Your system still resets" · banda 2 (9-15) "Your recovery is stretching" · banda 3 (16-24) "Your recovery is not completing". Sin puntaje visible. Enlaces a /tests/cbi/, /tests/who-5/ y wa.me según el texto de cada banda.
- FAQs (4): qué es la vida media de recuperación · diferencia con un test de burnout (reflexión vs psicometría; CBI validado) · qué hacer con banda 2 o 3 · privacidad. Schema MedicalWebPage + FAQPage, sin Quiz.
- Integración: card tercera en los hubs, frase en /burnout-therapy/ y /es/terapia-burnout/ (tras "…that does not happen through rest alone." / "…eso no ocurre solo con descanso."), llms.txt, sitemap → 81. Sin enlace al artículo de LinkedIn; puentes a /burnout-therapy/ y /tests/ (CBI).

## Vista previa

- http://localhost:8000/tests/thought-record/
- http://localhost:8000/es/tests/registro-pensamientos/
- http://localhost:8000/tests/
- http://localhost:8000/es/tests/
