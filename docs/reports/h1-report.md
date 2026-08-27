# Reporte Comando H-1 · "How Much Does Therapy Cost in Singapore?" (par EN/ES)

Fecha: 2026-08-27 · Base: `8f74943` (main) · Rama: `h1-review` · Regla maestra: clon estructural de blog/high-functioning-anxiety-finance (y su par ES), solo contenido nuevo (provisto y final).

## Páginas nuevas (2)

/blog/therapy-cost-singapore/ · /es/blog/costo-terapia-singapur/ — construidas por sustitución anclada de slots sobre el archivo de plantilla íntegro de cada idioma (el chrome queda byte-idéntico por construcción).

**Checklist de paridad estructural (verificado programáticamente, EN y ES): 24/24 componentes**
analytics bootstrap · og:type article + article:author + article:published_time · BreadcrumbList/Article/FAQPage en 3 JSON-LD single-line del patrón · Yandex Metrika (los blogs conservan la analítica estándar; la excepción de privacidad aplica solo a las páginas interactivas) · publisher.js · nav con Blog current y switcher al par · breadcrumb 3 niveles · article-hero (kicker/H1 con br/byline/imagen) · article-body/content · H2s de contenido · FAQ H2 + 3×H3/P = schema · blockquote de cierre (slot de cierre de la plantilla, mapea el "Cierre" del comando) · blog-cta · author box **byte-idéntico** · bloque Preferred Source · related articles ×3 · CTA section · footer · floating whatsapp · mobile bar · scripts · cookie banner · **CSS byte-idéntico a la plantilla**.

**Decisiones documentadas**:
- **Imagen**: no se proveyó asset nuevo; se reutiliza `blog-online-therapy-high-performers.webp` (temática afín: profesional/laptop) con alt propio veraz. Sustituible cuando el dueño aporte imagen propia del post.
- **Enlaces internos añadidos al texto final sin cambiar palabras**: "USD $120 per individual session"→/pricing/ (ES→/es/precios/); "burnout, anxiety, depression, a relationship under strain"→los 4 servicios del idioma.
- **Cierre como blockquote**: el párrafo de cierre del comando ocupa el slot de blockquote final de la anatomía de la plantilla (mismo rol editorial).

## Coherencia de cifras (puerta dura)

| Cifra del post | Canon del sitio | Veredicto |
|---|---|---|
| "S$200 to S$350" (rango de consultas establecidas) | pricing: "In Singapore, S$200 to S$350" · es/precios: "entre S$200 y S$350 (dólares de Singapur)" · blog high-performers ídem | **IDÉNTICO al canon** |
| USD $120 por sesión individual | canon universal del sitio | **IDÉNTICO** |
| "S$150 to S$350" (mapa amplio del mercado) y "below S$150" (opciones comunitarias) | cifras nuevas PROVISTAS por el dueño en el comando (no inventadas); no contradicen el canon: lo enmarcan | Documentadas como ampliación de canon del dueño |
| ES: "(dólares de Singapur)" en la primera mención de S$ | regla registrada | Cumplida |

Cifras divergentes viejas ($300 to $400, S$200 to S$300, £150...): **0 en los posts**.

## Integración

1. **Índices de blog**: card nueva como PRIMER ítem del grid en blog/ y es/blog/ (patrón single-line exacto de las cards existentes); lastmod de ambos índices al día en sitemap.
2. **Enlaces internos en pricing/es-precios**: frase nueva al final de la sección de valor (tras el párrafo de tarifas por ciudad, dentro de la sección), ES en tú; FAQs de pricing intactas.
3. **Sitemap 69→71** (par con hreflang recíproco, priority 0.6 como los blogs, lastmod 2026-08-27) + lastmod al día en blog/, es/blog/, pricing/, es/precios.
4. lastReviewed: no aplica (los posts no llevan MedicalWebPage; ninguna página con lastReviewed editada).

## Suite global (salida literal)

```
paridad estructural 24/24 EN y ES · CSS y author box byte-idénticos · FAQ 3+blockquote 1 por post ·
canon S$200-S$350 idéntico en pricing/posts · USD $120 · (dólares de Singapur) 1ª mención ·
cifras viejas divergentes 0 · titles 56/51 ≤65 · JSON-LD 0 err · em dashes 0 · <em> 0 ·
FAQ 202 (196+6) dup 0 · blockquotes NUEVO CANON = 148 (146 + 2 cierres de plantilla:
el gate "146" del comando era incompatible con la regla maestra de clon, documentado) ·
wa.me NUEVO CANON = 457 (445 + 2×6) · sitemap 71 válido ·
H1/titles intactos en las 4 preexistentes tocadas · cards en índices · enlaces pricing 2/2
RESULT: ALL PASS
```

**Canon actualizado**: wa.me = 457 · blockquotes = 148 · FAQ = 202 · sitemap = 71 · páginas con `<head>` = 72.

## Doble auditoría acotada

**Primer veredicto: NO-GO por B1 · Resuelto en el mismo pase · Estado final: GO global.**

- **B1 (real, encontrado por el auditor)**: el slot de imagen quedó incoherente en ambos posts: og:image y Article.image apuntaban a la imagen elegida (high-performers) pero el `src` del hero seguía siendo el de la plantilla (pantalla de trading), y el alt no describía ninguna de las dos. **Resuelto**: los tres puntos alineados a `blog-online-therapy-high-performers.webp` (verificación programática og==Article.image==hero en ambos), alt veraz nuevo (siluetas de profesionales en aeropuerto), og:image:height y dimensiones intrínsecas corregidas a 1200×812 (las reales, las mismas que usa el post dueño de la imagen).
- **Menores aplicados en el mismo pase**: (M1) x-default añadido a las 2 entradas nuevas del sitemap (patrón de los 20 posts); (M3) la frase del blog-cta ya no promete una "checklist" inexistente ("you keep the map either way" / "el mapa te lo quedas igualmente", referencia al mapa honesto del post).
- **Menores registrados sin tocar**: (M2) meta descriptions de 166/168 chars (texto dictado del comando; se truncará en SERP: decisión del dueño si acortar); (M4) dos giros de estilo ES señalados ("consultas...consultas", "a juego"), sin error gramatical.
- **Verificado limpio por el auditor**: clon byte-idéntico en CSS/author box/Preferred Source/footer/barras/scripts/banner con anatomía y orden exactos; FAQ schema=visible 3/3 por idioma y 6 preguntas únicas entre las 202; cifras EN↔ES idénticas y S$200-S$350 coincidente con pricing/es-precios/high-performers, USD $120 canon, cero contradicciones; cero 6-gramas compartidos con la sección de valor de pricing (complementariedad); enlaces permitidos sin alterar texto visible; integración correcta (cards primeras del grid, enlaces de pricing dentro de sección, lastmod al día); flujo y español natural aprobados en lectura completa.
