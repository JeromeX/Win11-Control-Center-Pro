<div align="center">
  <img src="src/Win11ControlCenter/Assets/Win11ControlCenter.png" alt="Win11 Control Center Pro icon" width="112" />
  <h1>Win11 Control Center Pro</h1>
  <p><strong>A practical control center for Windows 11 app management, privacy, tweaks, cleanup, and maintenance.</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Platform-Windows%2011-0078D4?logo=windows11&logoColor=white" alt="Platform: Windows 11" />
    <img src="https://img.shields.io/badge/Architecture-x64-555555" alt="Architecture: x64" />
    <img src="https://img.shields.io/badge/.NET-10-512BD4?logo=dotnet&logoColor=white" alt=".NET 10" />
    <img src="https://img.shields.io/badge/UI-WPF-5C2D91" alt="WPF" />
    <img src="https://img.shields.io/badge/Version-2.0.25-16A34A" alt="Version 2.0.25" />
    <img src="https://img.shields.io/badge/Language-English%20(US)-64748B" alt="English US" />
  </p>
  <p><a href="README.de.md">German project overview</a> · <a href="docs/FEATURES.md">Features</a> · <a href="docs/BUILD.md">Build guide</a> · <a href="docs/SAFETY-AND-DATA.md">Safety &amp; data</a></p>
</div>

---

## Overview

**Win11 Control Center Pro** is a Windows 11 desktop utility that brings common system-management tasks into one WPF application. It provides separate workspaces for reviewing Windows app packages and classic desktop software, inspecting system information, applying selected Windows and privacy settings, analysing cleanup targets, and managing supported configuration backups.

The application is built with **C#, WPF, and .NET 10**. The current source package is **version 2.0.25 – English (United States)**.

> **Important:** This is a system-management utility. It requests administrator privileges and can change Windows settings, remove selected applications, and delete selected cache or temporary files. Review every selection before confirming an operation. Read [Safety & Data](docs/SAFETY-AND-DATA.md) before using system-changing features.

## Main workspaces

| Workspace | What it provides |
|---|---|
| **Overview** | Hardware and Windows information, live CPU and memory indicators, disk and network status, security indicators, and quick actions. |
| **Remove Apps** | Review supported AppX/MSIX packages by exact package identity and selected removal scope. |
| **Install Apps** | Install catalogued software through the selected Microsoft Store or WinGet source. |
| **Installed Programs** | Review classic Win32/MSI entries registered with Windows, launch their publisher-provided uninstallers, and inspect possible leftovers. |
| **Windows Tweaks** | Browse categorized Windows adjustments, descriptions, impact notes, and recommendations. |
| **Privacy** | Review privacy-related controls, including advertising ID, diagnostics preferences, app permissions, feedback, and activity-related settings. |
| **System Cleanup** | Analyse selected cleanup areas before deletion; choose categories such as temporary files, thumbnails, browser caches, and optional browser cookies or history. |
| **History & Recovery** | Review activity logs and registry snapshots created by supported tweak and privacy operations; restore supported saved values. |

See [the detailed feature list](docs/FEATURES.md) for scope and limitations.

## Interface and operation highlights

- Collapsible navigation and responsive dashboard/cleanup cards.
- Live system indicators refreshed by the application.
- Separate handling for Windows app packages and classic desktop programs.
- Search and category filtering across app, tweak, and privacy catalogs.
- Explicit review and confirmation before selected changes are applied.
- Registry values are captured before supported tweak/privacy changes; supported operations include rollback handling.
- Application logs and startup diagnostics are stored in the current user's local profile.
- Close prompt with options to minimize to the system tray, exit completely, or cancel.
- Optional start-after-sign-in behaviour through an interactive Windows Task Scheduler logon task.
- Separate uninstaller application using the same product icon.

## Requirements

### Running the published application

- Windows 11, 64-bit (x64).
- The main application is published as a self-contained, single-file x64 executable by the supplied build script. It does not require a separately installed .NET runtime for the main executable.
- Windows may display a User Account Control (UAC) prompt because the application manifest requests administrator privileges.

### Building from source

- Windows 11 x64.
- .NET 10 SDK.
- .NET 10 Desktop Runtime x64 for running the compact, framework-dependent uninstaller.
- PowerShell on Windows.

The project targets `net10.0-windows` and uses WPF. A native Windows build is required; this WPF application is not intended to run on Linux or macOS.

## Build from source

### Option A: Build and install on your Windows account

The root-level `Build-Win11ControlCenter.ps1` is the project's **build-and-install script**. It performs source preflight checks, publishes the application and uninstaller, installs them into the current user's profile, registers Start Menu and uninstall entries, and optionally creates a desktop shortcut.

1. Download or clone this repository.
2. Extract the complete repository into a normal local folder.
3. Install the .NET 10 SDK and .NET 10 Desktop Runtime x64.
4. Open PowerShell in the repository root.
5. Run:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Build-Win11ControlCenter.ps1
```

Optional switches:

```powershell
# Do not create a desktop shortcut
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Build-Win11ControlCenter.ps1 -SkipDesktopShortcut

# Do not show the final prompt to launch the application
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Build-Win11ControlCenter.ps1 -NoLaunch
```

The script installs to `%LOCALAPPDATA%\Programs\Win11ControlCenter`. It may replace the existing application executable after creating a timestamped copy in `%LOCALAPPDATA%\Win11ControlCenter\BuildBackups`. It also creates or updates the current-user uninstall registration and Start Menu shortcuts. **Do not run this script if you only want a non-installing build.**

### Option B: Publish without installing

Use these commands to create the two executables in local build folders without running the installation logic in the PowerShell script:

```powershell
# Main application: self-contained, single-file, Windows x64
 dotnet publish .\src\Win11ControlCenter\Win11ControlCenter.csproj `
   --configuration Release `
   --runtime win-x64 `
   --self-contained true `
   --output .\artifacts\main `
   -p:PublishSingleFile=true `
   -p:IncludeNativeLibrariesForSelfExtract=true `
   -p:EnableCompressionInSingleFile=true `
   -p:DebugType=None `
   -p:DebugSymbols=false

# Uninstaller: separate application; requires .NET 10 Desktop Runtime x64
 dotnet publish .\src\Win11ControlCenterUninstaller\Win11ControlCenterUninstaller.csproj `
   --configuration Release `
   --runtime win-x64 `
   --self-contained false `
   --output .\artifacts\uninstaller `
   -p:PublishSingleFile=true `
   -p:IncludeNativeLibrariesForSelfExtract=false `
   -p:DebugType=None `
   -p:DebugSymbols=false
```

The commands above are also represented in the GitHub Actions workflow under `.github/workflows/windows-build.yml`. The workflow compiles and uploads build artifacts; it does **not** install the application on a user's PC.

## Installation and startup behaviour

The supplied installation script places the executables in the current user's local programs folder and registers Start Menu and Windows uninstall entries. A desktop shortcut is created unless `-SkipDesktopShortcut` is used.

The optional **Start with Windows** control creates an interactive logon task for the current user. When configured, the application is started after sign-in in the system tray. This is a Task Scheduler logon task, **not a Windows service**.

The main application and uninstaller are separate WPF projects and separate executables:

- `Win11ControlCenter.exe` — self-contained main application.
- `Win11ControlCenterUninstaller.exe` — compact, framework-dependent uninstaller; requires .NET 10 Desktop Runtime x64.

The uninstaller removes the app's startup task, shortcuts, uninstall registration, and application install directory. The implementation intentionally retains the user's data folder `%LOCALAPPDATA%\Win11ControlCenter`, including backups and logs.

## Data locations

The application stores its own user data under:

```text
%LOCALAPPDATA%\Win11ControlCenter\
├── Backups\   # Supported registry/configuration snapshots and related exports
└── Logs\      # Application log and startup diagnostics
```

The application may also interact with Windows-managed stores, the Windows registry, installed package registrations, Task Scheduler, and external package sources when the corresponding functions are used. See [Safety & Data](docs/SAFETY-AND-DATA.md).

## Known boundaries

- Registry snapshots are **not** full system images and do not back up personal files.
- Restoring a snapshot covers the supported values recorded by the application; it does not guarantee that every Windows or third-party side effect can be reversed.
- Removing an AppX/MSIX package or a classic desktop application can affect associated functionality or user data. Reinstallation may depend on the original publisher or package source.
- Browser cookies, sessions, and history are optional cleanup targets. Selecting them can sign users out or remove local browsing records.
- Some Windows changes take effect only after restarting File Explorer, signing out, or restarting Windows.
- Native Windows dialogs and output from external tools may appear in the language configured in Windows rather than English.
- Windows Security, UAC, and protected operating-system components remain subject to Windows policy and permissions.

## Repository layout

```text
.
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── workflows/windows-build.yml
├── docs/
│   ├── BUILD.md
│   ├── FEATURES.md
│   ├── GITHUB-METADATA.md
│   └── SAFETY-AND-DATA.md
├── src/
│   ├── Win11ControlCenter/
│   └── Win11ControlCenterUninstaller/
├── Build-Win11ControlCenter.ps1
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE-NOTICE.md
├── README.md
├── README.de.md
├── README-EN.md
├── SECURITY.md
└── SUPPORT.md
```

## Contributing and security

Bug reports and carefully scoped feature requests are welcome. Please do not publish personal data, logs containing usernames or machine details, or security vulnerabilities in public issues. Read [Contributing](CONTRIBUTING.md) and [Security](SECURITY.md) first.

## License and ownership

No open-source license is included in this repository at this time. The source is publicly viewable, but that does not grant permission to reuse, modify, redistribute, or publish derivative builds. See [LICENSE-NOTICE.md](LICENSE-NOTICE.md). A license should only be added after the project owner has selected and approved its terms.

## Disclaimer

Windows is a trademark of Microsoft Corporation. Win11 Control Center Pro is an independent project and is not affiliated with, endorsed by, or sponsored by Microsoft. All Windows product names and marks belong to their respective owners.

---

<p align="center"><sub>Win11 Control Center Pro 2.0.25 · English (United States) · © 2026 Malte Speck</sub></p>
