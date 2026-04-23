# Passwörter

## Was macht ein gutes Passwort aus?

Ein starkes Passwort zeichnet sich durch folgende Merkmale aus:

- **Länge**: Mindestens 12 Zeichen, besser 16+
- **Zeichenvielfalt**: Groß- und Kleinbuchstaben, Ziffern, Sonderzeichen
- **Keine Wörterbuchwörter**: Kein einfaches Wort aus einer Sprache
- **Kein persönlicher Bezug**: Kein Name, Geburtsdatum, Haustier
- **Einzigartigkeit**: Jeder Dienst erhält ein eigenes Passwort

Beispiel schwaches Passwort: `passwort123`  
Beispiel starkes Passwort: `T!9wX#mQ4&zR`  
Beispiel Passphrase: `Katze-Tisch-Regen-42!` (lang, merksam, stark)

## Methoden zur Passwortsicherheit

### Passwort-Manager
Speichert und generiert sichere Passwörter. Der Benutzer muss nur ein Master-Passwort merken. Bekannte Beispiele: Bitwarden, KeePass, 1Password.

### Multi-Faktor-Authentifizierung (MFA)
Kombiniert etwas, das man weiß (Passwort), mit etwas, das man hat (TOTP-App, Hardware-Token) oder ist (Biometrie). Auch bei gestohlenen Passwörtern bleibt das Konto geschützt.

### Passwort-Richtlinien (Password Policies)
Organisationen legen Mindestanforderungen fest: Mindestlänge, Komplexität, Ablaufzeitraum, Sperrung nach X Fehlversuchen.

### Have I Been Pwned?
Dienst, der prüft, ob eine E-Mail-Adresse oder ein Passwort in bekannten Datenlecks auftaucht. URL: haveibeenpwned.com

## Angriffsmethoden auf Passwörter

- **Brute Force**: Alle Kombinationen durchprobieren — langsam, aber vollständig
- **Dictionary Attack**: Wörterbuch-Passwörter und häufige Varianten testen
- **Credential Stuffing**: Gestohlene Login-Daten aus einem Leak bei anderen Diensten einsetzen
- **Phishing**: Benutzer gibt Passwort selbst auf einer Fake-Seite ein

## Prüfungs-Hotspots

- Eigenschaften eines starken Passworts nennen
- Unterschied Brute Force vs. Dictionary Attack
- Warum MFA notwendig ist, auch bei starkem Passwort
