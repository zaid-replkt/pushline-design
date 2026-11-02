## 13. Art, audio and IP

Everything on screen is original: names, characters, enemies, worlds, music and sounds. The game borrows a genre, not an asset. Art direction is chosen for portrait readability at 2x speed on a 6-inch screen before it is chosen for charm.

### 13.1 Visual direction

- Style: flat-shaded 2D with thick outlines and two-tone shadows; a "scrap and stone" palette per world (rust and sand, moss and violet, brass and teal, ice-blue and white, ember and charcoal, gold and night). Silhouette-first character design: every unit and enemy must be identifiable as a black shape at 48 pt.
- Units face up the lane; enemies face down. Player units use warm fills, enemies cool fills, in every world, so the lane reads without colour legend. Tag icons (Section 7.1) use shape as well as colour.
- Backgrounds are vertical parallax strips (3 layers) with the lane as a lit path; nothing in the background may contain high-contrast detail within the lane width.
- Bases are the two anchors: the player's base is a visible, upgradeable-looking structure at the bottom that cracks as HP falls; the enemy base is the world's landmark at the top.

### 13.2 Sprite and animation spec

| Asset | Spec |
| --- | --- |
| Unit sprite | 256 × 256 source at 2x, rendered 48-96 pt; skeletal 2D animation (idle, walk, windup, attack, hit, knockback, death); 6-8 frames equivalent |
| Enemy sprite | Same pipeline; bosses 512 × 768, with phase-change states |
| Forms | Form II is a recolour plus one prop; Form III is a new silhouette on the same rig |
| VFX | Hit flash, knockback pips, trait procs (slow trail, stun stars, pierce crack), Command effects; particle budget 200 on screen at 2x |
| UI | Vector, 3 pt stroke, 44/64 pt targets, one display font and one UI font, text minimum 13 pt |

Asset count at launch: 40 units × 3 forms, 72 enemies, 18 bosses (6 world, 6 mid, 6 side variants from modifiers), 6 world backgrounds, 6 base variants, roughly 60 VFX, 300 UI icons.

### 13.3 Audio

- One theme per world plus a boss variant (12 tracks), a map theme and a results sting. Loopable, with an intensity layer that rises when the enemy frontline is in Zone 1.
- Every deploy, hit, knockback, capture and Command has a distinct sound; the capture chime is the most important cue in the game because the zone bar is small. Sound is designed to carry the state for players who look away.
- Haptics: light on deploy, medium on zone capture, heavy on boss phase change; all optional.

### 13.4 IP rules

- No Roblox, Battle Bricks or Battle Cats names, characters, silhouettes, sounds, UI layouts or text. The word "brick" does not appear in the product. Design references are kept in a private mood board, never in the asset pipeline.
- All names in this document (PUSHLINE, unit and enemy names, world names) are placeholders to be trademark-checked before announcement.
