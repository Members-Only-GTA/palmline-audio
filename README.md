# Palmline Audio

This repository stores **external audio assets** for **Palmline**.

It allows audio to be maintained, versioned, and updated independently from the main Palmline codebase.

---

## Supported Audio Types

Currently supported audio includes:

- **Cutscene audio** (from the `cutscene/` directory)
- **Sound effects (SFX)** (from the `sfx` directory)

---

## Repository Structure

```text
palmline-audio/
├─ cutscene/
│  └─ Track_001.ogg
└─ sfx/
   └─ GENRL/
      └─ Bank_001/
         └─ sound_001.wav
```

---

## Adding Sound Effects (SFX)

When adding new sound effects, follow the steps below carefully.

### 1. Create an audio type folder

If one does not already exist, create a new folder inside the `sfx` directory.

**Examples:**
- `GENRL`
- `SPC_EA`
- `SPC_PA`

```text
sfx/
└─ GENRL/
```

---

### 2. Match the SAAT export structure

All SFX files **must mirror the folder structure** produced by a standard **SAAT export**.

**Required format:**

```text
sfx/
└─ <AUDIO_TYPE>/
   └─ Bank_<###>/
      └─ sound_<###>.wav
```

**Concrete example:**

```text
sfx/
└─ GENRL/
   └─ Bank_001/
      └─ sound_001.wav
```

> ✅ File numbers should match SAAT expectations  
> ✅ Folder names and casing must be exact  

---

## Adding Cutscene Audio

Cutscene audio is placed directly in the `cutscene` directory.

### Requirements

- Format: `.ogg`
- Naming convention: `Track_<###>.ogg`

**Example:**

```text
cutscene/
└─ Track_012.ogg
```

---

## Naming & Validation Rules

To ensure compatibility with the import pipeline:

- Folder names are **case-sensitive**
- File names must follow the exact conventions shown above
- Audio that does not match the expected structure **will be skipped**
- Do not rename files after committing unless the corresponding import data is updated

---

## Notes

- This repository is intended to reflect **exact SAAT-compatible layouts**
- Audio should be validated locally before committing
- Keep commits focused (for example: one audio type or feature per commit)

---

## License / Usage

This repository is intended for use with the **Palmline** project only.

Please ensure you have the right to distribute any audio content you add.
