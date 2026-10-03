# Battle Isle 2 KAIMAWA animation fix

The original ASCR062 animation was too large to fit in the game's available RAM, so the window closed instead of displaying it. This package installs a smaller animation that keeps the character aligned with the camera movement. It now loads and plays normally. It also removes a cursor-sound cue that restarted the typing sound after the text had finished appearing.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-kaimawa-animation-fix/main/ascr062.png)

## Installation

1. Close Battle Isle 2.
2. Find the installed game's `ISLE2` directory — it contains `BATTLE2.EXE`.
3. Back up `ISLE2/ANI/ASCR000.LIB` and `ISLE2/ANI/ABCK000.LIB`, if they are present.
4. Copy this package's two `ANI` files to `ISLE2/ANI`.

Do not copy them to `SCENERY/ANI`: that folder has its own files with the same names.
