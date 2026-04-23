# CAM Table Overflow

## Grundlagen: CAM-Tabelle

Ein Switch lernt, welche MAC-Adresse an welchem Port angeschlossen ist, indem er eingehende Frames analysiert. Diese Zuordnungen speichert er in der CAM-Tabelle (Content Addressable Memory), auch MAC-Adresstabelle genannt.

Wenn ein Frame für eine MAC-Adresse eintrifft, die bereits in der Tabelle steht, leitet der Switch ihn gezielt an den richtigen Port weiter — nicht als Broadcast. Das macht Switches effizienter als Hubs.

## Angriff: CAM Table Overflow

Die CAM-Tabelle hat eine begrenzte Kapazität. Der Angriff funktioniert so:

1. Angreifer sendet sehr viele Ethernet-Frames mit zufällig generierten, gefälschten Quell-MAC-Adressen
2. Der Switch trägt jede neue MAC-Adresse in seine CAM-Tabelle ein
3. Die Tabelle füllt sich und läuft voll (Overflow)
4. Neue, legitime MAC-Adressen können nicht mehr aufgenommen werden
5. Der Switch kann legitime Frames nicht mehr gezielt weiterleiten
6. Folge: Der Switch "degradiert" auf Hub-Verhalten — er sendet alle Frames an alle Ports (Broadcast/Flooding)
7. Der Angreifer empfängt nun den gesamten Netzwerkverkehr und kann ihn mitlesen

## Werkzeuge

Das Tool `macof` (Teil des Pakets `dsniff`) kann schnell Tausende von Frames mit zufälligen MAC-Adressen erzeugen.

## Ziele

- Netzwerkverkehr mitlesen (Sniffing), ähnlich wie bei ARP Spoofing
- Vorstufe für weitere MITM-Angriffe

## Gegenmaßnahmen

- **Port Security**: Switch-Funktion, die pro Port die maximal erlaubte Anzahl von MAC-Adressen begrenzt (z. B. max. 5). Bei Überschreitung: Port sperren (Shutdown) oder Pakete verwerfen
- **802.1X Authentifizierung**: Geräte müssen sich am Switch authentifizieren, bevor sie Frames senden dürfen
- **VLAN-Segmentierung**: Angriff ist auf das lokale VLAN beschränkt — kleinere Schadensbegrenzung

## Vergleich mit ARP Spoofing

| Merkmal | CAM Table Overflow | ARP Spoofing |
|---------|-------------------|--------------|
| Ziel | Switch-Tabelle überfluten | ARP-Cache vergiften |
| Ergebnis | Hub-Verhalten (alle sehen alles) | MITM-Position |
| Layer | Layer 2 (MAC) | Layer 2/3 (ARP) |
| Gegenmaßnahme | Port Security | Dynamic ARP Inspection |

## Prüfungs-Hotspots

- Was ist die CAM-Tabelle und wozu dient sie?
- Wie funktioniert der Overflow-Angriff?
- Warum sendet ein überlaufener Switch alles als Broadcast?
- Gegenmaßnahme Port Security erklären
