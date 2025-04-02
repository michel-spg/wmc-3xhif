---
title: Node.js & Express
nav_order: 4
layout: default
parent: JavaScript
---

![bg left:50% 80%](../../assets/imgs/spg_logo.png)

# JS – Node.js & Express

## Erstellung eines Node.js-Projekts

Initialisiere dein Projekt mit:

```bash
npm init
```

- Im gewünschten Projektverzeichnis ausführen
- Erstellt die Datei `package.json`
  - Enthält z. B. `dependencies`
  - Standardwerte können übernommen oder leer gelassen werden

---

## Package: Express

- **Express** ist ein **Framework für Webapplikationen** mit Node.js
- Besonders geeignet für die **Erstellung von APIs**

### Installation

Installiere Express via NPM:

```bash
npm install express
```

- Dies erstellt den Ordner `node_modules` und die Datei `package-lock.json`
- `node_modules` enthält alle Abhängigkeiten
- `package-lock.json` enthält die genaue Version der installierten Pakete
- `package.json` wird aktualisiert und enthält nun die Abhängigkeit `express`

---

## Einfacher Webserver mit Express

Datei: `app.js`

```javascript
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

---

## Webserver ausführen

```bash
node app.js
```

Dann im Browser öffnen:

```
http://localhost:3000/
```

Du solltest dort sehen: `Hello World!`

---
