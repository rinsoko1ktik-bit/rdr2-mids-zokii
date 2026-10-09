# Zokii RDR2 PRX — GitHub Actions starter

This is a **starter plugin project** intended to build on GitHub Actions so you can manage it from your phone. The current source is only a minimal GoldHEN plugin entry point; it does **not** modify Red Dead Redemption 2, patch memory, or implement gameplay mods yet.

## What the uploaded Orbx archive tells us

The supplied `Orbx1.4.7z` is an **Orbx Engine v1.4 package for GTA V**, not an RDR2 plugin source project. Its `Instructions.txt` says to place the `orbx` data folder under `/data/`, put `orbx.prx` under `/data/GoldHEN/plugins`, and configure `plugins.ini` for GTA V title IDs `CUSA00419` and `CUSA00411`. Those instructions are specific to that GTA V package and should not be copied as RDR2 installation instructions.

See `reference/ORBX_REFERENCE_NOTES.md` for the compatibility notes.

## Build from your phone

1. Create a new GitHub repository (for example `Zokii-RDR2-PRX`).
2. Upload the **contents** of this ZIP to the repository root (not the ZIP file itself).
3. Open **Actions** and enable workflows if GitHub asks.
4. Select **Build PS4 PRX**, press **Run workflow**, and wait for the job to finish.
5. Open the completed run and download the `Zokii-RDR2-PRX-artifact` artifact. It should contain `zokii_rdr2.prx` if the build succeeds.

The workflow uses the OpenOrbis toolchain action and fetches the GoldHEN Plugins SDK during the build. GitHub Actions is doing the compiling; Termux is only needed to download/unpack or edit files if you prefer.

## Important compatibility note

A `.prx` extension alone does not make a plugin compatible with a particular game. A working RDR2 mod needs a verified RDR2-compatible plugin entry point, the correct game/title build, and game-specific logic. This starter deliberately contains no guessed memory offsets or GTA V patches. Do not load a test plugin on your console until its compatibility has been verified; keep a backup of configuration files.
