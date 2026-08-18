# Reporte Comando F3-S · Críticas del dueño a las páginas de servicio (modo presupuesto)

Fecha: 2026-08-18 · Base: `8f8a1ae` (main) · Rama: `f3s-review` · **Sin bloqueantes abiertos** (el estructural de la card ancha se detectó en la auditoría acotada y quedó corregido y verificado antes del commit).

## T1 · Encabezados citables (50 reemplazos)

Los 14 pares de diferenciales/porqués/psicología + los 12 "Conditions Related"/"Condiciones Relacionadas" + los 24 de la política sin "Online" (expectativas y costo, 12 páginas × 2). Los `<br>` de balanceo conservados donde el largo lo pide (couples EN/ES); labels "The Differential"/"El Diferencial" en burnout y expat. Guardias: viejos anclados 0/20 patrones (el único hit residual de "How Much Does Online" es `pricing/index.html:441`, fuera del alcance de las 12 y donde "Online" es el sujeto real de la pregunta); nuevos ≥1; ningún H2 nuevo coincide con mainEntity de FAQPage (anti-dup global en 0); "Online" intacto en H1, titles y prosa.

## T2 · Patrón "general primero, Baseline después" (24 aperturas)

Costo ×12: apertura general + "At Baseline Psychotherapy, every session includes clinical preparation..." / "En Baseline Psychotherapy, cada sesión incluye...". Adaptación documentada en parejas EN/ES (su párrafo abre con la frase de 75 minutos, que se conserva completa tras la apertura general: "...At Baseline Psychotherapy, couples sessions are 75 minutes..."). Cifras y duraciones intactas (verificado en el diff). Expectativas ×12: "Effective X therapy is structured: assessment first, targeted intervention, then consolidation. At Baseline Psychotherapy, that structure has three defined phases..." con X natural por página, y espejo ES "Una terapia X efectiva es estructurada...". Ninguno de los 24 textos vive en FAQPage (sin resync necesario; suite schema=visible en 0).

## T3 · Léxico premium (5 reemplazos, viejos en 0)

travels alone→arrives alone · arrives with...attached→arrives alongside · travels with→accompany · viaja solo→llega solo · viaja más a menudo→acompañan. **Candidatos reportados sin tocar** para la próxima ronda: "running on fumes" (decisión pendiente registrada, en homes y About CTA compartido); "on fumes"/"funcionando al límite" (mismo bloque); "engine of the conflict" (metáfora aprobada en F3-B, se lista solo por inventario); "standing down"/"never stands down" (anxiety, intro de condiciones); "wired"/"switch off" (anxiety hub capsule, aprobada en F1). Ningún otro coloquialismo relevante en las 12.

## T4 · Sección de señales de regulación (tabla antes→después, palabras)

| Card | EN | ES |
|---|---|---|
| React/Reacciono | 70→55 | 76→55 |
| Feel Nothing/Ya No Siento | 66→55 | 69→51 |
| Too Much/Demasiado | 71→55 | 74→55 |
| Mood Shift/Cambio de Ánimo | 58→53 | 74→53 |
| Calm Down/Tardo en Calmarme | 69→52 | 79→55 |
| Decisions/Decisiones | 66→55 | 74→54 |
| Paso 1 Assessment | 70→49 | 78→53 |
| Paso 2 Skill-Building | 74→47 | 81→52 |
| Paso 3 Integration | 68→47 | 84→53 |

Todos los hechos clínicos conservados (umbral/appraisal, sobrecorrección protectora, inundación por capacidad excedida, inestabilidad basal "clínico y tratable", parasimpático/tiempo de recuperación, impulso de acción fight-flight-freeze-appease, cribado primaria-vs-secundaria, marcos EI/CBT/ACT/somático, mantenimiento post-tratamiento). La coletilla "y ofrezca resultados reales" (flag del F3-B) cayó con la condensación del paso 1 ES. **Card ancha**: el bloque gestión-vs-regulación es ahora una `symptom-card` con `grid-column:1/-1`, texto intacto (46/45 palabras, ya ≤55), **dentro del grid como última fila** en ambos idiomas (la primera inserción quedó fuera del grid tras el CTA; la auditoría acotada lo detectó como bloqueante y está corregido y verificado por profundidad de divs + HTML balanceado).

## T5 · Hero de burnout

Declarado "ya está bien" tras lectura: definición → clasificación OMS (referencia breve post-F3B) → mecanismo → resultados medibles, sin tropiezos en EN ni ES. **Sin cambios.**

## T6 · Ortografía EN

Chequeo programático (diccionario del sistema + límites de palabra, reseñas y nombres propios excluidos) sobre las 6 EN: **0 typos inequívocos**. Los términos no reconocidos son palabras legítimas ausentes del diccionario (waitlist, worldwide, timeline, mindset, dysthymia, catastrophizing, co-occur, standalone, dopamine, neuroscience...) o clínicos del dominio (dysregulate, downregulate, hyperactivated, neurobiological). Sin dudas pendientes.

## Auditoría acotada (diffs + sección de regulación renderizada)

- **BLOQUEANTE detectado y corregido**: card ancha fuera del `.symptoms-grid` (ver T4).
- **Menor, texto del dueño, solo reporte**: el H2 nuevo de burnout ("What's the Difference Between Work Stress and Burnout?") nombra 2 de los 3 términos que el cuerpo sigue diferenciando (falta "occupational exhaustion" del label viejo); el cuerpo responde los tres.
- Limpio: hechos clínicos comparados lado a lado en el diff, cifras/duraciones de costo intactas, em dashes 0 en los hunks, encabezados nuevos respondidos por sus secciones (spot-check 3 pares).

## Suite final

```
126 JSON-LD 0 errores · schema=visible 0 desync · FAQ dup 0 · em dashes 0 ·
wa.me 387 · blockquotes 146 · H1 12/12 y titles 12/12 byte a byte ·
lastmod 2026-08-18 en las 12 · HTML balanceado en las 2 de regulación
```

## En vivo previsto (tras merge autorizado)

1. burnout grep "What's the Difference Between Work Stress and Burnout?" ≥1 · 2. anxiety grep "Why Doesn't Anxiety Go Away on Its Own?" ≥1 · 3. es/regulacion-emocional grep "¿Qué Condiciones Se Relacionan con la Desregulación Emocional?" ≥1 · 4. burnout grep "What therapy costs depends on" ≥1 · 5. es/terapia-burnout grep "El burnout rara vez llega solo" ≥1
