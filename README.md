# Battle Isle 2 KAIMAWA and ULUARGE fixes

This package fixes two original Battle Isle 2 campaign missions.

## KAIMAWA animation

The original ASCR062 animation was too large to fit in the game's available RAM, so the window closed instead of displaying it. The two `ANI` files install a smaller animation that keeps the character aligned with the camera movement. They also remove a cursor-sound cue that restarted the typing sound after the text had finished appearing.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-kaimawa-animation-fix/main/ascr062.png)

## ULUARGE reinforcements

The original mission contains a deferred bridge and reinforcement layer, DF00, but no scheduled action activates it. `MIS/MISS021.DAT` adds that missing activation on displayed turn 10 after the bridge warning. It keeps both new overlays and all 23 Titan-Net reinforcement placements while preserving the existing roads and paths, preserving the existing weather events, announcements and mission rules.

The original bridge warning keeps its original timing after an action on turn 10. The added activation has a later event threshold than the warning. See [ULUARGE repair details](ULUARGE.md).

## Installation

1. Close Battle Isle 2.
2. Find the installed game's `ISLE2` directory — it contains `BATTLE2.EXE`.
3. Back up `ISLE2/ANI/ASCR000.LIB`, `ISLE2/ANI/ABCK000.LIB` and `ISLE2/MIS/MISS021.DAT`, if present.
4. Copy this package's `ANI` and `MIS` directories into `ISLE2`, merging the directories and replacing those files.

To install only one fix, copy only its files. Do not copy them to `SCENERY`: that folder has its own campaign and files with the same names. The patches belong in the installed game directory, not the CD image.

**Start ULUARGE again after installing its fix.** Existing saves contain their own scheduled-event queue and do not automatically acquire the new activation by replacing the mission file.
