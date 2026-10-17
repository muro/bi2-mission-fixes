# ULUARGE turn-10 reinforcement repair

The original `MIS/MISS021.DAT` contains DF00 with 25 map-change records: two overlay placements and 23 Titan-Net unit placements. Its MAP schedule contains no type-04 deferred-layer activation. The bridge announcement alone does not apply the layer.

This repair appends one 40-byte MAP action, preserving every original MAP record and all unit placements:

| Field | Value |
| --- | --- |
| Internal turn | 9 (displayed turn 10) |
| Event threshold | 4 (after the warning’s event threshold 2) |
| Selector | 1 (blue) |
| Action type | 04 (activate deferred layer) |
| Layer index | 0 (DF00) |

The DF section pointer is advanced by 40 bytes to account for the inserted action. Its size is unchanged. Four DF overlay words retain the original ACTN routes under arriving units: road source 90 at (26,3), (4,7), and (4,10), and path source 92 at (5,11). Without these edits the native writer clears those overlays. Both new overlays remain: source 90 at (4,9), and source 358 at (25,11). All original weather events, terminal conditions and announcements remain present. This is an explicit repair policy; it does not establish which missing or incorrect record the original author intended.

The warning about a bridge being “about to be built” retains its original internal turn-9/event-2 gate. The repaired layer has event threshold 4, later than the warning. The revised animation/dispatch ordering still requires native verification.

## Input and output identities

Original CD/GOG mission SHA-256:

`2d3d6e16753d117f138c478e429c8564a158f47822305bfb3a9114918240fefd`

Patched mission SHA-256:

`5d8d9462079a4b399486d702880a96ac6af6a3f2df44a11ba45ba754e52b00ce`

The generator and regression tests are in [bi2tools](https://github.com/muro/bi2tools), `tools/patch_uluarge_mission.mjs` and its test file. Generate the overlay from the original mission with:

```sh
node tools/patch_uluarge_mission.mjs ORIGINAL_MISS021.DAT output/MIS/MISS021.DAT
```

The generator checks the original identity, rejects other mission versions and accepts an already repaired file without adding a second action. Structural tests check preservation of the original actions, all deferred bytes except the four route words, and valid section pointers. Native verification uses a private mission setup; the test save must include the added request because restoring an old save replaces the mission's newly loaded queue.
