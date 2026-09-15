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

## Install on macOS

For Apple Silicon Macs (M1 or newer) on macOS 12 or later. In Terminal:

```sh
curl -fsSL https://github.com/cbfx-labs/relayer/releases/latest/download/Install-Relayer-macos.sh | sh
```

It downloads the runtime, checks its SHA-256, and installs it for your user only
(no admin) in `~/Applications/Relayer`. Installed this way there is no
"unidentified developer" prompt. Relayer opens; **drag the `.relayerkey` file
you were sent onto its window.** Keep the `Relayer` folder together — the
`Relayer.app` inside it is a shortcut into that folder; drag it to the Dock
from there. Running the command again upgrades and keeps you activated.

## Install on Linux

For x86_64 machines running Rocky 9, Ubuntu 22.04 or newer (glibc 2.34+). In a
terminal:

```sh
curl -fsSL https://github.com/cbfx-labs/relayer/releases/latest/download/Install-Relayer-linux.sh | sh
```

It downloads the runtime, checks its SHA-256, and installs it for your user only
(no root) in `~/.local/share/cbfx-relayer`, with an entry in your applications
menu. Relayer opens; **drag the `.relayerkey` file you were sent onto its
window.** Running it again upgrades it, keeps the previous version as
`cbfx-relayer.previous`, and keeps you activated.

To install without the internet download, put `Install-Relayer-linux.sh`, the
`Relayer_runtime_*_linux-x86_64.zip` and its `.sha256` in one folder and run
`sh Install-Relayer-linux.sh` there.

## Your key

The `.relayerkey` file is yours alone. Don't forward it or upload it anywhere.
If you think someone else has a copy, tell the studio and it will be replaced.

## Checking a download by hand

Every runtime zip has a matching `.sha256` file in the same release. In
PowerShell:

```powershell
(Get-FileHash .\Relayer_runtime_1.3.6_win32.zip -Algorithm SHA256).Hash
```

It must match the `.sha256` file exactly. On Linux:
`sha256sum Relayer_runtime_*_linux-x86_64.zip`; on macOS:
`shasum -a 256 Relayer_runtime_*_darwin-arm64.zip`.
