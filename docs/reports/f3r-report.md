# Reporte Comando F3-R · Ronda del dueño (main + about + transversales)

Fecha: 2026-08-12 · Base: `75f7f0f` (main) · Rama: `f3r-review` · **1 bloqueante esperando insumo del dueño (URLs de Google Play)**; el resto completo.

## Pre-flight

Sin bloqueantes de ejecución. Notas: la enumeración ES real del Approach era "sobreexigencia crónica, agotamiento relacional, perfeccionismo o un estado de alerta sostenido" (conservada según 1.4); T10 requería renombrar las tarjetas del taller ("Half-Day/Full-Day Session" son menciones de duración) bajo el mandato "la verdad según el contexto"; el barrido T7 encontró oferta divergente también en `blog/index.html` y `es/blog/index.html` (reportado, se corrige en F3-C).

## Tareas 1-8 aplicadas (tabla viejo→nuevo verificada: viejos 0, nuevos ≥1, 24 checks OK)

- **T1 (homes)**: "burnout or related conditions" / "condiciones relacionadas"; descargo de casos acortado en ambos idiomas; "Amazon and Google Play" / "Amazon y Google Play".
- **T2 (About hero, 2 párrafos exactos del dueño, EN+ES)**: primera persona, "I founded the practice in New York in 2019...", "My approach is both process-based and evidence-based...". Complementariedad: 8 frases >12 palabras del hero, 0 compartidas con FAQs de marca/author box.
- **T3 (PBT)**: "and has kept refining that practice since" + "integrated under one framework" y espejos ES.
- **T4 (intro formación)**: párrafos exactos del dueño EN/ES; "medical studies" = 0 en el repo.
- **T5**: "often in a new language" / "muchas veces en un idioma nuevo".
- **T6**: H2 "What Therapy Services Does J.R. Hernandez Offer?" / "¿Qué Servicios de Terapia Ofrece J.R. Hernandez?" + párrafos de oferta; guardia anti-FAQ sin coincidencias; viejos anclados a 0.
- **T7**: CTA del About = bloque exacto de la home en ambos idiomas (bloque funcional compartido, exento de complementariedad). **Barrido reportado sin corregir**: `blog/index.html` ("schedule your first session") y `es/blog/index.html` ("reservar tu primera sesión") divergen del embudo → F3-C.
- **T8 (footer Practice/Práctica)**: hallazgo del barrido: **la propia home ES no tenía "Blog"** en su columna; se añadió en la posición de la EN y se normalizaron 23 páginas (EN: faltaba Blog en about y 8 páginas más, pricing tenía el orden alterado; ES: variantes "Tarifas"/"Honorarios" y href `/es/#pricing` → "Precios" `/es/precios/`). Paridad final verificada: 6/6 ítems idénticos por idioma en las 52 páginas con footer completo.

## T9 · Ratings enlazados

24 enlaces discretos a `https://share.google/dQE0CvnGhGx0mbjZq` (`target="_blank" rel="noopener"`, `color:inherit;text-decoration:none`, texto visible idéntico): homes ×4 cada una (2 spans del marquee + chip del hero + bloque agregado), 12 páginas de servicio/taller ×1 (bloque agregado), pricing/es-precios ×1 (línea "★ 5.0 ..."). Cero dentro de texto de schema (los 4 hits de `share.google` en JSON-LD son los `sameAs` del Person, entidad preexistente del Comando A, no menciones de rating).

## T10 · Erradicación de duración del taller

Inventario y tratamiento: tarjetas renombradas **"Focused Session"/"Full Program"** ("Sesión Esencial"/"Programa Completo"); subtítulos → "Duration tailored on a scoping call · Online or On-Site · 8 to 30 participants" (+ES); "without a full-day commitment" → "without committing to the full program" (+ES); FAQ de formatos reescrita como cápsula con el hecho del dueño (visible + schema, resync); descripción del Service schema EN corregida. **Ampliación por auditoría (misma clase)**: resúmenes del taller en `index.html`/`es/index.html` (visible + schema) → "format and duration are tailored to each organization..." ; prefills de WhatsApp de las 4 tarjetas actualizados a la oferta renombrada (presencia y destino intactos; doctrina de parámetros F3-A). Grep de cierre: **0 menciones de duración en las 4 páginas** (homes + taller EN/ES).

## Doble auditoría (11.6): 3 bloqueantes, 2 resueltos, 1 esperando

1. **RESUELTO** · Fuga de "half-day/full-day/media jornada/jornada completa" en los prefills de WhatsApp del taller → alineados a la oferta renombrada.
2. **RESUELTO** · Los resúmenes del taller en ambas homes contradecían la política nueva (visible + JSON-LD) → erradicados.
3. **ESPERANDO INSUMO** · **"Amazon and Google Play" sin enlace accionable**: el texto es el mandado por el dueño (T1.3), pero las páginas solo tienen botones "Get It on Amazon"/"Consíguelo en Amazon"; `play.google` no existe en el repo. **Se necesitan las URLs de Google Play de los dos libros** para añadir el botón/enlace (propuesto para F3-C o mensaje siguiente). El texto mandado queda publicado en la rama tal como se ordenó.

Menores aplicados: capitalización del H2 del CTA de es/sobre-mi igualada a la home ("Comienza tu Proceso", bloque compartido). Menores reportados sin tocar: "Mi enfoque es basado en procesos y basado en evidencia" (texto exacto del dueño, calco leve; alternativa "se basa en procesos y en evidencia" si se quiere); discontinuidad 6 tarjetas visibles en home vs 7 en About (decisión de marca del Comando D: la credencial 7 es de segunda línea; el schema de las homes sí lista las 7); prefills de blog/index y es/blog/index divergentes del embudo (junto al CTA de T7, para F3-C).

## Veredicto de flujo (11.2, las 4 principales)

- **index.html / es/index.html**: flujo intacto; los tres deltas del dueño se leen naturales; resúmenes del taller ahora coherentes con la política de duración; paridad EN/ES correcta.
- **about/index.html**: hero en primera persona → secciones de entidad en tercera → relato en primera: alternancia deliberada que la auditoría valida como legible; cápsula→referencia respetada (hero vs PBT vs formación comparten conceptos con redacción distinta, 0 verbatim); CTA igualado al embudo bajo "Start Your Process".
- **es/sobre-mi/index.html**: paridad completa; mismos veredictos; nota del calco del hero (texto del dueño) arriba.

## Suite global final

```
126 JSON-LD 0 errores · schema=visible 0 desync · FAQ dup 0 · em dashes 0 ·
wa.me 387 · blockquotes 146 · price 2/2 · H1 34/34 tocadas intactos ·
lastmod 2026-08-12 en las 34 páginas del diff (incluida la home raíz) ·
share.google: 24 enlaces correctos, 0 en schema · duración taller: 0 en las 4 páginas
```

## Verificación en vivo prevista (tras merge autorizado)

1. `curl .../about/ | grep -c "What Therapy Services Does J.R. Hernandez Offer?"` → ≥1
2. `curl .../about/ | grep -c "often in a new language"` → ≥1
3. `curl .../ | grep -c "share.google"` → ≥1
4. `curl .../workplace-mental-health-training/` grep cifras de horas → 0
5. `curl .../es/sobre-mi/ | grep -c "¿Qué Servicios de Terapia Ofrece J.R. Hernandez?"` → ≥1
