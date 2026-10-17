# emails-public

Hosting estático (GitHub Pages) para emails de marketing/comunicaciones de Badamax. Sirve los HTML y assets (imágenes) en una URL pública para que clientes de mail externos (Gmail, Outlook) puedan cargar las imágenes.

## Cómo agregar una nueva campaña

1. Crear carpeta con slug descriptivo: `nombre-campana-NN/` (newsletter: `entregables-<mes>-<año>-NN/`).
2. Adentro: el `.html` + todas las imágenes referenciadas con paths relativos.
3. Editar `index.html` agregando un link.

## Cómo publicar en GitHub Pages

GitHub Pages publica automáticamente lo que está en `main` en
https://badamax-ti.github.io/emails-public/. **Mergear a `main` es publicar**, así que todo va por
rama + PR:

```bash
git checkout main && git pull
git checkout -b newsletter-NN-<mes>
git add <carpeta>/ index.html            # y README.md si cambió
git commit -m "Lo que entregamos NN · <rango de fechas>"
git push -u origin newsletter-NN-<mes>
gh pr create --base main --title "Lo que entregamos NN · <rango de fechas>"
```

Antes de mergear, revisar el PR contra la checklist de abajo. Después de mergear:

1. Esperar que termine el deploy de Pages (pestaña *Actions* → *pages build and deployment*,
   1–2 minutos).
2. Abrir `https://badamax-ti.github.io/emails-public/<carpeta>/<archivo>.html` y verificar que
   cargan las imágenes y que es la versión nueva (si se ve la antigua, recargar sin caché).
3. Recién ahí enviar el correo: las imágenes del mail se cargan desde esa URL pública.

## Newsletter "Lo que entregamos": checklist antes de publicar

Este repo es **público**: todo lo que quede en el HTML (incluidos comentarios y código fuente) lo
puede leer cualquiera. Tomar como base la edición anterior y revisar:

**Contenido que no se publica**

- Nada de comentarios HTML (`<!-- ... -->`), en especial los que anotan fuentes o informes internos.
- No mencionar los informes internos de donde salió cada dato ("según el reporte del 16", "el
  reporte del 9 señala…"). Se afirma el hecho.
- **No se dejan temas abiertos.** El newsletter cuenta lo entregado: nada de bloques "Alcance al
  cierre", "Queda pendiente…", "Falta…", ni "El siguiente paso es…" seguido de tareas
  concretas, en las secciones ni en el cierre. Lo que todavía no está terminado no entra, o espera la edición en que se cierre.
  Un piloto se cuenta por lo que ya hizo, sin la lista de lo que le falta.
- Nada de frases sobre cómo se redactó ("no es una afirmación de que…", "se conserva ese alcance").
- Sin condiciones comerciales de proveedores (tarifas, comisiones, porcentajes negociados): se
  cuenta el avance sin la cifra.
- Sin nombres de personas del equipo en el cuerpo (solo quien firma las palabras de apertura). Se
  nombran áreas o sistemas.
- Sin secretos, URLs internas, IPs ni nombres de servidores.

**Nombres y estructura**

- Nombres oficiales, no la herramienta de fondo:
  - **Copiloto AI** (no "ChatGPT y Claude"; se pueden nombrar solo para decir desde dónde se usa).
  - **Nueva Plataforma E-commerce** (no "Shopify").
  - **POS Mobile** para el punto de venta de Gate y su piloto con Baaskit.
- **Todos los proyectos van en un solo bloque "Proyectos"**, al final del cuerpo. Cada punto
  empieza con el nombre del proyecto en negrita: Contabilidad Digital, Nueva Plataforma
  E-commerce, POS Mobile, Telefonía e Internet, Migración SAP, Las Moras, Plan de seguridad.
- **Contabilidad Digital** agrupa Gestión de Proveedores, Órdenes de Compra, Recepción, Pagos y
  Control de Caja, aunque el cambio se haya hecho en Crew, Hangar o Nexum.
- Cada avance va en la sección del producto o proyecto al que pertenece; no hay sección
  "Transversal" de miscelánea. Un punto que no alcanza para una sección propia se integra a otra
  o no entra.
- **Badges de producto en cada sección**, bajo el título: los productos digitales involucrados
  (Nexum, Gate, Helix, Atelier, Crew, CockpIT, Hangar, Beaver, Runway, Flare, Las Moras,
  Copiloto AI, Plataforma de datos, Qlik). Sistemas externos (SAP, Retail Pro, OMS, proveedores)
  no llevan badge. Pastilla de fondo blanco con borde y texto del color del producto; copiar el
  HTML de una edición anterior para mantener los mismos colores.
- No mezclar temas en un mismo punto: si un proveedor o un tema es de otro proyecto (por ejemplo,
  Acktib es del Plan de seguridad), va en su propio punto.

**Consistencia**

- El número de edición y el rango de fechas coinciden en el encabezado, `<title>`, el pie y el
  link de `index.html`.
- El índice ("En este número") tiene los mismos títulos y la misma cantidad de secciones que el
  cuerpo, y el texto del total ("Diecisiete frentes…") calza.
- Cada cifra de las tarjetas destacadas aparece en el cuerpo con el mismo valor.
- No se presenta como terminado algo que no lo está: si no está terminado, no se incluye.

**Forma**

- Español de Chile con tuteo (tú, tienes; nunca vos, tenés). "solo" sin tilde.
- Preheader oculto al inicio del `<body>`, `<meta name="color-scheme" content="light">` y estilos
  inline (el `<style>` del `<head>` solo para ajustes en pantallas de celular).
- Imágenes con ruta relativa dentro de la carpeta de la edición (`mauricio.png` se copia); no
  cargan hasta que se haga push.
- Sin links ni firma en el cierre: "Para cerrar" termina con el agradecimiento, sin invitación a
  escribir ni botón de correo.
- El agradecimiento del cierre incluye al equipo y a los equipos de negocio: su colaboración y sus
  definiciones son las que hacen que la tecnología funcione.

## URL pattern

```
https://badamax-ti.github.io/emails-public/<slug>/<archivo>.html
```
