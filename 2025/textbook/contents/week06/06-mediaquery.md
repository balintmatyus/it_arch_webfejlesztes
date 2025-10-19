# Media Query-k – A Töréspontok kezelése

A Media Query-k a reszponzív webdesign kulcsfontosságú elemei, amelyek lehetővé teszik a CSS-szabályok szelektív alkalmazását a felhasználó eszközének tulajdonságai alapján. Ebben a tananyagban egy gyakorlati példán keresztül fogjuk megismerni őket.

## A példa HTML struktúra

Készítsünk egy egyszerű blog oldalt, amelyet fokozatosan teszünk reszponzívvá:

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reszponzív Blog</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <div class="container">
            <h1>Saját Blogom</h1>
            <nav>
                <ul class="menu">
                    <li><a href="#home">Kezdőlap</a></li>
                    <li><a href="#about">Rólam</a></li>
                    <li><a href="#blog">Blog</a></li>
                    <li><a href="#contact">Kapcsolat</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <main class="container">
        <article class="content">
            <section class="post">
                <h2>Első blogbejegyzésem</h2>
                <p class="meta">2025. október 15.</p>
                <img src="https://placehold.co/600x400" alt="Placeholder kép">
                <p>Ez egy hosszabb bekezdés, amely bemutatja, hogyan néz ki a tartalom. 
                A reszponzív tervezés célja, hogy az oldalunk minden eszközön jól 
                olvasható és használható legyen. A szöveg hossza fontos tényező a 
                töréspontok meghatározásánál.</p>
                <p>További tartalom következik itt, amely segít bemutatni, hogyan 
                viselkedik az oldalunk különböző képernyőméreteken.</p>
            </section>

            <section class="post">
                <h2>Második bejegyzés</h2>
                <p class="meta">2025. október 10.</p>
                <img src="https://placehold.co/600x400" alt="Placeholder kép">
                <p>A reszponzív webdesign alapelve, hogy a tartalom alkalmazkodjon 
                az eszközhöz, nem pedig fordítva. Ezért kezdjük a legkisebb nézettel.</p>
            </section>
        </article>

        <aside class="sidebar">
            <div class="widget">
                <h3>Rólam</h3>
                <p>Webes fejlesztő vagyok, és szeretem a reszponzív dizájnt.</p>
            </div>
            <div class="widget">
                <h3>Kategóriák</h3>
                <ul>
                    <li><a href="#">Webfejlesztés</a></li>
                    <li><a href="#">CSS</a></li>
                    <li><a href="#">Reszponzív dizájn</a></li>
                </ul>
            </div>
        </aside>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2025 Saját Blogom. Minden jog fenntartva.</p>
        </div>
    </footer>
</body>
</html>
```

## 1. Alap stílusok (Mobile First megközelítés)

A **"mobile first"** tervezés során a legkisebb nézettel kezdünk. Ez az alap CSS még **nem tartalmaz Media Query-ket**, és egyoszlopos, egyszerű elrendezést biztosít:

```css
/* Alapvető reset és globális stílusok */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

/* Konténer: korlátozza a szélességet és középre igazít */
.container {
    width: 95%;
    margin: 0 auto;
    max-width: 1200px;
}

/* Header stílusok */
header {
    background-color: #2c3e50;
    color: white;
    padding: 1rem 0;
}

header h1 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
}

/* Navigáció: mobil nézetben egymás alatt */
.menu {
    list-style: none;
}

.menu li {
    margin-bottom: 0.5rem;
}

.menu a {
    color: white;
    text-decoration: none;
    display: block;
    padding: 0.5rem;
    background-color: #34495e;
    border-radius: 4px;
}

.menu a:hover {
    background-color: #1abc9c;
}

/* Fő tartalom */
main {
    padding: 2rem 0;
}

/* Blogbejegyzések */
.post {
    margin-bottom: 2rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid #ddd;
}

.post h2 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
    color: #2c3e50;
}

.meta {
    color: #7f8c8d;
    font-size: 0.9rem;
    margin-bottom: 1rem;
}

.post img {
    width: 100%;
    height: auto;
    margin: 1rem 0;
    border-radius: 4px;
}

.post p {
    margin-bottom: 1rem;
}

/* Oldalsáv: mobil nézetben a tartalom alatt */
.sidebar {
    margin-top: 2rem;
}

.widget {
    background-color: #ecf0f1;
    padding: 1rem;
    margin-bottom: 1rem;
    border-radius: 4px;
}

.widget h3 {
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

.widget ul {
    list-style: none;
}

.widget li {
    margin-bottom: 0.3rem;
}

.widget a {
    color: #3498db;
    text-decoration: none;
}

.widget a:hover {
    text-decoration: underline;
}

/* Footer */
footer {
    background-color: #2c3e50;
    color: white;
    padding: 2rem 0;
    text-align: center;
    margin-top: 2rem;
}
```

**Fontos:** Figyeljük meg, hogy ebben az alapstílusban minden egyszerű, egyoszlopos. A navigációs elemek egymás alatt vannak, az oldalsáv a fő tartalom alatt helyezkedik el.

## 2. Media Query-k alapjai és szintaktikája

### A Media Query szerkezete

A Media Query egy **CSS3-ban bevezetett technika**, amely az `@media` szabályt használja. Az alapvető szintaktika:

```css
@media media-type and (media-feature-rule) {
    /* CSS szabályok */
}
```

Például:

```css
@media screen and (min-width: 600px) {
    /* Ezek a stílusok csak 600px-nél szélesebb képernyőkön érvényesek */
    body {
        font-size: 18px;
    }
}
```

A Media Query fő részei:

1. **Médiatípus (`media-type`)**: pl. `screen` (képernyő), `print` (nyomtatás), vagy `all`
2. **Média kifejezés (`media-feature-rule`)**: pl. `(min-width: 600px)`

## 3. Az első töréspont: Tablet nézet (≥40em / ~640px)

Most adjuk hozzá az első Media Query-t, amely **akkor lép életbe, ha a viewport legalább 40em széles**. Használjunk `em` egységet a töréspontoknál a jobb hozzáférhetőség érdekében:

```css
/* Tablet nézet: 40em felett (~640px, ha az alap font-size 16px) */
@media (min-width: 40em) {
    
    /* A navigáció most vízszintesen */
    .menu {
        display: block;
    }
    
    .menu li {
        display: inline-block;
        margin-right: 0.5rem;
        margin-bottom: 0;
    }
    
    .menu a {
        display: inline-block;
        padding: 0.5rem 1rem;
    }
    
    /* Képek kisebb méretben a szöveg mellett */
    .post img {
        width: 60%;
        float: right;
        margin-left: 1rem;
    }
    
    /* Oldalsáv kezd oldalt lebegni */
    .content {
        width: 65%;
        float: left;
        padding-right: 2rem;
    }
    
    .sidebar {
        width: 35%;
        float: right;
        margin-top: 0;
    }
    
    /* Clearfix a main konténerhez */
    main::after {
        content: "";
        display: table;
        clear: both;
    }
}
```

**Mit értünk el?**
- A navigáció most vízszintes sávként jelenik meg
- A képek kisebb méretben a szöveg mellett lebegnek
- A tartalom és az oldalsáv egymás mellett kezd megjelenni (65% - 35%)

## 4. Desktop nézet: Szélesebb töréspontok (≥60em / ~960px)

Hozzáadunk egy újabb töréspontot a nagyobb képernyőkhöz:

```css
/* Desktop nézet: 60em felett (~960px) */
@media (min-width: 60em) {
    
    /* Nagyobb header */
    header h1 {
        font-size: 2.5rem;
    }
    
    /* Navigáció jobbra igazítása */
    header .container {
        position: relative;
    }
    
    header h1 {
        display: inline-block;
        width: 40%;
    }
    
    nav {
        display: inline-block;
        width: 58%;
        text-align: right;
        vertical-align: bottom;
    }
    
    /* Nagyobb betűméret */
    body {
        font-size: 18px;
    }
    
    .post h2 {
        font-size: 2rem;
    }
    
    /* Képek eredeti méretben */
    .post img {
        width: 100%;
        float: none;
        margin-left: 0;
    }
}
```

## 5. Mértékegységek a töréspontokban

**Miért használjunk `em` vagy `rem` egységeket?**

Az `em` egységek használata biztosítja, hogy ha a felhasználó megnöveli a böngésző alap betűméretét, a töréspontok is arányosan eltolódnak:

```css
/* Rossz gyakorlat: fix pixel érték */
@media (min-width: 768px) { /* ... */ }

/* Jó gyakorlat: relatív em egység */
@media (min-width: 48em) { /* 768px / 16px = 48em */ }
```

**Átváltás:** Ha az alap font-size 16px, akkor:
- 600px = 37.5em
- 768px = 48em
- 1024px = 64em

## 6. Tartomány szintaktika (Range Syntax)

A modern CSS lehetővé teszi olvashatóbb tartomány-szintaktikát:

```css
/* Hagyományos módszer */
@media (min-width: 40em) and (max-width: 60em) {
    .sidebar .widget {
        background-color: #d5dbdb;
    }
}

/* Modern tartomány szintaktika (CSS4) */
@media (40em <= width <= 60em) {
    .sidebar .widget {
        background-color: #d5dbdb;
    }
}

/* Vagy így is írható */
@media (width >= 40em) and (width <= 60em) {
    .sidebar .widget {
        background-color: #d5dbdb;
    }
}
```

## 7. Logikai operátorok

### AND operátor

Több feltétel kombinálása:

```css
/* Mindkét feltételnek teljesülnie kell */
@media screen and (min-width: 40em) and (max-width: 60em) {
    .post {
        border: 2px solid #3498db;
    }
}
```

### OR operátor (vessző)

```css
/* Bármelyik feltétel teljesülése elég */
@media (max-width: 40em), (min-width: 80em) {
    /* Nagyon kicsi vagy nagyon nagy képernyőkön */
    .widget {
        border: 2px dashed #e74c3c;
    }
}
```

### NOT operátor

```css
/* Nem nyomtatáskor */
@media not print {
    nav {
        display: block;
    }
}
```

## 8. Tájolás (Orientation)

Az eszköz fekvő vagy álló tájolásának vizsgálata:

```css
/* Álló (portrait) tájolás */
@media (orientation: portrait) {
    .post img {
        width: 100%;
    }
}

/* Fekvő (landscape) tájolás */
@media (orientation: landscape) and (max-width: 60em) {
    /* Tablet fekvő módban */
    .post img {
        width: 50%;
        float: left;
        margin-right: 1rem;
    }
}
```

## 9. Mutatóeszköz vizsgálata (Hover és Pointer)

A modern Media Query-k lehetővé teszik annak tesztelését, hogy milyen mutatóeszközt használ a felhasználó:

```css
/* Ha van hover képesség (egér) */
@media (hover: hover) {
    .menu a {
        transition: background-color 0.3s ease;
    }
    
    .menu a:hover {
        background-color: #1abc9c;
        transform: translateY(-2px);
    }
}

/* Ha nincs hover (érintőképernyő) */
@media (hover: none) {
    .menu a {
        padding: 1rem;
        /* Nagyobb kattintási terület */
    }
}

/* Pontos mutató (egér) */
@media (pointer: fine) {
    .widget a {
        font-size: 0.9rem;
    }
}

/* Durva mutató (érintés) */
@media (pointer: coarse) {
    .widget a {
        font-size: 1rem;
        padding: 0.5rem;
        display: block;
        /* Nagyobb célterület ujjnak */
    }
}
```

## 10. Nyomtatási stílusok

A `@media print` segítségével eltávolíthatjuk a navigációt és optimalizálhatjuk a tartalmat nyomtatáshoz:

```css
@media print {
    /* Navigáció és oldalsáv elrejtése */
    header nav,
    .sidebar,
    footer {
        display: none;
    }
    
    /* Tartalom teljes szélességben */
    .content {
        width: 100%;
        float: none;
    }
    
    /* Fekete-fehér optimalizálás */
    body {
        color: black;
        background: white;
    }
    
    /* Linkek megjelenítése */
    a[href]::after {
        content: " (" attr(href) ")";
    }
    
    /* Oldaltörések */
    .post {
        page-break-inside: avoid;
    }
    
    h2 {
        page-break-after: avoid;
    }
}
```

## 11. Flexbox használata Media Query-kkel (Modern megközelítés)

Az előző példákban `float` alapú elrendezést használtunk, ami a klasszikus megközelítés. A modern CSS azonban a **Flexbox** használatát ajánlja, amely egyszerűbb, tisztább kódot eredményez és nem igényel clearfix megoldásokat.

Nézzük meg, hogyan írhatjuk újra a korábbi reszponzív elrendezést Flexbox segítségével!

### Alap stílusok módosítása (Mobile First)

A mobile nézetben még nincs szükség Flexbox-ra, minden marad egyoszlopos:
```css
/* Main konténer - mobil nézetben egyszerű blokk */
main {
    padding: 2rem 0;
}

.content,
.sidebar {
    width: 100%;
}
```

### Tablet nézet Flexbox-szal (≥40em)

A `float` helyett most Flexbox-ot használunk:
```css
@media (min-width: 40em) {
    
    /* Main konténer flexbox konténerré alakítása */
    main {
        display: flex;
        flex-wrap: wrap;
        gap: 2rem;
    }
    
    /* Tartalom és oldalsáv méretezése */
    .content {
        flex: 1 1 60%;
    }
    
    .sidebar {
        flex: 1 1 35%;
    }
    
    /* Navigáció is flexbox */
    .menu {
        display: flex;
        flex-wrap: wrap;
        gap: 0.5rem;
    }
    
    .menu li {
        margin-right: 0;
        margin-bottom: 0;
    }
}
```

**Előnyök a float-hoz képest:**
- Nincs szükség clearfix-re vagy `display: flow-root;`-ra.
- A `gap` tulajdonság egyszerűen kezeli a térközöket
- Automatikus magasság-kiegyenlítés a `.content` és `.sidebar` között

### Desktop nézet finomhangolása (≥60em)
```css
@media (min-width: 60em) {
    
    /* Header is flexbox elrendezés */
    header .container {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    
    header h1 {
        flex: 0 0 auto;
        margin-bottom: 0;
    }
    
    nav {
        flex: 0 0 auto;
    }
    
    /* Tartalom arányok módosítása */
    .content {
        flex: 1 1 65%;
    }
    
    .sidebar {
        flex: 1 1 30%;
    }
    
    /* Widget-ek flexbox elrendezése */
    .widget ul {
        display: flex;
        flex-direction: column;
        gap: 0.3rem;
    }
}
```

### Különleges esetek: Orientation és Flexbox
```css
/* Tablet fekvő módban más elrendezés */
@media (orientation: landscape) and (min-width: 40em) and (max-width: 60em) {
    
    main {
        display: flex;
        flex-direction: row;
    }
    
    .content {
        flex: 2;
    }
    
    .sidebar {
        flex: 1;
    }
    
    /* Blogbejegyzések is flexbox */
    .post {
        display: flex;
        flex-wrap: wrap;
    }
    
    .post h2,
    .post .meta {
        flex: 1 1 100%;
    }
    
    .post img {
        flex: 0 0 40%;
        margin-right: 1rem;
    }
    
    .post p {
        flex: 1;
    }
}
```

### Float vs Flexbox összehasonlítás

| Szempont | Float | Flexbox |
|----------|-------|---------|
| Clearfix szükséges | ✅ Igen | ❌ Nem |
| Térköz kezelés | `margin` | `gap` |
| Függőleges igazítás | Bonyolult | `align-items` |
| Sorrend változtatás | HTML módosítás | `order` |
| Rugalmas méretezés | Fix `width` | `flex-grow/shrink` |
| Kód olvashatóság | Kevésbé | Jobban |

### Gyakorlati tippek Flexbox + Media Query használatához

1. **Mobile first mindig**: A Flexbox tulajdonságokat fokozatosan add hozzá
2. **Gap használata**: A `gap` egyszerűsíti a térköz-kezelést a töréspontokon át
3. **Flex értékek változtatása**: Az arányokat könnyű módosítani különböző töréspontoknál
4. **Kombináld a flex-direction-nel**: Tájolásfüggő elrendezésekhez hasznos
```css
/* Példa: Álló tájolásban oszlopos, fekvőben soros */
@media (orientation: portrait) {
    main {
        flex-direction: column;
    }
}

@media (orientation: landscape) and (min-width: 40em) {
    main {
        flex-direction: row;
    }
}
```

### Mikor használj Float-ot és mikor Flexbox-ot?

**Használj Flexbox-ot:**
- Modern projekteknél (IE11+ nem számít)
- Komplex reszponzív elrendezéseknél
- Ha függőleges igazításra van szükség
- Komponens-alapú elrendezéseknél

**Használj Float-ot:**
- Régi böngésző támogatás szükséges (IE9-10)
- Szöveg körüli kép lebegtetésnél (klasszikus használat)
- Egyszerű, két-oszlopos elrendezésnél

A modern webfejlesztésben a **Flexbox az ajánlott megoldás**, különösen Media Query-kkel kombinálva, mert tisztább, karbantarthatóbb kódot eredményez.