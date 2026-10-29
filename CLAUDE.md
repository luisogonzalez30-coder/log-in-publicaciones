# Publicador de LOG-In (Instagram, y Facebook por copia automática)

Repositorio **público** a propósito: Instagram descarga cada foto y video desde `raw.githubusercontent.com`. No guardar aquí nada privado (tokens, precios internos, datos de clientes). El material de origen (motor de videos, diseños, voces) vive en `luisogonzalez30-coder/log-in-marketing`, que es privado.

## Cómo funciona

- `calendario.json`: una lista de piezas `{id, fecha, tipo, media, caption}`. `tipo` es `reel`, `feed`, `carrusel` (2 a 10 fotos) o `story`. Fechas con zona `-03:00` (Chile).
- `.github/workflows/publicar.yml`: corre cada hora entre las 9:07 y las 23:07 de Chile, publica lo que ya venció y anota el resultado en `estado.json`. Nunca publica dos veces la misma pieza.
- Secretos de GitHub: `IG_USER_ID` e `IG_PAGE_TOKEN` (token de la página, «Nunca vence»). Nunca pedirlos ni pegarlos en un chat.
- Facebook: en Instagram está activado «Compartir automáticamente» posts y reels a la página de LOG-In.
- TikTok: no se publica desde aquí. Cada semana se dejan los videos y textos para que el usuario los programe en TikTok Studio.

## Reglas del contenido

- **Sin precios.** Desde el 29-oct-2026 LOG-In no publica montos: el llamado es «Nos adaptamos a cualquier presupuesto» y «Comenta TIENDA».
- Promesas que no se pueden contradecir: vista previa gratis en 24 h, publicación en 48 h hábiles, armado en ~1 hora.
- Fotos en JPEG (Instagram no acepta PNG por la API). Reels en MP4 vertical 1080×1920.
- Una pieza al día, a las 19:30 de lunes a viernes y sábado a las 13:00.

## Rutina semanal (la hace Claude cada domingo)

1. Mirar `estado.json`: qué salió, qué falló.
2. Armar las 7 piezas de la semana siguiente con el motor de `log-in-marketing` y agregarlas a `media/` y `calendario.json`.
3. Ensayo local: `DRY_RUN=1 AHORA=<domingo siguiente> node publicar.mjs`.
4. Commit y push, y mandarle al usuario el resumen de la semana con los videos para TikTok.
