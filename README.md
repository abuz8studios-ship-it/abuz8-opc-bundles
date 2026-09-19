# OpenClaw Desktop — OPC-1

A click-to-run Windows desktop shell for [OpenClaw](https://github.com/openclaw/openclaw).
Double-click an installer, pick a model, press Start, chat. No Node, no Python, no
terminal.

This repository is **an overlay, not a fork.** It holds only the files that sit on top of
upstream OpenClaw — an Electron shell, a self-healing doctor, a model panel, and a brain
discovery lane. Upstream is consumed as-is and pinned; none of it is copied here.

It is designed to be added to a project as a **git submodule**:

```bash
git submodule add https://github.com/abuz8studios-ship-it/abuz8-opc-bundles.git desktop/opc-1
```

See [integration/SUBMODULE.md](integration/SUBMODULE.md) for the full wiring.

## What the overlay adds

| File | What it does |
| --- | --- |
| `desktop/electron-main.cjs` | Electron main process: native window, bundle-local gateway, per-user profile, boot doctor hook |
| `desktop/abuz8-doctor.cjs` | Boot self-heal. Restores a damaged workspace from a sealed template vault before the gateway starts |
| `desktop/abuz8-body-vault/` | The sealed templates the doctor restores from (`SOUL.md`, `IDENTITY.md`, `AGENTS.md`, …) |
| `desktop/abuz8-models.cjs` + `.html` | Model panel: scans local GGUFs, one-click download, engine start/stop, GPU layers, low-RAM mode |
| `desktop/models-registry.cjs` | Normalized adapter/model selection persisted to the user profile |
| `desktop/brain-discover.cjs` | Finds already-running local inference servers and binds them as providers |
| `desktop/abuz8-daemon-worker.cjs` | Background worker lane |
| `desktop/voice-pack.json` | Offline voice bundle manifest |

Roughly 180 KB of overlay. Everything else at runtime is upstream OpenClaw.

## Install (end user)

Binaries are **GitHub Release assets, never Git objects.** Grab them from
[Releases](https://github.com/abuz8studios-ship-it/abuz8-opc-bundles/releases):

- **Installer** — `OpenClaw-Desktop-OPC-1-Setup-1.2.2.exe` (739 MB: app + Vulkan/CPU + CUDA engines)
- **Portable** — `Zait-OPC-1-Portable-1.2.2.exe` (181 MB, one file, self-extracts on first run)

Or fetch and verify by checksum:

```powershell
./integration/install.ps1
```

Every asset's SHA256 is in [`release/manifest.json`](release/manifest.json), and the
acceptance run that produced them is in [`release/SMOKE_RECEIPT-1.2.2.json`](release/SMOKE_RECEIPT-1.2.2.json).

## Honest state

- Windows 10/11 x64 only. macOS and Linux are **not built** — that is a statement of fact,
  not a promise that the `.exe` runs elsewhere.
- Unsigned build: SmartScreen will say "More info → Run anyway".
- Works fully offline once a model is downloaded.
- In-app one-click voice install needs a published download URL that does not exist yet.
  Text chat, tools, browser and desktop control all work now.
- Known warts tracked in [`integration/SUBMODULE.md`](integration/SUBMODULE.md#known-warts).

## Upstream

Pinned to OpenClaw `2026.9.2`. See [UPSTREAM.md](UPSTREAM.md) for the boundary and the
update procedure.

Licensed MIT, same as upstream. Built by ABUZ8 LLC.
