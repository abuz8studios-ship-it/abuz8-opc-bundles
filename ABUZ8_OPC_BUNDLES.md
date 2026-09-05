# ABUZ8 OpenClaw Bundles

This fork is the public source and bundle catalog for ABUZ8's click-to-run OpenClaw desktop builds.

## Release status

**No binary release is published yet.** The repository is intentionally source
and catalog only until a clean staged payload passes the one-click acceptance
gate in `docs/ABUZ8_BUILD_AND_RELEASE.md`.

## Verified Windows bundle sources

| Label | Provider base | Bundle location | Runtime |
| --- | --- | --- | --- |
| ABUZ8 Sovereign | OpenClaw v3.13 fork | `G:\ABUZ8 opecla-Sovereign-9B\ABUZ8_SOVEREIGN` | Embedded Node, Electron shell, llama-server, local model, portable `home` |
| OpenClaw Portable | OpenClaw 2026.6.8 | `G:\ABUZ8-Agents\OpenClaw-Portable` | Embedded runtime, gateway, brain, skills, portable state |
| ABUZ8 OPC-1 | OpenClaw 2026.9.1 | `C:\ABUZ8-Agents\ABUZ8-OPC-1` | Native Windows Electron shell, gateway, local model services, isolated state |
| OpenClaw Desktop | ABUZ8 desktop source | `E:\ABU\02_PROJECTS\OPENCLAW_DESKTOP` | Electron shell with bundled runtime, engine, gateway, and portable home |

The paths above are the verified owner-machine locations used to build and test the
bundles. They are not required at runtime after a release package is assembled.

## Product contract

The GUI-complete source candidates are `ABUZ8 Sovereign` and `ABUZ8 OPC-1`. The
OpenClaw Portable launcher is excluded because it opens a terminal. The current
OpenClaw Desktop staging tree also contains a SQLite WAL in its bundled home;
that user state must be removed and replaced with a fresh profile before release.

Each finished Windows release must be:

- launched by double-clicking one installer or portable executable;
- self-contained, with its own runtime, engine, backend, frontend, and state;
- isolated from the owner's live OpenClaw gateway and credentials;
- usable without Node, Python, Git, or terminal setup on the target machine.

## Current gaps

The portable OpenClaw launcher still uses `runtime\node\node.exe` to start the
chat terminal. It must be replaced by, or chained into, the bundled Electron
desktop shell before that build is eligible.

The OpenClaw Desktop candidate needs a clean-profile rebuild and a clean-machine
test covering onboarding, provider/model selection, memory persistence, tools,
skills, voice/vision settings, GPU allocation, and upstream update controls.

## What is not committed

Executable payloads, model weights, live state, OAuth credentials, tokens, and
machine-specific configuration are intentionally excluded from Git. They belong in
versioned GitHub Release assets or a separate private delivery channel. Never commit
`home`, `.openclaw` state, `.env`, token files, model weights, or local databases.

OpenClaw remains available under its upstream license. The ABUZ8 desktop overlay,
packaging, branding, and integration work are separate from the upstream project.
