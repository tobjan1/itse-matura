# File Upload Vulnerability

Eine File Upload Vulnerability entsteht, wenn eine Webanwendung hochgeladene Dateien nicht ausreichend prüft. Ein Angreifer kann dadurch Schadcode auf den Server laden und unter Umständen ausführen oder sensible Informationen auslesen.

## Angriffsszenario

Wenn der Dateiname und Dateityp direkt vom Benutzer übernommen werden, ohne Validierung:

- Upload einer PHP-Webshell (`shell.php`) → Der Angreifer ruft die Datei über den Browser auf und kann Befehle ausführen
- Path Traversal im Dateinamen (`../../etc/passwd`) → Datei wird an einem unbeabsichtigten Ort abgelegt
- Denial of Service → Sehr große Dateien füllen Speicher oder RAM

## Gegenmaßnahmen

### Extension Whitelisting

Nur explizit erlaubte Dateiendungen zulassen — alles andere ablehnen:

```php
$allowed_extensions = array("jpg", "jpeg", "png", "pdf");
$file_extension = strtolower(pathinfo($filename, PATHINFO_EXTENSION));
if (!in_array($file_extension, $allowed_extensions)) {
    die("Dateityp nicht erlaubt.");
}
```

### MIME-Type Prüfung (Magic Bytes)

Der MIME-Type aus dem Browser kann gefälscht werden. Stattdessen: Dateiinhalt analysieren (Magic Bytes — die ersten Bytes einer Datei verraten den echten Typ):

```php
$finfo = finfo_open(FILEINFO_MIME_TYPE);
$real_mime_type = finfo_file($finfo, $temp_file);
finfo_close($finfo);

$allowed_mime_types = array("image/jpeg", "image/png");
if (!in_array($real_mime_type, $allowed_mime_types)) {
    die("Unzulässiger Dateityp.");
}
```

### Dateigröße begrenzen

Gegen DoS-Angriffe durch massive Uploads:

```php
$max_file_size = 2 * 1024 * 1024; // 2 MB
if ($_FILES["fileToUpload"]["size"] > $max_file_size) {
    die("Datei zu groß.");
}
```

Zusätzlich in `php.ini`: `upload_max_filesize` und `post_max_size` setzen.

### Zufälligen Dateinamen generieren

Der originale Dateiname darf nie direkt verwendet werden (Path Traversal, IDOR):

```php
$newFileName = bin2hex(random_bytes(16)) . '.' . $file_extension;
```

Vorteile:
- Verhindert Path Traversal (`../../etc/passwd`)
- Keine Konflikte bei gleichnamigen Dateien
- IDOR-Angriffe (Raten von Dateinamen) erschwert

### Logging und Monitoring

Alle Upload-Aktivitäten protokollieren, verdächtige Uploads als WARNING loggen.

## Zusammenfassung: Pflichtprüfungen bei File Upload

| Prüfung | Schutz vor |
|---------|-----------|
| Extension Whitelist | Ausführbare Dateien blockieren |
| MIME-Type (Magic Bytes) | Getarnten Dateitypen |
| Dateigröße | DoS |
| Zufälliger Dateiname | Path Traversal, IDOR |
| Logging | Nachvollziehbarkeit, Erkennung |

## Prüfungs-Hotspots

- Warum reicht Extension Whitelist alleine nicht? (MIME-Type kann gefälscht werden)
- Was sind Magic Bytes?
- Warum zufälliger Dateiname? (Path Traversal, IDOR)
- Wie entsteht ein DoS durch File Upload?
