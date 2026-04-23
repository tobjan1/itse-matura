# DOM-Based XSS

## Was ist DOM-Based XSS?

Bei DOM-Based XSS findet der Angriff vollständig clientseitig statt — im Document Object Model (DOM) des Browsers. Im Gegensatz zu Reflected und Stored XSS wird die Payload nicht vom Server in die Antwort eingebettet. Ein clientseitiges Skript liest unsanitisierte Daten aus einer unsicheren Quelle (Source) und schreibt sie in eine gefährliche Stelle (Sink).

## Source und Sink

**Source** = Eingangspunkt für Angreifer-kontrollierte Daten:

| Source | Beschreibung |
|--------|-------------|
| `window.location.hash` | URL-Fragment (alles nach `#`) |
| `window.location.search` | Query-String (alles nach `?`) |
| `document.referrer` | Adresse der zuvor besuchten Seite |
| `localStorage` / `sessionStorage` | Clientseitig gespeicherte Daten |

**Sink** = Gefährliche Ausgabestelle:

| Sink | Gefahr |
|------|--------|
| `element.innerHTML` | Führt eingebettetes HTML/JS aus |
| `document.write()` | Schreibt direkt ins Dokument |
| `element.setAttribute('onclick', ...)` | Setzt ausführbaren Event-Handler |
| `eval()` | Führt String als JS aus |

## Ablauf

1. Angreifer konstruiert eine manipulierte URL (Payload im Hash-Teil: `#loginTarget=...`)
2. Opfer ruft die URL auf
3. Clientseitiges Skript liest den bösartigen Wert aus der URL (`window.location.hash`)
4. Wert wird ohne Prüfung in eine Sink geschrieben (z. B. `element.setAttribute('onclick', ...)`)
5. Beim Klick auf den Button wird der Schadcode ausgeführt

## Beispiel: Phishing über DOM-XSS

Anfälliges Skript:
```javascript
function setLoginPage() {
    const hash = window.location.hash;
    if (hash.includes('#loginTarget=')) {
        const target = hash.substring(hash.indexOf('#loginTarget=') + 13);
        const btn = document.getElementById('loginBtn');
        btn.setAttribute('onclick', `window.location.href='${target}'`);
    }
}
```

Normaler Aufruf: `index.html` — Button führt zu `login.html`

Angriff: `index.html#loginTarget=http://angreifer.example/fake_login.html`

Der Button leitet nun zur gefälschten Login-Seite weiter.

## Besonderheit

Der Server sieht die Payload nicht — der URL-Fragment-Teil (`#...`) wird nicht an den Server gesendet. Server-seitige Filterung hilft nicht.

## Hardening

- **Whitelisting**: Nur erlaubte Werte akzeptieren — alle anderen verwerfen
  ```javascript
  const allowedTargets = ['login.html', 'register.html'];
  if (allowedTargets.includes(target)) { /* sicher */ }
  ```
- **DOMPurify**: Eingaben bereinigen bevor sie in Sinks geschrieben werden
- **`textContent` statt `innerHTML`**: Verhindert HTML-Interpretation
- **Content Security Policy (CSP)**: Schränkt erlaubte Script-Quellen ein

## Prüfungs-Hotspots

- Worin unterscheidet sich DOM-XSS von Reflected/Stored XSS? (rein clientseitig, Server nicht involviert)
- Was sind Source und Sink? Beispiele nennen
- Warum hilft serverseitige Filterung hier nicht?
