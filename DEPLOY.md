# 🚀 Deployment auf GitHub Pages

## Schritt-für-Schritt Anleitung

### 1. **Repository erstellen**
- Gehe zu [github.com/new](https://github.com/new)
- **Repository name:** `hochzeitstag`
- **Description:** "Online-Grußkarte zum 3. Hochzeitstag"
- Wähle **Public** (damit es über GitHub Pages erreichbar ist)
- Klick **Create repository**

### 2. **Dateien hochladen**
Jetzt sind zwei Optionen möglich:

**Option A: Über GitHub Web-Interface (einfach)**
1. Auf deinem neuen Repository klick auf **"Add file"** → **"Upload files"**
2. Lade diese Dateien hoch:
   - `index.html`
   - `README.md` (dieses hier)
3. Commit mit Nachricht: "Initial commit: Grußkarte"

**Option B: Über Git Command-Line (wenn du Git installed hast)**
```bash
cd /pfad/zu/hochzeitstag
git init
git add index.html README.md DEPLOY.md
git commit -m "Initial commit: Grußkarte"
git branch -M main
git remote add origin https://github.com/klur-tim/hochzeitstag.git
git push -u origin main
```

### 3. **GitHub Pages aktivieren**
1. Gehe in deinem Repository zu **Settings** (oben rechts)
2. Navigiere zu **Pages** (links im Menü)
3. Unter "Build and deployment":
   - Source: Wähle **Deploy from a branch**
   - Branch: Wähle **main** und **/root**
4. Klick **Save**
5. Nach ~1-2 Minuten bekommst du die URL angezeigt: `https://klur-tim.github.io/hochzeitstag/`

### 4. **Musik einfügen (WICHTIG)**
Die Datei `index.html` enthält derzeit einen Platzhalter für die Musik.

**Option A: Spotify (empfohlen)**
- Der Spotify-Track ist bereits im Code eingebunden
- "Liebe ist alles" von Rosenstolz läuft automatisch im Hintergrund
- ✅ Funktioniert auf den meisten Geräten (mit Internet)

**Option B: Lokale MP3 (volle Kontrolle)**
1. Lade eine MP3 von "Liebe ist alles" herunter
2. Benenne sie zu `music.mp3`
3. Lade die Datei in deinen Repository hoch
4. Bearbeite `index.html` und ersetze diese Zeile:
   ```html
   <source src="https://www.youtube.com/watch?v=qO3jHKUhkAM" type="audio/mpeg">
   ```
   Durch:
   ```html
   <source src="./music.mp3" type="audio/mpeg">
   ```
5. Committe die Änderung

### 5. **NFC-Chip programmieren**
1. Besorge dir einen NFC-Sticker/Chip (z.B. NTAG213 oder ähnlich)
2. Nutze eine NFC-App auf deinem Smartphone (z.B. "TagWriter by NXP")
3. Programmiere den Chip mit dieser URL:
   ```
   https://klur-tim.github.io/hochzeitstag/
   ```
4. Speichere auf dem Chip
5. Klebe den Chip auf deine gedruckte Grußkarte

### 6. **Test**
1. Öffne die URL `https://klur-tim.github.io/hochzeitstag/` auf deinem Smartphone
2. Die animierte Grußkarte sollte laden
3. Musik sollte automatisch im Hintergrund spielen (ggf. auf Vollbild tippen für Autoplay)
4. Teste auch mit NFC: Scannen mit Tobias' Handy

---

## 🎵 Musik-Troubleshooting

### Problem: Musik spielt nicht automatisch
**Grund:** Browser-Autoplay-Policies (viele Browser blocken Audio ohne User-Interaktion)

**Lösung:**
- Nutzer muss die Seite einmal antippen → Musik startet
- Oder: Lokale MP3 verwenden (funktioniert besser)

### Problem: Spotify-Embed lädt nicht
**Grund:** Keine Internetverbindung oder Spotify-Blockade

**Lösung:** Lokale MP3 hochladen (Option B oben)

---

## 📋 Checkliste vor dem NFC-Druck

- [ ] Repository erstellt & GitHub Pages aktiviert
- [ ] URL funktioniert: `https://klur-tim.github.io/hochzeitstag/`
- [ ] Animation lädt korrekt
- [ ] Musik spielt (klick auf Seite, falls nötig)
- [ ] Mobile-Responsive (teste auf iPhone & Android)
- [ ] NFC-Chip programmiert
- [ ] Karte gedruckt & NFC-Chip geklebt
- [ ] Final-Test mit Tobias' Handy

---

## 💡 Tipps

- **Backup:** Speichere die `index.html` lokal, bevor du sie auf GitHub uploadest
- **Domain:** Wenn du later eine eigene Domain nutzen möchtest, kannst du die in GitHub Pages konfigurieren
- **Design-Änderungen:** Bearbeite direkt in GitHub oder lade neue Version hoch
- **Link-Kürzen:** Optional kannst du die lange GitHub-URL mit bit.ly oder tinyurl kürzen

---

**Support:** Bei Fragen zu GitHub Pages: https://docs.github.com/en/pages

Viel Erfolg mit der Grußkarte! 🎉💕
