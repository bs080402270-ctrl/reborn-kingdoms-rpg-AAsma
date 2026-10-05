# AAsma Character Asset Credits

This branch uses real, rigged Quaternius assets at runtime. The game keeps the existing procedural rig as a graceful offline fallback, but the preferred path is the imported GLB pipeline.

## Character model

- **Pack:** Quaternius Universal Base Characters — free Standard edition
- **Source:** https://quaternius.itch.io/universal-base-characters
- **License:** CC0 1.0 Universal
- **Runtime source:** `public/assets/vendor/quaternius/night-striker.glb` from the audited public repository `Seyamalam/blood-league-kickoff`
- **Pinned source commit:** `aa02a4e6d8337a0604d2da131bcbbeb1f01badf0`
- **Source repository audit:** its asset ledger identifies the file as Quaternius Universal Base Characters, converted to embedded GLB, with CC0 provenance.

## Fantasy outfit integration

- **Pack:** Quaternius Modular Character Outfits - Fantasy
- **Source:** https://quaternius.com/packs/modularcharacteroutfitsfantasy.html
- **License:** CC0 / Quaternius asset license
- **Integrated asset:** `assets/characters/outfits/Male_Knight_Body_Armor.gltf` + its `.bin` geometry buffer.
- The source GLTF was adapted only to remove external texture dependencies for browser portability; the skinned knight armor geometry and humanoid bone structure are preserved. The runtime synchronizes its humanoid bones to the animated base character, so the outfit follows the same real animation clips.

## Animation libraries

- **Universal Animation Library 1 (UAL1):** 43 animations in the free Standard edition, including idle, walk, jog, sprint, jump, roll, sword attack, punch, spell, hit, talking and interaction clips.
- **Universal Animation Library 2 (UAL2):** 43 complementary Standard animations, including sword combos, sword block, shield actions, melee and additional reactions.
- **Source:** Quaternius official packs: https://quaternius.itch.io/universal-animation-library and https://quaternius.itch.io/universal-animation-library-2
- **License:** CC0 1.0 Universal
- **Pinned runtime source commit:** `84fd636910bf713099010efbab7f3c84550f4bcb` of `richardanaya/metaverse-avatar`, which documents the bundled UAL1/UAL2 files as Quaternius CC0 animation assets.

## Runtime integration

The browser loads the GLB model, fantasy outfit and animation libraries with Three.js GLTFLoader and SkeletonUtils. The Quaternius humanoid skeleton is kept intact; animations are played through Three.js AnimationMixer with cross-faded state transitions. Character movement remains game-controlled, so root-motion variants are not used.

## Race presentation

AAsma currently builds four distinct race presentations from the same production humanoid base:
- **Hero:** royal/adventurer palette and sword presentation.
- **Demon:** dark/crimson material treatment, horns and demonic aura.
- **Elf:** forest palette and pointed ears.
- **Fairy:** luminous palette, wings and halo.

These race-specific accessories are authored by AAsma and attached to the imported rig. They are not claimed to be separate Quaternius source models.

## Facial animation limitation

The current Quaternius runtime asset is a skinned humanoid with skeletal animation. The imported pipeline provides head/body animation and expressive gestures, but this branch does **not** claim full facial blendshape/lip-sync animation because advanced facial morph targets were not verified in the selected Standard model.

## Offline fallback

If the external asset CDN is unavailable, the existing procedural AAsma humanoid rig remains active. This prevents the RPG from becoming unusable, but the browser HUD reports the fallback state rather than pretending the imported asset loaded.

## Important licensing note

The game does not include Mixamo raw assets. Quaternius CC0 assets were selected because their official pages explicitly permit personal, educational and commercial use under CC0.