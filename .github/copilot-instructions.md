# Holgado web: instrucciones para Copilot

## Contexto del proyecto
- Sitio estatico de una sola pagina para el proyecto musical Holgado.
- No hay build system ni framework; se sirve directamente `index.html`.
- El CSS y JS estan embebidos en `index.html` por simplicidad.

## Estructura de contenido
- `assets/images/`: imagenes, iconos y portadas.
- `assets/audio/`: previews de audio en `.m4a`.
- `assets/vendor/`: librerias de terceros.
- `.well-known/`: rutas requeridas por validaciones externas.

## Reglas de edicion
- Mantener la web sin dependencias nuevas innecesarias.
- Priorizar cambios pequenos y seguros para no romper rutas ni estilos.
- Si se mueven recursos, actualizar siempre rutas `src`, `url(...)` y `data-*`.
- Mantener textos en espanol.

## Accesibilidad y calidad
- Toda imagen debe tener `alt` descriptivo.
- Evitar reproducir audio o video automaticamente al cargar pagina.
- Comprobar responsive en movil y escritorio tras cambios visuales.
