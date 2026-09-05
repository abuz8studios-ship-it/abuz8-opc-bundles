# ABUZ8 OpenClaw Bundles

This fork is the public source and bundle catalog for ABUZ8's click-to-run OpenClaw desktop builds.

## Release status

**No binary release is published yet.** The repository is intentionally source
and catalog only until a clean staged payload passes the one-click acceptance
gate in `docs/ABUZ8_BUILD_AND_RELEASE.md`.

## Source-backed candidates (not released)

| Label | Provider base | Bundle location | Runtime |
| --- | --- | --- | --- |
| ABUZ8 OPC-1 / OpenClaw Desktop | ABUZ8 desktop source | `E:\ABU\02_PROJECTS\OPENCLAW_DESKTOP` | Electron shell, gateway, engine integration, skills, model catalog, and portable home |

The following trial payloads are deliberately excluded from publication because
they embed model weights or still depend on terminal launchers:

- ABUZ8 Sovereign v3.13;
- OpenClaw Portable;
- the self-extracting model bundles on `E:`.

The path above is the owner-machine source used for staging. It is not a
downloadable release until a clean profile is generated and the acceptance gate
passes.

## Product contract

The current OpenClaw Desktop staging tree contains a SQLite WAL in its bundled
home. That user state must be removed and replaced with a fresh profile before
release.

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
