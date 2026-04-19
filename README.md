# AeroBeat Input Driver - Keyboards

This is the official Input driver for AeroBeat's Keyboard support.

Input Drivers bridge hardware (Webcams, VR Controllers, Smart Watches) to the AeroBeat Core contracts.

## 📋 Repository Details

*   **Type:** Input Driver
*   **License:** **Mozilla Public License 2.0 (MPL 2.0)**
*   **Dependencies:**
    *   `aerobeat-core` (Required)
    *   `aerobeat-vendor-*` (Allowed)

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

That installs the pinned `aerobeat-core` foundation plus GUT into `.testbed/addons/`.

### Open the workbench

From the repo root:

```bash
godot --editor --path .testbed
```

Use this `.testbed/` project as the canonical direct-development and bugfinding surface for input-driver work.

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
- The manifest pins `aerobeat-core` to `v0.1.0` and GUT to `main`.
- Repo-local unit tests live under `.testbed/tests/`; the workbench now uses a committed `.testbed/src -> ../src` bridge instead of `setup_dev.py` runtime setup.
- The current package shape is consumed from the repo root (`subfolder: "/"`) for downstream installs.
