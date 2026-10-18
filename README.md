# Battle Isle 2 mission fixes

This package fixes campaign animations, reinforcements and selected English mission texts.

## KAIMAWA animation

The original ASCR062 animation was too large to fit in the game's available RAM, so the window closed instead of displaying it. The two `ANI` files install a smaller animation that keeps the character aligned with the camera movement. They also remove a cursor-sound cue that restarted the typing sound after the text had finished appearing.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-mission-fixes/main/ascr062.png)

## ULUARGE reinforcements

The original mission contains a bug where Titan-Net reinforcements are announced, but they never arrive. `MIS/MISS021.DAT` keeps the warning on turn 10 and adds the bridge and reinforcements at the start of turn 11. Existing roads and paths are preserved. The lake tile on the right is loaded at mission start, kept hidden, and placed with the turn-11 changes.

![KAIMAWA ASCR062 animation frame](https://raw.githubusercontent.com/muro/bi2-mission-fixes/main/uluarge_announce.png)


## English mission text fixes

The `ENG` directory contains these English-only corrections:

- JOGRWAI (`MISS001`, report 018): remove RANGER from the required kills. Capturing Pank and destroying the enemy DEMON units can satisfy the mission without destroying all RANGERs.
- FITORGE (`MISS008`, report 052): add Titan-Net’s HQ as the third capture objective and correct “will bombardment” to “will bombard”.
- WABODAE (`MISS003`, report 031): correct “Bay of Maxis” to “Bay of Meltix”.
- GEEUSAT (`MISS012`): restore the existing English mission title and place names, which were shipped in `MISS011.TXT`. Report 095 now says “We are now preparing to attack Titan-Net's headquarters directly”, following the German version.
- WABIKDO (`MISS011`): replace place names 2–25 with names matching its facilities. Report 071 now places the naval base “in the north-west of your sector of operations”. Its mission title and description remain pending a separate translation decision.

`ENG/ATXT000.LIB` changes only reports 018, 031, 052, 071 and 095. The ASCR053 sound correction is shared by both languages. The corrections are all in `ENG/ATXT000.LIB` and install together.

## Installation

1. Close Battle Isle 2.
2. Find the installed game's `ISLE2` directory — it contains `BATTLE2.EXE`.
3. Back up `ISLE2/ANI/ASCR000.LIB`, `ISLE2/ANI/ABCK000.LIB`, `ISLE2/MIS/MISS021.DAT`, `ISLE2/ENG/ATXT000.LIB`, `ISLE2/ENG/MISS011.TXT` and `ISLE2/ENG/MISS012.TXT`, if present.
4. Copy this package's `ANI`, `MIS` and `ENG` directories into `ISLE2`, merging the directories and replacing those files.

To install only one fix, copy only its files. Do not copy them to `SCENERY`: that folder has its own campaign and files with the same names. The patches belong in the installed game directory, not the CD image.

**Start ULUARGE again after installing its fix.** Existing saves contain their own scheduled-event queue and terrain indices; replacing the mission file does not update them.
