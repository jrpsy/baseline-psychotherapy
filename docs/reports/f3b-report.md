# Reporte Comando F3-B · Sección de servicios completa (12 servicios + 2 taller)

Fecha: 2026-08-11 · Base: commit `01c0b15` (main) · Estado: trabajo completo en rama de revisión `f3b-review`, **pendiente de decisiones sobre 8 bloqueantes editoriales** antes de la doble auditoría final (5.5) y el merge a main.

## Pre-flight

Sin bloqueantes de ejecución. Hallazgo de mapeo: el H2 ES del bloque de tarjetas no era "Otras Especializaciones..." sino **"Otras Especialidades de Terapia Online"** (verificado en las 6 ES antes de tocar). Los 12 encabezados "What to Expect"/"Qué Esperar" localizados con su `<br>` de balanceo; mailtos de las 14 revisados (3 con bug de codificación, ver abajo); duplicación label/H2 confirmada en formacion ES **y** su gemelo EN ("What the Training Covers" vs "What Does the Training Cover?"); frase DSM-5 de 62 palabras localizada en visible + schema.

## Tarea 1 · Encabezados "What to Expect" a pregunta (12/12)

| Página | Viejo | Nuevo |
|---|---|---|
| burnout-therapy | What to Expect From\<br\>Online Burnout Therapy | What Should I Expect From Online Burnout Therapy? |
| anxiety-therapy-online | What to Expect From\<br\>Online Anxiety Therapy | What Should I Expect From Online Anxiety Therapy? |
| depression-therapy-online | What to Expect From\<br\>Online Depression Therapy | What Should I Expect From Online Depression Therapy? |
| emotional-regulation-therapy | What to Expect From Online\<br\>Emotional Regulation Therapy | What Should I Expect From Online Emotional Regulation Therapy? |
| couples-therapy-online | What to Expect From\<br\>Online Couples Therapy | What Should I Expect From Online Couples Therapy? |
| expat-therapy | What to Expect From Online\<br\>Expat & Transition Therapy | What Should I Expect From Online Expat & Transition Therapy? |
| es/terapia-burnout | Qué Esperar de la Terapia\<br\>Online para Burnout | ¿Qué Esperar de la Terapia Online para Burnout? |
| es/terapia-ansiedad | (ídem patrón) | ¿Qué Esperar de la Terapia Online para Ansiedad? |
| es/terapia-depresion | (ídem) | ¿Qué Esperar de la Terapia Online para Depresión? |
| es/regulacion-emocional | (ídem) | ¿Qué Esperar de la Terapia Online de Regulación Emocional? |
| es/terapia-parejas | (ídem) | ¿Qué Esperar de la Terapia de Pareja Online? |
| es/terapia-expatriados | (ídem) | ¿Qué Esperar de la Terapia Online para Expatriados y Transiciones? |

Los `<br>` internos se retiraron (el CSS `text-wrap:balance` mantiene el layout, precedente F2).

## Tarea 2 · Condiciones relacionadas (12/12)

H2 nuevos: Conditions Related to Burnout / Anxiety / Depression / Emotional Dysregulation / Relationship Distress / Expat Transitions y Condiciones Relacionadas con el Burnout / la Ansiedad / la Depresión / la Desregulación Emocional / el Malestar Relacional / las Transiciones de Expatriado. Los 12 párrafos introductorios exactos del comando insertados entre el H2 y la `related-grid`, con el estilo de párrafo centrado del patrón del sitio; tarjetas intactas. Guardia anti-FAQ: sin coincidencias. Anti-clonación: 0 frases >12 palabras compartidas entre los 12 hermanos ni con FAQs/hub/author box.

## Tarea 3 · Quirúrgicos

1. **DSM-5 (es/terapia-depresion)**: la oración de 62 palabras partida en tres (27-22-19), todos los hechos conservados, aplicado en visible + schema (2x por sustitución de texto plano; JSON válido).
2. **arousal (es/regulacion-emocional)**: los 2 usos convivían con "activación" en la misma frase (calco redundante también presente en el EN de origen: "activation, arousal"); la sustitución literal habría duplicado el término. Ejecución fiel a la intención: eliminado el término redundante → "(activación, valencia)" y "la activación emocional y la recuperación". arousal = 0 en la página. No vivían en respuestas FAQ (conteos 1x).
3. **label/H2 (formacion ES + gemelo EN, mismo defecto)**: label "Qué Cubre la Formación" → "Contenido del Programa"; label EN "What the Training Covers" → "Program Content" (los H2 pregunta se quedan).

## Correcciones inequívocas del examen de página completa (aplicadas)

1. **3 mailtos ES** con tilde sin percent-encode mezclada con `%20` (depresión, regulación, formación) → `%C3%B3n`; presencia y destino intactos (doctrina B4/F3-A: la regla de CTAs protege presencia y destino, no bugs de parámetros; Tarea 4 los autoriza explícitamente).
2. **couples EN**: "organise" → "organize", "marriage counselling" → "marriage counseling" (convención AmE del sitio; el "Counselling" del `<title>` de expat-therapy queda fuera de alcance, ya reportado en B).
3. **Horas del taller EN**: tarjetas Format & Delivery decían "2 to 4 / 4 to 6 hours" contradiciendo al FAQ de su misma página ("3 to 4 / 6 to 7", visible + schema) y a TODA la página ES ("3 a 4 / 6 a 7" consistente). Resuelto por mayoría del contenido existente (3 de 4 superficies): tarjetas EN → "3 to 4 / 6 to 7". **REVERSIBLE: si las duraciones reales son las de las tarjetas viejas, se invierte en las 4 superficies.**

## BLOQUEANTES editoriales (esperan decisión del estratega)

1. **burnout EN**: definición OMS/CIE-11 casi verbatim ×4 (hero, "Work Stress, Burnout or Occupational Exhaustion?", "Why Does Burnout Not Go Away on Its Own?", FAQ 1). Propuesta: completa en diferenciación + FAQ; hero y mecanismo a referencia breve.
2. **burnout ES**: mecanismo eje HPA + corteza prefrontal explicado completo ×2 (tarjetas de síntomas ~406-410 y sección de mecanismo ~455). Propuesta: segunda mención a referencia.
3. **anxiety EN + depression EN**: criterios DSM-5 casi idénticos en intro de síntomas y FAQ 1 de cada página (editar el FAQ implica resync de schema).
4. **Claims de superioridad** (tono de marca, 4 páginas EN): "A generalist may address surface symptoms..." (burnout); "A couples therapist who only works with the interaction pattern... treats the surface while the engine of the conflict remains running underneath." (couples); "Regular therapy may not account for these factors because the therapist has no framework..." (expat, FAQ + schema); "This training is not delivered by a corporate wellness facilitator" + "Most corporate wellness workshops deliver surface-level content..." (workplace, el más directo).
5. **parejas ES**: label "Crisis, Patrón o Ruptura de Confianza" (3 categorías) vs H2 binario "¿Es una Crisis de Pareja Normal o un Patrón Instalado?"; el cuerpo desarrolla las tres. Opciones: ampliar H2 o recortar label (verificar gemelo EN al aplicar: mismo patrón binario en su H2).
6. **formacion ES**: "Cómo el estrés laboral crónico se convierte en burnout a nivel biológico" idéntica ×2 (bullet "Neurofisiología, no lugares comunes" y Módulo 1); claim de cumplimiento ISO 45003/OMS casi verbatim ×3 (tarjeta de riesgo psicosocial, bullet de estándares, FAQ).
7. **Línea de credencial de plantilla** "Psychotherapist & Burnout Specialist" / "Psicoterapeuta y Especialista en Burnout" (×12 uniforme) bajo H2s que prometen "Anxiety/Depression/Emotional Intelligence Specialist". Opciones: (a) mantener (identidad primaria, la sección la respalda con la especialización APA); (b) cambiar las 12 al cargo canónico del Comando B ("Psychotherapist · Burnout and Mood Disorders Specialist" / "Psicoterapeuta · Especialista en Burnout y Trastornos del Estado de Ánimo").
8. **depression EN, intro de Tarea 2 (texto exacto del comando)**: "It also coexists often with anxiety and emotional numbness." Flagged por orden de palabras; propuesta mínima: "It also often coexists with...".

## Menores (solo reporte)

Anglicismo "feedback" (formacion ES, línea ~163); CSS muerto `.price-card.featured::before` (burnout EN, línea ~141); bloque de reseñas de psicoterapia individual sin transición ante el FAQ corporativo del taller (registro B2B); línea de credencial genérica también en expat/couples (variante del bloqueante 7); comparación leve con "cursos de gestión emocional" (emotional-regulation EN); "comunicarse con precisión total" (parejas ES, descripción de capacidad, no claim clínico).

## Veredicto de flujo por página (examen de las 14)

| Página | Veredicto |
|---|---|
| burnout-therapy | Coherente; lastre: repetición OMS ×4 (bloqueante 1) |
| anxiety-therapy-online | Coherente; DSM-5 ×2 (bloqueante 3) |
| depression-therapy-online | Coherente; DSM-5 ×2 + intro de comando (bloqueantes 3 y 8) |
| emotional-regulation-therapy | Coherente; la de mayor valor único (bloque gestión vs regulación) |
| couples-therapy-online | Coherente; ortografía BrE corregida; claim (bloqueante 4) |
| expat-therapy | Coherente y bien diferenciado; claim en FAQ (bloqueante 4) |
| workplace-mental-health-training | Coherente; horas corregidas; claims (bloqueante 4); registro de reseñas (menor) |
| es/terapia-burnout | Coherente; repetición HPA ×2 (bloqueante 2) |
| es/terapia-ansiedad | **Limpia en los 5 puntos** |
| es/terapia-depresion | Limpia tras quirúrgicos + mailto |
| es/regulacion-emocional | Limpia tras quirúrgicos + mailto |
| es/terapia-parejas | Coherente; label/H2 (bloqueante 5) |
| es/terapia-expatriados | **Limpia en los 5 puntos** |
| es/formacion-salud-mental-laboral | Coherente; repeticiones ×2 y ×3 (bloqueante 6) + mailto corregido |

## Verificaciones (salida literal resumida)

```
1) viejos anclados: 0 de los 14 patrones · nuevos: los 24 presentes · guardia FAQ: sin coincidencias
2) 12 intros en su página exacta: True · clones entre hermanos: 0 · compartidas con FAQs/hub: 0
3) DSM-5 por oración: [27, 22, 19] todas <=45 · arousal: 0 · labels: Contenido del Programa / Program Content
4) 126 JSON-LD 0 errores · schema=visible 0 desync · FAQ dup 0 · H1 intactos 14/14 ·
   lastmod 2026-08-11 en las 14 · em dashes 0 · wa.me 387 · blockquotes 146 · price 2/2
5) Doble auditoría independiente (5.5): PENDIENTE, se ejecuta tras las decisiones de bloqueantes
   sobre el estado final, antes del merge a main
```

## Verificación en vivo prevista (tras merge a main)

1. `curl .../burnout-therapy/ | grep -c "Conditions Related to Burnout"` → ≥ 1
2. `curl .../burnout-therapy/ | grep -c "What Should I Expect From"` → ≥ 1
3. `curl .../es/terapia-parejas/ | grep -c "Condiciones Relacionadas con"` → ≥ 1
4. `curl .../es/regulacion-emocional/ | grep -c "arousal"` → 0
5. `curl .../es/terapia-burnout/ | grep -c "El burnout rara vez viaja solo"` → ≥ 1

---

# Decisiones aplicadas + doble auditoría (2026-08-11, segunda pasada)

## Decisiones del estratega aplicadas (B1-B8 + menor)

- **B1 (burnout EN, doctrina cápsula)**: tratamiento completo OMS/CIE-11 en la sección de diferenciación **con el enlace S3 reubicado ahí desde el hero**; hero y mecanismo a referencia breve ("When the three WHO-defined dimensions of burnout converge and persist..."); FAQ reformulada como cápsula con otras palabras ("In the WHO's ICD-11 classification... three markers: energy that stays drained, growing mental distance from the job, and a felt drop in professional efficacy"), resync incluido.
- **B2 (burnout ES)**: glosas repetidas del eje HPA y la corteza prefrontal retiradas de la segunda mención (los datos nuevos de esa sección se conservan).
- **B3 (anxiety/depression EN)**: criterios completos del DSM-5 en la intro de síntomas (depression ganó la lista parentética); FAQs reformuladas como cápsulas ("worry becomes hard to switch off and shows up in the body..." / "low mood or a marked loss of interest has settled in alongside at least four other changes..."), resync incluido.
- **B4 (diferenciación positiva)**: couples y workshop con los textos fijados por el estratega. Redacciones propias bajo el principio, para lectura en el diff: **burnout EN** "Specialist training means the intervention starts from the specific mechanism driving the exhaustion, not from the surface symptoms alone." · **expat EN (FAQ+schema)** "Expat therapy works from a dedicated framework for how relocation destabilizes the internal model the mind relies on to predict and navigate daily life."
- **B5**: H2 de parejas ampliado en ambos idiomas ("¿Crisis Pasajera, Patrón Instalado o Ruptura de Confianza?" / "A Passing Crisis, an Established Pattern, or Broken Trust?").
- **B6 (formacion ES)**: Módulo 1 conserva su frase; bullet de neurofisiología con teaser distinto; ISO 45003 completa solo en la tarjeta de riesgo, referencia en el bullet ("es la pieza documentada de esa inversión"), cápsula reformulada en la FAQ ("deja constancia formal, con base en evidencia..."), resync incluido.
- **B7**: cargo canónico en las **14** páginas (las 12 de servicio + los 2 talleres, que comparten la plantilla "Your Trainer"): "Psychotherapist · Burnout and Mood Disorders Specialist" / "Psicoterapeuta · Especialista en Burnout y Trastornos del Estado de Ánimo".
- **B8**: "It also often coexists with anxiety and emotional numbness."
- **Menor autorizado**: "El feedback" → "La retroalimentación" (formacion ES).
- **Espejo ES de B4 descubierto al aplicar**: formacion ES tenía la frase "La mayoría de los talleres corporativos de bienestar ofrecen contenido superficial..." (FAQ+schema) → sustituida por el espejo del texto fijado: "Esta formación es contenido clínico adaptado a entornos organizacionales, no programación genérica de bienestar."
- **Doctrina intra-página, hallazgo mecánico nuevo**: es/terapia-expatriados duplicaba verbatim "El procesamiento emocional es más profundo en el idioma con el que creciste" entre cuerpo y FAQ → cápsula FAQ reformulada: "Las emociones se procesan con más profundidad en la lengua materna."

## Doble auditoría (5.5) y correcciones derivadas

La auditoría independiente detectó ejecución desigual de las doctrinas entre pares EN/ES (los espejos ES de los claims B4 y varias duplicaciones cápsula-sección seguían vivos). Al ser las mismas clases ya decididas, se aplicaron y quedan aquí para lectura en el diff:

- **es/terapia-burnout**: espejo completo de B1 (hero a referencia sin enlace; enlace S3 a la sección de diferenciación con CIE-11; mecanismo a referencia; FAQ cápsula "En la clasificación CIE-11 de la OMS... energía que no se recupera, creciente distancia mental... caída percibida del rendimiento profesional") + espejo de B4: "La formación especializada hace que la intervención parta del mecanismo específico que mantiene el agotamiento, no solo de los síntomas superficiales."
- **es/terapia-ansiedad**: cápsula DSM-5 reformulada ("Según el DSM-5, la ansiedad generalizada se diagnostica cuando la preocupación se vuelve difícil de apagar y se expresa en el cuerpo...").
- **couples EN + es/terapia-parejas**: la frase bilingüe duplicada bio↔FAQ reformulada en la FAQ de ambos idiomas ("In session, the language can shift from one exchange to the next..." / "En sesión, el idioma puede cambiar de un intercambio al siguiente..."); es/terapia-parejas además tenía el ataque a terceros que el EN ya había limpiado → espejo del texto fijado: "Este trabajo apunta al motor del conflicto, no solo al patrón de interacción visible en la superficie."
- **es/terapia-expatriados (el más grave de la auditoría)**: "La terapia regular puede no considerar estos factores porque el terapeuta no tiene un marco..." (FAQ visible + schema) → espejo del fix EN: "La terapia para expatriados trabaja desde un marco propio para entender cómo la reubicación desestabiliza el modelo interno..."; la continuación legítima ("Un terapeuta con experiencia intercultural reconoce...") se conserva.
- **expat EN**: bloque bio↔FAQ casi idéntico → cápsula FAQ reformulada ("working in your first language matters clinically: emotions carry more depth in the language you grew up with").
- **workplace EN**: los dos triples (claim ISO ×3 y "becomes burnout at a biological level" ×3) resueltos con el patrón que la auditoría elogió en la página ES: completa en la tarjeta de riesgo / referencia en el bullet ("it is the documented piece of that investment") / cápsula en la FAQ ("leaves a formal, evidence-based record..."); teaser del bullet de neurofisiología sin la frase del Módulo 1.

Menores de la auditoría, solo reportados: "y ofrezca resultados reales" (es/regulacion-emocional, coletilla); "occupational phenomenon, not a psychiatric diagnosis" repetido tolerable (burnout EN); "es la pieza documentada" levemente elíptica (formacion ES); el cargo canónico no replica literalmente las etiquetas de los H2 de ansiedad/depresión/IE (el texto que sigue tiende el puente; la auditoría no lo considera bloqueante).

## Suite final (estado del commit)

126 JSON-LD 0 errores · schema=visible 0 desync · duplicación cápsula-sección >12 palabras: 0 · claims a terceros: 0 · em dashes 0 · wa.me 387 · blockquotes 146 · precios 2/2 · H1 14/14 intactos · lastmod 2026-08-11.
