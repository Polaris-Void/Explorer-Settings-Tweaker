[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D6?logo=windows&logoColor=white)](https://github.com/Polaris-Void/Explorer-Settings-Tweaker)

English | [فارسی](README.FA.md)

# Windows File Explorer Settings Configurator

A lightweight, self-elevating Windows Batch script that applies a privacy-friendly and power-user-friendly File Explorer configuration in one click, using only native registry commands.

It sets File Explorer to open on **This PC**, turns off recent/frequent/cloud file suggestions, and enables item check boxes, file name extensions, and hidden items — then restarts Explorer so everything takes effect immediately.

---

## ✨ Features

- **🛠️ 100% Native:** Relies exclusively on built-in Windows tools (`reg`, `taskkill`, `PowerShell` for elevation) — zero third-party dependencies.
- **🔑 Auto-Elevation:** Automatically requests administrative privileges via UAC if not launched as Administrator.
- **🎯 Exact & Minimal Changes:** Writes only eight per-user (`HKCU`) values. No policy keys, no deletions, no binary `ShellState` / `Bags` / `BagMRU` edits.
- **🔒 Privacy-Oriented:** Disables *Recent files*, *Frequent folders*, and *Office.com files* in Quick Access.
- **⚡ Instant Effect:** Restarts `explorer.exe` automatically and verifies that it came back up.
- **🎨 Clean Terminal Output:** Formatted CLI interface with explicit status tags (`[ OK ]`, `[FAIL]`, `[WARNING]`) and an automatic 5-second close.
- **🛡️ Safe & Robust:** Per-value success tracking with a final summary and a fallback instruction if Explorer fails to restart.

---

## ⚙️ Applied Settings

| Tab | Option | State |
| --- | --- | --- |
| General | Open File Explorer to | **This PC** |
| General | Show recently used files | ❌ Off |
| General | Show frequently used folders | ❌ Off |
| General | Show files from Office.com | ❌ Off |
| View | Compact view | ❌ Off |
| View | Item check boxes | ✅ On |
| View | File name extensions | ✅ On |
| View | Hidden items | ✅ On |

> **Note:** The *Navigation pane* is intentionally **not** modified. Its state is stored inside a binary UI blob (`PageSpaceControlSizer`) that also holds the pane width, and touching it could affect unrelated settings. It is already enabled by default.

### Registry Values Written

| Key | Value | Data |
| --- | --- | --- |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` | `LaunchTo` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer` | `ShowRecent` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer` | `ShowFrequent` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer` | `ShowCloudFilesInQuickAccess` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` | `UseCompactMode` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` | `AutoCheckSelect` | `1` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` | `HideFileExt` | `0` |
| `HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced` | `Hidden` | `1` |

---

## 📋 System Requirements

- **Operating System:** Windows 10 / Windows 11.
- **Permissions:** Administrator privileges (handled automatically).
- **PowerShell:** Required for automatic UAC elevation.

---

## 🚀 How to Use

1. Download **`FileExplorer-Settings.bat`**.
2. Double-click the file.
3. Accept the **UAC** prompt if prompted.
4. The script applies the settings, restarts File Explorer, and closes automatically after 5 seconds.

> **Important:** Run the script while signed in to the account you want to configure. The settings are written to `HKCU`, which belongs to the account that elevates the script. If you approve the UAC prompt with a *different* administrator account, the settings are applied to that account instead.

---

## ↩️ Reverting Changes

To restore Windows defaults, change the options manually in **File Explorer → ⋯ → Options** (*General* and *View* tabs), or set the values listed above back to their Windows defaults.

---

## ⚖️ Absolute Legal Disclaimer, Waiver & Limitation of Liability

This project is licensed under the **Apache License, Version 2.0**. This disclaimer expressly supplements, expands, and reinforces **Section 7 (Disclaimer of Warranty)** and **Section 8 (Limitation of Liability)** of the Apache License 2.0, and shall control to the maximum extent permitted by applicable law.

**FOR EDUCATIONAL, RESEARCH, AND INFORMATIONAL PURPOSES ONLY. NO COMMERCIAL WARRANTY OR LIABILITY IS ASSUMED.**

### 1. Complete Disclaimer of All Warranties

To the maximum extent permitted by applicable law, the Software (including all code, documentation, data, and related materials) is provided strictly on an **"AS IS"** and **"AS AVAILABLE"** basis, without any warranties or conditions of any kind, whether express, implied, statutory, customary, or otherwise. This includes, without limitation, any warranties of merchantability, fitness for a particular purpose, non-infringement, title, security, accuracy, completeness, uninterrupted or error-free operation, or freedom from viruses or other harmful components. The author(s), copyright holder(s), maintainer(s), and contributor(s) expressly disclaim all such warranties.

### 2. Absolute Limitation of Liability

Under no circumstances and under no legal theory (whether in contract, tort — including negligence, gross negligence, and willful misconduct — strict liability, product liability, or otherwise) shall the author(s), maintainer(s), contributor(s), or copyright holder(s) be liable for any damages whatsoever, including but not limited to direct, indirect, incidental, special, consequential, exemplary, punitive, or any other damages (including loss of data, profits, revenue, business interruption, system failure, hardware damage, security breaches, personal injury, or any other loss), arising out of or related to the use, inability to use, modification, distribution, or reliance upon the Software, even if advised of the possibility of such damages and even if any remedy fails of its essential purpose.

### 3. Assumption of All Risk & User Responsibility

Any use, cloning, modification, deployment, distribution, or reliance upon this Software is undertaken entirely at the user’s sole risk and discretion. The user is exclusively and solely responsible for:

- Ensuring full compliance with all applicable local, national, and international laws, regulations, export controls, and third-party terms;
- Evaluating the suitability, security, and legality of the Software for any purpose;
- Any consequences arising from its use or misuse.

Nothing in this repository constitutes legal, financial, cybersecurity, medical, architectural, or any other form of professional advice.

### 4. Broad Indemnification

By accessing, downloading, cloning, forking, viewing, compiling, distributing, or using any part of this repository, you irrevocably agree to indemnify, defend, and hold harmless the author(s), contributor(s), and copyright holder(s) from and against any and all claims, demands, actions, proceedings, liabilities, damages, losses, costs, and expenses (including reasonable attorneys’ fees and legal costs) arising out of or related to your access, use, misuse, modification, distribution, or violation of this disclaimer or any applicable law.

### 5. Severability & Maximum Enforceability

If any provision of this disclaimer is held to be unenforceable or invalid under applicable law, such provision shall be modified to the minimum extent necessary to make it enforceable, or if modification is not possible, severed. The remaining provisions shall continue in full force and effect. This disclaimer shall be interpreted to provide the maximum protection permitted by law.

### 6. No Waiver of Non-Waivable Rights

Nothing in this disclaimer is intended to exclude or limit any liability that cannot be excluded or limited under applicable mandatory law (including liability for death or personal injury caused by negligence in jurisdictions where such exclusion is prohibited). In such cases, liability is limited to the maximum extent permitted by law.
