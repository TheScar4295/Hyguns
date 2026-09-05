# Hyguns 6.0.0 Changelog

## Overview

Version `6.0.0` adds the M1897 Trench Gun and real combat-state ADS flows for five pistols and the AK-47. Existing scope, durability, shotgun-ammo, and manifest assets are updated for Hytale `0.6.x` and HyGuns Plugin `6.0.0`.

## Added

### M1897 Trench Gun

Added the M1897 Trench Gun with:

- a dedicated weapon item, model, icon, attachment schema, and animation set
- first- and third-person locomotion, fire, failed-fire, reload, and melee animations
- shotgun fire/reload sounds, particles, camera effects, and shell effects
- a melee attack interaction chain in addition to normal shotgun fire

### Combat-State ADS

Added `Server/HyGuns/CombatStates/Aiming.json`. The `Aiming` state reduces projectile spread with a final `*0.5` settings modifier.

Added ADS interaction chains and animations for:

- AK-47 rifle aiming and aimed fire
- Colt Revolver
- Desert Eagle
- Five-seveN
- Glock 18
- USP-S

Added first- and third-person `Aim` and `AimShoot` animation assets for pistols and rifles, plus a dedicated `HygunsColtRevolver` animation set. Normal and aimed shots select separate animation ids while the equipped item remains the stable owner of its player animation set.

## Changed

### Weapon Interaction Assets

Moved the AK-47 and five pistol Primary/Secondary flows into reusable root interactions. Shooting now checks the active `Aiming` combat state and chooses `Shoot` or `AimShoot` without cancelling the held Secondary ADS interaction.

### Scope Zoom Format

Migrated existing weapon and scope attachment zoom definitions from distance/range fields to explicit `Steps` arrays. AWP optics use `2x`, `4x`, and `8x`; the Barret .50 scope extends through `64x`.

### Durability Assets

Added the Hytale `DurabilityLossOnHit` field to existing durable firearms and the Damage Booster, Damage Amplifier, and Projectile Splitter tiers so the plugin uses asset-defined wear.

### Platform and Manifest

Updated the pack and server compatibility to `6.0.0` / `>=0.6.0 <0.7.0`, raised the HyGuns Plugin dependency to `>=6.0.0`, and credited `pav_prokop` for the M1897 contribution.

## Fixed

- Fixed ADS fire animations snapping back to idle or starting from the wrong pose on the AK-47 and pistols.
- Fixed ADS being cancelled by the weapon stack metadata change performed after a shot. ADS `Wielding` interactions now use `OnItemChangeBehavior: "Ignore"`.
- Fixed held and automatic aimed fire by allowing Primary and Secondary roots to remain concurrent and branching each shot through the active `Aiming` state.
- Fixed the held ADS pose after Primary is released; `Aim` remains owned by the active Secondary wielding interaction while shots play `AimShoot`.
- Fixed Colt Revolver animation-set ownership with its dedicated `HygunsColtRevolver` set.
- Fixed a broken Trench Gun OGG asset and completed the missing shot sound variants.
- Fixed the standard, incendiary, and scout shotgun ammo assets and the Double Barrel weapon settings using the `Bullet` family instead of `Shell`.

## Compatibility Notes

- Requires Hytale Server `>=0.6.0 <0.7.0`.
- Requires HyGuns Plugin `>=6.0.0`.
- HyGuns Plugin also requires the separate WeaponCustomHUD plugin.
- Custom scopes must use `ZoomSettings.Steps`; the old distance and multiplier range fields are no longer used by `6.0.0`.
- For custom ammo-bearing ADS interactions, keep `PlayerAnimationsId` on the item, trigger only `ItemAnimationId` from interactions, and set `OnItemChangeBehavior` to `Ignore` on the ADS `Wielding` interaction.

## Short Version

- Added the M1897 Trench Gun with dedicated models, animations, sounds, effects, reload, and melee attack.
- Added the `Aiming` combat state with reduced projectile spread.
- Added ADS and aimed-fire animations for the AK-47 and five pistols.
- Fixed ADS snapping to idle, breaking after metadata updates, and dropping the aimed pose after Primary is released.
- Added a dedicated animation set for the Colt Revolver.
- Migrated weapon and attachment scopes to explicit magnification `Steps`.
- Added `DurabilityLossOnHit` to existing durable firearms and selected attachment tiers.
- Fixed shotgun ammo-family assignments and missing/broken M1897 shot sounds.
- Updated the pack for Hytale `0.6.x` and HyGuns Plugin `6.0.0`.

[Full changelog](FULL_CHANGELOG_URL)
