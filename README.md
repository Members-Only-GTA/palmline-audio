# Palmline Audio

This repository stores **external audio assets** for **Palmline**.

It allows audio to be maintained, versioned, and updated independently from the main Palmline codebase.

---

## Supported Audio Types

Currently supported audio includes:

- **Cutscene audio** (from the `cutscene/` directory)
- **Sound effects (SFX)** (from the `sfx` directory)
- **Radio stations** (from the `radio/` directory: one stream per station, the station logos, the radio bulletins)

---

## Repository Structure

```text
palmline-audio/
├─ cutscene/
│  └─ Track_001.ogg
├─ radio/
│  ├─ wildstyle.ogg
│  ├─ announce_bclosed.ogg
│  └─ logos/
│     └─ wildstyle.png
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

## Adding a Radio Station

The radio is Palmline's own (Vice City's system on San Andreas' engine, see `.asi/PL.Core/README.md`
in the main repo): every station is one continuous stream that loops and resumes where it was. The
stations themselves are listed in the main repo's `data/radio.dat`; this repo holds their audio and logos.

### Requirements

- Stream: `radio/<key>.ogg` — OGG Vorbis, **stereo** (a mono track plays at double speed), any length
  (the VC stations are about an hour). `<key>` is the first column of the station's `radio.dat` line.
- Logo: `radio/logos/<sprite>.png` — any size with transparency; it is fitted into the 256 x 256 square
  the Audio Setup row draws. `<sprite>` is the `sprite` column of the station's `radio.dat` line
  (`mp3.png` is the user track player's).
- Bulletins: `radio/announce_bclosed.ogg` / `radio/announce_bopen.ogg`, the two Vice City radio
  news pieces, stereo OGG as well.

To add a station: the `.ogg` and the `.png` here, a line in `data/radio.dat` on a free stream pack,
the name under a GXT key. To remove one: delete its `radio.dat` line (the files here may stay).
`import_audio.cmd` packs the streams into the game's `audio/streams/` packs and the logos into
`models/fronten1.txd`; the VC stations, bulletins, logos and retune sounds were pulled out of a
Vice City install with `.audio/import_vc_radio.py`.

**Example:**

```text
radio/
├─ vcur.ogg
└─ logos/
   └─ vcur.png
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
