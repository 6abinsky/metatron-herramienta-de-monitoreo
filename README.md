# Metatron: herramienta de monitoreo

Tablero público del monitoreo informativo de Bolivia realizado con **MET4TRON FLEX**. Presenta publicaciones, interacción, agenda temática, distribución por ciudades, personas mencionadas y señales de presión informativa sobre autoridades.

La herramienta de escritorio procesa los originales y publica exclusivamente `data/latest.json` mediante un token local de GitHub. El código Python, las claves de API, la base de datos y los archivos originales permanecen en el equipo del operador.

## Consulta

- Hoy, 7, 15, 30 días o fechas personalizadas dentro de los datos disponibles.
- Panorama general y ciudades de Bolivia.
- Categorías, publicaciones e interacción por hora o día y distribución territorial al 100% de la interacción geolocalizada.
- Indicador nacional; gobernación y alcaldía en la vista de cada ciudad.
- Personas, resumen de todas las ciudades, cinco temas principales, cuentas y palabras clave.
- Top 10 de publicaciones separado por Facebook, TikTok e Instagram.

Los indicadores son exploratorios y muestran su método y evidencia. La falta de datos no equivale a normalidad. Los casos ambiguos se revisan en la herramienta privada. Las interacciones se agrupan por fecha de publicación, no por el momento real de cada reacción.

## Actualización

La web consulta el archivo de datos cada cinco minutos. El archivo sincronizado contiene los últimos 30 días según la hora de Bolivia. El equipo del operador debe estar encendido para procesar y enviar nuevas actualizaciones; el sitio permanece disponible con la última versión recibida.

GitHub conserva las versiones anteriores en el historial de commits. La ventana de 30 días se aplica al archivo actual, no constituye borrado de datos previamente publicados en el historial.

No subas a este repositorio el archivo Python privado ni su carpeta de datos. La interfaz se construye con HTML, CSS, JavaScript y SVG; no requiere un servidor Python público.
