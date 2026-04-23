# Encoding und Hashing

## Encoding (Kodierung)

Encoding wandelt Daten in eine andere Darstellungsform um. Es ist **umkehrbar** — mit dem richtigen Verfahren kann man die ursprünglichen Daten wiederherstellen. Encoding dient nicht der Sicherheit, sondern der Übertragbarkeit und Kompatibilität.

### Beispiele

| Verfahren | Zweck | Beispiel |
|-----------|-------|---------|
| **Base64** | Binärdaten als ASCII-Text übertragen | `Hallo` → `SGFsbG8=` |
| **URL-Encoding** | Sonderzeichen in URLs darstellen | `Hallo Welt` → `Hallo%20Welt` |
| **HTML-Encoding** | HTML-Sonderzeichen maskieren | `<` → `&lt;` |
| **UTF-8** | Zeichen aller Sprachen als Bytes | `ä` → `0xC3 0xA4` |

**Wichtig**: Base64 ist keine Verschlüsselung und kein Schutz — jeder kann es einfach dekodieren.

## Hashing

Hashing ist eine **Einwegfunktion** — aus den Eingangsdaten wird ein Hash (Fingerabdruck) berechnet, aber aus dem Hash kann man die Eingangsdaten nicht zurückgewinnen. Hashing ist nicht umkehrbar.

### Eigenschaften einer guten Hash-Funktion

- **Deterministisch**: Gleiche Eingabe ergibt immer gleichen Hash
- **Schnell berechenbar**
- **Kollisionsresistent**: Verschiedene Eingaben ergeben (mit sehr hoher Wahrscheinlichkeit) verschiedene Hashes
- **Lawineneffekt**: Kleine Änderung der Eingabe → komplett anderer Hash
- **Präbildresistenz**: Aus dem Hash kann man die Eingabe nicht zurückrechnen

### Gängige Algorithmen

| Algorithmus | Output-Länge | Sicherheit |
|-------------|-------------|-----------|
| MD5 | 128 Bit / 32 Hex | Unsicher (kollisionsanfällig) |
| SHA-1 | 160 Bit / 40 Hex | Unsicher |
| SHA-256 | 256 Bit / 64 Hex | Sicher |
| SHA-512 | 512 Bit / 128 Hex | Sicher |
| bcrypt | variabel | Speziell für Passwörter |

### Anwendungsgebiete

- **Passwortspeicherung**: Nie das Passwort selbst speichern, nur den Hash (+ Salt)
- **Dateiintegrität**: Hash einer Datei prüfen, ob sie unverändert ist
- **Digitale Signatur**: Hash einer Nachricht wird signiert
- **Checksums**: Prüfen ob Daten bei der Übertragung korrumpiert wurden

### Salt beim Passwort-Hashing

Ein **Salt** ist ein zufälliger Zusatzwert, der vor dem Hashing an das Passwort angehängt wird:

```
Hash(passwort + salt) = gespeicherter_hash
```

Zweck: Zwei Benutzer mit gleichem Passwort haben verschiedene Hashes. Rainbow-Table-Angriffe werden unbrauchbar.

## Vergleich

| | Encoding | Hashing |
|-|---------|---------|
| Umkehrbar? | Ja | Nein |
| Schlüssel nötig? | Nein | Nein |
| Sicherheitsziel | Keine | Integrität, Passwortsicherheit |
| Beispiel | Base64 | SHA-256 |

## Prüfungs-Hotspots

- Unterschied Encoding vs. Hashing vs. Verschlüsselung
- Warum ist Base64 keine Sicherheitsmaßnahme?
- Was ist ein Salt und warum ist er wichtig?
- Welche Hash-Algorithmen sind sicher, welche nicht?
- Warum speichert man Passwörter als Hash und nicht im Klartext?
