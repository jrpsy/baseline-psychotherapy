# Reporte Comando PR-1 · Sesión Focal ($60) + escalera de precios + parejas a 90 min

Fecha: 2026-09-03 · Base: `cd0ea04` (main) · Rama: `pr1-review` · Los precios de este comando SON el canon nuevo (documentado abajo).

## T1 · Parejas 75 → 90 minutos (barrido completo, $170 intacto)

**Inventario del barrido: 25 sustituciones anclada-a-anclada** (cada hit verificado contextualmente como duración de parejas antes de tocar; cero falsos positivos tipo $107.50/21+):

| Superficie | Hits |
|---|---|
| index.html | Offer desc del catálogo + FAQ "How do I start" (schema + visible, ×2) |
| es/index.html | Offer desc + FAQ ES (schema + visible, ×2) |
| couples-therapy-online | Offer desc · prosa de costes ("couples sessions are 90 minutes") · price format · prosa de card · plan mensual format (5) |
| es/terapia-parejas | los 5 espejos (5) |
| pricing | Offer couples · Offer monthly couples · FAQ de apps "60- or 90-minute" (schema + visible ×2) · price-fmt couples · price-fmt monthly couples (6) |
| es/precios | los 6 espejos (6) |
| llms.txt | "Couples session $170 USD (90 min)" (1) |

Restos de duración "75 min*" repo-wide: **0**. Los 75 de la card de parejas de la HOME no se tocaron: esa card sale de la vitrina en T3 (desaparecen con ella). Resync schema=visible verificado donde la frase vive en FAQs.

## T2 · Pricing: escalera ascendente + cards nuevas

**Orden final verificado por posición DOM (EN y ES): Free Consultation → Focused Session → Individual Session → Couples (90) → Monthly 1:1 ($430) → Monthly Couples ($620) → Burnout ($1,200).**

**Interpretaciones documentadas**: (1) la card de **Consulta Gratuita no existía**: creada con copy sobrio del ejecutor (15 min, "Free"/"Gratis", CTA estándar), ya que el orden dictado la exige como primer peldaño; (2) **ambos planes mensuales se conservan** ("los existentes conservan precio y texto"): el peldaño "Monthly Plan" del comando los cubre en orden ascendente 430→620; (3) el **párrafo aclaratorio dictado en cursiva se renderiza como párrafo plano** (regla del sitio `<em>` = 0), en cuerpo más pequeño bajo el formato; (4) **grid de 5 → 4 columnas** para que 7 cards asienten 4+3 (antes 5+2 desbalanceado). Los textos dictados de Focused e Individual: byte-fieles; la card Focused lleva `id="focused"` (ancla del banner) y su CTA con prefill propio dictado. OfferCatalog de ambos pricing con la oferta Focused $60 añadida y las de parejas a 90.

## T3 · Home: swap en la vitrina

Card de parejas FUERA de la vitrina de precios, card **Focused** (texto dictado) DENTRO, orden Focused → Individual (featured) y Monthly → Burnout (ascendente). **Interpretación documentada**: la "Consulta gratuita" del orden es el primer peldaño ya representado por el CTA omnipresente de la home ("Start with a Free 15-Min Consultation" en cada card): T3 dicta un solo swap y la home conserva sus 4 slots. **Grilla de SERVICIOS intacta** (parejas sigue como issue-card, en nav y footer: verificado). OfferCatalog de la home: oferta de parejas sustituida por la de Focused (schema=visible con la vitrina).

## T4 · Barra de anuncio (temporal)

Presente en las **69 páginas con nav estándar** (las 5 de footer mínimo no tienen header donde anclarla: exentas, documentado). Diseño: barra FIJA sobre el header (navy, texto gold, estilo de la casa), con la nav desplazada 40px (52px móvil) y `body{padding-top}` compensando el flujo solo mientras la barra está visible (clase `html.has-banner`); X de cierre con `sessionStorage` (se reabre en sesión nueva: correcto para un anuncio temporal); enlace "30 min · $60 →" al pricing del idioma con ancla `#focused`. Textos dictados exactos EN/ES. **Probado en vivo por CDP**: visible por defecto en sesión fresca, nav desplazada, h1 despejado, X cierra y persiste tras navegar, ancla aterriza la card en viewport; sin overflow. **EXCEPCIÓN de lastmod aplicada** (chrome temporal): solo bumpean los 3 pares con cambio real de contenido (home, pricing, couples). **Fecha de retiro sugerida: ~4 semanas, alrededor del 1 de octubre de 2026** (micro-comando de retiro).

## T5 · FAQ nueva (pricing EN/ES)

Dictada, añadida visible + schema (resync verificado 7/7 en ambos), anti-dup global OK. Nota: convive sin colisión con la FAQ preexistente de las apps "$60 por semana" (semánticas distintas: suscripción de app vs sesión focal propia).

## Suite global (salida literal)

```
barrido 75→90: 25 hits, 0 restos · escalera 7 cards ascendente EN y ES · grid 4 col ·
home: focused en vitrina, parejas fuera de vitrina pero VIVA en servicios/nav/footer ·
banner 69/69 con X funcional y sessionStorage (CDP: fresh=visible, close=persistente, ancla OK) ·
FAQ 216 (214+2) dup 0 · schema=visible 7/7 en ambos pricing · JSON-LD 0 err · em dashes 0 · <em> 0 ·
blockquotes 154 intactos · H1/titles intactos en las 69 tocadas · reseñas intactas ·
imágenes: 0 rotas (los 3 lazy bajo el fold cargan al scroll, verificado) · overflow 0
RESULT: ALL PASS
```

**CANON NUEVO DE PRECIOS**: Consulta gratuita 15 min · **Sesión Focal 30 min USD $60** · Individual 60 min $120 · **Parejas 90 min $170** · Mensual $430 ($107.50/sesión) · Mensual Parejas $620 ($155/sesión) · Burnout $1,200 ($100/sesión). **Cánones de conteo**: wa.me = 473 (469 + free/focused en pricing ×2 + focused en home ×2 − couples de la vitrina ×2) · FAQ = 216 · blockquotes = 154 · sitemap = 73.

## Doble auditoría acotada

**VEREDICTO: APROBADO · 0 bloqueantes · 4 menores.** El auditor verificó hit-a-hit el barrido 75→90 (cero falsos positivos: los $107.50, "21+", y valores CSS quedaron intactos; cero restos repo-wide; sincronía visible↔schema confirmada), la escalera completa con textos dictados byte-fieles y prefills exactos, el swap de la home con parejas viva en servicios/nav/footer y las demás cards byte-intactas (los +</div> del diff son el cierre del propio banner), el banner en exactamente 69 páginas con 1 variante por idioma, X funcional sin FOUC y solo sessionStorage, la FAQ nueva sin colisiones (216 total) y la higiene en cero. Las 5 notas del ejecutor se verificaron fieles. (Incidencia del propio auditor: un `git stash` temporal restaurado de inmediato con stat idéntico.)

**Menores**: (M1, APLICADO en el mismo pase) el ancla #focused quedaba tapada por el chrome fijo (nav 72 + banner 40) al llegar desde el banner: `#focused{scroll-margin-top:130px}` en ambos pricing; (M2, registrado) la FAQ nueva va primera en el schema y última en el DOM: cosmético, schema.org no exige orden; (M3, registrado PARA LA RONDA VISUAL) la intro de la vitrina de la home dice "individual or couples appointment" y la vitrina ya no muestra parejas: tensión leve de copy del dueño, decisión suya si retocarla; (M4, registrado) tensión retórica entre la FAQ de apps (critica sesiones de 30 min de plataformas) y la Sesión Focal de 30 min adyacente: mitigada por el anclaje en "mismo especialista + consulta clínica", a criterio del estratega.
