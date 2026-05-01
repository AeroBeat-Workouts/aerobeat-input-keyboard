# aerobeat-input-keyboard

**Date:** 2026-05-01  
**Status:** Complete  
**Agent:** Chip 🐱‍💻

---

## Goal

Align `aerobeat-input-keyboard` with the locked AeroBeat v1 downscope so the repo truthfully presents keyboard input as future/deprioritized debug/tooling support rather than current official gameplay input.

---

## Overview

This repo is part of the AeroBeat input/platform downscope wave following the completed shell pass. The work stayed intentionally narrow: inspect the repo's obvious truth surfaces, remove stale parity claims, and keep the package testable without implying keyboard is part of the current official v1 gameplay story.

The locked docs truth from `aerobeat-docs` is that AeroBeat v1 gameplay input is camera-first, while keyboard remains future support only. This pass therefore focused on README wording, plugin metadata, the hidden testbed manifest, and a small repo-local assertion so future regressions are easier to catch.

---

## REFERENCES

| ID | Description | Path |
| --- | --- | --- |
| `REF-01` | Parent input/platform coordination plan | `/home/derrick/.openclaw/workspace/projects/openclaw-chip/.plans/2026-05-01-aerobeat-input-platform-downscope-pass.md` |
| `REF-02` | Downscoped docs source of truth | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs` |
| `REF-03` | Keyboard input docs truth | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/api/inputs/keyboard/index.md` |
| `REF-04` | Owning repo | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-input-keyboard` |

---

## Tasks

### Task 1: Audit and align repo truth

**Bead ID:** `oc-37h`  
**SubAgent:** `primary`  
**Role:** `coder`  
**References:** `REF-01`, `REF-02`, `REF-03`, `REF-04`  
**Prompt:** Claim the assigned bead, audit the repo against the downscoped AeroBeat docs truth, implement the required alignment changes, run relevant validation, commit/push to `main`, and leave concise QA handoff notes.

**Folders Created/Deleted/Modified:**
- `.plans/`
- `.testbed/tests/`

**Files Created/Deleted/Modified:**
- `README.md`
- `plugin.cfg`
- `.testbed/addons.jsonc`
- `.testbed/tests/test_example.gd`
- `.testbed/tests/test_example.gd.uid`
- `.plans/2026-05-01-input-keyboard-downscope-alignment.md`

**Status:** ✅ Complete

**Results:** Updated the repo's public truth surfaces to match the downscoped docs: README now marks keyboard as future/deprioritized support for debug/tooling/later exploration, plugin metadata explicitly says it is not official v1 gameplay input, and the testbed manifest comments now frame the hidden workbench as future/debug support instead of parity gameplay scope. Added a small GUT assertion to guard the plugin description wording. Validation required restoring hidden workbench dependencies first via `cd .testbed && godotenv addons install`; after that, `godot --headless --path .testbed --import` and `godot --headless --path .testbed --script addons/gut/gut_cmdln.gd -gdir=res://tests -ginclude_subdirs -gexit` both passed. A `.uid` file for the test script was generated during import and is included with the repo updates.

---

## Final Results

**Status:** ✅ Complete

**What We Built:** A light repo-truth pass for `aerobeat-input-keyboard` that removes stale "official keyboard support" framing and repositions the repo as future/deprioritized keyboard support for debugging, tooling, and later exploration.

**Reference Check:** Satisfied `REF-03` and broader `REF-02` downscope truth: keyboard remains future support only, while current official AeroBeat v1 gameplay input is camera-first. No deliberate deviations.

**Commits:**
- `Downscope keyboard input repo truth` (landed on `main`)

**Lessons Learned:** Even the small future-input repos benefit from a tiny automated truth assertion. The hidden testbed can drift if addons are not restored, so validation should explicitly include the `godotenv addons install` step before running GUT.

**QA Handoff Notes:**
- Verify README and `plugin.cfg` no longer imply keyboard is official v1 gameplay input.
- Confirm the repo now consistently frames keyboard as future/deprioritized debug/tooling support.
- Validation run used:
  - `cd .testbed && godotenv addons install`
  - `godot --headless --path .testbed --import`
  - `godot --headless --path .testbed --script addons/gut/gut_cmdln.gd -gdir=res://tests -ginclude_subdirs -gexit`
- Expect a generated `.testbed/tests/test_example.gd.uid` file from Godot import.

---

*Completed on 2026-05-01*
