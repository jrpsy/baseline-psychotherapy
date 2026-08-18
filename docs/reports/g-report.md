# Reporte Comando G · Confianza y mantenimiento (previo a graduación)

Fecha: 2026-08-18 · Base: `a4b1f4d` (main) · Rama: `g-review` · **Sin bloqueantes abiertos** (el único bloqueante de la doble auditoría, un calco en prosa propia, quedó corregido en la misma rama).

## Pre-flight (ojo crítico)

1. **T1**: el conteo NO existe en el formato que asume el comando ("22 reviews/22 reseñas"); los formatos reales son `22 Google Reviews` (EN), `22 Reseñas en Google` (ES) y `(22 reviews)` (llms.txt). El inventario se hizo con patrón numérico amplio para no depender del formato asumido.
2. **T2**: el inventario encontró una tercera superficie con la afirmación de costo NY: el par de finanzas (blog/high-functioning-anxiety-finance + es/blog/ansiedad-alto-funcionamiento-finanzas, "less than half the average session cost in New York"), más dos párrafos derivados en el propio par de profesionales (el "average cost" y la aritmética con $300). Todos tratados. Falsos positivos descartados: "pound/SGD" en otras 7 páginas era ruido léxico ("pounding", "compound").
3. **T3**: la API pública sin key comparte cuota diaria anónima; se agotó (429). Veredicto cubierto con Lighthouse local (mismo motor de laboratorio de PSI) + análisis estructural.

## T1 · Conteo de reseñas: inventario y mecanismo

| Superficie | Formato | Valor |
|---|---|---|
| 8 páginas EN (index, anxiety, burnout, couples, depression, emotional-regulation, expat, workplace) | `22 Google Reviews` (bloque agregado 5.0★) | 22 ✔ |
| 8 páginas ES (es/index, terapia-ansiedad, terapia-burnout, terapia-parejas, terapia-depresion, regulacion-emocional, terapia-expatriados, formacion) | `22 Reseñas en Google` | 22 ✔ |
| llms.txt | `Rated 5.0 on Google Reviews (22 reviews)` | 22 ✔ |

**17/17 consistentes, cero desviaciones que corregir** (ningún 21 viejo ni formato roto). `aggregateRating` en schema: **0** (regla del Comando A intacta). pricing/es-precios llevan la línea `★ 5.0 on/en Google Reviews` **sin conteo**: es su formato propio desde F3-R, coherente por superficie; se documenta para que nadie lo "corrija" a futuro. **`docs/update-review-count.md` creado**: micro-comando con las 3 cadenas exactas, verificaciones viejo=0/nuevo=N (auditoría detectó y se corrigió que la puerta combinada excluía llms.txt por el `--include`; ahora son dos puertas), lastmod, commit directo a main (diseño deliberado del comando: mantenimiento del dueño sin ronda de revisión; la auditoría lo señaló como fricción y queda registrado como decisión).

## T2 · Comparativa de precios a formulación defendible (antes→después)

Rangos evaluados y conservados sin ajuste: NY $250-400, Londres £100-200, Singapur $200-350 SGD son rangos conservadores y vigentes como observación de mercado; **sin bloqueante de cifras**. La auditoría verificó multiconjunto de números idéntico antes/después ($250, $400, £100, £200, $200-350 SGD, $120, $300, $480, $1,200, $720, $8,640).

| Superficie | Antes | Después |
|---|---|---|
| high-performers ¶101 | "In Manhattan, a single therapy session with a licensed psychologist costs between $250 and $400. In London, private therapy runs £100 to £200... In Singapore, the range is..." | "Private-practice rates commonly listed in New York run between $250 and $400 per session with a licensed psychologist. In London, private therapy is typically listed at £100 to £200 per session. In Singapore, the equivalent range is $200 to $350 SGD." |
| high-performers ¶137 | "less than half the average session cost in New York" | "less than half of the rates commonly listed in New York" |
| high-performers ¶139 | "four sessions at $300 in Manhattan" | "four sessions at a mid-range $300 in Manhattan" |
| high-performers meta + og:description | "$120 vs $300 in Manhattan." | "$120 per session, below the rates commonly listed in Manhattan." (misma clase T2 en superficie SERP; hallazgo de auditoría) |
| profesionales ¶101 | "En Manhattan, una sola sesión... cuesta entre $250 y $400 dólares..." | "Las tarifas de práctica privada que suelen anunciarse en Nueva York van de $250 a $400 dólares por sesión con un psicólogo licenciado. En Londres, la terapia privada se anuncia normalmente entre £100 y £200 por sesión. En Singapur, los precios habituales van de $200 a $350 SGD." |
| profesionales ¶137 | "menos de la mitad del costo promedio de una sesión en Nueva York" | "menos de la mitad de las tarifas que suelen anunciarse en Nueva York" |
| profesionales ¶139 | "a $300 en Manhattan" | "a un precio de rango medio de $300 en Manhattan" |
| finanzas EN/ES (inventario) | "less than half the average session cost..." / "menos de la mitad del costo promedio..." | espejo exacto de ¶137 en ambos idiomas |

**Nota sobre el texto de ejemplo del comando**: la redacción ES ilustrativa ("se listan comúnmente... rondan entre") contenía el calco *listar* = "publicar un precio", que no existe en español nativo (bloqueante de la doble auditoría, 5 ocurrencias). Se resolvió con el registro nativo "suelen anunciarse / se anuncia normalmente / precios habituales", conservando el framing de observación de mercado y las cifras. Greps de cierre: formulaciones viejas 0/0/0/0, calcos 0, "rondan entre" 0.

## T3 · Veredicto INP: ARTEFACTO de medición de Clarity

Salida literal de la API (12+ intentos a lo largo de ~15 min, home y anxiety-therapy-online, strategy=mobile): `ERROR 429 RESOURCE_EXHAUSTED · "Quota exceeded for quota metric 'Queries' and limit 'Queries per day' of service 'pagespeedonline.googleapis.com'"` (cuota diaria compartida del acceso anónimo sin key; reintentable otro día o con key propia, que además daría INP de campo CrUX si el sitio alcanza umbral de muestras).

Cobertura equivalente con **Lighthouse 12 local** (mismo laboratorio que PSI, mobile, throttling simulado):

```
home:    perf score 1.00 · TBT 20 ms · TTI 1.5 s · max-potential-FID 120 ms · LCP 1.5 s · CLS 0.001
         main-thread 0.7 s · bootup JS 0.0 s · long tasks: 2 (máx 121 ms)
anxiety: perf score 1.00 · TBT 10 ms · max-potential-FID 60 ms · LCP 1.6 s · CLS 0.016
         long tasks: 3 (máx 177 ms)
```

Estructural: sitio estático, 5 bloques de JS inline (~4 KB totales), 0 scripts externos síncronos, 0 setTimeout/setInterval, 7 listeners triviales (acordeón FAQ, fade-up observer). Un INP real de 23.000 ms exigiría una tarea que bloquee el hilo principal 23 segundos; la tarea más larga observada es 177 ms (130x menos). Con LCP 1.13 s y CLS 0 de la propia Clarity, el 23 s es un outlier clásico de atribución (interacción en pestaña en segundo plano o durante descarga de página, que en sitios de tráfico bajo domina el percentil por muestra escasa). **Sin problema real; nada que tocar.** Recomendación registrada: si Clarity lo repite el mes próximo, correr PSI con key para obtener el INP de campo de CrUX.

## T4 · Puente de reseñas en las páginas B2B

Líneas exactas del comando antepuestas en la section-intro de reseñas de workplace-mental-health-training y es/formacion-salud-mental-laboral (posición idéntica en ambos idiomas, formato `<p>` del resto de intros). **Reseñas byte-idénticas a HEAD verificadas** (grid completo comparado); bloque agregado y H1/titles intactos. La auditoría valida que el puente no contradice nada y resuelve una ambigüedad real (reseñas individuales en página B2B). Notas de auditoría sobre el texto mandado, reportadas SIN tocar (es copy exacto del comando): (a) sugiere colocarlo después de la bajada existente ("Clients who came looking for...") en vez de antes, porque la bajada es un fragmento sin verbo que se apoyaba en el H2; se siguió el "antepón" literal del comando; (b) alternativas idiomáticas para "What organizations hire is the same clinical standard that individual clients rate" y para "la práctica terapéutica detrás de la formación" (→ "que hay detrás de"). Decisión del estratega si quiere pulirlas.

## T5 · Decisiones cerradas para la graduación (sin código)

- **"running on fumes" SE CONSERVA**: voz de marca, idioma del dueño aprobado por él mismo en su ronda.
- **Jerga financiera** ("after-hours", "P&L") conservada por audiencia.
- **Conjunciones iniciales** (par de IE, EN): registro válido, en vigilancia.

## Menores reportados sin tocar

"They are the market rate for qualified professionals..." / "Son la tarifa del mercado..." (¶101, preexistente): tras el reencuadre, sigue siendo la afirmación más categórica del párrafo; decisión editorial si se suaviza. Deriva Nueva York (rango) / Manhattan (aritmética del $300): defendible (Manhattan ⊂ NY, "a mid-range $300" no afirma punto aritmético), registrada. Meta ES de profesionales sin mención de precio (brecha de paridad preexistente con la EN, hoy ya matizada). Duplicación preexistente entre blogs ("The clinical structure is the same... Park Avenue" en high-performers y finanzas): fuera del alcance anti-dup (que cubre FAQs/hub/author box), registrada.

## Suite global final

```
em dashes 0 · wa.me 387 · blockquotes 146 · price 2/2 · 126 JSON-LD 0 errores ·
hunks del diff tocando FAQ/schema: 0 (estado schema=visible y anti-dup invariante vs a4b1f4d,
verificado 0/0 en F3-C sobre esta misma base) · conteo 22: 17/17 · aggregateRating 0 ·
H1/titles intactos en los 6 HTML tocados · reseñas byte-idénticas · lastmod 2026-08-18 en los 6
```

## En vivo previsto (tras merge autorizado)

1. home grep `22` en contexto reviews ≥1 · 2. high-performers grep "commonly listed" ≥1 · 3. workplace grep "the therapy practice behind the training" ≥1 · 4. es/formacion grep "detrás de la formación" ≥1 · 5. es/ grep "5.0" ≥1
