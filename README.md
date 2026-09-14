# Relayer

Relayer moves shots between the studio and your machine, and checks every file
at both ends before it calls anything delivered.

This repository holds **releases only**: the installer and the runtime. There is
no source code here, and nothing in a release carries an account or a key.

## Install on Windows

1. Go to [Releases](https://github.com/cbfx-labs/relayer/releases/latest) and
   download **`Install-Relayer.cmd`**.
2. Double-click it. It downloads the runtime, checks its SHA-256, and installs it
   for your user only. No admin rights needed.
3. Relayer opens. **Drag the `.relayerkey` file you were sent onto its window.**
   That's the whole setup.

Relayer is not code-signed yet, so Windows may show **"Windows protected your
PC"**. Click **More info**, then **Run anyway**. That's expected.

To install without the internet download, put the runtime zip and its
`.sha256` file next to `Install-Relayer.cmd` before you run it.

It installs to `%LOCALAPPDATA%\Programs\Relayer`, with a Start menu and a
Desktop shortcut. Running the installer again upgrades it, keeps the previous
version as `Relayer.previous`, and keeps you activated.

## Your key

The `.relayerkey` file is yours alone. Don't forward it or upload it anywhere.
If you think someone else has a copy, tell the studio and it will be replaced.

## Checking a download by hand

Every runtime zip has a matching `.sha256` file in the same release. In
PowerShell:

```powershell
(Get-FileHash .\Relayer_runtime_1.3.1_win32.zip -Algorithm SHA256).Hash
```

It must match the `.sha256` file exactly.

macOS and Linux builds will follow.
