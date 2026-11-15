# Hojas de sprites — mascota web

Este paquete contiene tres animaciones pixel art del robot mascota, preparadas para integrarse en una página web.

## Especificaciones comunes

- **Formato:** PNG con fondo transparente.
- **Tamaño de cada fotograma:** 176 × 176 px.
- **Disposición:** 8 fotogramas en una sola fila horizontal.
- **Tamaño de cada hoja:** 1408 × 176 px.
- **Velocidad recomendada:** 8 fotogramas por segundo (125 ms por fotograma; ciclo de 1 s).
- **Orden:** de izquierda a derecha, empezando por el fotograma 1.
- **Escalado:** usar múltiplos enteros con `image-rendering: pixelated` para conservar los bordes pixel art.

## Animaciones

| Archivo | Uso recomendado | Reproducción |
|---|---|---|
| `Robot_Welcome_Wave_sheet.png` | Entrada de bienvenida: el robot aparece y saluda con un gesto enérgico. | Reproducir una vez al entrar; enlazar al reposo. |
| `Robot_Hover_Idle_sheet.png` | Estado de reposo: flotación con pequeños movimientos. | Repetir en bucle mientras la mascota espera. |
| `Robot_Talking_sheet.png` | Estado de conversación: movimiento de habla con pulsos visuales. | Repetir mientras se muestra diálogo; volver a reposo al terminar. |

## Transiciones sugeridas

Usa la animación de bienvenida como entrada y continúa con la de reposo. Al iniciar un diálogo, cambia a la animación de conversación y vuelve a reposo al terminar. Mantén el mismo tamaño y punto de anclaje del fotograma en los tres estados para evitar saltos. El reposo sirve como puente visual entre bienvenida y conversación.

## Implementación

Cada hoja contiene 8 cuadros consecutivos. Para mostrarlos con CSS, usa el ancho de un cuadro (`176px`) como ancho del elemento y el ancho completo de la hoja (`1408px`) como recorrido de `steps(8)`. Ajusta ambos valores al tamaño de presentación elegido y escala proporcionalmente.
