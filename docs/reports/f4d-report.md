# Reporte Comando F4-D · Fix es/precios (móvil) + Respiración y Medidor Emocional

Fecha: 2026-08-27 · Base: `58b455c` (main) · Rama: `f4d-review` · Fuente de lectura: `app-source.html` del dueño (NO commiteada; borrada al terminar y verificada como no trackeada).

## T0A · Fix es/precios (móvil)

**Diagnóstico**: en es/precios el override móvil de las cards estaba corrupto con un selector imposible (`.nav-links.active .nav-links.active .nav-links.active .price-row{grid-template-columns:1fr}`), de modo que nunca aplicaba y sobrevivía la regla de 2 columnas del breakpoint ≤1180px. El canon EN tiene el selector limpio `.price-row{grid-template-columns:1fr}` en el bloque móvil. **Corregido al canon** (2 líneas). **Barrido**: el selector corrupto solo existía en es/precios (grep repo-wide = 1 archivo). **Verificado por layout computado a 375px**: pricing y es/precios idénticos, `grid-template-columns` computa 1 columna, 5 cards apiladas con una sola posición X. lastmod sin bump (fix de CSS al canon, regla registrada).

## T0B · Inventario de la fuente (app-source.html)

1. **Patrones de respiración (const BREATHS de la app)**:

| Patrón (clave) | Condición (tag i18n) | Tiempos (s) | Título EN / ES |
|---|---|---|---|
| box | Rumination / Rumiación | inhalar 4 · retener 4 · exhalar 4 · retener 4 | Box Breathing / Respiración cuadrada |
| anxiety | Anxiety / Ansiedad | inhalar 4 · retener 7 · exhalar 8 | 4–7–8 Breathing / Respiración 4–7–8 |
| relaxation | Relaxation / Relajación | inhalar 4 · exhalar 8 | Baseline Breathing / Baseline breathing |

Motor: preparación de 5 s (Get ready → 3 → 2 → 1 → Start!), 5 ciclos, animación SVG por patrón (punto recorriendo el cuadrado / orbe que se expande / punto sobre onda), `prefers-reduced-motion` respetado.

2. **Nota de seguridad clínica (breath_safety, conservada verbatim)**: EN "Keep the breath gentle and comfortable. If you feel dizzy, short of breath, or more anxious, stop and return to normal breathing." / ES "Mantén la respiración suave y cómoda. Si aparece mareo, falta de aire o más ansiedad, detente y vuelve a respirar con normalidad."

3. **Medidor emocional**: mapa 2D con ejes **activación (arriba/abajo) × valencia (agradable/desagradable)**; el punto se fija con clic/toque o flechas del teclado (paso .08); cuadrante = energía(h/l)+valencia(p/u) con umbral .5; etiquetado con **VOCAB de 10 palabras por cuadrante × 2 idiomas** (40+40, inventario completo en `hu/hp/lu/lp`); devolución breve con `frame_pleasant`/`frame_unpleasant` interpolando la palabra. En la app le siguen un paso de "feeding" (qué mantiene/sostiene el estado) y el pase al protocolo: **eso pertenece al Método y NO se migra** (decisión de alcance documentada).

4. **i18n EN/ES de la app usados como fuente preferente de los textos de herramienta**: títulos/subs/patterns/phases de los 3 patrones, choose_title/sub, cycles/complete/prep/change, meter_title/sub/pick, etiquetas de cuadrantes y ejes, frame_*, aria del mapa. **Única adaptación de texto**: `<em>{w}</em>` → `<strong>{w}</strong>` en los frames (regla del sitio `<em>` = 0), documentada.

## T1/T2 · Páginas (4)

/tests/breathing/ · /es/tests/respiracion/ · /tests/emotional-meter/ · /es/tests/medidor-emocional/ — patrón del sitio completo (fragmentos reales de la plantilla canónica), CSS de herramienta en tokens del sitio (SVGs re-coloreados a gold/border; el gradiente de cuadrantes del medidor conserva los colores del diseño de la app), sin FAQs (herramientas), MedicalWebPage simple + BreadcrumbList + MedicalBusiness, cierre honesto (la respiración regula el momento, no el patrón de fondo → enlace a regulación) y línea de privacidad del medidor ("nada de lo que marques sale de tu dispositivo ni se guarda"), CTA estándar. **Solo-sesión real: cero localStorage/sessionStorage/fetch/beacon en las 4** (el `addLog` y el historial de la app NO se migraron).

**Pruebas funcionales**:

```
Node (matemática de fases, EN=ES): box 4-4-4-4 ciclo 16s sesión 85s · anxiety 4-7-8 ciclo 19s sesión 100s ·
relaxation 4-8 ciclo 12s sesión 65s · fronteras de fase EXACTAS en los 3 patrones ·
medidor: 6 casos de cuadrante correctos (incl. umbral .5) · vocab 10/10/10/10 en ambos idiomas
CDP en vivo (pacer relaxation): t≈1s "Get ready" · t≈6s "Inhale through your nose | count=4" ·
t≈10.5s "Exhale very slowly through your mouth | count=7" (8s de exhalación, 6.5 restantes → ceil 7 ✓)
CDP medidor: clic en cuadrante hu → 10 chips (primera "Anxious"/"Ansioso/a") → palabra → resultado con <strong> ·
teclado (6×ArrowRight) cruza al cuadrante hp ("Motivated"/"Motivado/a") ✓ accesible
Render: 12/12 combos (4 páginas × 375/768/1280) con viewport exacto y overflow-x 0
```

## T3 · Integración

- **Hub**: nueva sección `Interactive Tools`/`Herramientas Interactivas` DEBAJO de los seis tests, con las 2 cards en formato del dueño (Breathing · Guided regulation exercise · **3 patterns** · 2–5 minutes; Emotional Meter · Name what you feel · ~1 minute; espejos ES). **Decisión documentada**: el H2 "Six Validated Tests"/"Seis Tests Validados" NO se toca: los tests siguen siendo seis y las herramientas viven en su propia sección con su propio encabezado; la lectura natural es correcta.
- **Enlaces internos**: emotional-regulation-therapy (EN) y es/regulacion-emocional (ES), al final de sus secciones de señales (anclados por contenido, verificados entre H2s), a la respiración del idioma.
- **Sitemap 65→69** (2 pares con hreflang, lastmod 2026-08-27) + lastmod al día en hub pair y par de regulación. **llms.txt**: línea nueva de herramientas interactivas. **lastReviewed** 2026-08-27 en 4 nuevas + 2 hubs (regla vigente).

## Suite global (salida literal)

```
fidelidad app→página 0 diffs (tiempos, i18n, vocab, cuadrantes, seguridad) ·
prohibiciones 0 (Método/grounding/defusión/observer/feeding/log/storage/fetch) ·
HTML balanceado 4/4 · hreflang recíproco 2/2 · JSON-LD 0 err · em dashes 0 · <em> 0 ·
blockquotes 146 · FAQ 196 (sin nuevas) · wa.me NUEVO CANON = 445 (433 + 4×3) ·
H1/titles intactos en preexistentes · sitemap 69 válido · hub Six/Seis conservado + sección de herramientas ·
llms.txt OK · enlaces internos 2/2 · es/precios canon 1fr · lastReviewed 6/6
RESULT: ALL PASS
```

**Canon actualizado**: wa.me = 445 · sitemap = 69 · páginas HTML con `<head>` = 70 · FAQ = 196 · blockquotes = 146.

## Doble auditoría acotada

**Primer veredicto: NO APTO por 2 bloqueantes mecánicos · Ambos resueltos en el mismo pase · Estado final: APTO global.**

- **B1 (riesgo de publicación de IP)**: `app-source.html` estaba sin salvaguarda frente a un `git add` masivo en un repo que ES el sitio publicado. **Resuelto**: archivo borrado tras completar extracción y auditoría (orden del comando), verificado no-trackeado (`git ls-files` = 0), y el commit se hizo con rutas explícitas, nunca `add -A`.
- **B2 (byte-exactitud)**: el `frame_pleasant` EN del medidor llevaba apóstrofo tipográfico U+2019 ("let's" curvo) donde la app usa ASCII: segunda adaptación no autorizada. **Resuelto**: 1 byte corregido; gate de fidelidad re-ejecutado en 0 diffs.
- **Verificado limpio por el auditor**: fidelidad byte-exacta programática (durations, i18n EN/ES completos incluida la asimetría intencional "Baseline Breathing"/"Baseline breathing", VOCAB 40×2, cuadrantes/ejes, safety visible); fuga de IP = 0 (los hits de "Observer" son IntersectionObserver); lógica del pacer portada 1:1 (PREP, 5 ciclos, reduced-motion doble) y medidor accesible (clic+teclado, umbral .5 idéntico); patrón de página completo con hreflang recíproco y sin FAQs; integración correcta (sección de herramientas bajo los 6 tests con lectura natural correcta del "Six/Seis", enlaces internos en secciones de señales, es/precios restaurado, sitemap coherente).
- **Menores registrados**: (M1) "Un guía de respiración" en la meta description ES: género dudoso, solo meta; (M2) tensión honestidad/analítica heredada del patrón del sitio: la herramienta no guarda nada (0 storage/red verificado) pero Metrika/Clarity graban interacciones de sesión como en todo el sitio: registrado como decisión consciente del dueño a ratificar; (M3) "check-in" en la description del schema pertenece al componente medidor, no al Método: no es fuga; (M4) arruga semántica del breadcrumb (herramientas bajo "Screeners/Tests"), coherente con la ruta /tests/; (M5) llms.txt: la línea de herramientas solo en la sección EN, como la de screeners (la sección ES no lista tests: consistente, sin acción).

## Pulido de privacidad del dueño (2026-08-27, pre-merge; ratifica el M2 del auditor)

Eliminados **Microsoft Clarity** (del bootstrap consent-gated, conservando Google Analytics) y **Yandex Metrika** (script + noscript completos) de las **15 páginas interactivas reales** donde el usuario responde: los 6 tests en par + TMMS-24 solo-ES (11 páginas) y las 2 herramientas en par (4). Nota de conteo: el comando decía "10 páginas (los 8 tests y las 2 herramientas)"; el inventario real de superficies interactivas es 15 y el criterio del estratega (privacidad donde se responde) se aplicó al inventario completo, como en los precedentes de conteo documentados. De paso, el banner de cookies de esas 15 páginas pasa a decir solo "(Google Analytics)" (coherencia de honestidad con el cambio). Verificado: clarity=0, mc.yandex=0 y GA=1 en las 15; resto del sitio sin cambios. **Cánones actualizados: Yandex tag.js en 55 páginas (counter 111712864 total = 110) · Clarity en 54 páginas** (la única asimetría es 404.html, que lleva Yandex desde YX-1b pero nunca tuvo el bootstrap de Clarity: preexistente, fuera de alcance).
