# AeroBeat Input Driver - Keyboards

This is the official Input driver for AeroBeat's Keyboard support.

Input Drivers bridge hardware (Webcams, VR Controllers, Smart Watches) to the AeroBeat Core contracts.

## 📋 Repository Details

*   **Type:** Input Driver
*   **License:** **Mozilla Public License 2.0 (MPL 2.0)**
*   **Dependencies:**
    *   `aerobeat-core` (Required)
    *   `aerobeat-vendor-*` (Allowed)

## 🚀 Getting Started

1.  **Clone your new repo:**
    ```bash
    git clone https://github.com/YourOrg/aerobeat-input-custom.git
    ```
2.  **Run Setup:**
    Initialize the testbed environment.
    ```bash
    python setup_dev.py
    ```
3.  **Open in Godot:**
    Open the hidden `.testbed/project.godot` workbench in Godot `4.6.2 stable standard`.

## 🧪 Testing

This template comes pre-configured with **GUT (Godot Unit Test)** workflows.

*   **Local Testing:** Run tests via the "GUT" panel in the Godot Editor (inside the Testbed).
*   **Requirement:** 100% Code Coverage is enforced.

## 📂 Structure

*   `src/` - The driver logic (GDScript).
*   `.testbed/tests/` - Repo-local unit tests run by the hidden testbed.
*   `.testbed/` - The hidden Godot workbench used to run/debug the driver.