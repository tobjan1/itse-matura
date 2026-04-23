# Block Cipher und Stream Cipher

## Block Cipher (Blockchiffre)

Ein Block Cipher verschlüsselt Daten in fixen Blöcken fester Länge. Der gesamte Block wird als Einheit verarbeitet.

### Merkmale

- Feste Blockgröße (z. B. AES: 128 Bit = 16 Byte)
- Deterministische Ausgabe: gleicher Input + gleicher Schlüssel = gleicher Output
- Braucht Betriebsmodus für längere Nachrichten (ECB, CBC, CTR, GCM)
- Padding notwendig, wenn Nachricht kein Vielfaches der Blockgröße ist

### Beispiele

| Algorithmus | Blockgröße | Schlüssellänge |
|-------------|-----------|---------------|
| AES | 128 Bit | 128/192/256 Bit |
| DES | 64 Bit | 56 Bit (veraltet) |
| 3DES | 64 Bit | 112/168 Bit (veraltet) |
| Blowfish | 64 Bit | 32–448 Bit |

### Betriebsmodi

- **ECB**: Einfachster Modus — unsicher, da gleiche Blöcke gleich verschlüsselt werden
- **CBC**: Jeder Block wird mit dem vorherigen XOR-verknüpft — benötigt Initialisierungsvektor (IV)
- **CTR**: Block Cipher als Keystream-Generator — parallele Verarbeitung möglich
- **GCM**: CTR + Authentifizierungs-Tag — AEAD (Authenticated Encryption with Associated Data)

## Stream Cipher (Stromchiffre)

Ein Stream Cipher verschlüsselt Daten Bit für Bit oder Byte für Byte. Er erzeugt aus dem Schlüssel einen Pseudozufalls-Keystream, der mit dem Klartext XOR-verknüpft wird.

### Merkmale

- Verschlüsselung: `Ciphertext = Plaintext XOR Keystream`
- Sehr schnell — geeignet für Echtzeit-Anwendungen (Streaming, Mobilfunk)
- Kein Padding notwendig
- **Wichtig**: Jeder Schlüssel darf nur einmal verwendet werden (sonst angreifbar)

### Beispiele

| Algorithmus | Anmerkung |
|-------------|-----------|
| RC4 | Veraltet, unsicher |
| ChaCha20 | Modern, sicher — in TLS 1.3 und QUIC verwendet |
| A5/1 | GSM-Mobilfunk (veraltet, schwach) |
| Salsa20 | Vorgänger von ChaCha20 |

### XOR als Grundprinzip

```
Klartext:   0110 1001
Keystream:  1010 0101
Ciphertext: 1100 1100

Entschlüsselung:
Ciphertext: 1100 1100
Keystream:  1010 0101
Klartext:   0110 1001
```

XOR ist selbstinvers: zweimaliges XOR mit demselben Wert ergibt wieder den Ausgangswert.

## Vergleich

| | Block Cipher | Stream Cipher |
|-|-------------|--------------|
| Einheit | Block (z. B. 128 Bit) | Bit/Byte |
| Geschwindigkeit | Mittel | Sehr schnell |
| Padding | Ja | Nein |
| Betriebsmodus | Notwendig | Integriert |
| Beispiel | AES-CBC | ChaCha20 |
| Anwendung | Datei-/Festplattenverschlüsselung | TLS, VoIP, Video-Streaming |

## Prüfungs-Hotspots

- Was ist der Unterschied zwischen Block Cipher und Stream Cipher?
- Warum ist ECB-Modus unsicher?
- Was ist ein Keystream und wie funktioniert XOR?
- Welcher Modus wird in TLS empfohlen? (AES-GCM, ChaCha20-Poly1305)
