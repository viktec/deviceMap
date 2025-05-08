# deviceMap

LibreNMS plugin to locate indoor devices using LeafletJS and multi-level floor mapping.

---

## 🇮🇹 Descrizione

**deviceMap** è un plugin per LibreNMS che consente di:

- Visualizzare i dispositivi all'interno di edifici su una mappa indoor
- Supportare più piani (es. livello 0, 1, 2...)
- Mostrare lo stato dei dispositivi (es. Switch e Router ON/OFF)
- Mostrare lo stato delle **singole porte** (UP/DOWN)
- Gestire icone dinamiche in base allo zoom

---

## 🇬🇧 Description

**deviceMap** is a LibreNMS plugin to:

- Display devices inside buildings on an indoor map
- Support multiple floors (e.g. level 0, 1, 2...)
- Show device status (Switch/Router ON/OFF)
- Show **individual port status** (UP/DOWN)
- Use dynamic icons depending on zoom level

---

## 🛠️ Installazione / Installation

1. Clona il repository:

```bash
cd /opt/librenms/html/plugins/
git clone https://github.com/viktec/deviceMap.git deviceMap
```

2. Rinomina il file `config.php.example` in `config.php`:

```bash
cp deviceMap/config.php.example deviceMap/config.php
```

3. Inserisci il tuo API token di LibreNMS nel file `config.php`:

```php
<?php
return [
    'api_token' => 'INSERISCI_IL_TUO_TOKEN'
];
```

---

## 🗂️ File `data.json`

### 🇮🇹

Il file `data.json` è un esempio di struttura GeoJSON per la planimetria di un edificio.  
Ogni oggetto deve contenere una proprietà `level` all'interno di `reltags` per rappresentare il piano.

Puoi usare più file `data.json` per gestire più edifici.

### 🇬🇧

The `data.json` file is an example of a GeoJSON structure for a building floorplan.  
Each object must contain a `level` property inside `reltags` to represent the floor.

You can use multiple `data.json` files to represent multiple buildings.

#### Esempio / Example:
```json
{
  "type": "FeatureCollection",
  "features": [
    {
      "properties": {
        "tags": {
          "buildingpart": "room"
        },
        "relations": [
          {
            "role": "buildingpart",
            "rel": "....",
            "reltags": {
              "height": "4",
              "level": "0",
              "type": "level"
            }
          }
        ],
        "meta": {}
      },
      "geometry": {
        "type": "Polygon",
        "coordinates": [...]
      }
    }
  ]
}
```

---

## 🧭 Creazione della mappa (JOSM)

Puoi generare il file `data.json` usando l’editor [**JOSM**](https://josm.openstreetmap.de/), importando livelli e planimetrie da disegno o da OpenStreetMap.

---

## 📦 Contenuto del plugin

- `deviceMap.php` – codice principale PHP
- `deviceMap.inc.html` – rendering HTML e JavaScript con Leaflet
- `leaflet-indoor.js`, `leaflet-src.js` – librerie di mappatura
- `icone/` – icone personalizzate per dispositivi e porte
- `config.php.example` – configurazione API
- `data.json` – esempio planimetria

---

## ✍️ Autori

Creato da **Vittorio Russo**  
Supervisione: **Antonio Della Selva** – Università degli Studi di Urbino “Carlo Bo”

---

## 🚀 Aggiornamenti

Nuove funzionalità in arrivo... Stay tuned! 😉
