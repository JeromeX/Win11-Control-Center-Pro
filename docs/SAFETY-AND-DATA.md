# Safety & Data

Win11 Control Center Pro includes system-management functions. Use them deliberately and review each operation before confirming it.

## Before changing Windows

- Read the description and impact information for the selected option.
- Change only settings you understand and intend to change.
- Create or retain an appropriate backup before important system changes.
- Do not remove Windows components or application packages solely because their names are unfamiliar.
- Some changes may require signing out, restarting File Explorer, or restarting Windows.

## Application removal

Removing an AppX/MSIX package or a classic desktop application can affect functionality or user data associated with that application. Reinstallation may depend on the original publisher, Microsoft Store, WinGet, or another original source. Review the package identity and removal scope before proceeding.

## System cleanup

Cleanup targets can include temporary files, thumbnails, selected caches, and optional browser data. Cookies, sessions, and history may be used to keep websites signed in or preserve browsing state. Selecting these items can sign you out or delete local browsing records. Review the selected categories before deletion.

## Registry and configuration recovery

The application's registry/configuration snapshots cover supported values recorded for supported operations. They are **not**:

- a complete Windows system image;
- a backup of personal files;
- a guarantee that every effect of Windows or third-party software can be reversed.

Keep separate backups of personal files and important system data. Restore only a snapshot whose origin and purpose you understand.

## Administrator privileges

Windows may display a User Account Control (UAC) prompt. Review the publisher and file source before approving it. Download release files only from the official repository's Releases page.

## Local application data

The application stores its logs and supported backup data under:

```text
%LOCALAPPDATA%\Win11ControlCenter\
```

Logs may contain technical details about the PC or actions performed. Review and redact personal information before sharing logs with support.

## Uninstaller behaviour

The separate uninstaller is designed to remove application files and application-related shortcuts/registration while retaining the user's backup and log data. Read its confirmation carefully. The retained data can be reviewed and removed separately after uninstalling, when no longer needed.

## External services

Some catalogue or installation functions may use Microsoft Store, WinGet, or other external package sources. Their availability, content, and terms are controlled by those providers.
