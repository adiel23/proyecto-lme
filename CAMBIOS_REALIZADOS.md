# Cambios realizados para cumplir los criterios del proyecto

Este documento resume los cambios agregados al proyecto para cubrir los requisitos solicitados sin utilizar JavaScript.

## 1. Uso de Bootstrap

Se agrego Bootstrap mediante CDN solo como hoja de estilos.

Archivos modificados:

- `index.html`
- `contact.html`

Cambio aplicado:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
```

No se agrego ningun archivo JavaScript de Bootstrap.

Bootstrap se uso realmente en el proyecto mediante clases propias del framework.

En `index.html` se aplicaron clases de Bootstrap para:

- Tabla: `table`, `table-dark`, `table-hover`, `align-middle`.
- Grid responsivo: `container`, `row`, `col-lg-6`, `g-4`.
- Boton: `btn`, `btn-danger`, `btn-lg`.
- Tarjetas: `card`, `bg-dark`, `text-light`, `border-danger`, `border-secondary`, `h-100`.
- Etiquetas visuales: `badge`, `text-bg-danger`, `text-bg-secondary`.

Ejemplo:

```html
<div class="resource-card card bg-dark text-light border-danger h-100">
    <span class="badge text-bg-danger align-self-start mb-3">PDF</span>
    ...
</div>
```

En `contact.html` se aplicaron clases de Bootstrap para el formulario:

- Campos de texto, correo, fecha y mensaje: `form-control`.
- Radios y checkbox: `form-check-input`.
- Boton de envio: `btn`, `btn-danger`.

Ejemplo:

```html
<input type="email" id="email" name="email" class="form-control" required>
```

```html
<input type="checkbox" name="accept-info" class="form-check-input" required>
```

## 2. Uso de multimedia: video y audio

El proyecto ya tenia videos en varias partes del sitio, incluyendo el video de fondo de la pagina principal.

Se agrego un reproductor de audio en la pagina principal usando la etiqueta HTML5 `<audio>`.

Archivo modificado:

- `index.html`

Archivo nuevo:

- `aud/f1-ambiente.wav`

Cambio aplicado:

```html
<audio controls preload="metadata">
    <source src="aud/f1-ambiente.wav" type="audio/wav">
    Tu navegador no soporta audio HTML5.
</audio>
```

## 3. Uso de multicolumnas

Se agrego una seccion llamada `CRONICA MULTICOLUMNA` en la pagina principal.

Archivo modificado:

- `index.html`

Se agrego el estilo CSS con la propiedad `columns`.

Archivo modificado:

- `css/index.css`

Cambio aplicado:

```css
.multi-column-story {
    columns: 3 260px;
    column-gap: 42px;
    column-rule: 1px solid rgba(225, 6, 0, 0.35);
}
```

Esto permite que el texto se distribuya en varias columnas y se adapte al ancho disponible.

## 4. Uso de animaciones

El proyecto ya tenia varias animaciones CSS con `@keyframes`, por ejemplo:

- Fondo con cuadricula animada.
- Particulas flotantes.
- Efecto glitch del titulo.
- Marquesina de escuderias.

Adicionalmente, se agrego una animacion para el carrusel de imagenes.

Archivo modificado:

- `css/index.css`

Cambio aplicado:

```css
@keyframes imageCarousel {
    0%, 18% { transform: translateX(0); }
    25%, 43% { transform: translateX(-25%); }
    50%, 68% { transform: translateX(-50%); }
    75%, 93% { transform: translateX(-75%); }
    100% { transform: translateX(0); }
}
```

## 5. Uso de transformaciones

El proyecto ya usaba transformaciones CSS como `scale`, `translate`, `rotate` y `perspective`.

Tambien se agregaron transformaciones en las tarjetas nuevas de recursos:

Archivo modificado:

- `css/index.css`

Cambio aplicado:

```css
.resource-card:hover,
.audio-card:hover {
    transform: translateY(-8px);
}
```

## 6. Uso de transiciones

El proyecto ya contaba con transiciones en botones, tarjetas, enlaces y elementos interactivos.

Se agregaron transiciones a las nuevas tarjetas de recursos.

Archivo modificado:

- `css/index.css`

Cambio aplicado:

```css
.resource-card,
.audio-card {
    transition: transform 0.35s ease, border-color 0.35s ease;
}
```

## 7. Uso de tablas completas

La tabla del campeonato ya existia, pero se reforzo para cumplir todos los puntos solicitados:

- Titulo de tabla con `<caption>`.
- Combinacion de columnas con `colspan`.
- Combinacion de filas con `rowspan`.
- Pie de tabla con `<tfoot>`.

Archivo modificado:

- `index.html`

Cambios principales:

```html
<caption>Clasificacion final del Campeonato Mundial de Pilotos F1 2021</caption>
```

```html
<th colspan="4" class="table-super-title">Top 10 de pilotos - Temporada 2021</th>
```

```html
<th rowspan="2" scope="rowgroup">Duelo por el titulo</th>
```

```html
<tfoot>
    <tr>
        <td colspan="3">Diferencia entre Verstappen y Hamilton</td>
        <td>8 pts</td>
    </tr>
</tfoot>
```

## 8. Carrusel de imagenes

Se agrego un carrusel de imagenes hecho solo con HTML y CSS.

Archivo modificado:

- `index.html`

Seccion agregada:

```html
<section class="image-carousel-section">
    <h3 class="section-title">CARRUSEL DE IMAGENES</h3>
    <div class="css-carousel">
        <div class="css-carousel-track">
            ...
        </div>
    </div>
</section>
```

Archivo modificado:

- `css/index.css`

El carrusel se mueve con una animacion CSS y no utiliza JavaScript.

## 9. Comportamiento responsivo

El sitio ya tenia reglas responsive en varios archivos CSS.

Se reforzo la responsividad de:

- Navegacion.
- Encabezados.
- Footer.
- Formulario de contacto.
- Carrusel de imagenes.
- Secciones nuevas.

Archivos modificados:

- `css/styles.css`
- `css/index.css`
- `css/contact.css`

Ejemplo:

```css
@media screen and (max-width: 768px) {
    .resource-section,
    .story-section,
    .image-carousel-section {
        padding: 70px 20px;
    }
}
```

## 10. PDF descargable

Se creo un archivo PDF local con un resumen de la temporada 2021.

Archivo nuevo:

- `docs/f1-2021-resumen.pdf`

Se agrego un enlace de descarga en la pagina principal.

Archivo modificado:

- `index.html`

Cambio aplicado:

```html
<a href="docs/f1-2021-resumen.pdf" class="btn btn-danger btn-lg download-link" download>
    Descargar PDF
</a>
```

## 11. Formulario con checkbox, radio, submit y datetime-local

El formulario de contacto ya tenia campos de nombre, correo, mensaje y boton de envio.

Se agregaron:

- Campo `datetime-local`.
- Opciones `radio`.
- Campo `checkbox`.
- Se mantuvo el boton `submit`.

Archivo modificado:

- `contact.html`

Cambios principales:

```html
<input type="datetime-local" id="visit-date" name="visit-date" required>
```

```html
<input type="radio" name="topic" value="temporada" required>
```

```html
<input type="checkbox" name="accept-info" required>
```

```html
<button type="submit" class="btn-submit">Enviar Mensaje</button>
```

Tambien se agregaron estilos para estos nuevos controles.

Archivo modificado:

- `css/contact.css`

## 12. Verificacion de no uso de JavaScript

Se reviso que no se agregaran etiquetas `<script>` ni enlaces `javascript:`.

El carrusel, las animaciones, las transiciones y la interaccion visual se realizan con HTML y CSS.

## Archivos modificados

- `index.html`
- `contact.html`
- `css/index.css`
- `css/contact.css`
- `css/styles.css`

## Archivos nuevos

- `CAMBIOS_REALIZADOS.md`
- `aud/f1-ambiente.wav`
- `docs/f1-2021-resumen.pdf`
