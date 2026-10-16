# Mane Website – Hosting über GitHub + Firebase

Statische Website (8 HTML-Seiten, CSS inline, Bilder via Unsplash). Fertig für Firebase Hosting.

## Dateien
- index.html (Startseite)
- elektroinstallation.html, beleuchtungstechnik.html, smart-home.html, photovoltaik.html, e-check-wartung.html, muellertechnik.html, team.html
- 404.html
- firebase.json

## In 10 Minuten live – auf deinem Windows-PC

### 1. GitHub-Repo erstellen
1. Auf github.com → New repository → Name z.B. `mane-website`, Public, ohne README → Create
2. In PowerShell (in deinem Ordner `Mane Website`):

```powershell
cd "C:\Users\mrstr\Desktop\Mane Website"
git init
git add .
git commit -m "Website live"
git branch -M main
git remote add origin https://github.com/DEIN-NAME/mane-website.git
git push -u origin main
```

### 2. Firebase-Projekt erstellen
1. https://console.firebase.google.com → Add project → Name z.B. `mane-website` → ohne Analytics ok → Create
2. Node.js LTS installieren: https://nodejs.org (falls noch nicht da)
3. In PowerShell:
```powershell
npm install -g firebase-tools
firebase login
cd "C:\Users\mrstr\Desktop\Mane Website"
firebase init hosting
```
Bei `firebase init` wählen:
- `Use an existing project` → dein Projekt wählen
- `public directory`: `.` (Punkt! weil index.html direkt im Ordner liegt)
- `single-page app`: `No`
- `Set up automatic builds with GitHub`: `Yes` → Repo wählen

Die Datei `firebase.json` hier im Ordner passt bereits, du kannst sie einfach behalten.

### 3. Deployen
```powershell
firebase deploy
```
→ Du bekommst eine URL wie `https://DEIN-PROJEKT.web.app` – fertig!

Danach reicht bei jeder Änderung:
```powershell
git add .
git commit -m "Update"
git push
```
→ Firebase deployed automatisch neu (wenn GitHub-Integration aktiviert).

### Hinweise zu deiner Seite
- Alle internen Links (z.B. elektroinstallation.html) funktionieren – alle 8 Dateien müssen im selben Ordner auf GitHub liegen.
- Hero-Bild auf Startseite hat aktuell `url('')` (leer) → ggf. Bild-URL eintragen wie auf den Unterseiten.
- Kontaktformular nutzt `mailto:` – funktioniert ohne Backend, öffnet E-Mail-Programm des Besuchers.
