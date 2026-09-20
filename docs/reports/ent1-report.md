# Reporte ENT-1 · Costura de entidad de J.R. Hernandez

Fecha: 2026-09-20 · Base: `38d2371` (main) · Rama: `ent1-review` · Estado: vista previa, SIN merge (ronda visual del dueño + revisión de repo del estratega).

Dato del dueño: LinkedIn confirmado, `https://www.linkedin.com/in/baselinepsychotherapy/` (ya presente en el repo; se mantiene y se unifica).

## T1 · Entidad Person `#jr`

Inventario previo: 4 declaraciones completas (about, es/sobre-mi, index, es/index) con una lista `sameAs` idéntica de 10 URLs; 74 usos por referencia en 68 archivos (solo `@id`, name, jobTitle, url; seis con `alternateName`), que no se tocan.

Cambios en las 4 declaraciones completas:
- `sameAs` unificado a **14 URLs**, mismo orden en las cuatro: las 10 previas (Psychology Today, TherapyRoute, LinkedIn, Google share, Yandex, Expat.com, Mentalzon, Amazon canónico, Heallist, International Therapist Directory) + Instagram, Threads y las dos ediciones de Google Play (EN Eb0KEgAAQBAJ, ES uL8KEgAAQBAJ). Verificación cruzada: 1 sola lista distinta en todo el sitio.
- `description`: frase canónica EN en `about/`, ES en `es/sobre-mi/`. En las declaraciones de las home NO se añade description: la ley schema=visible exige que la frase esté visible donde se declara, y en la home no lo está (decisión documentada; las home conservan sameAs unificado y jobTitle).
- `jobTitle`: "Psychotherapist" en EN; en las páginas ES se mantiene "Psicoterapeuta" para no romper schema=visible con el texto visible en español (el comando pide "Psychotherapist" sin distinguir idioma; queda a decisión del estratega si prefiere el término EN también en ES).

## T2 · Ley schema=visible

Primera línea de la bio del par About = frase canónica del idioma, integrada con el texto existente sin duplicar información:
- EN: "J.R. Hernandez is a psychotherapist, founder of Baseline Psychotherapy, and creator of the Baseline Psychotherapy Protocol, a process-based method for working with emotional reactions. I specialize in burnout and mood disorders, and run an online private practice serving professionals, expats, and high performers worldwide, in both English and Spanish. I founded it in New York in 2019, and today it is based in Singapore. Since then, I have worked with clients from more than 21 countries."
- ES espejo. Las menciones de los tres libros y el enlace al método se conservan.
- lastReviewed: el par About no lleva MedicalWebPage ni dateModified (solo BreadcrumbList + Person), así que no hay clave que refrescar; se actualiza el lastmod del sitemap.

## T3 · Capa invisible

- llms.txt: la línea de identidad EN (blockquote de cabecera) pasa a la frase canónica EN (sustituye "Founder: J.R. Hernandez, psychotherapist, burnout and mood disorders specialist."); la sección "Servicios (Español)" gana un blockquote con la frase canónica ES (no existía línea de identidad ES).
- sitemap.xml: lastmod 2026-09-20 en `/`, `/es/`, `/about/`, `/es/sobre-mi/`.

## T4 · Verificación

| Control | Resultado |
|---|---|
| JSON-LD | 0 errores en 85 HTML |
| Em dashes / hrefs | 0 / 0 rotos |
| sameAs | 1 lista distinta en todo el sitio, 14 URLs, LinkedIn una vez por página |
| description visible | about y es/sobre-mi: frase canónica presente verbatim en el cuerpo |
| Render About par | 1280 y 375, sin overflow, párrafo de bio con la frase canónica en primera posición |

## Segunda auditoría (agente independiente, solo lectura)

Veredicto: **CONFORME 9/9** (4 declaraciones completas con sameAs idéntico de 14 URLs y 0 listas divergentes · description y jobTitle según lo especificado, home sin description por schema=visible · frase canónica visible como primera frase de la bio sin duplicar información, libros y enlace al método intactos · 78 usos por referencia intactos · JSON-LD válido sin claves duplicadas · em dashes 0, hrefs 0 rotos, LinkedIn una vez por página · llms.txt EN y ES · sitemap 4 lastmod · diff acotado a los 6 archivos).

Residuos señalados y decisión:
- Prosa de la segunda frase de la bio ("the practice is an online private practice" / "la práctica es una consulta privada online"): reescrita como "and run an online private practice…" / "y dirijo una consulta privada online…". Re-verificado: JSON válido, frase canónica visible, em dashes 0.
- El cambio de tercera persona (frase canónica) a primera persona en el resto de la bio es inherente a la frase mandada; queda a decisión del dueño en su ronda visual.
- jobTitle ES "Psicoterapeuta": permitido por el comando, mantenido por schema=visible.

## Vista previa

- http://localhost:8000/about/
- http://localhost:8000/es/sobre-mi/
