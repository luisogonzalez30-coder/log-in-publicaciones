# Publicador automático de Instagram — LOG-In

Publica solo, cada día, las piezas de `calendario.json` en el Instagram de LOG-In. Instagram las copia a la página de Facebook. Corre gratis en GitHub Actions.

## Dejarlo funcionando (una vez)

1. **Secretos** (Settings → Secrets and variables → Actions → New repository secret):
   - `IG_USER_ID`: el ID de la cuenta de Instagram de LOG-In.
   - `IG_PAGE_TOKEN`: el token de la página de LOG-In que dice «Nunca vence».
2. **Ensayo:** Actions → «Publicar en Instagram» → Run workflow, con *ensayo* marcado. El registro dice qué publicaría.
3. **Facebook:** en Instagram, Centro de cuentas → Compartir entre perfiles → activar compartir posts y reels en la página.

Si el token deja de funcionar, la corrida falla con «ERROR de acceso»: genera un token nuevo y reemplaza `IG_PAGE_TOKEN`.

## Cambiar o quitar una pieza

Edita `calendario.json` antes de su hora. Para que una pieza no salga, bórrala de la lista.
