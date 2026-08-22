# Reporte Comando F4-A · Crisis + Tests clínicos (hub, PHQ-9, GAD-7) EN/ES

Fecha: 2026-08-22 · Base: `b8c2666` (main) · Rama: `f4a-review` · Modo presupuesto extremo (textos del comando finales; ensamblaje al patrón del sitio).

## T0 · Verificación de citas (S7/S8)

| Cita | PMID | Verificación |
|---|---|---|
| S7 · Kroenke, Spitzer, Williams. "The PHQ-9: validity of a brief depression severity measure." J Gen Intern Med, 2001 Sep | 11556941 | Título **carácter a carácter EXACTO** vía API oficial NCBI E-utilities (HTTP 200); autores y revista confirmados |
| S8 · Spitzer, Kroenke, Williams, Löwe. "A brief measure for assessing generalized anxiety disorder: the GAD-7." Arch Intern Med, 2006 May 22 | 16717171 | Ídem: título exacto, autores (incl. Löwe con diéresis), revista y fecha confirmados |

**Matiz documentado**: el fetch directo de las fichas HTML devuelve HTTP 203 en esta red (interstitial de cookies de PubMed transformado por proxy; verificado con UA de navegador, redirects y cookie jar). Las URLs están vivas (2xx) y la verificación de contenido se hizo contra la fuente autoritativa de NCBI (E-utilities, HTTP 200), que es igual o más fuerte que leer el HTML. URLs usadas en las páginas: `https://pubmed.ncbi.nlm.nih.gov/11556941/` (S7) y `https://pubmed.ncbi.nlm.nih.gov/16717171/` (S8).

## Páginas nuevas (8)

/crisis/ · /es/crisis/ · /tests/ · /es/tests/ · /tests/phq-9/ · /es/tests/phq-9/ · /tests/gad-7/ · /es/tests/gad-7/

Todas ensambladas del patrón de página de servicio (head completo con analytics consent-gated, hreflang triplete con x-default→EN, og/twitter, fuentes self-hosted, CSS inline del bloque de servicio + componentes nuevos en el mismo estilo de una-regla-por-línea, Yandex Metrika, nav expandido sin `class="current"`, switcher de idioma al par exacto, footer de 38 líneas ya con los 2 enlaces nuevos, scripts de cola byte-idénticos). Schema por página: MedicalWebPage (tipo nuevo en el sitio) + BreadcrumbList + MedicalBusiness; las 2×2 de tests añaden FAQPage (visible=schema).

**Decisiones de diseño documentadas**:
- Las 8 páginas nuevas NO llevan botón flotante de WhatsApp ni mobile-cta-bar: en crisis nada debe competir con las líneas de emergencia; en tests obstruirían los radios en móvil. El JS compartido lo tolera (`if(!bar)return`). CTA estándar wa.me al pie en las 8, más nav y footer: **3 wa.me por página nueva**.
- **Usted/tú deliberado**: los ítems oficiales ES de PHQ-9/GAD-7 conservan su usted validado (editarlos invalidaría el instrumento); todo el texto de página alrededor va en tú. Es la regla clínica del comando, no una inconsistencia.
- Breadcrumb de test a 3 niveles (Home › Screeners › PHQ-9) con BreadcrumbList de 3 ítems.
- Los enlaces en prosa de las páginas nuevas usan subrayado gold (`.content-link` y reglas equivalentes), porque el reset global del sitio deja `<a>` sin estilo.

## Instrumentos y calculadores

- **Byte-exactos contra el comando: 0 diferencias** en 16+14 ítems (9+9 PHQ EN/ES, 7+7 GAD EN/ES), 4+4 opciones × 2 lenguas y las 2 instrucciones (diff literal de `<legend>`, `<span>` de opciones y `q-instruction`).
- Markup accesible: `fieldset` + `legend` (texto del ítem intacto; numeración por contador CSS, fuera del texto), labels clicables, radios con `accent-color` gold.
- JS vanilla inline: botón deshabilitado hasta responder todo (contador visible), score = suma, scroll suave, reinicio.
- **Pruebas de puntuación (Node, lógica extraída de las páginas reales)**:

```
PHQ-9 (EN y ES idénticos): todo-0 → 0 Minimal · todo-3 → 27 Severe ·
mixta [1,2,0,3,1,2,0,1,2] → 12 Moderate (ítem9=2 → crisis=true) ·
regla de crisis con score bajo: [0×8, ítem9=1] → score 1 Minimal, crisis=TRUE ·
barrido 0..27 → 0000011111222223333344444444 (fronteras 4/5, 9/10, 14/15, 19/20 exactas)
GAD-7 (EN y ES idénticos): todo-0 → 0 Minimal · todo-3 → 21 Severe ·
mixta [2,1,3,0,2,1,2] → 11 Moderate · sin elemento de crisis (correcto: no hay ítem de ideación) ·
barrido 0..21 → 0000011111222223333333 (fronteras 4/5, 9/10, 14/15 exactas)
```

- **Regla de crisis (inviolable) implementada**: recuadro estático borde gold/fondo suave con el texto EN final del comando (enlace a /crisis/ dentro de la frase "crisis resources") y espejo ES en tú (enlace a /es/crisis/); se muestra ANTES del score cuando ítem 9 > 0, con el score debajo. Presente solo en PHQ-9.

## Integración

1. **Footer columna Práctica/Practice** (resolución del estratega ante la inexistencia de columna "Resources"): `Free screeners`/`Tests gratuitos` + `Crisis resources`/`Recursos de crisis` (en ese orden, al final) en las **46** páginas con columnas + las 8 nuevas de serie = 54.
2. **Matiz de seguridad del estratega**: las 5 páginas de footer mínimo (policies, privacy-policy, es/politicas, politica-privacidad, 404) reciben SOLO el enlace de crisis, en el patrón local de cada footer. Crisis alcanzable desde las 59 páginas del sitio sin excepción.
3. **4 enlaces internos quirúrgicos** (anclados por CONTENIDO, no por línea, por orden del estratega): frase final de la sección de síntomas con enlace al test correspondiente en depression-therapy-online, es/terapia-depresion (PHQ-9), anxiety-therapy-online, es/terapia-ansiedad (GAD-7). Verificado post-inserción: cada `<p>` quedó entre su H2 de síntomas y el siguiente H2. No tocan FAQ: sin resync.
4. **Sitemap**: 50 → **58 URLs** (8 nuevas con pares hreflang en/es, lastmod 2026-08-22, priority 0.8, patrón de página de servicio sin x-default). XML válido.
5. **llms.txt**: bullet nuevo en la sección Services (English) con la frase literal del comando como descripción.
6. **lastmod**: las 8 nuevas + las 4 de servicio con frase nueva visible = 12 entradas en 2026-08-22. Las 51 tocadas solo en footer NO bumpean lastmod (extensión documentada de la regla de infraestructura: navegación global sin cambio de contenido de página).

## Suite global final (salida literal de la batería)

```
instruments byte-exact 0 diffs · JSON-LD 154 bloques 0 errores · aggregateRating 0 ·
FAQ 175 (163+12) dup 0 · schema=visible 175/175 0 desync (render real sin scripts;
convención .faq-link descontada) · em dashes 0 · <em> 0 · blockquotes 146 ·
wa.me NUEVO CANON = 411 (387 + 24 = 8 páginas × 3) · precios intactos $120/$430/$1,200 ·
footers 54 con ambos enlaces + 5 mínimos con crisis · 4 enlaces internos ·
sitemap 58 válido · llms.txt OK · lastmod 12×2026-08-22 · reseñas 22: superficies 8+8 sin cambio ·
HTML balanceado 8/8 nuevas · hreflang recíproco 4/4 pares · canonical propio 8/8
```

**Canon actualizado para futuros comandos**: wa.me = 411 · blockquotes = 146 (sin cambio) · FAQ = 175 · páginas HTML con `<head>` = 59 · sitemap = 58 URLs.

## Doble auditoría acotada (segundo auditor independiente, solo lectura)

**BLOQUEANTES: 0 · Veredicto: APROBADA ×8 páginas + integración APROBADA.** El auditor reprodujo por script: instrumentos carácter a carácter EXACTOS en las 4 páginas (legends, opciones con valores 0-3 en orden, instrucciones, incluido el ítem 8 ES con su «¿» inicial); regla de crisis del ítem 9 presente SOLO en PHQ-9, antes del score, con enlaces correctos; bandas JS = tabla en ambos tests con EN=ES; botón disabled por defecto y reset completo; teléfonos tel: correctos y externos con noopener; cero botón flotante/mobile-bar en las 8 (decisión de diseño confirmada); head/nav/footer en diff estructural vacío contra la página de referencia (única delta: `class="current"`, correcta); higiene en cero (em dashes, `<em>`, aggregateRating); FAQ visible=schema 3/3 en cada test; cero "usted" fuera de los ítems del instrumento en el copy ES.

**Menores registrados (sin tocar, a criterio del estratega)**: (M1) masculino no marcado en el copy ES de página ("no estás seguro", "cuando tú estés listo"), en contraste con los (a) de los ítems oficiales: convención del sitio, registrado por transparencia; (M2) los `tel:` de códigos cortos (999, 1767, 024) solo marcan dentro de su país; el párrafo Befrienders/findahelpline lo mitiga: diseño defendible; (M3) `lastReviewed` hardcodeado a 2026-08-22 en los MedicalWebPage, sin proceso de refresco; (M4) micro-inconsistencia cosmética del hub: hero "dos o tres minutos" vs cards "~2 minutos".
