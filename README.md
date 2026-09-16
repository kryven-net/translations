# kryven.net — Übersetzungen

Vorlagen für die Texte des Netzwerks, eine Datei pro Server/Modul:

| Datei | Server | Zweck |
|---|---|---|
| `proxy-plugin.yml` | Velocity-Proxy | MOTD, Party, Mod-Block, Tab-Liste, Bans, Freunde, Clans |
| `lobby-server.yml` | Lobby | Navigator, Party-GUI, Profil, Einstellungen, Onboarding |
| `duels-server.yml` | Duelle | Warteschlange, Kits, Bestenliste, Elo, Herausforderungen |
| `realms-server.yml` | Realms | Eigene Welten, Whitelist, Code-Block-System |

## Wie ausfüllen

Jeder Eintrag sieht so aus:

```yaml
# DE (aktuell im Code, nur zur Orientierung): "Party erstellen"
partyGuiCreate:
  de: ""
  en: ""
  fr: ""
```

- Der `# DE (...)`-Kommentar zeigt, was **aktuell im Spiel** an dieser Stelle steht — nur als
  Referenz, damit klar ist, worum es geht. Keine Vorgabe zum Abtippen.
- Darunter `de`/`en`/`fr` bitte von einem Menschen mit eigenen Worten ausfüllen.
- **`§`-Zeichen** (z. B. `§a`, `§c`, `§7`, `§l`) sind Minecraft-Farb-/Formatierungscodes — bitte
  in der Übersetzung an sinnvoller Stelle erhalten (§a = grün, §c = rot, §7 = grau, §l = fett, ...).
- **`%PLATZHALTER%`** (z. B. `%PLAYER%`, `%NAME%`, `%KIT%`) werden zur Laufzeit durch echte Werte
  ersetzt — der Platzhalter-Name muss **exakt** erhalten bleiben, nur seine Position im Satz darf
  sich pro Sprache anpassen.
- Der `Key` (z. B. `partyGuiCreate`) links vom Doppelpunkt bleibt **unverändert** - er ist die
  technische Kennung, keine Übersetzung.

## Rückführung in den Code

Diese Dateien sind eine Ausfüll-Vorlage, kein Live-System — sie werden NICHT automatisch vom
Netzwerk gelesen. Ausgefüllte Werte müssen manuell (oder per Skript) zurück in die jeweilige
`Lang.java` des Moduls übertragen werden (`<modul>-server/src/main/java/net/kryven/<modul>/lang/Lang.java`
bzw. `proxy-plugin/.../lang/Lang.java`), dort als `Map.entry("key", "wert")` in den passenden
Sprachblock (`"de"`, `"en"`, `"fr"`).
