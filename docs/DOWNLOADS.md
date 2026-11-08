# Downloads & First Start

## Official downloads

Get the current release from the [GitHub Releases page](https://github.com/JeromeX/Win11-Control-Center-Pro/releases).

The release contains executable application files only:

| File | Purpose | Requirement |
|---|---|---|
| `Win11ControlCenter.exe` | Main Windows 11 utility | Windows 11 x64; self-contained main executable |
| `Win11ControlCenterUninstaller.exe` | Separate uninstaller utility | Windows 11 x64 and .NET 10 Desktop Runtime x64 |

No MSI package, source archive, or PowerShell build script is offered as an end-user download.

## First start

1. Download `Win11ControlCenter.exe` from the selected release.
2. Save it to a folder you control.
3. Start the executable.
4. Review the Windows User Account Control (UAC) prompt. The application requests administrator privileges for system-management operations.
5. Read the in-app descriptions and review selections before applying changes.

Windows may display a security notice for an executable downloaded from the internet. Only run files obtained from the official repository's Releases page. Check the release notes and any published SHA-256 value when one is provided.

## Uninstall

Use the separate `Win11ControlCenterUninstaller.exe` supplied with the release, if you choose to remove the application installation. It requires the .NET 10 Desktop Runtime x64. Read its confirmation carefully.

The uninstaller is designed to retain the user's backup and log data under `%LOCALAPPDATA%\Win11ControlCenter\`. If you no longer need that data, review and remove it separately after the application has been uninstalled.

## Version updates

Check the Releases page for newer versions and read the release notes before replacing an existing executable. Keep any backups you need before updating or uninstalling.
