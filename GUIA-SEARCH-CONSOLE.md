# Guía: dar de alta coseqcose.com en Google Search Console

Objetivo: que Google indexe cuanto antes las 3 versiones de la web
(`/`, `/ca/`, `/en/`) y poder ver con qué búsquedas nos encuentra la gente.

Tiempo estimado: 10-15 minutos. Necesitas la cuenta de Google del negocio
(idealmente la misma que gestiona la ficha de Google Business Profile).

---

## Paso 1 — Entrar en Search Console

1. Ve a https://search.google.com/search-console
2. Inicia sesión con la cuenta de Google del negocio.

## Paso 2 — Añadir la propiedad

Te ofrecerá dos tipos de propiedad. **Elige "Prefijo de la URL"** (la opción
de la derecha) y escribe exactamente:

```
https://www.coseqcose.com/
```

> ¿Por qué no "Dominio"? La opción "Dominio" cubre más variantes pero exige
> verificar con un registro TXT en el DNS del dominio (donde compraste
> coseqcose.com). "Prefijo de URL" se puede verificar con un simple archivo
> en la web, que para GitHub Pages es lo más fácil. Si en el futuro quieres,
> puedes añadir la propiedad de Dominio además de esta.

## Paso 3 — Verificar que la web es tuya

Search Console te mostrará varios métodos. El más fácil con GitHub Pages es
el **archivo HTML**:

1. En la pantalla de verificación, método "Archivo HTML" → descarga el
   archivo (se llama algo como `google1a2b3c4d5e6f7890.html`).
2. Copia ese archivo a la **raíz del repo** (al lado de `index.html`):
   ```bash
   cp ~/Downloads/googleXXXXXXXX.html /Users/sdolgonos/Personal/coseqcose/
   cd /Users/sdolgonos/Personal/coseqcose
   git add googleXXXXXXXX.html
   git commit -m "Verificación de Search Console"
   git push
   ```
3. Espera 1-2 minutos a que GitHub Pages publique y comprueba que se ve en
   `https://www.coseqcose.com/googleXXXXXXXX.html` (debe mostrar una línea
   de texto, no un 404).
4. Vuelve a Search Console y pulsa **Verificar**.

⚠️ No borres nunca ese archivo del repo: Google re-comprueba la verificación
periódicamente.

*Alternativa:* método "Etiqueta HTML" — te dan una `<meta name="google-site-verification" ...>`
para pegar en el `<head>` de `index.html`. Funciona igual de bien, pero solo
verifica si la pegas antes de hacer push, y hay que mantenerla ahí.

## Paso 4 — Enviar el sitemap

1. En el menú lateral de Search Console: **Sitemaps** (dentro de "Indexación").
2. En "Añadir un sitemap", escribe:
   ```
   sitemap.xml
   ```
   (Google lo completa a `https://www.coseqcose.com/sitemap.xml`.)
3. Pulsa **Enviar**. Debería quedar en estado "Correcto" con 3 URLs
   descubiertas. El sitemap ya incluye las alternativas de idioma (hreflang),
   así que con esto Google conoce las 3 versiones.

## Paso 5 — (Opcional pero recomendado) Pedir indexación manual

Para no esperar a que Google pase solo, fuerza la primera indexación:

1. En la barra de arriba ("Inspecciona cualquier URL"), pega
   `https://www.coseqcose.com/` y pulsa Enter.
2. Cuando termine el análisis, pulsa **Solicitar indexación**.
3. Repite con `https://www.coseqcose.com/ca/` y
   `https://www.coseqcose.com/en/`.

Hay un límite de ~10 solicitudes al día; con estas 3 sobra.

## Qué esperar después

- **Días 1-3:** las páginas aparecen en el informe **Indexación → Páginas**.
- **1-2 semanas:** empiezan a salir datos en **Rendimiento** (con qué
  búsquedas aparece la web, clics, posición media). Ahí verás si funcionan
  las búsquedas tipo "arreglos ropa can baró" o "bolsos artesanales guinardó".
- Buscar `site:coseqcose.com` en Google es la forma rápida de comprobar qué
  hay indexado.

## Extra: conectar con Google Business Profile

Ya que estás con la cuenta de Google del negocio, entra en
https://business.google.com y comprueba que la ficha tiene como sitio web
`https://www.coseqcose.com/`. La web y la ficha enlazándose mutuamente
(la web ya enlaza a la ficha desde la insignia de 4,9★) refuerza el SEO local.

---
*Este archivo es solo una guía local — puedes borrarlo cuando termines,
o dejarlo sin commitear.*
