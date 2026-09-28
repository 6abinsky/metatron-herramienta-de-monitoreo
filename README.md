# Metatron: herramienta de monitoreo

Tablero público de monitoreo de publicaciones en Bolivia. HTML, CSS y JavaScript sin compilación; gráficas SVG interactivas y animadas, adaptables a teléfonos y con reducción de movimiento.

## Qué muestra

- Categorías por interacción: Política, Sociedad, Deporte, Espectáculo y Noticias internacionales; pendientes conservados como Sin clasificar.
- Publicaciones en barras e interacciones en línea, con ejes independientes.
- Ciudades con porcentajes que suman 100% de la interacción geolocalizada. Otros se excluye y su volumen se informa.
- Índice exploratorio de presión informativa del gobierno nacional; gobernación y alcaldía al seleccionar ciudad.
- Personas resueltas, resumen extractivo y Top 10 por Facebook, TikTok e Instagram.
- Hoy, 7, 15 y 30 días y fechas personalizadas. Hora de Bolivia.

## Datos y actualización

`data/latest.json` es el único archivo que actualiza rutinariamente la herramienta de escritorio. Contiene una ventana móvil de 30 días inclusivos hasta la fecha local de sincronización. La web consulta la última versión cada cinco minutos y permite actualizar manualmente. No se incluye una base de datos privada, claves, tokens ni código Python.

Al abrir por primera vez se muestra un estado vacío; no se inventan métricas. La herramienta personal configura usuario y token GitHub y ejecuta Sincronizar. La consulta temporal se recalcula en el navegador.

**Alcance de retención:** el JSON actual tiene 30 días; los commits anteriores de un repositorio público pueden conservar versiones antiguas. Esta arquitectura no promete borrado histórico de datos ya publicados.

## Publicación

GitHub → Settings → Pages → Deploy from a branch → main → /(root) → Save.

Para una prueba local: `python -m http.server 8080` en esta carpeta; abrir http://localhost:8080. Usar un servidor HTTP, no abrir index.html como file://.

## Metodología

Las interacciones son acumuladas por publicación y se agrupan por la fecha de publicación; no se dispone de timestamps de cada reacción. El medidor no es una encuesta ni un diagnóstico validado: combina en partes iguales gravedad media y gravedad ponderada por interacciones, escala 0–3 convertida a 0–100, mínimo cinco publicaciones institucionales. Normal <35; alerta 35–<65; crisis ≥65. El nivel departamental usa todas las publicaciones identificadas del departamento.

Las personas cuentan una vez por publicación; se ordenan por publicaciones con mención y se desempata por interacción. Los alias no unívocos quedan pendientes en la herramienta de escritorio. Los resúmenes citan titulares originales y cifras calculadas, no generan hechos nuevos.

## Contrato JSON

Schema 1; campos `generated`, `start`, `end`, `timezone`, `methodology`, `categories`, `cities`, `records`. Cada registro: `id`, `fecha` ISO con offset -04:00, `titulo`, `perfil`, `red`, `link`, `interaccion_total`, `category`, `city`, `department`, `risk`, `people`. Los campos de texto se insertan usando `textContent`, y los enlaces admiten solo HTTP/HTTPS.

La primera sincronización y todas las posteriores se realizan desde el equipo personal. La web sigue disponible con el último corte cuando el equipo está apagado; no obtiene datos nuevos por sí sola.
