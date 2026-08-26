# Reporte Comando F4-B · WHO-5 + CBI de burnout (EN/ES)

Fecha: 2026-08-26 · Base: `bbfd16f` (main) · Rama: `f4b-review` · Plantilla canónica: /tests/phq-9/ post-fixes (legends dentro de card, píldoras con envoltura, nav/footer F4-N).

## T0 · Citas

| Cita | Verificación |
|---|---|
| S9 · Topp, Østergaard, Søndergaard, Bech. "The WHO-5 Well-Being Index: A Systematic Review of the Literature." Psychother Psychosom, 2015 | PMID **25831962** vía NCBI E-utilities (HTTP 200): título carácter a carácter idéntico salvo caja tipográfica (PubMed lo almacena en sentence case: "a systematic review of the literature"); autores 4/4 con diacríticos exactos, revista y año confirmados. URL usada: pubmed.ncbi.nlm.nih.gov/25831962/ |
| S10 · Kristensen, Borritz, Villadsen, Christensen. "The Copenhagen Burnout Inventory: A new tool for the assessment of burnout." Work & Stress, 2005 | Crossref API (works/10.1080/02678370500297720): **título carácter a carácter EXACTO**, autores 4/4, revista y año (2005-07) confirmados. doi.org resuelve (302 → tandfonline.com). URL usada: doi.org/10.1080/02678370500297720 |

## Páginas nuevas (4)

/tests/who-5/ · /es/tests/who-5/ · /tests/cbi/ · /es/tests/cbi/ — ensambladas extrayendo los fragmentos reales de la plantilla /tests/phq-9/ (analytics, CSS con los fixes de la ronda visual, Yandex, nav F4-N con "Tests", footer F4-N, scripts de cola): solo cambian contenido, escala y lógica.

- **Instrumentos byte-exactos: 0 diffs** (5+5 ítems WHO-5, 6+6 CBI, opciones 6/5 con sus valores 5→0 y 100/75/50/25/0, instrucciones; diff literal contra el comando).
- **Rejillas adaptadas**: WHO-5 con 6 opciones → 3 columnas desktop; CBI con 5 opciones → 5 columnas; mismos breakpoints (2 col ≤1024, 1 col ≤480). **Geometría verificada con render real (CDP, 375/768/1280 px)**: 22 legends × 3 anchos dentro de su card, píldoras sin recorte (`scrollWidth ≤ clientWidth` por span), overflow-x 0 en las 12 combinaciones.
- **Puntuación**:
  - WHO-5: suma cruda 0-25 mostrada junto al índice ×4 ("18/25 · index 72/100"); bandas por índice 51-100/29-50/0-28; banda 0-28 enlaza el PHQ-9 del idioma.
  - CBI: promedio redondeado de los 6 ítems (0-100); bandas 0-24/25-49/50-74/75-100; bandas 50-74 y 75-100 enlazan burnout-therapy del idioma.
- **Pruebas (Node, lógica extraída de las páginas)**:

```
WHO-5 (EN=ES): todo-5 → 25/25 · índice 100 → banda favorable · todo-0 → 0 · muy bajo ·
mixta [5,3,2,4,1] → 15/25 · índice 60 → favorable · [2,2,2,2,2] → 10/25 · índice 40 → bajo ·
fronteras band(28,29,32,48,50,51,52) → 2,1,1,1,1,0,0 EXACTAS (28/29 y 50/51 correctas)
CBI (EN=ES): todo-Always → 100 → alto a severo · todo-Never → 0 → bajo ·
mixta [100,75,50,25,0,0] → promedio 42 → señales tempranas ·
fronteras band(24,25,49,50,74,75) → 0,1,1,2,2,3 EXACTAS
```

- Sin recuadro de crisis de ítem 9 (exclusivo del PHQ-9); línea discreta a /crisis/ al pie, como la plantilla.
- **Decisión de dedup documentada**: el comando especificaba la misma FAQ de privacidad ("What happens to my answers?", patrón F4-A) para ambos tests, lo que colisionaría entre sí y con el gate de FAQ únicas. Resolución: WHO-5 usa "What happens to my answers?"/"¿Qué pasa con mis respuestas?" y CBI usa "Are my answers stored anywhere?"/"¿Se guardan mis respuestas en algún sitio?" (mismos hechos, patrón F4-A). Sin colisiones en las 187.

## T3 · Integración

1. **Hub**: 4 cards en orden PHQ-9 · GAD-7 · CBI · WHO-5, formato 4 líneas del dueño (CBI: Burnout screener/Cribado de burnout · 6 questions · ~2 minutes; WHO-5: Wellbeing index/Índice de bienestar · 5 questions · ~1 minute), delays escalonados.
2. **Enlaces internos** en burnout-therapy y es/terapia-burnout: frase final de la sección de síntomas con enlace al CBI, anclada por CONTENIDO (último párrafo real verificado por archivo) y verificada post-inserción entre el H2 de síntomas y el siguiente H2.
3. **Sitemap 58→62** (pares who-5 y cbi, lastmod 2026-08-26) + lastmod al día en hub pair y burnout pair (8 entradas en 2026-08-26). **llms.txt** actualizado a los cuatro screeners.
4. **Menores F4-A cerradas (ride-along)**: (M4) hero del hub unificado a "~2 minutes"/"~2 minutos"; (M3) `lastReviewed` = fecha del commit en los 8 tests (4 existentes actualizados + 4 nuevos). **Regla registrada: lastReviewed se actualiza en cada edición de la página.** Nota: los 4 tests existentes solo cambian ese campo de schema; su lastmod de sitemap se conserva conforme al alcance del comando.

## T4 · Suite global (salida literal)

```
instruments byte-exact 0 diffs · HTML balanceado 4/4 · hreflang recíproco 2/2 pares ·
JSON-LD 170 bloques 0 err · em dashes 0 · <em> 0 · blockquotes 146 · aggregateRating 0 ·
FAQ 187 (175+12) dup 0 · schema=visible 187/187 0 desync ·
wa.me NUEVO CANON = 424 (412 + 4 páginas × 3) ·
H1/titles intactos en las 8 preexistentes tocadas · sitemap 62 URLs válido ·
lastmod 2026-08-26 ×8 · lastReviewed 2026-08-26 en 8/8 tests ·
hub 4 cards en orden + hero ~2 · enlaces internos burnout 2/2 · llms.txt 4 screeners
RESULT: ALL PASS
```

**Canon actualizado**: wa.me = 424 · FAQ = 187 · sitemap = 62 · páginas HTML con `<head>` = 63 · blockquotes = 146.

## Doble auditoría acotada

**Primer veredicto: NO-GO por B1 · Resuelto en el mismo pase · Estado final: APROBADO.**

- **B1 (bloqueante real, encontrado por el auditor)**: el H2 del hub seguía diciendo "Two Validated Tests"/"Dos Tests Validados" con cuatro cards debajo: contradicción factual introducida por la integración F4-B (añadí las cards sin actualizar el encabezado). **Corregido**: "Four Validated Tests"/"Cuatro Tests Validados".
- **M1 (recomendado en el mismo pase, aplicado)**: title/description/og y la description del MedicalWebPage del hub nombraban solo PHQ-9 y GAD-7; actualizados a los cuatro instrumentos en ambos idiomas (los titles del hub cambian deliberadamente: excepción documentada en la puerta de H1/titles; los H1 quedan intactos en todo el sitio). `lastReviewed` de los 2 hubs bumpeado por la regla nueva (total 10: 8 tests + 2 hubs). Batería re-ejecutada: **ALL PASS**.
- **Aprobado por el auditor sin reservas**: las 4 páginas nuevas (instrumentos byte-exactos verificados carácter a carácter de forma independiente, pareo valor↔etiqueta correcto, scoring coherente con las tablas, flujo fiel a la plantilla, pares EN/ES con esqueleto de tags idéntico, citas correctas, higiene en cero) y los 2 enlaces internos de burnout (dentro de sus secciones de síntomas).
- **Menores registrados**: (M2) tensión residual aceptada del hero "~2 minutes" con la card WHO-5 "~1 minute" (M4 de F4-A quedó cerrada tal como se ordenó); (M3) casi-colisión benigna de las FAQs de privacidad (variantes deliberadas del dedup, cada una en exactamente 1 archivo, verificado repo-wide).
