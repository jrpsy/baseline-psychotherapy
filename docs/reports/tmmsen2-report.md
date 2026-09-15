# Reporte TMMSEN-2 · Test de inteligencia emocional EN (TMMS-30 original) + barrido de CTAs en instrumentos

Fecha: 2026-09-15 · Base: `1c407e2` (main) · Rama: `tmmsen2-review` · Estado: vista previa, SIN merge.

## T0 · Ítems verbatim y clave de inversión

**Fuente S1 (re-fetch 2026-09-15, 205 397 bytes)**: Ayele, F. A., Bjelica, F., Qian, J., Cadenas-Santos, J. A., & Barchard, K. A. (2021, June 14-15). *The dimensions of meta-mood experience* [Poster]. AABSS Annual Conference, Las Vegas. Barchard Lab, University of Nevada, Las Vegas. https://img.faculty.unlv.edu/lab/wp-content/uploads/2021/06/Dimensions-of-Meta-Mood-Fitsum-Filip-Jin-handout-9-Kim-DONE-1.pdf. Tabla 1: los 30 ítems del TMMS-30 con su texto literal; cuerpo del póster: número de ítem y factor "originally designed to measure" (Salovey et al., 1995) para 25 ítems.

**Fuente S5**: Fitness, J., & Curtis, M. (2005). Emotional intelligence and the Trait Meta-Mood Scale. *E-Journal of Applied Psychology: Social section, 1*(1), 50-62 (PDF abierto, Macquarie University). Cita literal: "Attention - 13 items (8 reverse scored)… Clarity - 11 items (5 reverse scored)… Repair - 6 items (2 reverse scored)".

**Pedigrí (Crossref)**: Salovey, P., & Mayer, J. D. (1990). Emotional intelligence. *Imagination, Cognition and Personality, 9*(3), 185-211. https://doi.org/10.2190/DUGG-P24E-52WK-6CDG (título, revista, volumen, número y páginas confirmados por la API de Crossref).

Texto usado: la Tabla 1 de S1 (columna de ítems). Numeración: la del cuerpo del póster, que corrige tres erratas de la tabla (el ítem "I almost always know exactly how I am feeling." es el 30, no "3."; "I feel at ease about my emotions." es el 20, no "2."; "I believe in acting from the heart." es el 10, no "1."). Variantes menores entre tabla y cuerpo, resueltas a favor de la tabla: ítem 4 ("I don't usually care much about what I'm feeling." frente a "I usually don't care much about what I feel"), ítem 26 ("think about pleasant things" frente a "think of"), ítem 30 ("how I am feeling" frente a "how I'm feeling").

| # | Ítem (verbatim, Tabla 1) | Subescala | Inverso | Base |
|---|---|---|---|---|
| 1 | I try to think good thoughts no matter how badly I feel. | Repair | no | S1 cuerpo (Repair) |
| 2 | People would be better off if they felt less and thought more. | Attention | sí | S1 cuerpo; "felt less" |
| 3 | I don't think it's worth paying attention to your emotions or moods. | Attention | sí | S1 cuerpo; "don't" |
| 4 | I don't usually care much about what I'm feeling. | Attention | sí | S1 cuerpo; "don't" |
| 5 | Sometimes I can't tell what my feelings are. | Clarity | sí | S1 cuerpo; "can't" |
| 6 | I am rarely confused about how I feel. | Clarity | no | S1 cuerpo |
| 7 | Feelings give direction to life. | Attention | no | recuento S5 (13 - 10 = 3 ítems de Attention entre los cinco no clasificados en S1) |
| 8 | Although I am sometimes sad, I have a mostly optimistic outlook. | Repair | no | S1 cuerpo |
| 9 | When I am upset I realize that the "good things in life" are illusions. | Repair | sí | recuento S5 (6 - 5 = 1); "illusions" |
| 10 | I believe in acting from the heart. | Attention | no | recuento S5 |
| 11 | I can never tell how I feel. | Clarity | sí | S1 cuerpo; "never" |
| 12 | The best way for me to handle my feelings is to experience them to the fullest. | Attention | no | recuento S5 |
| 13 | When I become upset I remind myself of all the pleasures in life. | Repair | no | S1 cuerpo |
| 14 | My beliefs and opinions always seem to change depending on how I feel. | Clarity | sí | recuento S5 (11 - 10 = 1 ítem; 5 - 4 = 1 inverso): único candidato restante; redacción de inestabilidad |
| 15 | I am often aware of my feelings on a matter. | Clarity | no | S1 cuerpo |
| 16 | I am usually confused about how I feel. | Clarity | sí | S1 cuerpo; "confused" |
| 17 | One should never be guided by emotions. | Attention | sí | S1 cuerpo; "never" |
| 18 | I never give in to my emotions. | Attention | sí | S1 cuerpo; "never" |
| 19 | Although I am sometimes happy, I have a mostly pessimistic outlook. | Repair | sí | S1 cuerpo; "pessimistic" |
| 20 | I feel at ease about my emotions. | Clarity | no | S1 cuerpo |
| 21 | I pay a lot of attention to how I feel. | Attention | no | S1 cuerpo |
| 22 | I can't make sense out of my feelings. | Clarity | sí | S1 cuerpo; "can't" |
| 23 | I don't pay much attention to my feelings. | Attention | sí | S1 cuerpo; "don't" |
| 24 | I often think about my feelings. | Attention | no | S1 cuerpo |
| 25 | I am usually very clear about my feelings. | Clarity | no | S1 cuerpo |
| 26 | No matter how badly I feel, I try to think about pleasant things. | Repair | no | S1 cuerpo |
| 27 | Feelings are a weakness humans have. | Attention | sí | S1 cuerpo; "weakness" |
| 28 | I usually know my feelings about a matter. | Clarity | no | S1 cuerpo |
| 29 | It is usually a waste of time to think about your emotions. | Attention | sí | S1 cuerpo; "waste of time" |
| 30 | I almost always know exactly how I am feeling. | Clarity | no | S1 cuerpo |

Totales: Attention 13 (8 inversos: 2, 3, 4, 17, 18, 23, 27, 29) · Clarity 11 (5 inversos: 5, 11, 14, 16, 22) · Repair 6 (2 inversos: 9, 19). Coinciden exactamente con S5. Los cinco ítems que S1 no asigna a factor original (7, 9, 10, 12, 14) quedan determinados por los recuentos de S5 (Attention necesita 3 más, Clarity 1, Repair 1) y por la valencia de su redacción; el ítem 14, que no lleva negador explícito, es el único candidato posible al quinto inverso de Clarity, con lo que la ambigüedad se resuelve objetivamente y no hubo que detener la construcción. La combinación de 30 ítems en inglés es la escala original tal como la publican Salovey et al. (1995) según S1 y S5.

## T1 · Página `/tests/emotional-intelligence/`

Plantilla de herramienta EN (emotional-meter) con el CSS de screener de la casa (el del TMMS-24 ES). Title "Emotional Intelligence Test (Original TMMS) | Free & Private" (60). H1 "The Trait Meta-Mood Scale: measure your emotional intelligence". Intro con el pedigrí verificado (Salovey & Mayer, 1990, enlazado al DOI; escala de Salovey, Mayer, Goldman, Turvey y Palfai, 1995). 30 ítems verbatim en orden original, escala de 5 puntos del original (Strongly disagree · Disagree · Neutral · Agree · Strongly agree). Puntuación en el navegador: inversos como 6 − v, media por subescala en 1-5 con un decimal.

Bandas interpretativas, transparentes y ancladas a la escala: media por debajo de 2,5 · entre 2,5 y 3,5 · por encima de 3,5, con etiquetas y textos por dimensión; en Attention la banda alta incluye el matiz establecido (puntuar muy alto puede reflejar atención excesiva o rumiación, no siempre fortaleza), repetido en la FAQ de interpretación. La NOTA DE HONESTIDAD literal aparece antes del formulario y dentro de la tarjeta de resultados. Bloque puente del T2 dentro de los resultados. Tabla de bandas, descargo (autoinforme; 13/8, 11/5, 6/2; enlace al TMMS-24 ES), referencias APA visibles (las tres), FAQs (4) con schema. Schema: MedicalWebPage (lastReviewed 2026-09-15) · BreadcrumbList · MedicalBusiness · FAQPage. Sin Quiz.

Decisión hreflang: sin par con /es/tests/tmms-24/ (instrumentos distintos: 30 ítems originales frente a 24 adaptados con cortes por sexo); cada página es standalone. El conmutador de idioma del nav en la nueva página apunta al hub ES de tests.

## T2 · Barrido de CTAs en instrumentos

Inventario real: 20 páginas interactivas tras esta ronda (10 EN + 10 ES, hubs excluidos). Ninguna de las 19 preexistentes mostraba un bloque de puente a consulta junto a los resultados (los enlaces a wa.me estaban solo en el CTA final de página o en el chrome). Bloque estandarizado (`.bridge-cta`, discreto, borde superior fino, botón outline): EN "Your result is a starting point, not a verdict. If you want to make sense of it with a professional, the first conversation is free: 15 minutes, honest, no commitment." + wa.me estándar · ES "Tu resultado es un punto de partida, no un veredicto. Si quieres darle sentido con un profesional, la primera conversación es gratuita: 15 minutos, honesta, sin compromiso." + wa.me estándar ES.

| Página | Antes | Después · posición |
|---|---|---|
| tests/phq-9 · es/tests/phq-9 | no | dentro de la tarjeta de resultados, tras la nota de crisis y los textos de banda, antes de "Start over" |
| tests/gad-7 · es/tests/gad-7 | no | idem (los textos de banda remiten a los recursos de crisis; el puente va después) |
| tests/who-5 · es/tests/who-5 | no | idem |
| tests/dass-21 · es/tests/dass-21 | no | idem |
| tests/cbi · es/tests/cbi | no | idem |
| es/tests/tmms-24 | no | idem |
| tests/emotional-intelligence (nueva) | n/a | incorporado: tras la nota de honestidad y los textos de banda |
| tests/recovery-half-life · es/tests/vida-media-recuperacion | no | dentro de la tarjeta de lectura, tras el texto de banda |
| tests/thought-record · es/tests/registro-pensamientos | no | dentro del panel resumen del registro |
| tests/emotional-meter · es/tests/medidor-emocional | no | tarjeta bajo el resultado del medidor, visible solo con el resultado y oculta al reiniciar |
| tests/breathing · es/tests/respiracion | n/a | sin resultados (ejercicio guiado): sin bloque |

Regla de orden cumplida: en PHQ-9 y GAD-7 el puente está después de la nota de crisis (verificado por posición en el DOM con la nota visible).

## T3 · Integración

Hub /tests/: la card del TMMS pasa a "Emotional Intelligence Test · The original emotional intelligence scale (TMMS) · 30 questions · ~5 minutes" y enlaza a /tests/emotional-intelligence/ (desaparece "in Spanish"). Hub ES sin cambios. Sitemap 81 → **82** (URL nueva sin alternates, lastmod 2026-09-15; lastmod del hub EN). llms.txt: línea nueva del instrumento EN; menciones del TMMS-24 intactas en ambas secciones. Interactivas sin Clarity/Metrika: **20** (el comando esperaba 21 partiendo de 20 previas; las previas eran 19 porque el TMMS-24 solo existía en ES).

## T4 · Verificación

| Control | Resultado |
|---|---|
| Ítems en la página | 30, verbatim Tabla 1 |
| Perfiles sintéticos (EN, 1280 y 375) | positivos=1/inversos=5 → medias 1,0 en las tres (banda baja) · todo 3 → 3,0 (media) · positivos=5/inversos=1 → 5,0 (alta) · control de inversión positivos=5/inversos=5 → Attention 2,5 · Clarity 3,2 · Repair 3,7 (la inversión actúa) |
| Nota de honestidad | 2 apariciones: antes del test y en resultados |
| Puente en resultados | presente en la nueva página y en las 17 páginas con resultado; PHQ-9 tras nota de crisis; medidor oculto hasta resultado y oculto al reiniciar |
| FAQ globales | **258** (254 + 4), 0 duplicadas; similitud máxima 0,73 con una FAQ de privacidad de otra herramienta (pregunta distinta) |
| Schema = visible | 8/8 Q/A |
| Privacidad del script | localStorage 0, sessionStorage 0, fetch 0, XHR 0, beacon 0, URLs 0; Clarity 0, Metrika 0 |
| Suite global (85 HTML) | JSON-LD 0 errores · em dashes 0 · `<em>` 0 (títulos de revista en cursiva vía span) · hrefs 0 rotos |
| Render | 1280 y 375 sin overflow; capturas de página, resultados, PHQ-9 y TMMS-24 ES con puente, ítems móviles, hub |

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 11/11** (ítems verbatim frente a la Tabla 1 del PDF · subescalas 13/11/6 e inversos 8/5/2 con redacción negativa verificada ítem a ítem y los 25 factores de S1 coincidentes · scoring ejecutado en Node (umbrales 2,5 y 3,5, inversión 6 − v, reset) · nota de honestidad antes del formulario y en resultados, matiz de Attention en banda y FAQ · head, 4 JSON-LD, schema=visible, sin hreflang ni Quiz · referencias APA, 0 `<em>`, 0 em dashes · reglas de interactivas · barrido: 18 páginas con un único puente, 0 en respiración; PHQ-9 tras la nota de crisis; medidor oculto hasta resultado · integraciones acotadas a los 20 archivos esperados · 20 interactivas sin Clarity/Metrika · 258 FAQ sin duplicados).

Residuos señalados y decisión:
- Siete ítems usaban apóstrofos y comillas ASCII donde el PDF lleva glifos tipográficos (’ “ ”): sustituidos por los glifos del PDF; tras la reconstrucción, 30/30 legends son byte-idénticos a la Tabla 1.
- `sessionStorage` aparece solo en el snippet compartido del banner de anuncio, como en todas las páginas del sitio; el script de la herramienta no lo usa.
- Este informe forma parte del commit de la rama.
- El auditor hizo por error un `git stash`/`git stash pop` durante la lectura; verificado que el árbol quedó idéntico (mismo `diff --stat`, stash vacío) antes de reconstruir desde main.

## Referencias (APA)

- Salovey, P., & Mayer, J. D. (1990). Emotional intelligence. *Imagination, Cognition and Personality, 9*(3), 185-211. https://doi.org/10.2190/DUGG-P24E-52WK-6CDG
- Salovey, P., Mayer, J. D., Goldman, S. L., Turvey, C., & Palfai, T. P. (1995). Emotional attention, clarity, and repair: Exploring emotional intelligence using the Trait Meta-Mood Scale. In J. W. Pennebaker (Ed.), *Emotion, disclosure, and health* (pp. 125-154). American Psychological Association. https://doi.org/10.1037/10182-006
- Fernández-Berrocal, P., Extremera, N., & Ramos, N. (2004). Validity and reliability of the Spanish modified version of the Trait Meta-Mood Scale. *Psychological Reports, 94*(3), 751-755. https://doi.org/10.2466/pr0.94.3.751-755
