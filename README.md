# Backrooms

Juego en primera persona ambientado en los *Backrooms*: un laberinto de paredes amarillas y luces parpadeantes del que hay que escapar antes de que se acabe el tiempo (2 minutos).

**Jugar:** https://ferjoo.github.io/backrooms/

## Controles

| Acción | Tecla |
|--------|-------|
| Avanzar / retroceder | `W` / `S` o flechas ↑ / ↓ |
| Girar | `A` / `D`, flechas ← / → o el mouse |
| Liberar el mouse | `Esc` |

## Cómo está hecho

Un solo `index.html` sin dependencias: renderizado por *raycasting* sobre `<canvas>` 2D, control con Pointer Lock API y bucle de juego con `requestAnimationFrame`.

Tarea del curso de Manejo e Implementación de Archivos, Universidad de San Carlos de Guatemala (USAC).
