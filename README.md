# Fotos de Gema Pastelería

Por ahora el sitio funciona con solo 4 fotos reales dentro de `img/`:

| Archivo             | Dónde se usa                                              |
|----------------------|------------------------------------------------------------|
| `img/logo.png`       | Logo en el encabezado y en la portada (inicio)             |
| `img/especial.jpg`   | Torta tipo "Especial", categoría "Tortas", "Brownies"      |
| `img/semi.jpg`       | Torta tipo "Semiespecial", categoría "Brazos", "Vasos"     |
| `img/pay.jpg`        | Torta tipo "Normal", categoría "Pays", "Masitas", "Mini tortas" |

Todo lo demás (sabores especiales, productos sin foto propia, categorías sin
foto propia) recicla automáticamente estas mismas 3 fotos de torta en orden,
para que ninguna tarjeta quede vacía o sin imagen. Esto es temporal: es una
demo con pocas fotos reales.

## Cómo asignar las fotos (editar `index.html`)

Las asignaciones están centralizadas cerca del inicio del `<script>`, justo
después de `ICONOS_EXTRA`:

```js
const FOTOS_DEMO = ["img/especial.jpg", "img/semi.jpg", "img/pay.jpg"];

const FOTOS_CATEGORIA = {
  tortas: "img/especial.jpg",
  pays: "img/pay.jpg",
  ...
};
const FOTOS_TIPO_TORTA = { Normal: "img/pay.jpg", Semi: "img/semi.jpg", Especial: "img/especial.jpg" };
```

- **`FOTOS_CATEGORIA`**: foto de portada de cada tarjeta de categoría en el
  inicio. Cambia el valor por la ruta de la foto real cuando la tengas.
- **`FOTOS_TIPO_TORTA`**: foto de cada tarjeta de tipo en el armador de
  tortas (Normal / Semiespecial / Especial).
- **`FOTOS_DEMO`**: lista de fotos que se van reciclando (en orden) para
  sabores especiales, productos sin foto propia y cualquier categoría que no
  tenga entrada en `FOTOS_CATEGORIA`. Agrega más rutas a este arreglo a
  medida que tengas más fotos reales, y la variedad mejora sola.

## Agregar más fotos reales

1. Copia el archivo a `img/` (nombre libre, ej. `img/tortas.jpg`,
   `img/vasos.jpg`, `img/sabores/tres-leches.jpg`).
2. Agrega o reemplaza la ruta correspondiente en `FOTOS_CATEGORIA`,
   `FOTOS_TIPO_TORTA`, o súmala a `FOTOS_DEMO` para que entre al reciclado
   general.

No hace falta tocar nada más: las tarjetas, el `object-fit: cover` y el
tamaño ya están resueltos en el CSS.

## Logo

`img/logo.png` se usa en dos lugares, ambos con `object-fit: contain` (nunca
se recorta ni se deforma):

- Encabezado: círculo pequeño junto al nombre de la tienda.
- Portada (inicio): tarjeta centrada sobre el banner, con buen tamaño tanto
  en celular como en pantallas grandes.

## Respaldo de seguridad

Cada imagen igual conserva un ícono de línea de respaldo (Lucide) por si
algún archivo no carga (ruta incorrecta, archivo corrupto, etc.): si la foto
falla, el ícono queda visible solo sobre un fondo de color en vez de dejar
un espacio roto.
