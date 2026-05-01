# emails-public

Hosting estático (GitHub Pages) para emails de marketing/comunicaciones de Badamax. Sirve los HTML y assets (imágenes) en una URL pública para que clientes de mail externos (Gmail, Outlook) puedan cargar las imágenes.

## Cómo agregar una nueva campaña

1. Crear carpeta con slug descriptivo: `nombre-campana-NN/`
2. Adentro: el `.html` + todas las imágenes referenciadas con paths relativos
3. Editar `index.html` agregando un link
4. `git add . && git commit -m "..." && git push`

GitHub Pages publica automáticamente en https://badamax-ti.github.io/emails-public/

## URL pattern

```
https://badamax-ti.github.io/emails-public/<slug>/<archivo>.html
```
