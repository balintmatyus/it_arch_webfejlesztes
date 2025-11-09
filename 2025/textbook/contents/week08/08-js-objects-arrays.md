# JavaScript Objektumok és Tömbök

## Komplex Adattípusok Bevezetése: Objektumok

A JavaScript egy objektumalapú nyelv. Ez az jelenti, hogy szinte mindent objektumként kezel, ami komplex adatokat tárol. Míg az alapvető típusok, mint a `string` vagy `number`, egyetlen elemi értéket tárolnak, az objektumok lehetővé teszik számunkra, hogy összetartozó információkat csoportosítsunk egyetlen elnevezett "konténerbe". Egy **objektum** lényegében egy komplex változó, amely több, elnevezett értéket (kulcs-érték párokat) tárol. Ezek az értékek lehetnek **tulajdonságok** (adatok) vagy **metódusok** (fügvények, amelyek viselkedést definiálnak).

Gondoljunk például egy *hallgatói rekordra*. Egy hallgatónak van például neve, Neptun-kódja és tanulmányi átlaga. Ezeket a különböző típusú adatokat egyetlen objektumban tárolhatjuk.

### Objektumok használata és felépítése

Objektumot létrehozhatunk a literál szintaxissal (kapcsos zárójelekkel).

```javascript
const hallgato = {
    // Tulajdonságok (kulcs: érték párok)
    nev: "Minta János",
    neptunKod: "A1B2C3",
    szak: "Gazdaságinformatikus",
    aktivFelev: true,
    tanulmanyiAtlag: 4.25,

    // Metódus (egy függvény, ami az objektumhoz tartozik)
    koszon: function() {
        // A 'this' kulcsszó az aktuális objektumra (hallgato) hivatkozik
        console.log(`Sziasztok, a nevem ${this.nev} és a Neptun-kódom ${this.neptunKod}.`);
    },

    // Modern (ES6) szintaxis metódusokra
    setAtlag(ujAtlag) {
        if (ujAtlag >= 1.0 && ujAtlag <= 5.0) {
            this.tanulmanyiAtlag = ujAtlag;
            console.log(`A tanulmányi átlag frissítve: ${this.tanulmanyiAtlag}`);
        } else {
            console.error("Érvénytelen átlag!");
        }
    }
};
```

> [!NOTE]
> **Miért `const`?**
>
> A `const` kulcsszót objektumok (és tömbök) esetén azért preferáljuk, mert magát a **hivatkozást (referenciát)** teszi állandóvá, nem az objektum tartalmát.
>
>   * **Megakadályozza:** Azt nem tehetjük meg, hogy a `hallgato` változónak egy teljesen új objektumot vagy más értéket adjunk (`hallgato = { ... }`). Ez hibát dobna.
>   * **Lehetővé teszi:** Azt viszont szabadon megtehetjük, hogy az objektum *belül* lévő tulajdonságait módosítjuk (pl. `hallgato.nev = "Minta Janka"` vagy `hallgato.setAtlag(4.5)`).

| Elemtípus | Leírás | Példák (a `hallgato` objektumból) |
| :--- | :--- | :--- |
| **Tulajdonság** | Az objektumot leíró adat. Meghatározzák az objektum állapotát. | `hallgato.nev` (a hallgató neve), `hallgato.szak` (szak neve). |
| **Metódus** | Az objektumon végrehajtható művelet, azaz egy hozzárendelt függvény. | `hallgato.koszon()` (hallgató köszön), `hallgato.setAtlag(4.1)`. |

### Gyakorlati objektum tulajdonságok

A weboldalunkkal kapcsolatban rengeteg hasznos információt érhetünk el a beépített `document` objektumon keresztül, például:

*   `document.lastModified`: a dokumentum utolsó módosításának ideje.
*   `document.title`: a dokumentum címe.
*   `document.body.style.backgroundColor`: a dokumentum háttérszíne.

## Tömbök (Arrays) – Listák Kezelése

A **tömbök** (arrays) listaszerű objektumok, amelyek több értéket tárolnak egyetlen változónév alatt. Ez a kulcs ahhoz, hogy hatékonyan tudjunk kezelni nagy mennyiségű, hasonló adatot (gondoljunk csak 100 hallgatóra egy évfolyamon!).

### Tömbök létrehozása és elérése

1.  **Létrehozás:** Szögletes zárójelekkel `[]` és vesszővel elválasztott elemekkel. Lehet bennük string, szám, objektum, sőt, akár más tömb is (többdimenziós tömb).

    ```javascript
    const gyumolcsok = ["alma", "körte", "szilva"];
    const vegyesAdatok = ["fa", 795,]; // vegyes típusok engedélyezettek
    ```

2.  **Hossz (Length):** A `length` tulajdonság adja vissza a tömbben lévő elemek számát.
3.  **Indexelés és elérés:** Az elemek számozása **nullától (0)** kezdődik. Az egyes elemeket szögletes zárójelekkel érhetjük el:

    ```javascript
    console.log(gyumolcsok[0]); // "alma"
    console.log(gyumolcsok[gyumolcsok.length - 1]); // Utolsó elem
    ```

4.  **Módosítás:** Az egyes indexekhez új értéket rendelve módosíthatjuk a tömb tartalmát.

    ```javascript
    const kedvencEtelem = ["pizza", "csoki"];
    kedvencEtelem[1] = "tökfőzelék"; // a "csoki" helyére kerül
    ```

5.  **Elem indexének keresése:** Az `indexOf()` metódus visszaadja a keresett elem első előfordulásának indexét, vagy `-1`-et, ha nem találja.

### Elemek hozzáadása és eltávolítása

| Metódus | Leírás | Hol történik a módosítás? | Visszatérési érték | Forrás |
| :--- | :--- | :--- | :--- | :--- |
| `push()` | Egy vagy több elemet ad a tömb végéhez. | Vég | A tömb új hossza. | |
| `pop()` | Eltávolítja az utolsó elemet. | Vég | Az eltávolított elem. | |
| `unshift()` | Egy vagy több elemet ad a tömb elejéhez. | Eleje | A tömb új hossza. | |
| `shift()` | Eltávolítja az első elemet. | Eleje | Az eltávolított elem. | |
| `splice(i, n)` | Eltávolítja az $i$-edik indextől kezdve $n$ darab elemet. | Bárhol | Az eltávolított elemek tömbje. | |

## Adatfolyam kezelése

A nagy mennyiségű adat (pl. táblázatok, felhasználói listák) kezelésének kulcsa, hogy képesek legyünk végigmenni a tömbökön, szűrni őket, vagy átalakítani az elemeket.

### Iteráció

A ciklusok arra szolgálnak, hogy elvégezzünk egy feladatot a tömb minden elemén.

*   **`for...of` ciklus (Érték-alapú iteráció)**: Ezzel a ciklussal közvetlenül a tömb **értékein** (elemein) tudunk végigmenni, indexek használata nélkül. Ez a leggyakrabban használt és legolvashatóbb módszer tömbök bejárására.

    ```javascript
    for (const elem of tomb_nev) {
      console.log(elem); // Elem értékét kapjuk meg
    }
    ```

*   **`for...in` ciklus (Kulcs-alapú iteráció)**: Ezt a ciklust inkább **objektumok tulajdonságainak kulcsain** (nevein) való iterálásra használjuk, nem tömbök elemeinek bejárására. Tömböknél a kulcsok az indexek.

*   **Hagyományos `for` ciklus**: Akkor hasznos, ha feltétlenül szükségünk van az aktuális indexre, vagy ha speciális számlálást akarunk végezni.

    ```javascript
    for (let i = 0; i < tomb.length; i++) {
      console.log(`Elem az indexen ${i}: ${tomb[i]}`);
    }
    ```

### Leképezés (`map()`)

A `map()` metódus minden elemet átalakít egy tömbön belül a megadott függvény szerint, majd az eredményekből egy **új tömböt** hoz létre.

**Például:** Tömb elemeinek megkettőzése: [1,2,3] --> [2,4,6]

```javascript
// 1. Az eredeti tömb
const szamok = [1, 2, 3];

// 2. Definiáljuk a logikát egy különálló, elnevezett függvényben
// Ez a függvény egyetlen számot vár (amit "egySzam"-nak nevezünk)
// és visszaadja annak a dupláját.
function duplazoFuggveny(egySzam) {
    return 2 * egySzam;
}

// 3. A .map() metódus hívása
// A map-nek átadjuk a 'duplazoFuggveny' nevét.
// Fontos: Zárójel () nélkül adjuk át!
// A JavaScript motor automatikusan meghívja ezt a függvényt
// a tömb minden elemére (először 1-re, aztán 2-re, végül 3-ra).
const duplaSzamok = szamok.map(duplazoFuggveny);

// Rövidebb (és gyakoribb) szintaxis arrow function-nel:
// const duplaSzamok = szamok.map(szam => szam * 2);

// 3. Az eredmény
console.log(duplaSzamok); // Eredmény: [2, 4, 6]

// Fontos: Az eredeti tömb változatlan marad!
console.log(szamok);       // Eredmény: [1, 2, 3]
```

### Szűrés (`filter()`)

A `filter()` metódus egy **logikai tesztet** (predicate) futtat minden elemen, és csak azokat az elemeket gyűjti össze egy **új tömbbe**, amelyekre a feltétel `true` értéket ad vissza.

**Például:** Megfelelő adatok kiválasztása egy halmazból (lásd: csak a 8 karakternél hosszabb városnevek kiválasztása).

```javascript
// 1. Az eredeti tömb (a "halmaz")
const varosok = ['Budapest', 'Debrecen', 'Szeged', 'Miskolc', 'Pécs', 'Győr', 'Nyíregyháza'];

// 2. A szűrő függvény (a "logikai teszt")
// Ez a függvény minden elemre lefut. Ha true-t ad vissza,
// az elem bekerül az új tömbbe, ha false-t, akkor nem.
const hosszuVarosok = varosok.filter((varosnev) => {
  return varosnev.length > 8;
});

// Rövidebb (gyakoribb) szintaxis:
// const hosszuVarosok = varosok.filter(varosnev => varosnev.length > 8);

// 3. Az eredmény
console.log(hosszuVarosok);
// Eredmény: ['Budapest', 'Debrecen', 'Nyíregyháza']

// Fontos: Az eredeti tömb most sem változott!
console.log(varosok);
// Eredmény: ['Budapest', 'Debrecen', 'Szeged', 'Miskolc', 'Pécs', 'Győr', 'Nyíregyháza']
```

### Sorbarendezés (`sort()`)

A `.sort()` metódus a tömb elemeit rendezi sorba.

>[!WARNING]
> A `.map()` és `.filter()` metódusokkal ellentétben (amelyek új tömböt hoznak létre), a `.sort()` **közvetlenül módosítja (mutálja) az eredeti tömböt!** Ez egy alapvető különbség és gyakori hibaforrás.

#### Alapértelmezett (szöveges) rendezés

A `sort()` metódus alapértelmezés szerint **minden elemet szövegként kezel** és ábécé sorrendbe (pontosabban: UTF-16 kódpontok szerint) rendezi. Ez stringeknél tökéletesen működik, de számoknál váratlan és hibás eredményt ad.

```javascript
// Stringek rendezése (Várt eredmény)
const gyumolcsok = ['körte', 'alma', 'banán', 'szilva'];
gyumolcsok.sort();
console.log(gyumolcsok);
// Eredmény: ['alma', 'banán', 'körte', 'szilva']

// ---

// Számok rendezése (Hibás eredmény)
const pontszamok = [10, 5, 100, 2];
pontszamok.sort();
console.log(pontszamok);
// Eredmény: [10, 100, 2, 5]
```

A fenti példa azért hibás, mert a `sort()` a számokat szövegként hasonlítja össze: a "100" szöveg a "2" szöveg elé kerül az ábécében (az első karakter, "1", előbb van, mint "2").

#### Helyes rendezés: Az összehasonlító függvény

Ahhoz, hogy a rendezés helyesen (pl. számérték szerint) működjön, egy **összehasonlító függvényt** (compare function) kell átadnunk a `sort()` metódusnak.

Ez a függvény két elemet kap paraméterként (nevezzük őket `a`-nak és `b`-nek), és a visszatérési értékével jelzi a helyes sorrendet:

  * Ha **negatív számot** ad vissza: `a` kerül `b` elé (a sorrend jó).
  * Ha **pozitív számot** ad vissza: `b` kerül `a` elé (cserélni kell).
  * Ha **nullát** ad vissza: a sorrend mindegy.

Szerencsére számok esetén ezt nagyon egyszerűen meg lehet oldani:

  * **Növekvő sorrend:** `(a, b) => a - b`
  * **Csökkenő sorrend:** `(a, b) => b - a`

```javascript
const pontszamok = [10, 5, 100, 2];

// Számok növekvő rendezése (helyesen)
pontszamok.sort((a, b) => a - b);
console.log(pontszamok);
// Eredmény: [2, 5, 10, 100]

// Számok csökkenő rendezése (helyesen)
pontszamok.sort((a, b) => b - a);
console.log(pontszamok);
// Eredmény: [100, 10, 5, 2]
```

#### Objektumok rendezése tulajdonság szerint

Az összehasonlító függvény logikája tökéletesen alkalmas arra, hogy objektumokból álló tömböket is rendezzünk egy adott tulajdonságuk alapján.

```javascript
// Lásd a korábbi 'hallgato' objektum sémáját
const hallgatok = [
  { nev: 'Minta János', tanulmanyiAtlag: 4.25 },
  { nev: 'Kovács Éva', tanulmanyiAtlag: 3.8 },
  { nev: 'Nagy Béla', tanulmanyiAtlag: 4.5 }
];

// Rendezés tanulmányi átlag szerint (csökkenő)
hallgatok.sort((a, b) => b.tanulmanyiAtlag - a.tanulmanyiAtlag);

console.log(hallgatok);
// Eredmény:
// 1. Nagy Béla (4.5)
// 2. Minta János (4.25)
// 3. Kovács Éva (3.8)

// Rendezés név szerint (növekvő, ábécé)
// Stringek összehasonlítására a .localeCompare() a legbiztosabb módszer!
hallgatok.sort((a, b) => a.nev.localeCompare(b.nev));

console.log(hallgatok);
// Eredmény:
// 1. Kovács Éva
// 2. Minta János
// 3. Nagy Béla
```

A szöveg AI felhasználásával készült.