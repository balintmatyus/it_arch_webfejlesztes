# Gyakorló Feladatok - JavaScript Objektumok és Tömbök



## **1. feladat: Könyvtári katalógus**

### Kiinduló állapot
Egy kis iskolai könyvtár digitális nyilvántartását kell elkészítened. A könyvtáros szeretné követni, hogy mely könyvek vannak a polcokon, és melyek vannak éppen kikölcsönözve.

### Lépések

**A) Hozz létre egy könyv objektumot**

Készíts egy `konyv1` nevű objektumot, amely a következő tulajdonságokkal rendelkezik:
- `cim`: a könyv címe (pl. "Az öreg halász és a tenger")
- `szerzo`: a szerző neve
- `oldalszam`: hány oldalas a könyv (szám típus!)
- `kolcsonozve`: logikai érték, hogy éppen ki van-e kölcsönözve

Adj hozzá egy `adatokKiirasa` nevű metódust is, amely a konzolra kiírja a könyv adatait olvasható formában. Használd a `this` kulcsszót a tulajdonságok eléréséhez!

**Gondolkodtató:** Hogyan tudod egy metóduson belül hivatkozni az objektum saját tulajdonságaira?



**B) Készíts katalógust (tömböt)**

Hozz létre egy `konyvtar` nevű üres tömböt, amely a könyveket fogja tárolni.



**C) Könyvek hozzáadása**

- Adj hozzá 3-4 könyvet a katalógushoz. Használd a megfelelő tömb metódust!
- Írd ki a konzolra, hogy hány könyv van összesen a katalógusban.

**Tipp:** Melyik tulajdonság mondja meg egy tömb hosszát?



**D) Legutolsó könyv eltávolítása**

Valaki kivette az utolsó könyvet a rendszerből (hibás bevitel volt). Távolítsd el a legutolsó elemet a tömbből, és írd ki, hogy melyik könyvet távolítottad el.

**Tipp:** Van egy metódus, amely kifejezetten az utolsó elemet távolítja el ÉS vissza is adja azt.



**E) Új könyv az elejére**

Érkezett egy új beszerzés, ami prioritást kap. Add hozzá egy új könyv objektumot a tömb **elejéhez**.

**Gondolkodtató:** Melyik metódus ad hozzá elemet a tömb elejéhez, nem a végéhez?



## **2. feladat: Termék leltár**

### Kiinduló állapot
Egy kisvállalkozás raktárkészletét kell nyilvántartanod. A termékeknél a nevet és az egységárat tárolják.

```javascript
const termekek = [
    { nev: "Laptop", ar: 250000 },
    { nev: "Egér", ar: 5000 },
    { nev: "Billentyűzet", ar: 15000 },
    { nev: "Monitor", ar: 80000 },
    { nev: "Webkamera", ar: 12000 }
];
```

### Lépések

**A) Listázd ki az összes terméket**

Írd ki a konzolra az összes termék nevét és árát olvasható formában (pl. "Laptop - 250000 Ft"). 

**Gondolkodtató:** Melyik ciklus típust érdemes használni, ha nem kell az index, csak az értékek kellenek?



**B) Keress egy konkrét terméket**

Kérdezd le, hogy a "Monitor" termék hányadik helyen található a tömbben (hanyadik index).

**Tipp:** Van egy metódus, amely egy keresett elem indexét adja vissza. Mit ad vissza, ha nem találja?



**C) Számítsd ki az összes termék átlagárát**

Járd be a tömböt, add össze az árakat, majd oszd el a termékek számával.

**Gondolkodtató:** Milyen kezdőértékkel kell indítanod egy összeadást? Hogyan jutasz hozzá egy termék `ar` tulajdonságához a cikluson belül?



**D) Drága termékek számlálása**

Számold meg, hogy hány olyan termék van, amelynek az ára meghaladja a 20000 Ft-ot. Használj egy számlálót és egy feltételes utasítást a cikluson belül!



**E) Termékrotáció**

Az első terméket mozgasd a lista végére (szimulálva egy raktári rotációt):
- Távolítsd el az első elemet
- Add hozzá a tömb végéhez

Írd ki az új sorrendet!

**Tipp:** Van metódus a tömb elejéről való eltávolításra, és van a végére való hozzáadásra is.



## **3. feladat: Hallgatói eredmények feldolgozása**

### Kiinduló állapot
Egy vizsga eredményeit kaptad meg pontszámokban (0-100 skálán). Ezeket kell feldolgoznod és különböző riportokat készítened.

```javascript
const pontszamok = [85, 92, 78, 45, 67, 88, 91, 34, 72, 95];
```

### Lépések

**A) Alakítsd át a pontszámokat százalékká**

Hozz létre egy új tömböt, amely minden pontszámhoz egy szöveget tartalmaz: `"85%"`, `"92%"` stb.

**Gondolkodtató:** Melyik tömb metódus hoz létre új tömböt úgy, hogy minden elemet átalakít? Hogyan fűzhetsz össze egy számot egy szöveggel?



**B) Szűrd ki a bukott hallgatókat**

Készíts egy új tömböt csak azokkal a pontszámokkal, amelyek 50 alatt vannak (bukás).

**Tipp:** Melyik metódus választja ki azokat az elemeket, amelyek megfelelnek egy feltételnek?

**Próbáld ki:** Módosítsd a feltételt úgy, hogy a sikeres (50 vagy feletti) pontszámokat kapd meg!



**C) Számítsd ki a sikeres vizsgák átlagát**

Kombináld a szűrést és az átlagszámítást:
1. Először szűrd ki a sikeres vizsgákat (50 vagy magasabb)
2. Majd számítsd ki ezek átlagát

**Gondolkodtató:** Hogyan lehet egy metódus eredményén (ami egy tömb) további műveleteket végezni?



**D) Többszintű szűrés**

Készíts egy új tömböt, amely csak a "közepes" eredményeket tartalmazza: 60 és 80 közötti pontszámok (mindkettő beleértve).

**Tipp:** Egy `filter()` feltételében használhatsz `&&` (és) operátort két feltétel egyidejű ellenőrzésére.



**E) Láncolt műveletek**

Egyetlen utasításban (metóduslánccal):
1. Szűrd ki a 70 feletti pontszámokat
2. Alakítsd át őket úgy, hogy mindegyikhez hozzáadsz 5 bónuszpontot
3. Az eredményt tárold egy új tömbben

**Gondolkodtató:** Hogyan lehet egy `filter()` után közvetlenül `map()`-et hívni?



## **4. feladat: Versenyeredmények rangsorolása**

### Kiinduló állapot
Egy atlétikai verseny futóinak eredményeit kell feldolgoznod és különböző szempontok szerint rangsorolnod.

```javascript
const versenyzok = [
    { nev: "Kiss Anna", orszag: "Magyarország", ido: 12.5 },
    { nev: "Smith John", orszag: "USA", ido: 11.8 },
    { nev: "Müller Hans", orszag: "Németország", ido: 12.1 },
    { nev: "Kovács Béla", orszag: "Magyarország", ido: 13.2 },
    { nev: "Dubois Marie", orszag: "Franciaország", ido: 11.9 }
];
```

### Lépések

**A) Rendezd ABC sorrendbe a neveket**

Rendezd a versenyzőket név szerint, ábécé sorrendben. Írd ki az eredményt!

**Figyelem:** A `sort()` módosítja az eredeti tömböt! Gondolkodj el, hogy szeretnéd-e megőrizni az eredeti sorrendet is.

**Tipp stringekhez:** A `localeCompare()` metódus a legmegbízhatóbb szövegek összehasonlítására.



**B) Rangsorold eredmény szerint (legjobb → legrosszabb)**

Rendezd a versenyzőket idő szerint, ahol a legkisebb idő (leggyorsabb) az első.

**Gondolkodtató:** Milyen összehasonlító függvényt kell írnod számokhoz? Emlékszel, hogy `a - b` növekvő vagy csökkenő sorrendet ad?



**C) Fordított rangsor**

Most rendezd úgy, hogy a leglassabb legyen elöl (csökkenő idő szerint).

**Tipp:** Csak a kivonás sorrendjét kell megfordítanod az összehasonlító függvényben.



**D) Védett rendezés**

Mielőtt újra rendeznél, készíts egy másolatot a tömbről, hogy az eredeti sorrend megmaradjon!

Rendezd országonként ABC sorrendbe ezt az új tömböt.

**Gondolkodtató:** Hogyan tudsz egy tömb másolatot készíteni? (Tipp: spread operátor `[...eredeti]` vagy `slice()`)



**E) Hibakeresés: Miért hibás ez a rendezés?**

Futtasd le a következő kódot és figyeld meg az eredményt:

```javascript
const idok = [12.5, 11.8, 12.1, 13.2, 11.9];
idok.sort();
console.log(idok);
```

**Kérdések:**
- Helyes a sorrend? Miért nem?
- Mit kellene használnod összehasonlító függvény helyett?
- Javítsd ki a kódot!



## **5. feladat: Online áruház kezelő (Komplex integráció)**

### Kiinduló állapot
Egy webáruház termékkatalógusát kell kezelned. Minden termék objektum a következő adatokat tartalmazza:

```javascript
const termekek = [
    { id: 1, nev: "Okostelefon", ar: 150000, kategoria: "Elektronika", keszlet: 15 },
    { id: 2, nev: "Laptop", ar: 300000, kategoria: "Elektronika", keszlet: 0 },
    { id: 3, nev: "Póló", ar: 5000, kategoria: "Ruházat", keszlet: 50 },
    { id: 4, nev: "Futócipő", ar: 25000, kategoria: "Sport", keszlet: 8 },
    { id: 5, nev: "Könyv", ar: 4000, kategoria: "Könyv", keszlet: 30 },
    { id: 6, nev: "Fejhallgató", ar: 15000, kategoria: "Elektronika", keszlet: 12 },
    { id: 7, nev: "Hátizsák", ar: 18000, kategoria: "Sport", keszlet: 0 }
];
```

### Lépések

**A) Black Friday akció - Árcsökkentés**

Készíts egy új tömböt, ahol az összes Elektronika kategóriájú termék ára 20%-kal csökkentett. A többi termék eredeti áron marad.

**Gondolkodtató:** 
- Melyik metódussal alakíthatsz át minden elemet?
- Hogyan ellenőrzöd a kategóriát?
- Hogyan számolod a 20%-os csökkentést? (Tipp: eredeti ár * 0.8)

**B) Csak raktáron lévő termékek**

Szűrd ki azokat a termékeket, amelyek raktáron vannak (készlet > 0). Az eredményt tárold egy új változóban.

**Tipp:** Ez egy egyszerű `filter()` művelet egy feltétellel.

**C) Kategóriánkénti szűrés és számítás**

Válaszd ki csak a "Sport" kategóriájú termékeket, majd számítsd ki, hogy összesen mekkora értékben van Sport termék a raktárban (ár × készlet mindegyiknél, majd összeadva).

**Gondolkodtató:** 
1. Először szűrés kategória alapján
2. Majd egy ciklus vagy `map()` az értékek kiszámítására
3. Végül összegzés

**D) Árrangsor készítése**

Rendezd a termékeket ár szerint csökkenő sorrendbe (legdrágább elől), de csak azokat, amelyek raktáron vannak!

Írd ki az első 3 legdrágább, raktáron lévő terméket!

**Lépések:**
1. Szűrés (készlet > 0)
2. Rendezés (ár szerint csökkenő)
3. Az első 3 elem kiírása

**Tipp:** A tömb első N elemét elérheted indexszel vagy a `.slice(0, 3)` metódussal.

**E) Bevásárlókosár objektum metódusokkal**

Készíts egy `kosar` objektumot a következő metódusokkal:

```javascript
const kosar = {
    termekek: [],  // üres tömb a kosárban lévő termékeknek
    
    hozzaad: function(termek) {
        // Add hozzá a terméket a kosárhoz
        // Írd ki: "Hozzáadva: [terméknév]"
    },
    
    eltavolit: function(termekId) {
        // Távolítsd el a terméket ID alapján
        // Tipp: indexOf() + splice() vagy filter()
    },
    
    osszegez: function() {
        // Számítsd ki és írd ki a kosár összértékét
        // Tipp: Végigmenni a termékek tömbjén és összeadni az árakat
    },
    
    listaz: function() {
        // Írd ki az összes kosárban lévő termék nevét és árát
    }
};
```

**Feladat:** 
1. Valósítsd meg a metódusokat!
2. Teszteld: adj hozzá 3 terméket, távolíts el egyet ID alapján, számold ki az összeget!

**Gondolkodtató:** 
- A metódusokon belül hogyan éred el a `termekek` tömböt? (`this.termekek`)
- Az `eltavolit` metódusnál hogyan találod meg a terméket ID alapján?
- Az `osszegez` metódusnál hogyan adsz össze értékeket egy tömbből?



**Bónusz kihívás:** Módosítsd a `kosar` objektumot úgy, hogy ne a teljes termék objektumot tárolja, hanem csak az ID-t és a darabszámot. Így ugyanabból a termékből többet is lehet vásárolni!



## Megoldás után

Miután végeztél a feladatokkal, érdemes átgondolni:
- Melyik metódus módosítja az eredeti tömböt, és melyik hoz létre újat?
- Mikor használsz `for...of` ciklust és mikor `map()`/`filter()`-t?
- Hogyan kombinálhatod a metódusokat (láncolás)?
- Mikor kell összehasonlító függvényt használnod a `sort()`-nál?