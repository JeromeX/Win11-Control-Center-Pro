# Changelog

Changes are listed for the source packages included in this repository. This file is not a guarantee that every feature has passed runtime testing on every Windows configuration.

## [2.0.25] – English Edition

### Added / included

- English (United States) interface localization for application-owned pages, catalogues, dialogs, prompts, tray text, diagnostics, and uninstaller.
- Live overview indicators for CPU, memory, storage/disk activity, and network status.
- Separate workspaces for Windows app packages and classic desktop programs.
- Searchable Windows tweak and privacy catalogues with descriptions, recommendations, and supported registry snapshots.
- Analysis-first system cleanup with selectable categories and optional browser data cleanup.
- Drive analysis/check and media-aware optimization controls.
- Activity history, manual supported-configuration backup, and restore of recorded values.
- Collapsible navigation and responsive dashboard/cleanup layouts.
- Close prompt for system-tray minimization, complete exit, or cancellation.
- Optional start-after-sign-in through an interactive current-user Task Scheduler logon task.
- Separate uninstaller WPF project and executable using the shared product icon.
- Uninstaller retains the user's `%LOCALAPPDATA%\Win11ControlCenter` data folder containing backups and logs.
- Build preflight checks for project structure, key source conditions, version alignment, and English-language content.

### Packaging / runtime notes

- Main application is published as a self-contained Windows x64 single-file executable.
- Uninstaller is published as a framework-dependent Windows x64 single-file executable and requires the .NET 10 Desktop Runtime x64.
- The `EN-R2` source package uses a flat archive layout so the build script, language metadata, and source folders are at the repository root.

### Verification status

The included localization report records static checks performed on the source package. A native Windows 11 x64 build and runtime test must still be performed before publishing a release as verified.
