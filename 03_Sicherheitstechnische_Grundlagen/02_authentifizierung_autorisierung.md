# Authentifizierung und Autorisierung

## Authentifizierung (Authentication)

Authentifizierung prüft die Identität — "Wer bist du?". Das System stellt sicher, dass jemand wirklich derjenige ist, der er zu sein behauptet.

### Authentifizierungsfaktoren

| Faktor | Beschreibung | Beispiel |
|--------|-------------|---------|
| Wissen (Knowledge) | Etwas, das man weiß | Passwort, PIN, Sicherheitsfrage |
| Besitz (Possession) | Etwas, das man hat | Smartphone (TOTP), Hardware-Token, Smartcard |
| Sein (Inherence) | Etwas, das man ist | Fingerabdruck, Gesichtserkennung, Iris-Scan |

### Multi-Faktor-Authentifizierung (MFA)

Kombiniert mindestens zwei verschiedene Faktoren. Auch wenn ein Faktor (z. B. Passwort) kompromittiert ist, bleibt das Konto geschützt.

**Zwei-Faktor-Authentifizierung (2FA)**: Zwei Faktoren (z. B. Passwort + TOTP-Code).

## Autorisierung (Authorization)

Autorisierung legt fest, was ein authentifizierter Benutzer darf — "Was darfst du?". Sie prüft Berechtigungen und Rechte nach erfolgter Authentifizierung.

### Beispiele

- Eingeloggter Benutzer darf seine eigenen Daten lesen, aber nicht die anderer Benutzer
- Administrator darf Benutzer löschen, normaler Benutzer nicht
- API-Endpoint `/admin` darf nur von Administratoren aufgerufen werden

### Prinzip der minimalen Rechte (Least Privilege)

Jeder Benutzer (und Prozess) bekommt nur die Berechtigungen, die er für seine Aufgabe tatsächlich braucht. Dadurch begrenzt man den Schaden bei einer Kompromittierung.

### Rollenbasierte Zugriffskontrolle (RBAC — Role Based Access Control)

Berechtigungen werden Rollen zugewiesen, Rollen werden Benutzern zugewiesen:

- Rollen: Admin, Manager, Mitarbeiter, Gast
- Benutzer erbt alle Rechte seiner Rolle(n)

## Abgrenzung

| | Authentifizierung | Autorisierung |
|-|-------------------|---------------|
| Frage | Wer bist du? | Was darfst du? |
| Wann | Vor dem Zugriff | Nach der Authentifizierung |
| Verletzung | Gestohlene Credentials, schwaches Passwort | IDOR, fehlende Berechtigungsprüfung |

## Accounting / Auditing

Dritter Teil des AAA-Modells: Protokollierung aller Aktionen (Wer hat wann was getan?). Dient der Nachvollziehbarkeit und Erkennung von Angriffen.

## Prüfungs-Hotspots

- Unterschied Authentifizierung vs. Autorisierung erklären
- Welcher Angriff verletzt die Autorisierung? (IDOR)
- Drei Authentifizierungsfaktoren mit Beispielen nennen
- Was ist MFA und warum ist es sicherer?
- Least Privilege erklären
