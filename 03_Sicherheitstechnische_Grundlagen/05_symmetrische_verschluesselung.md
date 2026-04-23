# Symmetrische Verschlüsselung

Bei der symmetrischen Verschlüsselung wird zum Verschlüsseln und Entschlüsseln derselbe Schlüssel verwendet. Sender und Empfänger müssen diesen Schlüssel vorab sicher austauschen.

## Merkmale

- **Gleicher Schlüssel** für Ver- und Entschlüsselung
- **Schnell und effizient** — geeignet für große Datenmengen
- **Problem**: Schlüsselaustausch muss sicher erfolgen (Key Distribution Problem)
- Schützt: **Confidentiality** (Vertraulichkeit)

## Gängige Algorithmen

| Algorithmus | Schlüssellänge | Sicherheit | Anmerkung |
|-------------|---------------|-----------|-----------|
| **AES** (Advanced Encryption Standard) | 128, 192, 256 Bit | Sehr sicher | Aktueller Standard |
| **3DES** (Triple DES) | 112 oder 168 Bit | Veraltet | Nachfolger von DES |
| **DES** (Data Encryption Standard) | 56 Bit | Unsicher | Seit 1999 gebrochen |
| **ChaCha20** | 256 Bit | Sicher | Alternative zu AES, für mobile Geräte |

## Betriebsmodi

Ein Algorithmus wie AES verschlüsselt immer exakt einen Block. Für längere Daten gibt es verschiedene Betriebsmodi:

- **ECB (Electronic Codebook)**: Gleiche Klartextblöcke → gleiche Chiffretextblöcke — unsicher, erkennbare Muster bleiben erhalten
- **CBC (Cipher Block Chaining)**: Jeder Block wird mit dem vorherigen XOR-verknüpft — sicher, aber sequenziell
- **CTR (Counter Mode)**: Block-Chiffre als Stream-Chiffre betrieben — parallele Verarbeitung möglich
- **GCM (Galois/Counter Mode)**: CTR + Authentifizierung (AEAD) — aktuell empfohlen für TLS

## Hybride Verschlüsselung

Da asymmetrische Verschlüsselung langsam ist, wird in der Praxis eine hybride Form verwendet:

1. Asymmetrische Verschlüsselung tauscht einen symmetrischen Session Key aus
2. Die eigentliche Kommunikation läuft symmetrisch verschlüsselt (z. B. AES)

So nutzt TLS: RSA/DH für den Schlüsselaustausch, AES-GCM für die Datenverschlüsselung.

## Prüfungs-Hotspots

- Unterschied symmetrisch vs. asymmetrisch
- Was ist das Key Distribution Problem?
- Warum ist AES der aktuelle Standard?
- Was ist hybride Verschlüsselung und warum wird sie verwendet?
