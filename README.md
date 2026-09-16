# kryven.net — Übersetzungen

Eine Datei pro **Minecraft-Sprachcode** unter `lang/` (`de_de.yml`, `en_us.yml`, `fr_fr.yml`, ...
alle ~129 offiziellen Java-Edition-Sprachen, siehe [minecraft.wiki/w/Language](https://minecraft.wiki/w/Language)).
Jede Datei enthält **alle** Texte aus **allen 4 Server-Modulen** zusammen.

## Aktuell live im Spiel

Nur **`de_de.yml`**, **`en_us.yml`**, **`fr_fr.yml`** sind komplett ausgefüllt — das sind die drei
Sprachen, die das Netzwerk aktuell wirklich anbietet. Alle anderen ~126 Dateien sind leere
Vorlagen, bereit für eine neue Sprache.

## Format

```yaml
# DE: "Party erstellen"
lobby-server.partyGuiCreate: "Party erstellen"
```

- Der Key hat die Form `<modul>.<key>` — das Präfix (`proxy-plugin`, `lobby-server`,
  `duels-server`, `realms-server`) sagt, zu welchem Server der Text gehört, weil derselbe Key-Name
  in mehreren Modulen unterschiedliche Bedeutung haben kann (z. B. `backButton` gibt's dreimal).
- Der `# DE: "..."`-Kommentar zeigt den aktuellen deutschen Text zur Orientierung, was gemeint ist.
- **`§`-Zeichen** (z. B. `§a`, `§c`, `§7`, `§l`) sind Minecraft-Farb-/Formatierungscodes — bitte in
  der Übersetzung erhalten (§a = grün, §c = rot, §7 = grau, §l = fett, ...).
- **`%PLATZHALTER%`** (z. B. `%PLAYER%`, `%NAME%`, `%KIT%`) werden zur Laufzeit durch echte Werte
  ersetzt — der Platzhalter-Name muss **exakt** erhalten bleiben, nur seine Position im Satz darf
  sich pro Sprache anpassen.

## Eine neue Sprache hinzufügen

1. Die passende `lang/<code>.yml` öffnen (Code aus der Minecraft-Sprachliste, z. B. `es_es.yml`
   für Spanisch)
2. Jeden `"": ""`-Wert mit der Übersetzung füllen (der `# DE`-Kommentar zeigt was gemeint ist)
3. Fertige Datei hier committen/pushen

## Rückführung in den Code

Diese Dateien sind eine Ausfüll-Vorlage, kein Live-System — sie werden NICHT automatisch vom
Netzwerk gelesen. Ausgefüllte Werte müssen manuell (oder per Skript) zurück in die jeweilige
`Lang.java` übertragen werden (`<modul>/src/main/java/net/kryven/<modul>/lang/Lang.java`), dort
als `Map.entry("key", "wert")` im passenden Sprachblock. Neue Sprachen brauchen zusätzlich eine
kleine Code-Änderung (neuer Sprachblock + `Lang.isSupported()` erweitern).
