# Felhasználói felület tervezése I.

Egy nagy látogatottsú weboldal jelentős értékkel bír. Miután növeli a cég imidzsét, láthatóvá teszi a céget akár távoli régiókban is, növeli a piacot, gyors és megbízható kommunikációt tesz lehetővé. Nem mellesleg 24 órás reklámhordozó.

A hatékony digitális design messze túlmutat az esztétikán: tudatos problémamegoldás, amelynek célja a felhasználói viselkedés pozitív befolyásolása. A **jó design** nem szubjektív ízlés kérdése, hanem jól definiált elveken alapul.

## A webfejlesztés folyamata dióhéjban

Bár a kurzus a HTML, CSS és JavaScript technikai részleteire koncentrál, a kódolás egy nagyobb, több lépésből álló folyamat része. A sikeres weboldal titka a gondos előkészítésben rejlik. Az alábbi vázlat egy általánosan elfogadott, **felhasználóközpontú folyamatot** mutat be, amely segít elhelyezni a programozói munkát a teljes projekt térképén.

### 1. Kutatás és Stratégia (A „Miért?”)

Mielőtt egyetlen vonalat is rajzolnánk vagy kódot írnánk, tisztázni kell a weboldal alapjait. Ebben a fázisban határozzuk meg a projekt **célját** (pl. eladás, informálás, regisztráció) és a **célközönségét** (kiknek készül az oldal?). Itt történik a piackutatás, a versenytársak elemzése és a legfontosabb funkciók meghatározása. Az eredmény egy letisztázott koncepció, ami a további munka alapját képezi.

### 2. Tervezés: UX és UI (A „Hogyan?”)

Ez a fázis alakítja a stratégiát kézzelfogható tervekké. A folyamat a durva vázlatoktól halad a részletesen kidolgozott, interaktív tervek felé. A két fő területe a felhasználói élmény (UX) és a felhasználói felület (UI) tervezése.

* **UX (User Experience) Design**: A felhasználói élmény stratégiai tervezése. A cél, hogy a weboldal használata logikus, intuitív és hatékony legyen. A UX-tervező felel a tartalom struktúrájáért, a felhasználói útvonalakért és azért, hogy a felhasználó könnyen elérje a célját.
* **UI (User Interface) Design**: A felhasználói felület vizuális megtervezése. Ide tartozik a gombok, menük, űrlapok és egyéb elemek kinézete, a színek, a tipográfia és a grafikai elemek egységes, esztétikus rendszere.

A tervezési folyamat kézzelfogható lépései és eredményei:

1.  **Drótváz (Wireframe):** Az első konkrét lépés. A drótváz egy **alacsony részletességű, fekete-fehér vázlat**, amely a weboldal „csontváza”. Csak az elemek elhelyezkedésére, a funkciókra és az információs architektúrára fókuszál, a vizuális megjelenésre nem. Célja a szerkezet gyors és olcsó tesztelése.

![Low-fidelity-web](./Low-fidelity-web.png)

2.  **Látványterv (Mockup):** A drótvázra épülő **statikus, de vizuálisan kidolgozott terv**. A mockup már a végleges kinézetet mutatja be: tartalmazza a színeket, betűtípusokat, ikonokat és képeket. Lényegében egy nagy felbontású kép arról, hogyan fog kinézni a kész weboldal, de még nem interaktív.
3.  **Prototípus (Prototype):** A látványtervekből készített **interaktív, kattintható verzió**. A prototípus már szimulálja a weboldal működését: a gombokra kattintva lehet navigálni az oldalak között, meg lehet nézni az animációkat. Lehetővé teszi a felhasználói élmény alapos tesztelését és a visszajelzések begyűjtését még a fejlesztés megkezdése előtt.

> [!NOTE]
> Több elmélet is létezik, amely leírja, hogy „mitől jó egy design”. Érdemes megemlíteni a [Gestalt-alapelveket](https://uxdesignblog.hu/articles/gestalt), valamint [Jakob Nielsen 10 használhatósági heurisztikáját](https://innovationdesign.hu/ux/10-usability-heurisztika-nielsen/), amelyek a jó felhasználói felület alapkövei.

### 3. Fejlesztés (A megvalósítás)

Itt kel életre a terv. A fejlesztők a jóváhagyott prototípus és a vizuális tervek alapján leprogramozzák a weboldal működő, interaktív felületét. A két fő területéről (Frontend, Backend) már korábban olvashattunk az [Egy modern webalkalmazás anatómiája](../week01/01-fullstack.md) fejezetben.

### 4. Tesztelés, Indítás és Optimalizálás (A finomhangolás)

Az elkészült oldalt alaposan tesztelni kell különböző eszközökön és böngészőkben, hogy minden hibátlanul működjön. Az indítás (élesítés) után a munka nem áll meg: **analitikai adatok** (pl. Google Analytics) alapján a szakemberek folyamatosan figyelik a felhasználói viselkedést, és fejlesztik a weboldalt a még jobb eredményekért.

A webfejlesztés és a webdesign nem választható el élesen; a sikeres végtermék e szakterületek szoros együttműködésének eredménye.

> [!NOTE]
> Fenti felosztás egy lineáris ([vízesésszerű](https://www.geeksforgeeks.org/software-engineering/waterfall-model/)) megközelítést vázol fel az érthetőség kedvéért. A modern gyakorlatban gyakran használnak iteratív, rugalmasabb módszereket, mint az [Agilis módszertan](https://www.geeksforgeeks.org/software-testing/what-is-agile-methodology/) vagy a [DevOps](https://www.geeksforgeeks.org/devops/introduction-to-devops/).

## CSS alapjai

CSS (Cascading Style Sheets) stílusleíró nyelv. Az első megjelenése 1994-ben volt Hakon Wium Lie ötlete alapján. Bár korábban verziókat (pl. CSS 2.1) különböztettünk meg, ma már a CSS-t modulokra bontva (színek, elrendezés, animációk stb.) fejlesztik és verziózzák. Ez a moduláris felépítés a modern CSS.

A HTML önmagában struktúrát ad a dokumentumnak, de a böngészők alapértelmezett stílusai csak nagyon alapvető olvashatóságot biztosítanak. A CSS-sel azonban sokkal többet tehetünk:
* Szöveg stílusozása (szín, méret, betűtípusok).
* Elrendezések létrehozása (pl. grid vagy többoszlopos elrendezések).
* Speciális effektek, például animációk hozzáadása.

### Stílusok definiálása

2 fő részből állnak: szelektorból (`h1`) és deklarációból (`color: red;`). A deklaráció is 2 részből, tulajdonságból (`color`) és értékből áll (`red`).

```css
h1 {
  color: red;
  font-size: 24px;
}
```

A CSS definiálása többféle módon lehetséges. HTML forráskódon belül:
* `<style>` utasítás segítségével a HTML `<head>` blokkjában,
* külső stíluslapok használatával külön `*.css` kiterjesztésű fájlként kezelve
* in-line, amikor az egyes HTML elemek tag-jeiben definiáljuk

#### **Stíluslap készítése `<style>` utasítás segítségével**
```html
<head>
   <style>
     h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
     h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
     h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
   </style>
</head>
<body>
   <h1>Repülőgépek</h1>
   <h2>Vitorlázó gépek</h2>
   <h3>R26 Góbé</h3>
</body>
```
Ez a megközelítés általában akkor lehet "kézenfekvő", ha egy adott HTML oldalhoz nagyon specifikus, vagy csak arra az egy oldalra vonatkozó stílusokat szeretnél alkalmazni.

#### **Stíluslap használata külső stíluslapokkal**

A stíluslap külön, .css kiterjesztésű fájlban is létrehozható. Ilyenkor is a `<head>` részben hivatkozunk rá.

**Példa:**
```html
<head>
   <link rel="stylesheet" href="style.css">
</head>
```

A törzsrész ugyanúgy néz ki, mint az első esetben.

A külső stíluslap (`style.css`) a következőképpen nézhet ki:
```css
h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
```

A külső stíluslap előnyei:
* **Könnyebben kezelhető:** A HTML módosítása nélkül változtatható a stílus.
* **Átlátható:** A stílus elkülönül a tartalomtól és a struktúrától.
* **Gyorsabb betöltés:** A böngésző gyorsítótárazza (cache) a fájlt.
* **Újrahasznosítható:** Egy CSS fájl több HTML oldalhoz is csatolható.

#### **Stíluslap készítése style paraméter segítségével, in-line CSS**
```html
<body>
   <h1 style="font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;">Repülőgépek</h1>
   <h2 style="font-size: 24px; color: red; font-family: Verdana, sans-serif;">Vitorlázó gépek</h2>
   <h3 style="font-size: 18px; color: blue; font-family: 'Courier New', monospace;">R26 Góbé</h3>
</body>
```
Az inline stílusoknak magas a prioritásuk és azonnal hatnak, de használatuk a legtöbb esetben **rossz gyakorlatnak** minősül.

>[!WARNING]
> **Miért kerülendő az inline CSS?**
>1.  **Rossz karbantarthatóság:** Több száz oldalas webhelyen egy apró módosítás (pl. a betűszín megváltoztatása) több száz fájl szerkesztését igényelné. Külső stíluslap esetén ez egyetlen sor módosítása.
>2.  **Nem újrahasznosítható:** A stílus egy konkrét HTML elembe van "égetve", máshol nem használható fel.
>3.  **Szennyezi a HTML-t:** A HTML feladata a struktúra leírása, a CSS-é a megjelenés. Az inline CSS összemossa ezt a két feladatkört, rontva a kód olvashatóságát.

#### A kaszkád elve: Ki nyer a végén?

A CSS a **Cascading Style Sheets** rövidítése, ahol a "Cascading" (lépcsőzetes) szó a legfontosabb. Ez a mechanizmus dönti el, hogy melyik stílusszabály érvényesül, ha egy elemre több szabály is vonatkozik. Az erősorrend általában a következő (a leggyengébbtől a legerősebbig):

1.  **Böngésző alapértelmezett stílusai** (pl. a linkek kékek és aláhúzottak).
2.  **Külső stíluslap** (`.css` fájl).
3.  **Belső stíluslap** (a `<style>` elemen belül).
4.  **Inline stílus** (a HTML elem `style` attribútumában megadott).

Ezért van az, hogy az inline stílus felülír minden mást. Ezt a hierarchiát nevezzük kaszkádnak.

## CSS szelektorok

A CSS szelektorok mondják meg a böngészőnek, hogy mely HTML elemekre kell a stílusokat alkalmazni.

Induljunk ki a következő HTML-ből.

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Szelektorok Gyakorló</title>

</head>
<body>

    <h1 id="heading">CSS Szelektorok a gyakorlatban</h1>

    <h2>Típus-szelektor</h2>
    <p>Ez egy sima bekezdés, de van benne egy <span>span elem</span>, aminek sárga a háttere a típus-szelektor miatt.</p>
    
    <hr>
    
    <h2>Osztály-szelektorok</h2>
    <h1 class="highlight">Ez egy h1 elem "highlight" osztállyal (rózsaszín háttér).</h1>
    <p class="highlight">Ez egy bekezdés "highlight" osztállyal (sárgás háttér).</p>
    <div class="notebox">Ez egy sima "notebox". Nincs narancs kerete.</div>
    <div class="notebox warning">Ez a "notebox" megkapta a "warning" osztályt is, ezért vastag és narancs keretes.</div>
    
    <hr>
    
    <h2>ID-szelektor</h2>
    <p id="one">Ennek a bekezdésnek "one" az ID-ja, ezért kék a háttere.</p>
    
    <hr>
    
    <h2>Szelektorkészlet</h2>
    <p class="special">Ez a bekezdés a ".special" osztály miatt alá van húzva. (A h1 címek is aláhúzottak a szelektorkészlet miatt).</p>

    <hr>
    
    <h2>Kombinátorok</h2>
    
    <h3>Leszármazott szelektor (szóköz)</h3>
    <div id="leszarmazott-teszt">
        <p>Ez a bekezdés a div-en belül van, ezért zöld a bal oldali kerete.</p>
        <div>
            <p>Ez egy mélyebben beágyazott bekezdés, de mivel leszármazott, ez is megkapja a zöld keretet.</p>
        </div>
    </div>
    <p>Ez a bekezdés a div-en kívül van, nincs zöld kerete.</p>
    
    <h3>Gyermek szelektor (>)</h3>
    <div id="gyermek-teszt">
        <p>Ez a bekezdés a div **közvetlen gyermeke**, ezért piros a bal oldali kerete.</p>
        <div>
            <p>Ez egy mélyebben beágyazott bekezdés. Ő már nem közvetlen gyermek, így **nem kapja meg** a piros keretet.</p>
        </div>
    </div>
    
    <hr>
    
    <h2>Pszeudo-osztályok</h2>
    <p>Vidd az egeret a gombra, kattints a beviteli mezőbe, vagy tartsd lenyomva a gombot!</p>
    
    <button>Interaktív Gomb</button>
    <br><br>
    <input type="text" placeholder="Kattints ide a fókuszért!">

</body>
</html>
```

#### Típus-szelektorok (Element Selectors)
A HTML elem nevével választják ki az elemeket. A lenti `span` szelektor az összes `<span>` elem háttérszínét sárgára állítja.
```css
span { background-color: yellow; }
```

#### Osztály-szelektorok (Class Selectors)
Egy pont (`.`) karakterrel kezdődnek, és minden olyan elemet kiválasztanak, amely rendelkezik a megadott `class` attribútummal.

* **Alapvető használat**: A `.highlight` az összes `highlight` osztályú elemet célozza.
    ```css 
    .highlight { background-color: yellow; }
    ```
* **Célzás adott elemen**: A `h1.highlight` csak az `<h1>` elemekre érvényes, amelyeknek van "highlight" osztályuk.
    ```css
    h1.highlight { background-color: pink; }
    ```
* **Több osztály együttes célzása**: A `.notebox.warning` csak azokra az elemekre vonatkozik, amelyeknek *mind* a "notebox", *mind* a "warning" osztályuk meg van adva.
    ```css
    .notebox {font-weight: bold;}
    .warning { border: 10px solid orange;}
    ```

#### ID-szelektorok (ID Selectors)
Egy hash jellel (`#`) kezdődnek. Fontos különbség, hogy egy `id` értéknek **egyedinek kell lennie** az egész HTML dokumentumban.
```css
#one { background-color: blue; color: white}
h1#heading { color: rebeccapurple; }
```

>[!WARNING]
>Az azonos ID többszöri használata érvénytelen kódot eredményez, és hibás működést okozhat.

#### Szelektorkészletek (Selector Lists)
Ha több szelektorhoz azonos stílust szeretnénk rendelni, vesszővel elválasztva felsorolhatjuk őket.
```css
h1, .special { text-decoration: underline; }
```

#### Univerzális szelektor (Universal Selector)
A csillag (`*`) jelöli, és a dokumentum összes elemét kiválasztja. Gyakran használják böngésző stílusok "resetelésére".
```css
* {
  margin: 0;
  padding: 0;
}
```

#### Kombinátorok és Pszeudo-osztályok

A szelektorokat kombinálhatjuk is, hogy még pontosabban célozhassunk.

* **Leszármazott szelektor (szóköz):** Egy elemen belüli *bármely* leszármazottat eléri. A `div p` minden `<p>` elemet kiválaszt, ami egy `<div>`-en belül van.
* **Gyermek szelektor (`>`):** Csak a *közvetlen* gyermek elemeket választja ki. A `div > p` csak azokat a `<p>` elemeket célozza, amelyek közvetlenül a `<div>` elemen belül vannak.

A **pszeudo-osztályok** egy elem speciális állapotát jelölik, és kettősponttal (`:`) kezdődnek. Elengedhetetlenek az interaktív felületekhez.
* `:hover`: Akkor lép érvénybe, amikor a felhasználó az egeret az elem fölé viszi.
* `:focus`: Akkor aktív, amikor egy elem (pl. egy űrlapmező) fókuszt kap (belekattintanak).
* `:active`: Egy elem aktív állapotát jelöli (pl. amíg a gombot lenyomva tartjuk).

**Példa:**
```css
/* Amikor az egeret a gomb fölé visszük */
button:hover {
    background-color: #555;
    color: white;
    cursor: pointer;
}

/* Amikor a beviteli mezőre kattintunk (fókuszba kerül) */
input:focus {
    border-color: dodgerblue;
    outline: 2px solid lightblue;
}

/* Amikor a gombot lenyomva tartjuk */
button:active {
    transform: scale(0.95);
}
```

## Szöveg formázása

Fontos a szöveg formázásáról is külön szót ejteni, hisz a legtöbb információtartalmat a szöveg hordozza. Ez a tudományterület - **tipográfia** - már [Gutenberg](https://en.wikipedia.org/wiki/Johannes_Gutenberg) kora óta fejlődik.

A képernyőn való olvasás gyökeresen eltér a nyomtatott szöveg befogadásától. A szemünk nem folyamatosan halad, hanem ugrásokkal (fixációkkal) pásztázza a tartalmat. A kutatások azt mutatják, hogy egyszerre egy 12-20 karakteres blokkot vagyunk képesek hatékonyan feldolgozni. A jó web-tipográfia célja, hogy segítse ezt a folyamatot, és a szöveget könnyen "szkennelhetővé" tegye. Emiatt részesítjük előnyben a *sans-serif* betűtípusokat, a rövid, tömör mondatokat és a megfelelő sortávolságot.

### Szövegek használata a képernyőn

Kétféle betűforma létezik. Az emberek a **serif** betűformákat klasszikusnak és elegánsnak tartják, ezzel szemben a **sans serif** betűformát modernnek és világosnak ítélik meg. Honlapok esetében célszerű a sans serif formákat előnyben részesíteni, mert a szem könnyebben behatárolja a betűformákat a képernyőn.

Ha egy oldalon túl sok betűtípus található, a megjelenés zavaros lesz. A néző a szerkezet megfejtésével törődik, és nem összpontosít az üzenetre. A szövegelemek megkülönböztetésére használjunk inkább különböző betűméreteket, stílusokat vagy háttereket.

>[!WARNING]
>A csupa nagybetűből álló szöveg kevésbé olvasható, mint a nagy- és kisbetűt keverve használó. A szem nehezebben ismeri fel a szavakat, és a mondatok kezdete sem tűnik ki. A nagybetűs szöveg használatát rövid címekre és kiemelésekre korlátozzuk.
>A **félkövér** betűket is korlátozottan használjuk. Túl sok félkövér szövegrész a szöveget súlyossá teszi és elvész a figyelemfelkeltő jellege.

### Betűtípusok használata (`font-family`)

#### 1. Rendszer (biztonságos) betűtípusok
Ezek a legtöbb operációs rendszeren előre telepített betűtípusok (pl. Arial, Helvetica, Times New Roman). Érdemes mindig egy "fallback" listát (betűtípus-családot) megadni. A böngésző az első elérhető típust fogja használni. A lista végén általában egy általános kategóriát adunk meg (pl. `sans-serif`).
```css
p {
  font-family: Helvetica, Arial, sans-serif;
}
```

#### 2. Google Fonts és más webszolgáltatások
A **Google Fonts** egy ingyenes, hatalmas betűtípus-gyűjtemény. Használata:
1.  Válaszd ki a betűtípust a [fonts.google.com](https://fonts.google.com) oldalon.
2.  Generálj egy `<link>` taget, amit a HTML fájlod `<head>` részébe kell illeszteni.
3.  A CSS-ben a megadott `font-family` névvel hivatkozhatsz rá.

**Példa:**
A HTML `<head>` szekciójában:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```
A CSS fájlban:
```css
h3 {
  font-family: 'Roboto', sans-serif;
}
```

#### 3. Saját, egyedi betűtípusok (`@font-face`)
Ha teljesen egyedi betűtípust szeretnél használni, azt a `@font-face` szabállyal teheted meg. Szükséged lesz a betűtípus fájljaira (pl. `.woff2`, `.woff`).
```css
@font-face {
  font-family: 'SajatBetutipusom'; /* Tetszőlegesen választott név */
  src: url('/fonts/sajatbetutipus.woff2') format('woff2'),
       url('/fonts/sajatbetutipus.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}
```
Ezután a megadott `font-family` névvel már bárhol használhatod:
```css
body {
  font-family: 'SajatBetutipusom', Arial, sans-serif;
}
```

---

### Szövegstílus és méret

A szöveg kinézetét számos tulajdonsággal finomhangolhatjuk.

| Tulajdonság | Leírás | Gyakori értékek |
| :--- | :--- | :--- |
| **`font-size`** | Betűméret | `16px`, `1.2em`, `1.2rem`, `12pt`, `large`, `80%` |
| **`font-weight`**| Betűvastagság | `normal` (400), `bold` (700), `100`-`900` |
| **`font-style`** | Betűstílus | `normal`, `italic` (dőlt) |
| **`color`** | Betűszín | `#333`, `rgb(51, 51, 51)`, `black` |
| **`text-decoration`** | Szövegdíszítés | `none`, `underline` (aláhúzás), `line-through` (áthúzás) |
| **`font-variant`**| Betűvariáns | `normal`, `small-caps` (kiskapitális) |

**`font` rövidítés (shorthand) használata:**

Ahelyett, hogy minden tulajdonságot külön sorban adnánk meg, használhatjuk a `font` rövidítést. A sorrend fontos: `font-style`, `font-weight`, `font-size`/`line-height`, `font-family`.
```css
p {
  /* Hosszú változat */
  font-style: italic;
  font-weight: bold;
  font-size: 16px;
  line-height: 1.5;
  font-family: Georgia, serif;

  /* Ugyanaz röviden */
  font: italic bold 16px/1.5 Georgia, serif;
}
```

---

### Térközök és igazítás

A szöveg olvashatóságát nagyban befolyásolja a sorok, szavak és betűk közötti távolság.

| Tulajdonság | Leírás | Példa értékek |
| :--- | :--- | :--- |
| **`text-align`** | Vízszintes igazítás | `left`, `right`, `center`, `justify` (sorkizárt) |
| **`line-height`**| Sorköz (sortávolság)| `1.5`, `1.6em`, `24px` |
| **`letter-spacing`**| Betűköz | `1px`, `0.1em`, `-0.5px` (negatív is lehet) |
| **`word-spacing`** | Szóköz | `5px`, `0.4em` |
| **`text-indent`** | Első sor behúzása | `20px`, `2em` |