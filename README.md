# EmuCoreP Runtime

[![Manifest schema](https://img.shields.io/badge/Manifest-v2-4D9EFF)](manifest.json)
[![Components](https://img.shields.io/badge/Components-SHA--256%20verified-2E7D32)](manifest.json)

EmuCoreP Runtime is the versioned component catalog used by EmuCoreP. Release
assets provide the minimal Windows compatibility stack, CPU translation layers
and graphics drivers used to start compatible PC games on ARM64 Android
devices.

## Component Catalog

| Component | Available versions | Recommended |
| --- | --- | --- |
| Root file system | 11.1 | 11.1 |
| Wine | 10.10 | 10.10 |
| Box64 | 0.3.7, 0.4.0 | 0.4.0 |
| DXVK | 1.10.3, 2.4.1, 2.6.1 Preview | 2.4.1 |
| VKD3D-Proton | 2.12, 2.14.1, 3.0b Preview | 2.14.1 |
| Mesa Turnip | 25.0.0, 26.0.3, 26.1.0 | 26.1.0 |

The recommended set is selected automatically during first-run setup. Other
versions remain available in the component manager for per-game compatibility.

## Manifest

`manifest.json` is the canonical machine-readable catalog. Every entry records:

- component type, version and release channel;
- recommended-release status;
- dependency identifiers and isolated install directory;
- compressed and unpacked sizes;
- unpacked file count and archive format;
- HTTPS release URL and SHA-256 checksum.

Manifest revisions increase monotonically. EmuCoreP rejects malformed entries,
checksum mismatches, dependency cycles, unsafe archive paths and revision
rollback.

## Release Channels

- **Stable** — validated default or compatibility release.
- **Preview** — newer upstream build available for manual selection.
- **Experimental** — isolated testing release excluded from automatic setup.

Only stable releases can be marked as recommended.

## Integrity and Provenance

Release archives retain Unix permissions and symbolic links required by the
Linux and Wine runtimes. Installation uses staged extraction and structural
validation before activation.

Source repository, pinned commit, source path, source SHA-256, transformation
and output SHA-256 are recorded in
[`metadata/provenance.json`](metadata/provenance.json). Third-party attribution
is recorded in
[`metadata/THIRD_PARTY_NOTICES.md`](metadata/THIRD_PARTY_NOTICES.md).

## Third-Party Software

- [Winlator](https://github.com/brunodev85/winlator) — LGPL-2.1
- [Wine](https://gitlab.winehq.org/wine/wine) — LGPL-2.1-or-later
- [Box64](https://github.com/ptitSeb/box64) — MIT
- [DXVK](https://github.com/doitsujin/dxvk) — Zlib
- [VKD3D-Proton](https://github.com/HansKristian-Work/vkd3d-proton) — LGPL-2.1-or-later
- [Mesa Turnip](https://gitlab.freedesktop.org/mesa/mesa) — MIT

Each component remains governed by its upstream license. The repository does
not contain Windows, commercial games, credentials or DRM circumvention tools.
