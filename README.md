# Battle Isle 2 KAIMAWA and ULUARGE fixes

This package fixes two original Battle Isle 2 campaign missions.

## KAIMAWA animation

The original ASCR062 animation was too large to fit in the game's available RAM, so the window closed instead of displaying it. The two `ANI` files install a smaller animation that keeps the character aligned with the camera movement. They also remove a cursor-sound cue that restarted the typing sound after the text had finished appearing.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-mission-fixes/main/ascr062.png)

## ULUARGE reinforcements

The original mission contains a bug where Titan-Net reinforcements are announced, but they never arrive. `MIS/MISS021.DAT` keeps the warning on turn 10 and adds the bridge and reinforcements at the start of turn 11. Existing roads and paths are preserved.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-mission-fixes/main/uluarge_announce.png)


## Installation

1. Close Battle Isle 2.
2. Find the installed game's `ISLE2` directory — it contains `BATTLE2.EXE`.
3. Back up `ISLE2/ANI/ASCR000.LIB`, `ISLE2/ANI/ABCK000.LIB` and `ISLE2/MIS/MISS021.DAT`, if present.
4. Copy this package's `ANI` and `MIS` directories into `ISLE2`, merging the directories and replacing those files.

To install only one fix, copy only its files. Do not copy them to `SCENERY`: that folder has its own campaign and files with the same names. The patches belong in the installed game directory, not the CD image.

**Start ULUARGE again after installing its fix.** Existing saves contain their own scheduled-event queue and do not automatically trigger after replacing the mission file.
