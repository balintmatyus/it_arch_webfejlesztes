# CSS Flexbox: Egydimenziós elrendezés

A Flexbox, vagy hivatalos nevén CSS Flexible Box Layout, egy modern layout módszer, amely kiemelten fontos szerepet játszik a reszponzív webdesignban.

## HTML alapstruktúra

Minden példánkhoz az alábbi HTML alapstruktúrát használjuk:

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flexbox példák</title>
    <style>
        /* Alapvető stílusok a jobb láthatóságért */
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        
        .pelda {
            margin-bottom: 40px;
        }
        
        .flex-container {
            background-color: #e0e0e0;
            padding: 10px;
            margin: 10px 0;
        }
        
        .flex-item {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            margin: 5px;
            text-align: center;
        }
    </style>
</head>
<body>
    <h1>CSS Flexbox Példák</h1>
    
    <!-- A példák ide kerülnek -->
    
</body>
</html>
```

---

## Flexbox koncepciója és terminológiája

### 1. A Flexbox célja és jellege
A Flexbox egy **egy-dimenziós** elrendezési módszer, ami azt jelenti, hogy egyszerre egy tengely mentén (sorban vagy oszlopban) rendezi az elemeket. Célja az, hogy hatékonyan rendezze az egyes elemek közötti teret akkor is, ha az adott elemek mérete előre ismeretlen és/vagy változó.

A Flexbox lehetővé teszi az elemek szélességének, magasságának és sorrendjének dinamikus változtatását a rendelkezésre álló tér optimális kitöltése érdekében. A Flexbox használatával a reszponzív beállítások teljes mértékben a CSS-ben tarthatók.

A Flexbox elrendezés a benne lévő elemeket meg tudja nyújtani (flex) a szabad terület kitöltésére, vagy össze tudja zsugorítani (shrink) az *overflow* (túlcsordulás) megelőzésére.

### 2. Flexbox terminológia (Tengelyek)
A flexbox elrendezés flex-konténerekből és a bennük elhelyezett flex-elemekből áll. Az elemek két tengely mentén helyezkednek el:

*   **Fő-tengely (Main axis):** Az a tengely, amelynek irányában a flex elemek el vannak rendezve (például sorban a lapon át, vagy oszlopban a lapon lefelé).
*   **Kereszt-tengely (Cross axis):** A tengely, amely merőlegesen fut a fő-tengelyre.

A szülő elem, amelyen a `display: flex` beállítás szerepel, a **flex-konténer**. A flex-konténerben rugalmas dobozként elrendezett elemek a **flex-elemek**.

---

## Flex konténer tulajdonságai

### 1. A konténer meghatározása

A flex-konténert úgy határozzuk meg, hogy egy blokkszintű elem `display` tulajdonságát `flex` értékre állítjuk. Amikor az elem flex-konténerré válik, annak **közvetlen gyermekei** automatikusan flex-elemekké alakulnak.

**HTML:**
```html
<div class="pelda">
    <h2>Alapvető flex konténer</h2>
    <div class="flex-container" style="display: flex;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
}
```

**Eredmény:** A három elem vízszintesen, egymás mellett jelenik meg (alapértelmezett `row` iránnyal).

---

### 2. Tengelyirány (`flex-direction`)

A `flex-direction` tulajdonság határozza meg, hogy a fő-tengely milyen irányban fusson, azaz a flex-elemek milyen sorrendben helyezkedjenek el (vízszintesen vagy függőlegesen).

*   Az alapértelmezett beállítás a **`row`** (sorban, balról jobbra), ami létrehozza a többoszlopos elrendezést.
*   A **`column`** oszlopos elrendezést eredményez, hasonlóan a normál folyáshoz.

**HTML és példák:**
```html
<div class="pelda">
    <h2>flex-direction: row (alapértelmezett)</h2>
    <div class="flex-container" style="display: flex; flex-direction: row;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-direction: column</h2>
    <div class="flex-container" style="display: flex; flex-direction: column;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-direction: row-reverse</h2>
    <div class="flex-container" style="display: flex; flex-direction: row-reverse;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
    flex-direction: row; /* vagy column, row-reverse, column-reverse */
}
```

---

### 3. Sortörés (`flex-wrap` és `flex-flow`)

A `flex-wrap` tulajdonság azt szabályozza, hogy a flex-elemek sortörést használjanak-e. Ha az aktuális képernyőméret nem engedné, hogy az elemek elférjenek, új sorba/oszlopba rendeződjenek-e.

*   Alapértelmezés szerint a böngésző igyekszik az összes elemet egy sorba vagy oszlopba zsúfolni, ami túlcsorduláshoz vezethet.
*   A **`wrap`** értékkel engedélyezzük, hogy az elemek új sorba rendeződjenek, amennyiben az eredeti méretük szerint már nem férnének el.
*   A **`flex-flow`** egy rövidített tulajdonság, amellyel egyszerre állítható be a `flex-direction` és a `flex-wrap`.

**HTML:**
```html
<div class="pelda">
    <h2>flex-wrap: nowrap (alapértelmezett)</h2>
    <div class="flex-container" style="display: flex; flex-wrap: nowrap; width: 400px;">
        <div class="flex-item" style="min-width: 150px;">Széles elem 1</div>
        <div class="flex-item" style="min-width: 150px;">Széles elem 2</div>
        <div class="flex-item" style="min-width: 150px;">Széles elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-wrap: wrap</h2>
    <div class="flex-container" style="display: flex; flex-wrap: wrap; width: 400px;">
        <div class="flex-item" style="min-width: 150px;">Széles elem 1</div>
        <div class="flex-item" style="min-width: 150px;">Széles elem 2</div>
        <div class="flex-item" style="min-width: 150px;">Széles elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-flow: row wrap (rövidített forma)</h2>
    <div class="flex-container" style="display: flex; flex-flow: row wrap; width: 400px;">
        <div class="flex-item" style="min-width: 150px;">Elem 1</div>
        <div class="flex-item" style="min-width: 150px;">Elem 2</div>
        <div class="flex-item" style="min-width: 150px;">Elem 3</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
    flex-wrap: wrap;
    /* vagy */
    flex-flow: row wrap; /* flex-direction és flex-wrap egyben */
}
```

---

### 4. Igazítás a fő-tengelyen (`justify-content`)

A `justify-content` tulajdonság a flex-elemek elrendezését kezeli a **fő-tengely** mentén. Segítségével elhelyezhetjük az elemeket a konténer elején, végén, vagy eloszthatjuk a köztük lévő térközt.

*   A **`center`** középre igazítja az elemeket a fő-tengelyen.
*   A **`space-between`** egyenlően osztja el az elemeket úgy, hogy nem hagy teret a két végén.
*   A **`space-around`** egyenlően osztja el az elemeket, kis helyet hagyva a két végén.
*   A **`space-evenly`** teljesen egyenlő térközöket hoz létre az elemek között és a konténer széleinél is.

**HTML:**
```html
<div class="pelda">
    <h2>justify-content: flex-start (alapértelmezett)</h2>
    <div class="flex-container" style="display: flex; justify-content: flex-start;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>justify-content: center</h2>
    <div class="flex-container" style="display: flex; justify-content: center;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>justify-content: space-between</h2>
    <div class="flex-container" style="display: flex; justify-content: space-between;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>justify-content: space-around</h2>
    <div class="flex-container" style="display: flex; justify-content: space-around;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>justify-content: space-evenly</h2>
    <div class="flex-container" style="display: flex; justify-content: space-evenly;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
    justify-content: center; /* vagy flex-start, flex-end, space-between, space-around, space-evenly */
}
```

---

### 5. Igazítás a kereszt-tengelyen (`align-items`)

Az `align-items` tulajdonság a flex-elemek elrendezését/igazítását kezeli a **kereszt-tengelyen** belül.

*   Ha a fő-tengely vízszintes (`row`), az `align-items` a függőleges igazítást kezeli.
*   A **`center`** középre állítja az elemeket a kereszttengely mentén.
*   Az alapértelmezett érték, ami általában a `stretch`, kinyújtja az összes flex-elemet, hogy kitöltsék a konténert a kereszttengely irányában, így ha a szülőnek nincs fix mérete, az összes elem akkora magasságú (vagy szélességű) lesz, mint a legnagyobb/legszélesebb elem.

**HTML:**
```html
<div class="pelda">
    <h2>align-items: stretch (alapértelmezett)</h2>
    <div class="flex-container" style="display: flex; align-items: stretch; height: 150px;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>align-items: center</h2>
    <div class="flex-container" style="display: flex; align-items: center; height: 150px;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2<br>Két soros</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>align-items: flex-start</h2>
    <div class="flex-container" style="display: flex; align-items: flex-start; height: 150px;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>

<div class="pelda">
    <h2>align-items: flex-end</h2>
    <div class="flex-container" style="display: flex; align-items: flex-end; height: 150px;">
        <div class="flex-item">Elem 1</div>
        <div class="flex-item">Elem 2</div>
        <div class="flex-item">Elem 3</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
    align-items: center; /* vagy stretch, flex-start, flex-end, baseline */
    height: 150px;
}
```

---

## Flex elemek tulajdonságai

A flex-elemek azok az elemek, amelyeknek a viselkedését, méretét és sorrendjét szeretnénk szabályozni a konténeren belül.

### 1. Méretezés és térfoglalás (`flex-grow`, `flex-shrink`, `flex-basis`)

Ezek a tulajdonságok szabályozzák, hogy a flex-elemek milyen arányban osszák fel a rendelkezésre álló helyet, és mennyire legyenek rugalmasak.

*   **`flex-grow`**: Relatív egység, amely megadja, hogy az adott elem milyen mértékben növekedjen a testvér flex-elemekhez képest, hogy kitöltse a szabad teret. Például ha minden elemnek `flex-grow: 1` értéket adunk, mindegyik egyenlő arányban kap a fennmaradó térből.
*   **`flex-shrink`**: Szintén relatív érték, amely a zsugorodást szabályozza (akkor lép életbe, ha az elemek túlnyúlnak a konténeren).
*   **`flex-basis`**: Az elem kezdeti mérete a fő-tengely irányában.
*   **`flex` (rövidített)**: Egy rövidített tulajdonság, amellyel a `flex-grow`, `flex-shrink` és `flex-basis` értékek egyszerre adhatók meg. A `flex: 1 1 100px` beállítás azt jelenti, hogy az elem először 100 pixelt kap, tud növekedni és zsugorodni is.

**HTML:**
```html
<div class="pelda">
    <h2>flex-grow példa - Minden elem flex: 1</h2>
    <div class="flex-container" style="display: flex;">
        <div class="flex-item" style="flex: 1;">Elem 1 (flex: 1)</div>
        <div class="flex-item" style="flex: 1;">Elem 2 (flex: 1)</div>
        <div class="flex-item" style="flex: 1;">Elem 3 (flex: 1)</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-grow példa - Különböző értékek</h2>
    <div class="flex-container" style="display: flex;">
        <div class="flex-item" style="flex: 1;">Elem 1 (flex: 1)</div>
        <div class="flex-item" style="flex: 2;">Elem 2 (flex: 2) - Duplán széles</div>
        <div class="flex-item" style="flex: 1;">Elem 3 (flex: 1)</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-basis példa</h2>
    <div class="flex-container" style="display: flex;">
        <div class="flex-item" style="flex: 1 1 100px;">Elem 1 (flex: 1 1 100px)</div>
        <div class="flex-item" style="flex: 1 1 200px;">Elem 2 (flex: 1 1 200px)</div>
        <div class="flex-item" style="flex: 1 1 100px;">Elem 3 (flex: 1 1 100px)</div>
    </div>
</div>

<div class="pelda">
    <h2>flex-shrink = 0 (nem zsugorodik)</h2>
    <div class="flex-container" style="display: flex; width: 400px;">
        <div class="flex-item" style="flex: 0 0 200px;">Elem 1 (flex: 0 0 200px) - Fix</div>
        <div class="flex-item" style="flex: 1 1 auto;">Elem 2 (flex: 1 1 auto) - Rugalmas</div>
    </div>
</div>
```

**CSS:**
```css
.flex-item {
    flex: 1; /* Rövidített forma: flex-grow: 1, flex-shrink: 1, flex-basis: 0 */
    /* vagy részletesen: */
    flex-grow: 1;
    flex-shrink: 1;
    flex-basis: 100px;
}
```

---

### 2. Sorrend (`order`)

Az `order` tulajdonság lehetővé teszi, hogy a flex-elemek megjelenési sorrendjét megváltoztassuk anélkül, hogy a forráskód sorrendjét módosítanánk.

*   Alapértelmezés szerint minden flex elem `order: 0` értékkel rendelkezik.
*   A magasabb `order` értékkel rendelkező elemek később jelennek meg, mint az alacsonyabb értékűek.
*   Negatív `order` értékeket is be lehet állítani.

**HTML:**
```html
<div class="pelda">
    <h2>order példa - Megváltoztatott sorrend</h2>
    <div class="flex-container" style="display: flex;">
        <div class="flex-item" style="order: 2;">Elem 1 (order: 2) - Harmadik</div>
        <div class="flex-item" style="order: 1;">Elem 2 (order: 1) - Második</div>
        <div class="flex-item" style="order: 0;">Elem 3 (order: 0) - Első</div>
        <div class="flex-item" style="order: -1;">Elem 4 (order: -1) - Legelső</div>
    </div>
</div>
```

**CSS:**
```css
.flex-item:nth-child(1) {
    order: 2;
}

.flex-item:nth-child(2) {
    order: 1;
}

.flex-item:nth-child(3) {
    order: 0;
}
```

---

### 3. Egyéni igazítás (`align-self`)

Az `align-self` tulajdonság felülírja az `align-items` általános igazítási beállításait egy adott, egyedi flex-elem esetében. Például használható arra, hogy egyetlen elemet a kereszttengely végére igazítsunk.

**HTML:**
```html
<div class="pelda">
    <h2>align-self példa</h2>
    <div class="flex-container" style="display: flex; align-items: flex-start; height: 150px;">
        <div class="flex-item">Elem 1 (alapértelmezett)</div>
        <div class="flex-item" style="align-self: center;">Elem 2 (align-self: center)</div>
        <div class="flex-item" style="align-self: flex-end;">Elem 3 (align-self: flex-end)</div>
        <div class="flex-item" style="align-self: stretch;">Elem 4 (align-self: stretch)</div>
    </div>
</div>
```

**CSS:**
```css
.flex-container {
    display: flex;
    align-items: flex-start;
}

.flex-item:nth-child(2) {
    align-self: center;
}

.flex-item:nth-child(3) {
    align-self: flex-end;
}
```

