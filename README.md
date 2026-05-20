# Modulo de votacion publica

Este modulo no controla el evento. Escucha Firebase, muestra el estado publico y envia votos.

## Rutas Firebase usadas

- `/state`
  - `waitingRoom: true` muestra sala de espera.
  - `votingOpen: true` muestra votacion activa.
  - `votingEnded: true` muestra votacion cerrada.
  - `currentRound` separa votos por ronda.
  - `totalVotes` se incrementa al registrar un voto.
  - `resetToken` permite reiniciar seleccion local cuando el panel lo cambie.
  - `stage` se guarda en el payload del voto; por defecto usa `parejas`.

- `/participantes`
  - Cada participante debe incluir `id`, `numero`, `nombre` e `imagen`.
  - El modulo no genera participantes falsos si esta ruta esta vacia.

- `/voteSettings`
  - `menuBackground` cambia el fondo inicial.
  - `waitingSymbol` cambia el caballo/simbolo de espera.
  - `texts.menuLine1`, `texts.menuLine2`, `texts.menuNote`, `texts.waitingTitle`, `texts.waitingMessage`, `texts.waitingSignature` actualizan textos publicos.

- `/votos`
  - Recibe cada voto con ronda, etapa, deviceId, timestamp de servidor y cinco parejas.

- `/voteRegistry/round_{currentRound}/{deviceId}`
  - Registro anti doble voto por dispositivo y ronda.
