<div align="center">
  <img src="src/Win11ControlCenter/Assets/Win11ControlCenter.png" alt="Win11 Control Center Pro Icon" width="104" />
  <h1>Win11 Control Center Pro</h1>
  <p><strong>Zentrale für App-Verwaltung, Datenschutz, Windows-Anpassungen und Systemwartung.</strong></p>
  <p><a href="README.md">English README</a> · <a href="docs/FEATURES.md">Funktionsübersicht (Englisch)</a> · <a href="docs/BUILD.md">Build-Anleitung (Englisch)</a></p>
</div>

## Überblick

Win11 Control Center Pro ist eine Desktop-Anwendung für Windows 11. Sie bündelt die Übersicht über System und Hardware, die Verwaltung ausgewählter Windows-App-Pakete und klassischer Desktop-Programme, kategorisierte Windows- und Datenschutzoptionen, die Analyse von Bereinigungsbereichen sowie Protokolle und unterstützte Konfigurationssicherungen.

**Aktuelle Quellversion:** 2.0.25 – English (United States)  
**Technik:** C#, WPF, .NET 10, Windows x64.

> **Achtung:** Die Anwendung benötigt Administratorrechte und kann Windows-Einstellungen ändern, ausgewählte Anwendungen entfernen und markierte temporäre Dateien oder Caches löschen. Prüfe jede Auswahl vor der Bestätigung. Registry-Sicherungen sind kein vollständiges Systemabbild.

## Funktionsbereiche

- **Übersicht:** System- und Hardwareinformationen, Live-Werte und Schnellzugriffe.
- **Apps entfernen:** Prüfung unterstützter AppX-/MSIX-Pakete anhand der Paketidentität und des gewählten Geltungsbereichs.
- **Apps installieren:** Katalogisierte Programme über Microsoft Store oder WinGet installieren.
- **Installierte Programme:** Klassische Win32-/MSI-Programme anzeigen, deren Hersteller-Deinstaller starten und mögliche Programmreste einzeln prüfen.
- **Windows Tweaks:** Beschriebene, kategorisierte Windows-Anpassungen und Empfehlungen.
- **Datenschutz:** Übersicht ausgewählter Datenschutz- und Diagnoseoptionen.
- **Systembereinigung:** Erst Analyse, dann explizite Auswahl und Bestätigung. Browser-Cookies, Sitzungen und Verlauf sind optionale Bereinigungsziele.
- **Verlauf & Wiederherstellung:** Aktivitätsprotokolle und unterstützte Registry-Sicherungen prüfen und gespeicherte Werte wiederherstellen.

## Voraussetzungen

- Windows 11, 64-Bit (x64).
- Für den Quellcode-Build: .NET 10 SDK und PowerShell.
- Der Hauptclient wird vom Build-Skript als selbstständige Single-File-Anwendung veröffentlicht.
- Der separate, kompakte Deinstaller benötigt die .NET 10 Desktop Runtime x64.
- Die Anwendung fordert über UAC Administratorrechte an.

## Build und Installation

Die Datei `Build-Win11ControlCenter.ps1` ist ein **Build-und-Installationsskript**. Sie prüft den Quellcode, erstellt Hauptanwendung und Deinstaller und installiert beide in das Profil des aktuellen Benutzers. Außerdem registriert sie Startmenü- und Deinstallations-Einträge und erstellt standardmäßig eine Desktop-Verknüpfung.

Im Repository-Hauptordner in PowerShell ausführen:

```powershell
powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\Build-Win11ControlCenter.ps1
```

Mit `-NoLaunch` wird die abschließende Startabfrage unterdrückt; mit `-SkipDesktopShortcut` wird keine Desktop-Verknüpfung erstellt. Das Skript installiert die Anwendung trotzdem. Für einen reinen Publish ohne Installation siehe [Build guide](docs/BUILD.md) (Englisch).

## Autostart und Deinstallation

Der optionale Windows-Start wird als interaktive Aufgabenplaner-Aufgabe nach der Benutzeranmeldung eingerichtet. Die Anwendung startet dabei im Infobereich (System-Tray). Es handelt sich **nicht** um einen Windows-Dienst.

Der Deinstaller ist eine eigene EXE. Er entfernt Autostart-Aufgabe, Verknüpfungen, Deinstallationsregistrierung und Programmordner. Der persönliche Datenordner `%LOCALAPPDATA%\Win11ControlCenter` mit Sicherungen und Protokollen bleibt erhalten.

## Lizenzstatus

Derzeit ist keine Open-Source-Lizenz enthalten. Die öffentliche Sichtbarkeit eines GitHub-Repositories erteilt keine Erlaubnis zur Wiederverwendung, Änderung oder Weiterverbreitung. Details: [LICENSE-NOTICE.md](LICENSE-NOTICE.md).

## Hinweis

Win11 Control Center Pro ist ein unabhängiges Projekt und steht in keiner Verbindung zu Microsoft. Windows ist eine Marke der Microsoft Corporation.

---

<p align="center"><sub>Win11 Control Center Pro 2.0.25 · © 2026 Malte Speck</sub></p>
