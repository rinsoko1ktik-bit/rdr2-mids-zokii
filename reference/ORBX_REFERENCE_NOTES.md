# Orbx 1.4 archive — reference inspection

The provided `Orbx1.4.7z` contains an `Orbx Engine v1.4/orbx/gta/` directory tree and GTA V-oriented files such as `handling.meta`, `carcols.omt`, `carvariations.omt`, `weapons.meta`, and related GTA data.

Its embedded `Instructions.txt` says:

- Copy the `orbx` folder to `/data/`.
- Copy `orbx.prx` to `/data/GoldHEN/plugins`.
- Add plugin entries for title IDs `CUSA00419` and `CUSA00411` in `/data/GoldHEN/plugins.ini`.

These are instructions for that specific GTA V package. The archive does not provide RDR2 source code, RDR2 offsets, or a generic PRX SDK, so it cannot directly serve as the implementation for an RDR2 mod. This project uses it only as a reference for understanding the GoldHEN plugin deployment concept—not as code or assets to copy.
