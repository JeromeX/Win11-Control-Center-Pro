# Contributing

Thank you for taking the time to report a problem or suggest an improvement.

## Before opening an issue

- Check existing issues for duplicates.
- Confirm the application version shown in the app.
- Include the Windows edition and OS build.
- Describe the exact workspace, action, and expected versus actual result.
- Include minimal reproduction steps.
- Remove usernames, device names, IP addresses, personal paths, and unrelated information from screenshots or logs.

## Bug reports

Use the **Bug report** issue template. For a crash, include the relevant excerpt from `%LOCALAPPDATA%\Win11ControlCenter\Logs\Win11ControlCenter.log` or `Startup.log`, after redacting personal information.

## Feature requests

Use the **Feature request** template. Explain the use case, expected behaviour, and any Windows-version or permission assumptions.

## Pull requests

- Keep changes focused and explain the user-visible impact.
- Preserve the `net10.0-windows` target and Windows x64 publishing behaviour unless the change explicitly updates the support matrix.
- Do not introduce destructive default actions.
- Keep package removal, registry changes, cleanup, and restore operations explicit and reviewable.
- Update the README, feature reference, safety notes, and changelog when behaviour changes.
- Run the Windows build and manually test affected features on Windows 11 x64 before requesting review.
- Do not include personal logs, machine backups, signing keys, or generated executables unless specifically required for a release.

## License note

No open-source license is currently included. Opening a pull request does not grant permission to relicense or redistribute this project. See [LICENSE-NOTICE.md](LICENSE-NOTICE.md).
