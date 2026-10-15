# Backrooms

Juego de terror en primera persona ambientado en los *Backrooms*: un laberinto de paredes amarillas y luces que zumban. Algo te persigue por los pasillos; encuentra la **salida verde** antes de que te atrape.

**Jugar:** https://ferjoo.github.io/backrooms/ (en computadora, con teclado, mouse y de preferencia audífonos)

## Controles

| Acción | Tecla |
|--------|-------|
| Moverte | `W` `A` `S` `D` o flechas ↑ / ↓ |
| Girar | mouse o flechas ← / → |
| Correr | `Shift` (gasta energía; si se agota, tienes que recuperarte) |
| Silenciar | `M` |
| Reintentar | `R` o clic |
| Liberar el mouse | `Esc` |

## El ente

- Se dibuja como un *billboard* dentro del raycaster, recortado columna por columna contra el z-buffer de las paredes, así que se esconde detrás de esquinas de forma correcta. Tiene la misma niebla y el mismo parpadeo que el nivel.
- Aparece después de unos segundos en la celda alcanzable más lejana a ti y te persigue con un campo de distancias BFS que se recalcula cuatro veces por segundo.
- Es más rápido que tú caminando y más lento que tú corriendo, y acelera poco a poco.
- Si te alcanza, hay *jump scare*.

## Audio espacial

Todo el audio se genera en tiempo real con la **Web Audio API**; no hay archivos de sonido:

- **Zumbido fluorescente:** 60 Hz, su armónico de 120 Hz y un siseo eléctrico filtrado.
- **Pasos, respiración y gruñido del ente:** pasan por un `PannerNode` con HRTF colocado en su posición. El oyente sigue tu posición y orientación en cada frame, así que lo escuchas más fuerte cuando se acerca y del lado correcto (izquierda o derecha).
- **Paredes:** amortiguan su sonido con un filtro paso bajo cuando no hay línea de vista.
- **Latido:** se acelera y sube de volumen según la distancia.
- **Golpe disonante:** suena la primera vez que te ve.

## Cómo está hecho

**100% Vanilla JS**, sin motor ni dependencias: un solo `index.html` más la imagen del ente.

- **Raycasting DDA** sobre `<canvas>` 2D, con z-buffer por columna y paletas de color precalculadas, sin asignar memoria en el ciclo de render.
- **Pointer Lock API** para el mouse y `requestAnimationFrame` para el bucle de juego.
- **Web Audio API** para todo el sonido, con audio espacial HRTF.
- En celulares y tablets muestra un aviso, porque el juego necesita teclado y mouse.
