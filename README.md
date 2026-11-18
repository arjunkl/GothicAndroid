# GothicAndroid

**A free, open-source Android build of OpenGothic, focused on Gothic II.**

Bring your own Gothic II: Night of the Raven / Gold installation and play with touch controls designed for phones and tablets.

GothicAndroid is an independent project based on **OpenGothic** and **OpenGothic-Android**. It is not an official Gothic release. No game files are included.

## Features

- **One ARM64 APK for Mali and Snapdragon/Adreno devices**, with runtime GPU-specific handling.
- Context-sensitive touch controls with independently created pewter-style glyphs.
- **Customizable controls:** long-press the pause button to open the layout editor, move and resize controls, or restore defaults. A short tap still opens the game menu.
- **30, 60, 90 and 120 FPS caps.**
- **Native, 0.67× and 0.5× rendering scales.**
- Layout adapted to the actual rendering surface and device safe areas.
- Persistent performance settings and control layouts.
- Folder, file and ZIP importing through Android’s file picker.
- Separate installation and save handling for optional supported games.

Choosing a frame-rate cap sets a limit, not a performance guarantee. Your hardware, Android’s display policy and thermal conditions determine the frame rate you actually get.

## Requirements

- A 64-bit ARM Android device with a compatible Vulkan driver.
- Your own legitimately acquired Gothic II: Night of the Raven / Gold game data.
- Enough storage for the imported installation and at least 512 MiB of additional free space.

ZIP importing also temporarily needs space for the compressed archive. Selecting an existing game folder is preferable when storage is tight.

Gothic I and Archolos are available as **optional experimental choices**. They are not the primary compatibility target of this preview.

## Getting started

1. Install the ARM64 APK.
2. Open **GothicAndroid**.
3. Tap **Import Gothic II game files**.
4. Choose your complete game folder, select the required files, or use the optional ZIP importer.
5. Wait for importing to finish, then select **Play**.

The importer searches nested folders and handles common filename-case differences. You do not need to rename an outer ZIP folder to a specific name.

Missing files, conflicting installations and unsupported layouts are reported rather than silently guessed. Existing installations and saves are not overwritten.

On Android 8 and newer, ZIP support includes Store, Deflate, BZip2 and Zstandard. Android 7 supports Store and Deflate. Encrypted archives and excessively large Zstandard windows are unsupported.

Successful importing confirms the detected layout and file checks, not that every part of a particular installation will work perfectly.

## Controls

The action button changes with context, such as interacting, talking or fighting. Dedicated controls cover movement, camera look, jumping, walking, drawing weapons, inventory and journal access.

**Hold the pause glyph to edit the touch layout.** Reposition controls, change their size and save your arrangement. Use Reset to return to the default layout.

## Testing status

Earlier ARM QA builds rendered the opening Xardas scene on:

| Device | GPU |
|---|---|
| Google Pixel 9 | Mali-G715 |
| Samsung Galaxy A54 | Mali-G68 |
| Samsung Galaxy S23 Ultra | Adreno 740 |

At a 30 FPS cap and half resolution, short opening-scene measurements were approximately **30, 24 and 30 FPS**, respectively. These are not sustained benchmarks or measurements of every subsequent build.

The actual ARM 0.16 build also imported the original game archive and rendered the tower, dialogue and gameplay HUD in **MuMu Android 15**. The owner tested the controls and reported that they seemed fine. The 0.17 preview uses that same native engine.

**BlueStacks did not pass:** it remained black during native/driver shader startup. No x86 build is substituted for ARM validation.

Automated tests cover launcher settings, real Android folder and single-file picker flows, import safeguards, Zstandard decoding, corruption rollback and native lifecycle policies.

Long sessions, every combat interaction, save/reload combinations and high-refresh behavior across all devices remain ongoing testing areas.

## Game data and saves

Game data is not provided with this project. Do not upload copyrighted game archives to issues or discussions.

Use the launcher’s save-export feature before uninstalling the app or clearing its data. Android can remove app-private saves during uninstall.

## Credits and licensing

Built on [OpenGothic](https://github.com/Try/OpenGothic) and [OpenGothic-Android](https://github.com/borsuczyna/OpenGothic-Android), with Tempest, GothicKit ZenKit/dmusic and other credited dependencies.

Preserve the included licenses and notices. The top-level MIT license does not replace dependency-specific terms, including the LGPL terms for OpenAL Soft and the FFmpeg-derived Bink implementation.

The release materials include corresponding source and ARM64 relinking instructions. Replacement UI artwork is independently authored; commercial game assets and reference screenshots are not included.

## Reporting problems

Include your device and GPU, Android version, APK version, selected performance settings and clear reproduction steps. Attach relevant logs when available, but remove account details and other personal information.

This is a preview. Compatibility and performance will vary.
