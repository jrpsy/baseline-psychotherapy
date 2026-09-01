# Reporte Comando YER-1 · /yerevan/ + /es/yerevan/ (embajada local, anatomía de la home)

Fecha: 2026-09-01 · Base: `4c4527f` (main) · Rama: `yer1-review` · Regla maestra: anatomía y diseño de la home con contenido nuevo provisto (final); cero doorway.

## T0 · Línea de crisis de Armenia (puerta previa: SUPERADA)

| Dato publicado | Fuentes |
|---|---|
| Emergencias: **911 · 112** | Prensa oficial armenia (Armenpress/ARKA): 112 activo como número unificado desde el 15 de febrero de 2026; 911/102/101 siguen operando y redirigen. Ambos publicados con tel: |
| **Emotional Support Hotline: 0800 00 900**, lunes a viernes 09:00-18:00 | findahelpline.com/countries/am (listado marcado "verified by this helpline") + **hotline.mha.am** (sitio oficial: número, gratuita, confidencial, toda Armenia, especialistas formados y voluntarios) + anuncios del Ayuntamiento de Ereván con el horario L-V 09:00-18:00 |

Bloque **In Armenia / En Armenia** añadido a /crisis/ y /es/crisis/ tras España (orden geográfico oeste→este del tramo España→Armenia→EAU), patrón de los demás países, tel: correctos (tel:911, tel:112, tel:080000900).

## Páginas nuevas (2)

/yerevan/ · /es/yerevan/ — anatomía de la home con cuerpo nuevo:

**Checklist de anatomía (verificado programáticamente)**
- **Usados (17/17)**: hero-grid con HERO.webp + hero-image-accent (foto del dueño, kicker, markers con 5.0 Google, doble CTA: wa.me + screener→/tests/), about navy con ABOUT_BG, issues-grid con las 6 issue-cards accesibles (frases NUEVAS, una por servicio, enlazando a las páginas globales), sección de sesiones/precios, reviews navy, sección de screeners con botón al hub, tarjeta de ubicación con enlace prominente a Yandex Maps (SIN embeds ni scripts de terceros), faq-list (6), cta, footer/nav/floating/mobile-bar/cookie-banner estándar. **CSS byte-idéntico al de la home.**
- **Omitidos limpiamente (0 fugas en el body)**: marquee de stats, acordeón de credenciales, process, clinical-work, workshops, books, price-cards, caja about-spanish.

**Anti-doorway**: en el contenido principal (entre la primera sección y el footer, excluyendo el chrome y las reseñas byte-exactas): **0 secuencias >12 palabras compartidas** con index.html, es/index.html, expat-therapy y es/terapia-expatriados, en ambos idiomas.

**Reseñas (Bloque 5)**: las 3 con acento expat/internacional del inventario, **byte-idénticas** a la home de cada idioma (verificado): **Venny Sanjaya** (siguió en terapia online tras dejar Singapur), **Anna Vergés** (terapia en Singapur y el extranjero, comparación internacional), **K Siana** (trasfondos multiculturales). Jamás editadas.

**Cifras**: $120/$170 = canon (con enlace a pricing del idioma). La prosa del dueño introduce dos superficies nuevas del conteo de reseñas ("22 Google reviews" / "22 reseñas de Google"): **registradas en docs/update-review-count.md** en este mismo commit (regla del acta de graduación). Nota: el texto del dueño dice "more than 20 countries" (la home usa "21+"): compatible, más conservador, sin contradicción.

**Schema**: MedicalWebPage + FAQPage (6) + BreadcrumbList + MedicalBusiness. **Decisión documentada: SIN LocalBusiness todavía** (registro clínico local en trámite; se añadirá cuando el estratega lo ordene). hreflang recíproco con x-default; canonical propio; título EN 54 / ES 56 (≤65).

**Fuera de navegación**: cero menciones de Yerevan en nav/footer de las 74 páginas restantes (verificado); descubrible por sitemap, enlaces contextuales del par expat y URL directa.

## Integración

1. **Enlaces contextuales** en expat-therapy y es/terapia-expatriados, dentro de su sección principal de síntomas ("What Does Adjustment Difficulty Look Like?" / "¿Cómo Se Manifiesta la Dificultad de Ajuste?"), verificados entre H2s. (Nota de proceso: el primer anclaje automático cayó en la sección de reseñas y se detectó y reubicó en el mismo pase.)
2. **sameAs**: mentalzon.com añadido en las 4 páginas de entidad junto a expat.com; JSON-LD 0 errores.
3. **Sitemap 71→73** (par con hreflang + x-default, lastmod 2026-09-01) + lastmod al día en crisis pair y expat pair. lastReviewed 2026-09-01 en las 2 nuevas.

## Suite global (salida literal)

```
anatomía 17/17 usados + 8/8 omitidos (body) · CSS byte-idéntico a la home ×2 ·
anti-doorway contenido principal: 0 secuencias >12 palabras vs home y expat (EN y ES) ·
3 reseñas byte-idénticas ×2 idiomas · $120/$170 canon · JSON-LD 0 err · em dashes 0 · <em> 0 ·
FAQ 214 (202+12) dup 0 · blockquotes NUEVO CANON = 154 (148 + 3×2 reseñas) ·
wa.me NUEVO CANON = 469 (457 + 2×6) · titles 54/56 ≤65 · hreflang recíproco ·
crisis Armenia EN/ES con fuentes · nav/footer sin Yerevan en todo el sitio · sitemap 73 válido ·
mentalzon sameAs 4/4 · enlaces expat 2/2 · H1/titles intactos en las 8 preexistentes tocadas ·
render 375/1280 sin overflow (viewport exacto)
RESULT: ALL PASS
```

**Canon actualizado**: wa.me = 469 · blockquotes = 154 · FAQ = 214 · sitemap = 73 · páginas con `<head>` = 74 · superficies del conteo de reseñas: 17 + 2 nuevas (registradas).

## Doble auditoría acotada

**Primer veredicto: NO APTO por 4 bloqueantes de chrome · Todos resueltos en el mismo pase · Estado final: APTO.**

- **Raíz única encontrada por el auditor**: el ejecutor clonó el nav de la HOME (rutas relativas y anclas locales) en vez del chrome estándar de subpágina. Consecuencias: **B1** logo del nav en 404 en ambas páginas (`LOGO.webp` relativo); **B2** "Contacto" muerto en la ES (`#contacto` vs `id="contact"`); **B3** anclas `#home`/`#services` muertas; **B4** breadcrumb sin CSS (la home no define `.breadcrumb`), oculto bajo la nav fija.
- **Resolución**: nav reemplazado por el estándar de subpágina (de la plantilla canónica tests/phq-9) con switcher al par correcto; breadcrumb visible retirado (la anatomía de la home no lo tiene; el BreadcrumbList del schema se conserva). **Re-verificado con render CDP ampliado**: 0 imágenes rotas (`naturalWidth>0` en todas), h1 despejado de la nav fija, marca→home, Contacto→`/#contact` y `/es/#contacto`, sin overflow, en 375 y 1280 y ambos idiomas. Los checks de imágenes-rotas y oclusión quedan incorporados al gate estándar (lección registrada).
- **Menores aplicados**: (M1) el enlace de las páginas expat estaba fuera del `.container` (sin padding lateral en móvil): reubicado dentro, verificado; (M4) dos calcos ES corregidos ("se basa en procesos", "para ver si encajamos").
- **Menores registrados sin tocar**: (M2) "more than 20 countries" convive con el "21+" de la home: compatible, más conservador; unificar en la próxima actualización de conteos; (M3) "seis mudanzas por tres continentes" es cifra biográfica nueva del dueño (la home dice "seis países"): compatible si Ereván es la sexta, confirmar con el dueño; (M5) el enlace corto de Yandex Maps no es verificable en local: confirmar en la ronda visual que abre Komitas Avenue 52; (M6) x-default solo en las entradas nuevas del sitemap (patrón mixto preexistente).
- **Verificado limpio por el auditor con evidencia propia**: CSS byte-idéntico a la home (md5), anatomía 17/17 + 8/8 omitidos, anti-doorway 0 secuencias, reseñas byte-idénticas, cifras canon, crisis Armenia con corroboración externa propia (solidez ALTA), nav del resto del sitio intacto, schema sin LocalBusiness conforme a la decisión, FAQs 12/12 sin colisiones, flujo y español aprobados.
