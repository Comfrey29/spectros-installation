# SpectrOS Apps v2.0 — ArCom Corporation

Apps GTK3 per a SpectrOS (FreeBSD base), completament reescrites des de zero.

---

## 📦 Contingut

```
spectros-apps-v2/
├── spectros-config/
│   └── spectros-config.py       # Panell configuració (6 pestanyes)
├── spectros-filemanager/
│   └── spectros-filemanager.py  # Gestor fitxers 3 panells
├── spectros-shop/
│   └── spectros-shop.py         # Botiga de programari
├── spectros-updater/
│   └── spectros-updater.py      # Actualitzador (GitHub)
└── version.json                 # Pujar a Comfrey29/spectros-updater
```

---

## ⚙️ spectros-config.py

**6 pestanyes funcionals:**

| Pestanya    | Contingut                                                       |
|-------------|-----------------------------------------------------------------|
| 🌐 General  | Hostname, SO, kernel, uptime, zona horària. Editor de hostname. |
| 💻 Sistema  | CPU, RAM, disc, serveis amb switchs on/off.                     |
| 👤 Usuaris  | Llistat d'usuaris (uid≥1000), crear usuari, canviar contrasenya.|
| 📶 WIFI     | ifconfig, escaneig de xarxes, connectar amb WPA.                |
| 🔵 Bluetooth| hccontrol, activar/desactivar, escaneig, emparellament.         |
| 🔄 Updater  | pkg audit, pkg upgrade -n, freebsd-update, llançar Updater.     |

---

## 🗂️ spectros-filemanager.py

**Millores respecte v1:**
- GTK3 correcte (sense errors d'API)
- Icones per extensió (30+ tipus)
- Previsualització d'imatges (GdkPixbuf escalat)
- Previsualització de text (primeres 3000 chars)
- Propietats de fitxer (mida, data, permisos, UID/GID)
- Barra de navegació amb historial enrere/endavant/amunt
- Barra de cerca integrada amb filtratge en temps real
- Menú contextual (obrir, copiar ruta, propietats, suprimir)
- Ordenació per nom/mida/data fent clic a les capçaleres
- Barra d'estat amb recompte d'elements

---

## 🛒 spectros-shop.py

**Dues seccions:**

### ArCom Apps (10 apps)
- SpectrOS Config, FileManager, Updater (ja instal·lats)
- ArCom Terminal, TextEditor, ImageViewer, PDFReader
- ArCom SystemMonitor (gratis)
- ArCom Backup (4,99 €), ArCom VPN Client (9,99 €/any)

### FreeBSD / Codi Obert (12 paquets)
Firefox, LibreOffice, VLC, GIMP, Inkscape, Thunderbird,
Vim, Git, Audacity, Transmission, Calibre, KeePassXC

**Funcionalitats:**
- Filtre per categoria i cerca en temps real
- Botó "Instal·lar" → `pkexec pkg install -y <paquet>`
- Botó "Comprar" per apps de pagament → web ArCom
- Franja de donació al peu
- Barra d'estat amb recompte filtrat

---

## 🔄 spectros-updater.py

**Connexió real a GitHub:**
- URL: `https://raw.githubusercontent.com/Comfrey29/spectros-updater/main/version.json`
- Compara versió local vs. remota amb comparació semàntica (1.2.3)
- Mostra changelog del `version.json`
- Diàleg de confirmació si hi ha nova versió → obre GitHub Releases
- Secció d'actualitzacions de sistema: `pkg upgrade` i `freebsd-update`
- Tots els comandos via `pkexec` (no cal ser root directament)

---

## 🔧 Instal·lació

### Dependències
```sh
pkg install python3 py39-gobject3 gtk3 py39-pip
```

### Còpia als directoris
```sh
cp spectros-config.py    /usr/local/bin/spectros/
cp spectros-filemanager.py /usr/local/bin/spectros/
cp spectros-shop.py      /usr/local/bin/spectros/
cp spectros-updater.py   /usr/local/bin/spectros/
chmod +x /usr/local/bin/spectros/*.py
```

### Repositori GitHub Updater
Puja `version.json` a `Comfrey29/spectros-updater` a la branca `main`.
Quan vulguis publicar una nova versió, edita el fitxer canviant:
- `"version"`: nou número de versió (ex: `"1.1.0"`)
- `"date"`: data de llançament
- `"changelog"`: notes de la nova versió

L'Updater ho detectarà automàticament la propera vegada que els usuaris premem "Comprovar actualitzacions".

---

**ArCom Corporation © 2026**
⚠️ This is proprietary software.
Unauthorized copying, redistribution, or modification outside the license is strictly prohibited.
