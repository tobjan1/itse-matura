# SQL Injection

SQL Injection ist ein Angriff, bei dem ein Angreifer bösartigen SQL-Code in Eingabefelder einer Webanwendung einschleust. Wird die Eingabe ungefiltert in eine SQL-Abfrage eingebaut, führt die Datenbank den Schadcode aus.

## Angriff

### Klassische Login-Umgehung

Anfälliger Code:
```sql
SELECT * FROM users WHERE username = '$user' AND password = '$pw';
```

Eingabe des Angreifers als Benutzername: `' OR '1'='1`

Resultierende Abfrage:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '...';
```

Da `'1'='1'` immer wahr ist, liefert die Abfrage alle Benutzer — Login ohne gültiges Passwort möglich.

### UNION-Based Injection

Der Angreifer hängt eine eigene SELECT-Abfrage an, um andere Tabellen auszulesen:

```sql
SELECT name FROM products WHERE id = 1 UNION SELECT password FROM users;
```

Voraussetzung: Die Spaltenzahl muss übereinstimmen. Mit `ORDER BY`-Tricks oder `NULL`-Füllern lässt sich die Spaltenzahl ermitteln.

### Error-Based Injection

Der Angreifer provoziert absichtlich Datenbankfehler, die Informationen über die Datenbankstruktur preisgeben (Tabellennamen, Spalten, Datenbankversion). Nur gefährlich, wenn detaillierte Fehlermeldungen an den Benutzer ausgegeben werden.

Beispiel: Eingabe `'` löst einen Syntaxfehler aus, der Datenbankname o. Ä. erscheint in der Fehlermeldung.

### Blind SQL Injection (Time-Based)

Wenn kein Fehler und kein Ergebnis sichtbar ist, kann der Angreifer trotzdem Informationen ableiten — durch zeitbasierte Abfragen:

```sql
-- MySQL/MariaDB
' AND SLEEP(5) --
-- MSSQL
'; WAITFOR DELAY '0:0:5' --
```

Antwortet die Seite verzögert, ist die Bedingung wahr. So können Datenbankinhalt Bit für Bit extrahiert werden.

## Hardening

### Prepared Statements (Parametrierte Abfragen)

Trennen SQL-Code von Benutzereingaben vollständig. Der SQL-Code wird zuerst kompiliert, die Eingabe erst danach als reiner Wert eingesetzt — sie kann nie als Code interpretiert werden.

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email");
$stmt->bindParam(':email', $email);
$stmt->execute();
```

### Eingaben validieren

Erlaubte Zeichen, Datentypen und Längen prüfen. Unerwartete Eingaben frühzeitig ablehnen.

### Zeichen escapen

Sonderzeichen wie `'` und `--` maskieren, sodass sie nicht als SQL-Syntax wirken. Bei Prepared Statements ist das automatisch abgedeckt.

### Detaillierte Fehlermeldungen vermeiden

- Richtig: "Benutzername oder Passwort falsch"
- Falsch: "ERROR 1064 (42000): You have an error in your SQL syntax..."

Detaillierte Fehlermeldungen gehören ins Logfile, nicht in die Benutzeroberfläche.

### Berechtigungen einschränken (Principle of Least Privilege)

Datenbankbenutzer für Webanwendungen sollten nur die minimal notwendigen Rechte haben:

```sql
REVOKE DELETE ON datenbankname.* FROM 'webapp'@'localhost';
FLUSH PRIVILEGES;
```

### PDO in PHP

PHP Data Objects (PDO) implementiert Prepared Statements, Eingabevalidierung (via Typbindung) und automatisches Escaping. Bevorzugte Schnittstelle für Datenbankzugriff in PHP.

### Regelmäßige Updates

Datenbankserver aktuell halten — bekannte Schwachstellen werden durch Patches behoben.

## Prüfungs-Hotspots

- Klassisches `' OR '1'='1` Beispiel erklären
- Unterschied UNION-based vs. Blind/Time-based
- Warum schützen Prepared Statements? (Trennung von Code und Daten)
- Warum sind detaillierte Fehlermeldungen gefährlich?
- Least Privilege bei Datenbankbenutzern erklären
