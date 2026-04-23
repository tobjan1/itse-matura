# ARP Spoofing

## Grundlagen: ARP

Das Address Resolution Protocol (ARP) löst IP-Adressen in MAC-Adressen auf. Im lokalen Netzwerk (LAN) kommunizieren Geräte auf Schicht 2 (Ethernet) mit MAC-Adressen. Um die MAC-Adresse zu einem bekannten IP zu finden, sendet ein Gerät einen ARP-Request als Broadcast:

```
"Wer hat IP 192.168.1.1? Sagt es an MAC AA:BB:CC:DD:EE:FF"
```

Das Gerät mit dieser IP antwortet mit seiner MAC-Adresse. Diese Zuordnung wird im ARP-Cache gespeichert.

## Angriff: ARP Spoofing (ARP Poisoning)

ARP hat keine Authentifizierung. Jedes Gerät im Netzwerk kann auf einen ARP-Request antworten — auch ohne gefragt worden zu sein (Gratuitous ARP). Ein Angreifer nutzt das aus:

1. Angreifer sendet gefälschte ARP-Antworten an Opfer A: "Die IP des Routers (192.168.1.1) hat die MAC-Adresse des Angreifers"
2. Angreifer sendet gefälschte ARP-Antworten an den Router: "Die IP von Opfer A hat die MAC-Adresse des Angreifers"
3. Beide Geräte tragen die falsche Zuordnung in ihren ARP-Cache ein
4. Opfer A schickt Pakete an den Router — diese landen beim Angreifer
5. Angreifer leitet die Pakete weiter (Man-in-the-Middle) — beide Seiten bemerken nichts

## Ziele eines ARP Spoofing-Angriffs

- **Man-in-the-Middle (MITM)**: Gesamten Netzwerkverkehr mitlesen und manipulieren
- **Credential Harvesting**: Unverschlüsselte Logins abgreifen
- **Session Hijacking**: Session Cookies aus dem Netzwerkverkehr stehlen
- **Denial of Service**: Pakete absichtlich nicht weiterleiten (Verbindung unterbrechen)

## Gegenmaßnahmen

- **Dynamic ARP Inspection (DAI)**: Switch prüft ARP-Pakete gegen eine DHCP-Snooping-Datenbank und verwirft ungültige Einträge
- **Statische ARP-Einträge**: Für kritische Geräte (Router) feste MAC/IP-Zuordnungen eintragen — keine automatische Aktualisierung möglich
- **VPN / Verschlüsselung**: Selbst wenn der Angreifer den Verkehr abfängt, sieht er nur verschlüsselte Daten
- **HTTPS**: Schützt den Inhalt der Kommunikation auch bei MITM

## Prüfungs-Hotspots

- Was ist ARP, warum ist es unsicher?
- Ablauf eines ARP-Spoofing-Angriffs
- Was ist ein MITM-Angriff?
- Gegenmaßnahme Dynamic ARP Inspection erklären
