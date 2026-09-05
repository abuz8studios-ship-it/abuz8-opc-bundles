# ABUZ8 OpenClaw Bundles

This fork is the public source and bundle catalog for ABUZ8's click-to-run OpenClaw desktop builds.

## Release status

**Windows x64 acceptance prerelease published:** [ABUZ8 OPC-1
1.0.0](https://github.com/abuz8studios-ship-it/abuz8-opc-bundles/releases/tag/v1.0.0-abuz8-win1).
SHA256:
`D7BC65D53256CD1B69AB8E20C703BFF96B2FA09DB153BF695714902D667DD8B8`.
The release contains no embedded GGUF model weights.

## Source-backed candidates (not released)

| Label | Provider base | Bundle location | Runtime |
| --- | --- | --- | --- |
| ABUZ8 OPC-1 / OpenClaw Desktop | ABUZ8 desktop source | `E:\ABU\02_PROJECTS\OPENCLAW_DESKTOP` | Electron shell, gateway, engine integration, skills, model catalog, and portable home |

The following trial payloads are deliberately excluded from publication because
they embed model weights or still depend on terminal launchers:

- ABUZ8 Sovereign v3.13;
- OpenClaw Portable;
- the self-extracting model bundles on `E:`.

The path above is the owner-machine source used for staging. The published
prerelease was built with an isolated writable profile; its native window
launched successfully and the bundle-local gateway reached HTTP 200.

## Product contract

OpenClaw Desktop stores user state in a writable per-user profile rather than
inside installed resources. The inference registry follows the same contract as
Hermes and persists only normalized adapter selections there.

Each finished Windows release must be:

- launched by double-clicking one installer or portable executable;
- self-contained, with its own runtime, engine, backend, frontend, and state;
- isolated from the owner's live OpenClaw gateway and credentials;
- usable without Node, Python, Git, or terminal setup on the target machine.

## Current gaps

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
