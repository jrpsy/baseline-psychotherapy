# Reporte Comando F4-N · "Tests" al navegador + footer reordenado (sitio completo)

Fecha: 2026-08-25 · Base: `cc763a4` (main, post-lanzamiento F4-A) · Rama: `f4n-review` · Main intacta hasta autorización.

## T1 · Navegador

Ítem `Tests` insertado entre Workshops/Talleres y Pricing/Precios en las **54 páginas con header estándar** (EN→`/tests/`, ES→`/es/tests/`, label "Tests" en ambos idiomas). **Conteo verificado: 54 páginas × 1 variante de nav = 54 ítems** (el sitio tiene una sola `ul.nav-links` por página; el menú móvil/hamburguesa reutiliza exactamente ese markup vía JS, no hay duplicado que tocar: documentado). Anclaje por regex dentro del bloque `<nav>` (el string de Workshops existe también en el footer) tolerando el `class="current"` de las páginas de Talleres/Workshops. Las 5 páginas sin header estándar (4 legales + 404) no llevan nav por diseño.

## T2 · Footer, bloque de marca (54 páginas estándar)

Orden EXACTO verificado por posición en 54/54: **descripción → mailto → Políticas → Privacidad → Crisis → CTA wa.me**. Markup y estilos conservados (mismas clases y estilos inline del bloque legal). Cambios de contenido:

- **Descripción ES actualizada al verbatim del dueño en 27 páginas**: "Apoyando a expatriados..." → "**Acompañando** a expatriados y profesionales en todo el mundo, en español e inglés, desde 2019." La EN ya coincidía verbatim (27 páginas, sin cambio).
- **Crisis Resources / Recursos de Crisis** añadido tras Privacidad en las 54 (era el eslabón nuevo del orden; estilo idéntico a los legales).

**Defectos preexistentes encontrados y corregidos de paso (documentados para el estratega):**
1. **9 blogs ES**: el enlace "Políticas de Servicio y Reembolso" apuntaba a `/politica-privacidad.html` (la página de privacidad) en vez de `/es/politicas.html`. Corregido en los 9.
2. **es/precios**: era la única página estándar sin CTA "Reservar una consulta gratuita →" en el bloque de marca. Añadido el estándar ES → **wa.me pasa de 411 a 412 (nuevo canon)**.
3. **index.html**: `href="policies.html"` relativo (única desviación del sitio, que usa root-relative). Normalizado a `/policies.html`.

## T3 · Limpieza

- Columna Practice/Práctica: eliminados `Free screeners`/`Tests gratuitos` (ahora en nav) y `Crisis resources`/`Recursos de crisis` (ahora en bloque de marca): **108 enlaces retirados (54 × 2)**. Duplicados de tests/crisis por footer: **0** (verificado: 0 enlaces a tests en footer, exactamente 1 de crisis por footer, en el bloque de marca).
- **Footers mínimos 5/5** (policies, privacy-policy, es/politicas, politica-privacidad, 404) con los 3 enlaces en orden **Policies · Privacy · Crisis** por idioma, en su patrón mínimo local (las 4 legales con sus `<p>` de pie; 404 en su línea única con separadores `·`), sin descripción ni CTA. Labels normalizados a "Crisis Resources"/"Recursos de Crisis".

## T4 · Verificación (salida literal de la batería)

```
TABLA | nav items Tests insertados: 54 (54 páginas con header estándar × 1 variante de nav)
TABLA | footers estándar con bloque de marca en orden 1-6: 54 / 54
TABLA | duplicados de tests/crisis por footer: 0 · restos "Free screeners"/"Tests gratuitos": 0
URLs legales por idioma 54/54 OK (EN /policies.html + /privacy-policy.html · ES /es/politicas.html + /politica-privacidad.html)
descripción ES verbatim (Acompañando) 27/27 · descripción EN verbatim 27/27
footers mínimos 5/5 Policies·Privacy·Crisis en orden
JSON-LD 154 bloques 0 err · em dashes 0 · <em> 0 · blockquotes 146 ·
wa.me NUEVO CANON = 412 (411 + 1 CTA completado en es/precios) ·
H1/titles intactos en las 59 tocadas · FAQ intactas 175 · schema=visible sin cambios ·
sitemap byte-idéntico (EXCEPCIÓN DOCUMENTADA: cambio de chrome global no toca lastmod;
las 8 páginas de tests/crisis conservan su lastmod actual)
RESULT: ALL PASS
```

**Canon actualizado**: wa.me = 412 · blockquotes = 146 · FAQ = 175.

## Doble auditoría acotada al diff

**VEREDICTO: APROBADO · BLOQUEANTES: 0.** El segundo auditor recorrió los 59 archivos del diff (54 estándar + 5 mínimos, cuadre exacto), muestreó 12+ páginas en profundidad y verificó por script las 54 completas: nav 27 EN + 27 ES con UNA inserción cada una siempre entre Workshops/Talleres y Pricing/Precios (dropdown y switcher intactos); orden 1-6 del bloque de marca en 54/54 con cero cruces de idioma en los hrefs; cero restos de los enlaces retirados y cero `<li>` huérfanos; footers mínimos 5/5; em dashes y `<em>` 0 en las líneas añadidas; ninguna línea del diff toca `<title>`, `<h1>` ni `ld+json`; confinamiento total del diff a nav/footer (barrido de todas las líneas +/−); instrumentos de los 4 tests byte-idénticos a `cc763a4`; y las 5 correcciones registradas confirmadas tal cual (con matiz: en 2 de los 11 blogs ES el href de Políticas ya estaba bien, el bug preexistente afectaba a 9).

**Menores registrados (sin tocar)**: (M1) el ítem "Tests" no lleva `class="current"` cuando se está en las páginas de tests, la convención del sitio marca la página activa: cosmético, para futura pasada; (M2) preexistente: index.html y faq usan `&` crudo en "Service Policies & Refund Notice" donde el resto usa `&amp;`; (M3) preexistente conservado: el mailto de es/precios no lleva el onclick de gtag que tienen las demás.
