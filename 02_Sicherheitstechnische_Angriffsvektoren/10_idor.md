# IDOR — Insecure Direct Object Reference

IDOR (Insecure Direct Object Reference) ist eine Schwachstelle in Webanwendungen, bei der ein Angreifer auf Ressourcen (Dateien, Datenbankeinträge, Benutzerdaten) zugreift, ohne dazu autorisiert zu sein.

Der Angriff zielt nicht auf die Authentifizierung, sondern auf eine **Verletzung der Autorisierung**.

## Grundprinzip

Die Anwendung verwendet eine direkte, vorhersagbare Referenz (ID) zum Zugriff auf Objekte und prüft nicht, ob der anfragende Benutzer berechtigt ist:

```
https://example.com/profile?user_id=123
```

Ein Angreifer ändert den Parameter:

```
https://example.com/profile?user_id=124
```

Falls der Server die Berechtigung nicht prüft, sieht der Angreifer das Profil von Benutzer 124.

## Angriffsformen

### IDOR in der URL

Einfache numerische IDs oder fortlaufende IDs in URL-Parametern. Der Angreifer probiert systematisch andere Werte aus.

### IDOR mit codierter ID

Manchmal sind IDs Base64-codiert. Das sieht verschleiert aus, bietet aber keinen Schutz:

```
cGFzc3dvcmQxMjM=  →  base64-decode  →  password123
```

Codierung ist keine Verschlüsselung und bietet keine Sicherheit.

### IDOR mit Hash

Auch gehashte oder JWT-basierte Identifier können anfällig sein, wenn der Token manipuliert werden kann. Siehe [09_jwt.md](../01_Sicherheitstechnische_Methoden/09_jwt.md).

### IDOR in Cookies oder HTTP-Headern

IDOR beschränkt sich nicht auf die URL — Referenzen können auch in Cookies, POST-Body oder HTTP-Headern versteckt sein.

## Beispiel

```
GET /download?file_id=42   → Datei des eigenen Benutzers
GET /download?file_id=43   → Datei eines anderen Benutzers (IDOR wenn kein Check)
```

## Hardening

- **Autorisierungsprüfung bei jedem Zugriff**: Prüfen, ob der angemeldete Benutzer berechtigt ist, auf das konkrete Objekt zuzugreifen — nicht nur ob er eingeloggt ist
- **Indirekte Referenzen**: Statt direkter Datenbank-IDs interne Mapping-Tabellen verwenden (Angreifer kennt die interne ID nicht)
- **Zufällige, nicht erratbare IDs**: UUIDs statt fortlaufende Ganzzahlen

## Prüfungs-Hotspots

- Was ist der Unterschied zwischen Authentifizierung und Autorisierung? IDOR verletzt welche davon?
- Warum ist Base64-Codierung kein Schutz?
- Was ist die richtige Gegenmaßnahme? (serverseitige Autorisierungsprüfung)
