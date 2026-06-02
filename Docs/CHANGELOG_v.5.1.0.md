# Hyguns 5.1.0 Changelog

## Overview

Version `5.1.0` updates the Hyguns content pack for the new HyGuns Plugin attachment system and `WeaponSettings` format.

## Added

### Attachment Types

Added attachment type assets under `Server/HyGuns/AttachmentTypes`:

- `Scope`
- `Suppressor`
- `Magazine`

Each type defines the UI slot icon used by the attachment inventory. Scope and suppressor types are limited to one installed attachment; magazine attachments are capped by their type max count.

### Attachment Items

Added attachment items under `Server/Item/Items/Attachments`:

- `Scope_Barret50`
- `Scope_AWP`
- `Suppressor`
- `Magazine_Tier_I`
- `Magazine_Tier_II`
- `Magazine_Tier_III`

Added matching models, textures, generated icons, and creative category support for attachments.

### Weapon Visual State Models

Added attachment-driven weapon state models for Barret .50 and AWP:

- base weapon model
- scope-only model
- suppressor-only model
- scope plus suppressor model

These states are selected automatically by the plugin based on installed visual attachments.

### Attachment Slot Icons

Added attachment UI icons under `Common/UI/Custom/Attachments`:

- `scope.png`
- `suppressor.png`
- `magazine.png`

## Changed

### Weapon JSON Format

Updated weapon assets from the old HyGuns settings block to:

```json
"HyGuns": {
  "WeaponSettings": {}
}
```

### Ammo JSON Format

Updated ammo assets to use `HyGuns.AmmoSettings.SettingsModifiers`.

Numeric stat changes now use operation strings such as `+10`, `*0.75`, and `=5`.

### Barret .50

Updated `Weapon_Barret50.json` as the main example weapon for the attachment system:

- supports one `Scope` slot
- supports one `Suppressor` slot
- supports two dedicated `Magazine` slots
- supports three wildcard slots
- creates `Scope_Barret50` by default
- uses visual attachment indices to build `Scope`, `Suppressor`, and `Scope_Suppressor` state keys
- gates zoom interactions behind `Hyguns_AttachmentsInstalled`
- uses `Hyguns_PlayWeaponFireSound` so suppressors can reduce shot volume

### AWP

Updated `Weapon_AWP.json` for attachment-compatible scope and suppressor visual states.

### Sound and Language Assets

Updated server language entries for new attachment items, dynamic weapon descriptions, and attachment-related UI text.

Updated weapon/fire sound usage so compatible weapons can use attachment-aware fire sound playback.

## Fixed

- Replaced the temporary magazine test item with tiered magazine items.
- Updated attachment item ids and weapon references to the current names.
- Updated Barret .50 and AWP models/textures for state-based attachment visuals.
- Cleaned up hard-coded weapon descriptions that are now generated dynamically by the plugin tooltip system.

## Short Version

Hyguns `5.1.0` adds real attachment content: scopes, suppressors, magazines, attachment slot icons, Barret .50/AWP visual state models, default scoped weapons, and updated weapon/ammo JSON using the new `WeaponSettings` and `SettingsModifiers` format.
