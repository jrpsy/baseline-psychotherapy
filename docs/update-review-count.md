# Micro-comando: actualizar el conteo de reseñas

Uso: con cada reseña nueva de Google, pega este comando en Claude Code sustituyendo `VIEJO` y `NUEVO` por los números reales (p. ej. 22 → 23). El texto de las reseñas individuales NO se toca; solo cambia el conteo.

---

Eres el ejecutor técnico de baselinepsychotherapy.com. Actualiza el conteo de reseñas de Google de VIEJO a NUEVO en sus 17 superficies inventariadas (Comando G, 2026-08-18). Árbol limpio sobre main.

1. Reemplaza exactamente estas tres cadenas en todo el repo:
   - `VIEJO Google Reviews` → `NUEVO Google Reviews` (8 páginas EN: index, anxiety-therapy-online, burnout-therapy, couples-therapy-online, depression-therapy-online, emotional-regulation-therapy, expat-therapy, workplace-mental-health-training)
   - `VIEJO Reseñas en Google` → `NUEVO Reseñas en Google` (8 páginas ES: es/index, es/terapia-ansiedad, es/terapia-burnout, es/terapia-parejas, es/terapia-depresion, es/regulacion-emocional, es/terapia-expatriados, es/formacion-salud-mental-laboral)
   - `(VIEJO reviews)` → `(NUEVO reviews)` (llms.txt, línea "Rated 5.0 on Google Reviews")
2. Verifica (salida literal, todo debe cumplirse antes del commit):
   - `grep -rc "VIEJO Google Reviews\|VIEJO Reseñas en Google" --include="*.html" . | grep -v ":0$"` → vacío
   - `grep -c "(VIEJO reviews)" llms.txt` → 0 (el `--include` de la línea anterior excluye llms.txt; esta línea lo cubre)
   - `grep -rl "NUEVO Google Reviews" --include="*.html" . | wc -l` → 8
   - `grep -rl "NUEVO Reseñas en Google" --include="*.html" . | wc -l` → 8
   - `grep -c "(NUEVO reviews)" llms.txt` → 1
   - `grep -rn "aggregateRating" --include="*.html" . | wc -l` → 0 (el schema nunca lleva rating; regla del Comando A)
   - em dashes en el repo → 0
3. Actualiza `<lastmod>` en sitemap.xml a la fecha de hoy para las 16 páginas HTML tocadas.
4. Commit directo a main: `Review count update: VIEJO -> NUEVO across 17 surfaces` y push.
5. Tras el despliegue (sondeo ≤5 min), verifica en vivo: `curl -s https://baselinepsychotherapy.com/ | grep -c "NUEVO Google Reviews"` → 1 y el espejo ES en /es/.

Si cualquier verificación falla, NO hagas commit: reporta la salida literal y espera.

Nota de mantenimiento: si una futura ronda añade o quita superficies con el conteo (p. ej. una página nueva con bloque agregado), actualiza el inventario de este archivo en el mismo commit.

- NUEVAS SUPERFICIES (YER-1, 2026-09-01): yerevan/index.html contiene "22 Google reviews" (prosa, minúscula) y es/yerevan/index.html contiene "22 reseñas de Google" (prosa). Actualizar junto con las 17 superficies canónicas al cambiar el conteo.
