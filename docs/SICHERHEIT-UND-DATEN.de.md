# Sicherheit & Daten

Win11 Control Center Pro enthält Funktionen zur Systemverwaltung. Verwende sie bewusst und prüfe jeden Vorgang vor der Bestätigung.

## Vor Änderungen an Windows

- Lies die Beschreibung und die Hinweise zu den Auswirkungen der ausgewählten Option.
- Ändere nur Einstellungen, die du verstehst und bewusst ändern möchtest.
- Erstelle vor wichtigen Systemänderungen eine geeignete Sicherung oder bewahre eine vorhandene Sicherung auf.
- Entferne keine Windows-Komponenten oder Anwendungspakete nur deshalb, weil dir deren Name unbekannt ist.
- Manche Änderungen werden erst nach Ab- und erneuter Anmeldung, einem Neustart des Explorers oder einem Neustart von Windows wirksam.

## Anwendungen entfernen

Das Entfernen eines AppX-/MSIX-Pakets oder eines klassischen Desktop-Programms kann Funktionen oder Benutzerdaten der jeweiligen Anwendung beeinträchtigen. Eine Neuinstallation kann vom ursprünglichen Herausgeber, Microsoft Store, WinGet oder einer anderen Originalquelle abhängen. Prüfe vor dem Fortfahren die Paketidentität und den Geltungsbereich.

## Systembereinigung

Zu den Bereinigungszielen können temporäre Dateien, Miniaturansichten, ausgewählte Caches und optionale Browserdaten gehören. Cookies, Sitzungen und Verlauf können dazu dienen, Webseiten angemeldet zu halten oder den Browserzustand zu speichern. Ihre Auswahl kann dich von Webseiten abmelden oder lokale Browserdaten löschen. Prüfe vor dem Löschen die ausgewählten Kategorien.

## Registry- und Konfigurationswiederherstellung

Die Registry-/Konfigurationssicherungen der Anwendung umfassen unterstützte Werte, die für unterstützte Aktionen gespeichert wurden. Sie sind **kein**:

- vollständiges Windows-Systemabbild;
- Backup persönlicher Dateien;
- Garant dafür, dass jede Auswirkung von Windows oder Drittanbieter-Software rückgängig gemacht werden kann.

Bewahre persönliche Dateien und wichtige Systemdaten zusätzlich separat auf. Stelle nur eine Sicherung wieder her, deren Herkunft und Zweck du kennst.

## Administratorrechte

Windows kann eine Abfrage der Benutzerkontensteuerung (UAC) anzeigen. Prüfe Herausgeber und Dateiquelle, bevor du zustimmst. Lade Release-Dateien ausschließlich von der offiziellen Releases-Seite des Repositorys herunter.

## Lokal gespeicherte Anwendungsdaten

Die Anwendung speichert Protokolle und unterstützte Sicherungsdaten unter:

```text
%LOCALAPPDATA%\Win11ControlCenter\
```

Protokolle können technische Angaben zum PC oder zu ausgeführten Aktionen enthalten. Prüfe und anonymisiere persönliche Informationen, bevor du Protokolle an den Support weitergibst.

## Verhalten des Deinstallationsprogramms

Das separate Deinstallationsprogramm ist darauf ausgelegt, Programmdateien sowie programmbezogene Verknüpfungen und Registrierungseinträge zu entfernen und persönliche Sicherungs- und Protokolldaten beizubehalten. Lies die Bestätigung sorgfältig. Nicht mehr benötigte gespeicherte Daten können nach der Deinstallation separat geprüft und entfernt werden.

## Externe Dienste

Einige Katalog- oder Installationsfunktionen können Microsoft Store, WinGet oder andere externe Paketquellen verwenden. Verfügbarkeit, Inhalte und Nutzungsbedingungen werden von diesen Anbietern festgelegt.
