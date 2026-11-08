# Downloads & erster Start

## Offizielle Downloads

Die aktuelle Version steht auf der Seite [GitHub Releases](https://github.com/JeromeX/Win11-Control-Center-Pro/releases) bereit.

Der Release enthält ausschließlich ausführbare Anwendungsdateien:

| Datei | Zweck | Voraussetzung |
|---|---|---|
| `Win11ControlCenter.exe` | Hauptanwendung für Windows 11 | Windows 11 x64; Haupt-EXE ist selbstständig lauffähig |
| `Win11ControlCenterUninstaller.exe` | Separates Deinstallationsprogramm | Windows 11 x64 und .NET 10 Desktop Runtime x64 |

Es werden kein MSI-Paket, kein Quellcode-Archiv und kein PowerShell-Buildskript als Endanwender-Download angeboten.

## Erster Start

1. `Win11ControlCenter.exe` aus dem gewünschten Release herunterladen.
2. Die Datei in einem Ordner speichern, auf den du Zugriff hast.
3. Die EXE starten.
4. Den Hinweis der Windows-Benutzerkontensteuerung (UAC) prüfen. Für Systemverwaltungsfunktionen fordert die Anwendung Administratorrechte an.
5. Die Beschreibungen in der Anwendung lesen und jede Auswahl vor der Ausführung prüfen.

Windows kann bei einer aus dem Internet heruntergeladenen EXE eine Sicherheitswarnung anzeigen. Starte ausschließlich Dateien aus dem offiziellen Releases-Bereich dieses Repositorys. Prüfe außerdem die Release-Hinweise und einen veröffentlichten SHA-256-Wert, sofern vorhanden.

## Deinstallation

Verwende bei Bedarf die separate `Win11ControlCenterUninstaller.exe` aus dem Release, um die Programminstallation zu entfernen. Dafür wird die .NET 10 Desktop Runtime x64 benötigt. Lies die angezeigte Bestätigung sorgfältig.

Das Deinstallationsprogramm ist darauf ausgelegt, persönliche Sicherungs- und Protokolldaten unter `%LOCALAPPDATA%\Win11ControlCenter\` beizubehalten. Wenn diese Daten nicht mehr benötigt werden, prüfe und entferne sie nach der Deinstallation separat.

## Versionsaktualisierungen

Prüfe auf der Releases-Seite, ob eine neuere Version verfügbar ist, und lies vor dem Ersetzen einer vorhandenen EXE die Release-Hinweise. Bewahre benötigte Sicherungen vor einer Aktualisierung oder Deinstallation auf.
