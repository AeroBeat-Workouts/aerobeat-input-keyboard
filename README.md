# AeroBeat Input Driver - Keyboard

🚧 **Future / Deprioritized Support**

This repo preserves AeroBeat's keyboard input driver as a **future support** path.
For the locked AeroBeat v1 product slice, **official gameplay input is camera-first**, so this package should not be read as current official gameplay support.

Today this repo is mainly useful for:

- debug and tooling experiments
- future keyboard-input exploration
- maintaining the package boundary for later work without implying v1 parity

Input Drivers bridge hardware to shared AeroBeat input contracts, but this specific driver is intentionally outside the current official gameplay path.

## 📋 Repository Details

- **Type:** Input Driver
- **Current Product Status:** Future / deprioritized keyboard support
- **License:** **Mozilla Public License 2.0 (MPL 2.0)**
- **Dependencies:**
  - `aerobeat-core` (current transition-era workbench foundation)
  - `aerobeat-vendor-*` (allowed)

## GodotEnv development flow

This repo uses the AeroBeat GodotEnv package convention.

- Canonical dev/test manifest: `.testbed/addons.jsonc`
- Installed dev/test addons: `.testbed/addons/`
- GodotEnv cache: `.testbed/.addons/`
- Hidden workbench project: `.testbed/project.godot`
- Repo-local unit tests: `.testbed/tests/`

The repo root remains the package/published boundary for downstream consumers. Day-to-day development, debugging, and validation happen from the hidden `.testbed/` workbench using the pinned OpenClaw toolchain: Godot `4.6.2 stable standard`.

### Restore dev/test dependencies

From the repo root:

```bash
cd .testbed
godotenv addons install
```

That restores this repo's current dev/test manifest into `.testbed/addons/`. The manifest still reflects the lightweight workbench needed to keep this future/debug package testable; it should not be mistaken for official v1 gameplay scope.

### Open the workbench

From the repo root:

```bash
godot --editor --path .testbed
```

Use this `.testbed/` project as the canonical direct-development and bugfinding surface for future keyboard-driver work.

### Import smoke check

From the repo root:

```bash
godot --headless --path .testbed --import
```

### Run unit tests

From the repo root:

```bash
godot --headless --path .testbed --script addons/gut/gut_cmdln.gd \
  -gdir=res://tests \
  -ginclude_subdirs \
  -gexit
```

### Validation notes

- `.testbed/addons.jsonc` is the committed dev/test dependency contract.
- The current workbench still pins the transition-era `aerobeat-core` package key at `v0.1.0` alongside GUT `main`; this is acceptable for the present light truth pass because the repo is future/deprioritized rather than an active v1 gameplay path.
- Repo-local unit tests live under `.testbed/tests/`.
- The current package shape is consumed from the repo root (`subfolder: "/"`) for downstream installs.

## Scope note

If AeroBeat resumes official non-camera gameplay expansion later, this repo can be upgraded then. Until that happens, keep keyboard support framed as future/debug/tooling work rather than current v1 gameplay input.
