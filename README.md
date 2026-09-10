# LAE Secret Chat – Releases

Dieses öffentliche Repository enthält installierbare Builds und Update-Metadaten für **LAE Secret Chat / LAE Weather**.

Der eigentliche Quellcode, das Backend und die Entwicklungsinfrastruktur befinden sich in einem separaten privaten Repository.

## Aktueller Release-Kanal

Die hier veröffentlichten Builds sind derzeit **Development-/Preview-Releases**. Sie dienen zum Testen der Android-App, der Messenger-Funktionen, des versteckten privaten Bereichs und der laufenden Signal-v4-/Multi-Device-Entwicklung.

Ein finaler produktiver Release erfolgt erst nach vollständigen Plattform-Cross-Tests und abgeschlossenem Multi-Device-/History-Sync-Test.

## App

Paketname:

```text
at.almirit.lae.secretchat
```

Die App kombiniert:

- Wetteroberfläche
- versteckten privaten Messenger-Bereich
- Benutzerkonten und Gerätebindung
- Multi-Device-Unterstützung
- Ende-zu-Ende-Verschlüsselung
- verschlüsselte Medien
- Push-Benachrichtigungen
- In-App-Update-Unterstützung für Android

## Verschlüsselungsstatus

Android verwendet bereits Signal Protocol / LibSignal v0.101.1 mit PQXDH und Double Ratchet.

iOS verwendet ebenfalls LibSignalClient v0.101.1 und ist auf denselben Signal-v4-Nachrichtenpfad vorbereitet.

Die vollständige plattformübergreifende Interoperabilität wird noch abschließend getestet. Der Web-Client befindet sich noch in Migration auf echte Signal-v4-kompatible Browser-Krypto.

## Releases herunterladen

Die installierbaren APKs werden über GitHub Releases veröffentlicht.

Die Datei `version.json` zeigt immer auf den aktuell vorgesehenen Android-Build für die Updateprüfung der App.

Aktueller Inhalt von `version.json` enthält unter anderem:

```text
app
package
versionCode
versionName
apk
versionedApk
sha256
release
```

Damit kann die App feststellen, ob eine neuere Version verfügbar ist und welchen Build sie laden soll.

## Installation auf Android

1. Die gewünschte APK aus dem neuesten GitHub Release herunterladen.
2. Android muss die Installation aus der verwendeten Quelle erlauben.
3. APK öffnen und installieren.

Bei Updates mit derselben App-Signatur kann die vorhandene Installation aktualisiert werden, ohne die App vorher zu deinstallieren.

Das ist wichtig, weil lokale App-Daten, Geräteidentität und kryptografische Zustände bei einer normalen Aktualisierung erhalten bleiben sollen.

## Update-Verhalten

Die App ist so vorgesehen, dass spätere Builds möglichst als normales Update installiert werden können.

Eine Deinstallation vor einem Update sollte vermieden werden, da dabei lokale Daten und je nach Plattform auch gerätespezifische Schlüsselzustände entfernt werden können.

Für Testgeräte gilt daher bevorzugt:

```text
bestehende App behalten → neue APK darüber installieren
```

## Versionsschema

Development-Builds verwenden derzeit ein Schema wie:

```text
0.1.<build>-dev
```

Beispiel:

```text
0.1.359-dev
```

Die GitHub-Release-Tags verwenden entsprechend:

```text
v0.1.359-dev
```

## Integritätsprüfung

`version.json` enthält für den veröffentlichten APK-Build einen SHA-256-Hash.

Damit kann die Integrität des Downloads geprüft werden.

Unter Linux beispielsweise:

```bash
sha256sum LAE-Weather-0.1.359-dev.apk
```

Unter Windows PowerShell:

```powershell
Get-FileHash .\LAE-Weather-0.1.359-dev.apk -Algorithm SHA256
```

Der ausgegebene Hash muss mit dem Wert `sha256` aus `version.json` übereinstimmen.

## Was dieses Repository nicht enthält

Dieses Repository enthält bewusst nicht:

- den Android-Quellcode
- den iOS-Quellcode
- Backend-Quellcode
- Docker-Konfiguration
- PostgreSQL-Schema
- private API-Konfiguration
- Signierschlüssel
- Firebase-/APNs-Secrets
- produktive Zugangsdaten

Diese Komponenten verbleiben im privaten Entwicklungsrepository.

## Aktueller Projektstatus

| Bereich | Status |
| --- | --- |
| Backend Multi-Device / Registry / Linking | ✅ |
| Android Signal-v4 | ✅ |
| Android Multi-Device Fan-out | ✅ |
| Android Build | ✅ |
| iOS Geräteverwaltung / Linking | ✅ |
| iOS Build | ✅ |
| iOS Signal-v4 Implementierung | ✅ Build grün |
| Web v4 Backend | ✅ |
| Web echte Signal-v4 Browser-Krypto | 🔧 |
| Android ↔ iOS Cross-Test | 🔧 |
| Android ↔ Web Cross-Test | ❌ |
| iOS ↔ Web Cross-Test | ❌ |
| History-Sync kompletter Multi-Device-Test | ❌ |
| Finaler Release | ❌ |

## Hinweise für Tester

Bitte Development-Builds nicht als final produktiv betrachten. Insbesondere bei Messenger-/E2EE-Tests können sich Nachrichtenformate, Geräte-Registrierung und lokale Kryptozustände bis zum finalen Release noch ändern.

Bei Problemen nach einem Update sollte eine Deinstallation nur als letzter Schritt verwendet werden, weil dadurch lokale kryptografische Daten verloren gehen können.

## Sicherheit

- APKs nur aus diesem offiziellen Release-Repository verwenden.
- SHA-256 bei Bedarf gegen `version.json` prüfen.
- Keine APKs aus unbekannten Drittquellen installieren.
- Secrets und private Schlüssel werden nicht in diesem Repository veröffentlicht.
- Nachrichteninhalte sollen Ende-zu-Ende verschlüsselt bleiben.

## Support

**Almir-IT e.U.**

Website: https://almir-it.at  
Support: support@almir-it.at

---

LAE Secret Chat ist eine eigenständige Neuentwicklung.