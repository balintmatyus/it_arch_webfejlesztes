# Gyakorló Feladatok - JavaScript DOM manipuláció és események

## **1. feladat: Termékek megjelenítése táblázatban**

### Kiinduló állapot

Egy webáruház termékadatait kaptad JSON formátumban. A feladatod, hogy ezeket az adatokat dinamikusan jelenítsd meg egy HTML táblázatban a DOM manipuláció segítségével.

```javascript
const termekek = [
    { id: 1, nev: "Wireless egér", kategoria: "Elektronika", ar: 8500, keszlet: 23 },
    { id: 2, nev: "USB-C kábel", kategoria: "Kiegészítők", ar: 2500, keszlet: 150 },
    { id: 3, nev: "Laptop táska", kategoria: "Kiegészítők", ar: 12000, keszlet: 8 },
    { id: 4, nev: "Bluetooth hangszóró", kategoria: "Elektronika", ar: 15000, keszlet: 0 },
    { id: 5, nev: "Webkamera", kategoria: "Elektronika", ar: 18000, keszlet: 12 },
    { id: 6, nev: "Monitor állvány", kategoria: "Kiegészítők", ar: 9500, keszlet: 15 },
    { id: 7, nev: "Mechanikus billentyűzet", kategoria: "Elektronika", ar: 25000, keszlet: 5 },
    { id: 8, nev: "HDMI kábel", kategoria: "Kiegészítők", ar: 3000, keszlet: 89 }
];
```

### HTML kiinduló struktúra

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terméklista</title>
    <style>
        table {
            border-collapse: collapse;
            width: 100%;
            margin: 20px 0;
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            text-align: left;
        }
        
        th {
            background-color: #4CAF50;
            color: white;
        }
        
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
        
        .keszlet-nincs {
            color: red;
            font-weight: bold;
        }
        
        .keszlet-keves {
            color: orange;
        }
    </style>
</head>
<body>
    <h1>Terméklista</h1>
    <div id="tablazat-container"></div>
    
    <script src="script.js"></script>
</body>
</html>
```

### Lépések

**A) Táblázat alapstruktúrájának létrehozása**

Hozd létre a táblázat vázát JavaScriptben:
- Készíts egy `<table>` elemet
- Add hozzá a fejlécet (`<thead>`) a következő oszlopokkal: "ID", "Terméknév", "Kategória", "Ár (Ft)", "Készlet"
- Hozz létre egy üres `<tbody>` elemet a termékek számára
- Add hozzá a táblázatot a `tablazat-container` div-hez

**Tipp:** Használd a `document.createElement()` és `appendChild()` metódusokat!

```javascript
function tablazatLetrehozas() {
    // 1. Táblázat létrehozása
    const tabla = document.createElement("table");
    
    // 2. Fejléc létrehozása
    const thead = document.createElement("thead");
    const fejlecSor = document.createElement("tr");
    
    // Oszlopnevek tömbje
    const oszlopnevek = ["ID", "Terméknév", "Kategória", "Ár (Ft)", "Készlet"];
    
    // TODO: Ciklussal hozd létre a th elemeket és add hozzá a fejlécsorhoz
    
    // 3. Tbody létrehozása
    const tbody = document.createElement("tbody");
    
    // TODO: Add hozzá a thead-et és tbody-t a táblázathoz
    
    // 4. Táblázat hozzáadása a containerhez
    // TODO: Keresd meg a container elemet és add hozzá a táblázatot
    
    return tbody; // Visszaadjuk, mert később ebbe tesszük a terméksorokat
}
```

---

**B) Terméksorok generálása**

Írd meg azt a függvényt, amely végigmegy a `termekek` tömbön, és minden termékhez létrehoz egy sort a táblázatban.

```javascript
function termekekMegjelenites(tbody) {
    // TODO: Menj végig a termekek tömbön
    // Minden termékhez:
    // 1. Hozz létre egy sort (tr)
    // 2. Hozz létre 5 cellát (td) az adatoknak
    // 3. Állítsd be a cellák tartalmát (innerHTML vagy textContent)
    // 4. Add hozzá a cellákat a sorhoz
    // 5. Add hozzá a sort a tbody-hoz
}
```

**Segítség a cella létrehozásához:**
```javascript
const idCella = document.createElement("td");
idCella.textContent = termek.id;
```

---

**C) Feltételes formázás készletre**

Módosítsd a készlet cella megjelenítését:
- Ha a készlet 0, add hozzá a `keszlet-nincs` CSS osztályt (piros, vastag betű)
- Ha a készlet 1-10 között van, add hozzá a `keszlet-keves` CSS osztályt (narancssárga)

**Tipp:** Használd a `classList.add()` metódust!

```javascript
// Példa:
if (termek.keszlet === 0) {
    keszletCella.classList.add("keszlet-nincs");
} else if (termek.keszlet >= 1 && termek.keszlet <= 10) {
    keszletCella.classList.add("keszlet-keves");
}
```

---

**D) Ár formázása**

Az ár celláknál jelenítsd meg az árat ezres tagolással és "Ft" végződéssel (pl. "8 500 Ft").

**Tipp:** Használd a `toLocaleString('hu-HU')` metódust!

```javascript
const formataltAr = termek.ar.toLocaleString('hu-HU') + " Ft";
```

---

**E) A program összeállítása**

Hívd meg a megfelelő sorrendben a függvényeket, amikor az oldal betöltődött:

```javascript
// Amikor az oldal betöltődik
window.addEventListener('load', function() {
    const tbody = tablazatLetrehozas();
    termekekMegjelenites(tbody);
});
```

---

## **2. feladat: Termékek szűrése név alapján**

### Kiinduló állapot

Bővítsd az előző feladatot úgy, hogy a felhasználó egy beviteli mező és egy gomb segítségével szűrhesse a termékeket név szerint.

### HTML bővítése

Add hozzá a következő HTML kódot a `<h1>` címsor alá, a táblázat elé:

```html
<div style="margin: 20px 0;">
    <label for="kereses">Keresés terméknévre:</label>
    <input type="text" id="kereses" placeholder="Írd be a termék nevét...">
    <button id="kereses-gomb">Keresés</button>
</div>
```

* A `label for="kereses"` egy szöveges címke. Arra szolgál, hogy leírja egy űrlapmező (mint például egy input) funkcióját.
* Az `input` maga a beviteli mező, ahová a felhasználó gépelni tud. A `type="text"` jelzi, hogy ez egy sima, egysoros szöveges mező.
* A `button` lesz a kattintható gomb, amivel keresés indítható.

### Lépések

**A) Alapszintű szűrés - Pontos egyezés**

Írd meg azt a függvényt, amely a keresőmezőbe írt szöveg alapján szűri a termékeket (pontos egyezés, kis- és nagybetű érzékeny).

```javascript
function termekekSzures() {
    // 1. Keresd meg a keresőmező elemet
    const keresoMezo = document.getElementById("kereses");
    
    // 2. Olvasd ki az értékét
    const keresettNev = keresoMezo.value;
    
    // 3. Szűrd a termékek tömböt
    // TODO: Használj filter() metódust, amely csak azokat a termékeket adja vissza,
    // amelyek neve pontosan megegyezik a keresett névvel
    
    // 4. Frissítsd a táblázatot a szűrt eredménnyel
    // TODO: Töröld a tbody tartalmát
    // TODO: Jelenítsd meg a szűrt termékeket
}
```

---

**B) Eseménykezelő hozzáadása**

Add hozzá az eseménykezelőt a gombhoz, hogy kattintásra frissüljön a lista.

```javascript
window.addEventListener('load', function() {
    const tbody = tablazatLetrehozas();
    termekekMegjelenites(tbody);
    
    // Eseménykezelő a keresés gombhoz
    const keresGomb = document.getElementById("kereses-gomb");
    keresGomb.addEventListener("click", termekekSzures);
});
```

> [!NOTE]
> A `click` esemény akkor aktiválódik, amikor a felhasználó rákattint egy elemre (pl. gombra). Ez a leggyakrabban használt esemény interaktív elemek esetén.

---

**C) EXTRA: Részleges egyezés (startsWith)**

Módosítsd a szűrési logikát úgy, hogy ne csak pontos egyezést keressen, hanem minden olyan terméket mutasson, amelynek neve a beírt szöveggel kezdődik.

**Tipp:** Használd a `.toLowerCase()` metódust mindkét oldalon!

```javascript
const szurtTermekek = termekek.filter(termek => {
    return termek.nev.toLowerCase().startsWith(keresettNev.toLowerCase());
});
```

---

**D) EXTRA: Kijelzés, ha nincs találat**

Ha a szűrés után nem marad egyetlen termék sem, jelenítsd meg egy üzenetet: "Nincs találat a keresésre."

```javascript
function termekekSzures() {
    // ... előző kód ...
    
    const szurtTermekek = termekek.filter(/* ... */);
    
    if (szurtTermekek.length === 0) {
        // TODO: Hozz létre egy sort egyetlen cellával (colspan="5")
        // TODO: Írd bele: "Nincs találat a keresésre."
        // TODO: Add hozzá a tbody-hoz
    } else {
        // TODO: Jelenítsd meg a szűrt termékeket
    }
}
```

**Segítség a colspan használatához:**
```javascript
const uzenetSor = document.createElement("tr");
const uzenetCella = document.createElement("td");
uzenetCella.setAttribute("colspan", "5");
uzenetCella.textContent = "Nincs találat a keresésre.";
uzenetCella.style.textAlign = "center";
uzenetCella.style.fontStyle = "italic";
```

---

**E) EXTRA: Találatok száma**

Jelenítsd meg a keresőmező alatt, hogy hány termék felel meg a keresési feltételnek.

Módosítsd a HTML-t:
```html
<div style="margin: 20px 0;">
    <label for="kereses">Keresés terméknévre:</label>
    <input type="text" id="kereses" placeholder="Írd be a termék nevét...">
    <button id="kereses-gomb">Keresés</button>
    <p id="talalatok-szama"></p>
</div>
```

JavaScript kód:
```javascript
function termekekSzures() {
    // ... szűrési logika ...
    
    // Találatok számának kijelzése
    const talalatokSzamaElem = document.getElementById("talalatok-szama");
    talalatokSzamaElem.textContent = `Találatok száma: ${szurtTermekek.length}`;
}
```