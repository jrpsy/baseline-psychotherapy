# Reporte Comando F3-C · Blogs y páginas de sistema (cierre del examen F3)

Fecha: 2026-08-18 · Base: `959f8ec` (main) · Rama: `f3c-review` · **1 bloqueante editorial esperando decisión** (redundancia de plantilla en las políticas de privacidad); todo lo demás completo.

## Pre-flight

Sin bloqueantes de ejecución. Hallazgos de mapeo: los T4 son tarjetas "Continue Exploring" (no encabezados de artículo); las oraciones >55 reales del par de IE son 3 por idioma (los conteos 4/5 del comando incluían artefactos del aplanado título+nav, documentado); el barrido T1.3 destapó un hit EN adicional (FAQ de anxiety) cuyo espejo ES ya había sido limpiado en F1.

## T1 · Artículos de efectividad + barrido de invocaciones

Intros sin invocación sin nombre ("The short answer is yes." / "La respuesta breve es sí."); la sección de investigación queda como única portadora del respaldo (S1+S2, aperturas answer-first que ya diferían de las intros en redacción: sin reformulación necesaria). **Inventario del barrido**: (a) las 2 intros (resueltas); (b) `anxiety-therapy-online` FAQ "with decades of clinical research supporting its effectiveness" → eliminada la invocación (espejo del fix F1 de es/terapia-ansiedad; visible+schema 2x); (c) `blog/online-depression-treatment` "Decades of clinical research support that causal direction..." (mayúscula que escapó a los greps case-sensitive de F1) → espejo EN de la decisión F1 ya tomada para su gemelo ES: "Behavioral activation works in precisely that causal direction..." (la primera redacción "works precisely that" era un calco; la auditoría final lo bloqueó y quedó corregido a la forma nativa). Cierre case-insensitive: 0 restos en el repo.

## T2 · Índices del blog al embudo

Ambos CTAs con el copy exacto mandado (consulta gratuita de 15 minutos); H2s "Start Your Process"/"Inicia Tu Proceso" conservados (no contradicen la oferta); botones y prefills intactos. Nota: es/blog/index ya usaba "Escríbeme" en el copy viejo.

## T3 · Escríbeme

2 páginas (es/index, es/sobre-mi); grep global confirma que no vivía en más. "Escríbenos" = 0 en el repo.

## T4 · Encabezados de tarjeta

2 tarjetas EN → "What Is Emotional Intelligence and Why Does It Matter?" (guardia anti-FAQ sin coincidencia; viejos 0). **ES no tocado y reportado**: "Qué Es la Inteligencia Emocional y Por Qué Importa" es una construcción indirecta bien formada en español (no comparte la cojera del EN).

## T5 · Oraciones kilométricas del par de IE (tabla antes→después)

| Oración | EN | ES |
|---|---|---|
| Burnout (4 ramas) | 61→32+37 (2 or.) | 72→33+41 (2 or.) |
| Ansiedad (4 ramas) | 66→30+28+19 (3 or.) | 76→31+27+21 (3 or.) |
| Depresión (4 facetas) | 57→33+27 (2 or.) | 66→36+31 (2 or.) |

Todos los hechos (las 4 ramas con sus déficits nombrados) conservados; paralelismo EN/ES verificado por la auditoría. Oraciones largas de otros posts: ninguna >55 real detectada fuera del par (los conteos de otros posts quedaron bajo el umbral); el post protegido ni se examinó para esto (excepción absoluta).

## T6 · Examen de 19 posts + sistema: inequívocos corregidos

**EN**: enlace "Privacy Policy" ilegible (blanco sobre fondo claro) en `policies.html` → `color:inherit;opacity:.7` (mismo defecto encontrado y corregido en `es/politicas.html`); doble espacio en `pricing`. **ES**: 3 tarjetas "5 Técnicas" entity-encoded que escaparon al replace UTF-8 del Comando E → "7 Técnicas" (misma corrección, variante de codificación); typo "escíbeme" → "escríbeme"; footers "Políticas de Servicio" incompletos normalizados a la convención mayoritaria "y Reembolso" (**22 instancias** en total: las 4 del examen + 8 más del mismo defecto en servicios ES + la variante "y Aviso de Reembolso" de es/preguntas-frecuentes); link "Política de Privacidad" ausente en el footer de `es/precios` → añadido (regresión confirmada contra el gemelo EN); href cruzado de idioma en `politica-privacidad.html` (/policies.html → /es/politicas.html) + "Políticas del Servicio" → "de Servicio". Los 2 "Políticas de Servicio" cortos restantes son legítimos (H1 de la propia página y su referencia por nombre).

**Verificaciones de paso**: author box canónico 20/20; los 4 posts con FAQ conservan 3 preguntas (visible+schema).

## BLOQUEANTE editorial (espera decisión)

**Redundancia de plantilla en las políticas de privacidad (ambos idiomas)**: la información "última actualización + contacto" se repite tres veces al final (sección Cambios, sección Contacto y nota de cierre). Es plantilla preexistente del sitio, no defecto de traducción; tocarla es decisión de estructura de contenido. Opciones: (a) dejar como está (redundancia inofensiva en página legal), (b) eliminar la nota de cierre duplicada en ambos idiomas conservando las dos secciones.

## Menores (solo reporte)

"Online vía Google Meet" (terapia-online-profesionales, es/precios) vs "Online por Google Meet" (mayoría de blogs ES); anglicismos de jerga financiera en ansiedad-alto-funcionamiento-finanzas ("after-hours", "P&L") que el examinador recomienda conservar por audiencia; dos oraciones nuevas del párrafo de ansiedad EN empiezan con conjunción (registro editorial válido, patrón a vigilar).

## Veredictos de página (resumen)

Los 19 posts editables + índices + legales: coherentes y limpios tras los fixes (tabla completa en los exámenes; las páginas con más defectos mecánicos eran terapia-online-profesionales y las legales, todos resueltos). **Post protegido es/blog/burnout-expatriados: veredicto de lectura "sólido, sin fricciones", CERO cambios, diff contra main = 0 bytes (verificado dos veces).** Confirmación pricing/es-precios/books: sin cabos sueltos de rondas previas (solo el doble espacio y el footer, resueltos).

## Suite final

```
Greps T1-T4: 16/16 en el valor esperado · cierre case-insensitive de invocaciones: 0
126 JSON-LD 0 errores · schema=visible 0 · FAQ dup 0 (163 preguntas) · em dashes 0 ·
wa.me 387 · blockquotes 146 · precios 2/2 · H1 y titles intactos en todas las tocadas ·
author boxes 20/20 · lastmod 2026-08-18 en las 30 tocadas · post protegido diff 0 bytes
```

## En vivo previsto (tras merge autorizado)

1. does-online-therapy-work grep "The short answer is yes." ≥1 · 2. es/blog/index grep "consulta gratuita de 15 minutos" ≥1 · 3. es/index grep "Escríbeme" ≥1 y "Escríbenos" = 0 · 4. emotional-regulation-techniques grep "Why Does It Matter?" ≥1 · 5. title del post protegido sin cambios (curl)
