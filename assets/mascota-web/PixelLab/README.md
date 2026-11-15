# Animaciones de la mascota web — PixelLab

Variante generada con PixelLab a partir de una referencia común del robot. Los archivos originales de SpriteCook están en la carpeta superior y se conservan separados.

## Especificaciones

- **Formato:** PNG RGBA de 8 bits, con transparencia.
- **Lienzo de cada hoja:** 640 × 512 px.
- **Cuadro:** 128 × 128 px.
- **Distribución:** 5 columnas × 4 filas, orden de izquierda a derecha y de arriba hacia abajo.
- **Cuadros con contenido:** 17 por hoja; los tres espacios finales están vacíos y transparentes.
- **Ajuste de PixelLab:** 16 cuadros; el resultado exportado contiene 17 posiciones activas.
- **Reproducción sugerida:** 8 fps (125 ms por cuadro; 2,125 s para 17 cuadros). La velocidad se controla desde la página web.
- **Escalado:** usar múltiplos enteros y `image-rendering: pixelated`.

## Archivos

| Archivo | Uso | Comportamiento web sugerido |
|---|---|---|
| `Robot_Welcome_Wave_sheet.png` | Entrada de bienvenida con gesto de saludo. | Reproducir una vez y enlazar a Hover/Idle. |
| `Robot_Hover_Idle_sheet.png` | Flotación de reposo con leves gestos. | Repetir en bucle mientras la mascota espera. |
| `Robot_Talking_sheet.png` | Gestos de conversación y movimiento facial. | Repetir durante el diálogo y volver a Hover/Idle al terminar. |

## Uso de la cuadrícula

El índice de cuadro es de base cero. Para `i` entre 0 y 16:

```js
const column = i % 5;
const row = Math.floor(i / 5);
element.style.backgroundPosition = `${-column * 128}px ${-row * 128}px`;
```

El elemento debe medir 128 × 128 px y usar el PNG correspondiente como `background-image`, con `background-repeat: no-repeat`. Los cuadros 18–20 son espacios vacíos y no deben reproducirse.

## Transiciones

La entrada Welcome conduce a Hover/Idle; Talking usa la flotación como estado de reposo al finalizar. PixelLab se configuró para volver a una pose neutral común, aunque el cuadro 1 y el 17 no son idénticos píxel a píxel en las exportaciones. Revisa el empalme en el reproductor web; Hover/Idle es el puente entre estados.
