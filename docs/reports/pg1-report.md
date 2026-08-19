# Reporte Comando PG-1 · Verdades únicas (post-graduación)

Fecha: 2026-08-18 · Base: `a10ef34` (main) · Rama: `pg1-review` · **2 decisiones resueltas por el estratega el 2026-08-19** (ambas: CONSERVAR; detalle en T3 y B3). Merge autorizado.

## T1 · Cifras de ciudad: un solo canon (tabla)

| Superficie | NY | Londres | Singapur | Encuadre |
|---|---|---|---|---|
| pricing (¶"value") | $250 to $400 | £100 to £200 | S$200 to S$350 | "is commonly listed in New York at" (añadido: antes era dato duro) |
| es/precios | entre $250 y $400 | entre £100 y £200 | entre S$200 y S$350 (dólares de Singapur) | "suele anunciarse en Nueva York" (añadido) |
| blog/online-therapy-high-performers | $250 and $400 | £100 to £200 | S$200 to S$350 | "commonly listed" (ya lo tenía, Comando G) |
| es/blog/terapia-online-profesionales | de $250 a $400 | £100 y £200 | de S$200 a S$350 (dólares de Singapur) | "suelen anunciarse" (ya lo tenía) |

Cifras viejas divergentes: **0 en todo el repo** ($300 to $400, £150 to £250, $200 to $300, sus formas ES, y "SGD" como etiqueta suelta: todos 0). El par de finanzas no imprime cifras de ciudad (solo "las tarifas que suelen anunciarse"): coherente sin cambios. Nota de auditoría (M3/M4, registradas): "less than half" de NY se cumple contra $250 por $5 de margen; el "$300 in Manhattan (rango medio)" de la aritmética sigue dentro del canon.

## T2 · Gestión vs regulación: doctrina única (la del hub)

Tarjetas reescritas en `emotional-regulation-therapy` y `es/regulacion-emocional` (symptom-cards, fuera del FAQPage: sin resync necesario): respuesta nueva "Not exactly, though they are trained together." / "No exactamente, aunque se entrenan juntas." con la distinción del hub (gestión = estrategias conscientes del momento; regulación = proceso de fondo del sistema nervioso) en palabras propias. Palabras clave de búsqueda conservadas (gestión emocional en adultos, manejo emocional, control de las emociones). Complementariedad verificada computacionalmente: n-grama común más largo tarjeta↔hub = 6 palabras (umbral: 12); hub NO tocado en esta pregunta (byte-idéntico, verificado por la auditoría).

**Extensión de clase (bloqueante B2 de la auditoría, corregido)**: `es/blog/tecnicas-regulacion-emocional` mantenía la doctrina vieja ("hablamos de lo mismo... El nombre importa menos") bajo su H2 "¿Regulación Emocional o Gestión Emocional?" y enlazando a la landing corregida. Párrafo reescrito a la doctrina nueva con tercera redacción propia; complementariedad blog↔hub 0 y blog↔tarjeta 0. El blog EN no tiene bloque equivalente (verificado). Restos de doctrina vieja ("hablamos de lo mismo", "Es la misma capacidad", "It is the same capacity"): **0 repo-wide**. De paso, esto elimina la duplicación entre-páginas que el acta de graduación registró en su familia 4 (bloque "casi calcado" servicio↔blog).

## T3 · TEPT/PTSD fuera de las enumeraciones de lanza

**10 retiradas** (no 8: faq y es/preguntas-frecuentes cuentan doble por visible+schema, resync automático por reemplazo total): faq ×2, does-online-therapy-work ×2, online-therapy-high-performers ×1, es/preguntas-frecuentes ×2, es/blog/funciona-la-terapia-online ×2, es/blog/terapia-online-profesionales ×1. La auditoría leyó las 10 frases resultantes: gramática natural, cero comas cojas, paridad EN/ES.

**DECISIÓN 1 — RESUELTA (estratega, 2026-08-19): CONSERVAR (excepción documentada)**: quedan exactamente **4 menciones** en el repo, todas en la FAQ diagnóstica "Is emotional dysregulation a diagnosis?/¿La desregulación emocional es un diagnóstico?" del par de regulación emocional (visible+schema, simétricas EN/ES): "...aparece en múltiples condiciones, incluyendo trastornos de ansiedad, depresión, TDAH, trastorno límite de personalidad, TEPT y burnout." Es una enumeración DSM-5 descriptiva en contexto educativo diferencial (junto a TDAH y TLP, que tampoco son servicios), no una lista de servicios de la práctica: no es lanza. El estratega confirma la opción (a): estas 4 menciones se conservan como supervivientes legítimos — retirar TEPT de una lista diagnóstica junto a TDAH/TLP la haría clínicamente coja. Esta FAQ queda registrada como la única excepción autorizada a la regla "TEPT/PTSD fuera de enumeraciones". En reseñas: 0 menciones.

## T4 · Par expat a tres niveles

"two levels/dos niveles" → "three levels/tres niveles" con tercer nivel nuevo en redacción propia ("environmental adjustment/ajuste del entorno": evaluar qué demandas pueden cambiarse y dirigir la energía a los cambios que más estabilidad devuelven). Complementariedad contra la sección "Qué Ayuda Realmente" del post protegido: n-grama común más largo = 5 palabras. **Bonus verificado por la auditoría**: el post protegido ya decía "sigue esta estructura de tres niveles"; el cambio cierra esa contradicción exacta. Post protegido: fuera del diff, **0 bytes** contra main.

## Auditoría acotada (resolución de sus 3 bloqueantes)

- **B1 (sitemap "no hecho") — FALSO BLOQUEANTE, documentado**: las 13 tocadas ya llevaban lastmod 2026-08-18 estampado hoy mismo por el merge de graduación; el paso corrió, reescribió valores idénticos y por eso el sitemap no aparece en el diff. Verificado explícitamente: 13/13 tocadas en 2026-08-18. Las 5 URLs con fechas anteriores (2026-08-12/13) son páginas NO tocadas hoy: correcto por diseño (lastmod = último cambio real).
- **B2 (blog ES con doctrina vieja) — CORREGIDO** (extensión de clase, arriba).
- **B3 (hub EN sin pregunta puente) — DECISIÓN 2 RESUELTA (estratega, 2026-08-19): CONSERVAR la asimetría 19/20**: es diseño de datos deliberado — la búsqueda "gestión emocional en adultos" solo existe en español, por lo que la pregunta puente solo tiene razón de ser en el hub ES. El hub EN se queda en 19 preguntas por diseño; no se añade la pregunta espejo. La tarjeta nueva EN no contradice frontalmente la definición amplia del hub (capacidad vs proceso), así que no queda tensión bloqueante. Asimetría registrada como intencional.

Menores registrados: margen de $5 en "less than half" (M3); "$300 mid-range" vs punto medio $325 (M4); "(dólares de Singapur)" tras la segunda cifra y también en es/precios (M5); eco fondo/base en la tarjeta ES (M6); &pound; en blogs vs £ literal en pricing (M7, preexistente).

## Suite global final

```
126 JSON-LD 0 errores · schema=visible 0 · FAQ 163 dup 0 · em dashes 0 · wa.me 387 ·
blockquotes 146 · H1/titles intactos en las 13 tocadas · protegido diff 0 bytes ·
lastmod 2026-08-18 en 13/13 tocadas · complementariedad: tarjeta↔hub 0, blog↔hub 0, blog↔tarjeta 0,
expat↔post protegido 0 (máximos 5-6 palabras, umbral 12)
```

## En vivo previsto (tras merge autorizado)

1. pricing grep "commonly listed" ≥1 · 2. es/regulacion-emocional grep "No exactamente, aunque se entrenan juntas" ≥1 (forma exacta declarada) · 3. faq grep "PTSD" = 0 · 4. es/terapia-expatriados grep "tres niveles" ≥1
