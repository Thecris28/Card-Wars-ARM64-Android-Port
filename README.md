# Card-Wars-ARM64-Android-Port

# Changelog

## Version 1.12.12 — November 1

- **Save Data Import on Android:** You can import save data from another version of Card Wars using the decrypted `game.json` file.
- **Bilingual Profile Selector:** Automatically switches between Spanish and English based on the device's language settings.

## Version 1.12.11 — October 31

### 1. Regionalization and Numeric Data Handling

- **Numeric parsing normalization:** Implemented `ParseInvariantFloat` and `ParseInvariantInt` using `CultureInfo.InvariantCulture`.
  - Fixed visual issues in menus and battle arenas caused by the device's regional settings.
  - Fixed parsing issues involving periods (`.`) and commas (`,`) as decimal separators.
- **Decimal value support:**
  - Fixed parsing of roulette parameters.
  - Corrected positions, scales, offsets, rotations, and dialogue timings.
  - Fixed the configuration of leaders' areas, timings, and critical damage.
- **Facial animations:** Applied the regionalization fixes to the `mouth` files and animations.

### 2. Battle Rewards and Chests

- Adjusted reward banner selection to use the rarity of the obtained card.
- Added diagnostic logs to identify the selected card and prefab.
- Removed an additional delay when displaying the banner.
- Adjusted the order in which scaling and parenting are applied to preserve the banner's original visible size.
- Fixed the Gacha chest animation.

### 3. Animations, Visual Effects, and UI

#### Spells and Battle Sequences

- **Spell speed improvements:** Reduced the execution times of *Cerebral Bloodstorm*, *Volcano*, and *Throne of Doom*.
- Combined target destruction effects to reduce delays when destroying cards.
- Added a one-second delay before resuming the battle phase after a card is destroyed.
- Integrated the `Volcano_anim` animation into the Volcano spell sequence.
- Repositioned Volcano's main effect to the first target's lane.
- Reorganized the destruction and magic recovery sequence to prevent conflicts with the camera and battle phases.
- **Spell prefabs:** Assigned the `attack` clip as the default animation in:
  - `FX_Battle_Spell_CerebralBloodstorm.prefab`
  - `low_FX_Battle_Spell_CerebralBloodstorm.prefab`

#### Character and Object Animations

- **Maize Walker:**
  - Updated the normal and *low-quality* prefabs to fix the halo rotation.
  - Fixed the shader used to render `mmw_face`, resolving the face visibility issue.
- **Crafting Hammer:** Fixed the animation that plays when crafting a card.
- **Characters:** Fixed animations to match the clips available in the following characters' prefabs:
  - Ghost Jake
  - Doctor Finn
  - Pajama Finn

#### User Interface (UI)

- **Splash Screens:** Fixed the width of the splash screens displayed when launching the game.
- **Star Banner:** Adjusted its exit position to ensure it completely disappears off-screen.

### 4. Audio and Sound Effects

- **Fionna & Cake Map:**
  - Added music to the normal and *low-quality* map prefabs.
  - A different music track now plays when entering the Fionna & Cake map.
- **Battle Jukebox:**
  - Stops the previous track before starting a new one, fixing playback issues related to BerryBones, SnowBerry, and Princess Bubblegum.
  - Fixed the issue that prevented Bubblegum's music from playing correctly.
  - Fixed music playback so that it works across all quests.
- **New sound effects:** Added sound effects for Fionna and Marshall Lee.

### 5. Quest and Side Quest Fixes

- **Quest 24 – Fionna & Cake:**
  - Fixed the `CharacterID` of `Leader_Gunter_FC` in `db_Leaders.json`.
  - Fixed the `KeyNotFoundException` error.
  - Fixed Gunter's animation reference.
- **Locked Quest Notification:**
  - Added an alternative lookup for the `ShowLockedErrorButtonTween` tween in `CWMapTap.cs` when the reference is not assigned.
  - Added error logs if the resource cannot be found.
- **Side Quests:**
  - Removed the oversized `BoxCollider` from the `SideQuestButton` in the normal and *low-quality* prefabs, preventing accidental clicks outside the button's area.
  - Fixed animation paths.
  - Optimized `SideQuestManager.cs` to prevent exceptions when battles end.

### 6. Events, Seasonal Decorations, and Redeem Codes

- **Recurring yearly events:**
  - Added support for yearly events in `ScheduleData.cs`.
  - Implemented the reading of `repeatAnnually` in `ScheduleDataManager.cs`.
  - Halloween and Christmas events now activate automatically every year.
- **Decorations and rewards:**
  - Enabled Halloween and Christmas decorations, including the menu, arena, table, and chair.
  - Enabled the daily reward calendar.
- **Redeem codes:**
  - Enabled the existing redeem codes in the game.
  - Activated the codes `DRKUNGFU`, `UND3RPANT5`, and `GHOST DOG`.
  - Added the new code `GHOSTNINJA`.
