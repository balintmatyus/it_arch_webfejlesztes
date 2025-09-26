# Felhasználói felület tervezése I.

Egy nagy látogatottságú weboldal jelentős értékkel bír. Miután növeli a cég imidzsét, láthatóvá teszi a céget akár távoli régiókban is, növeli a piacot, gyors és megbízható kommunikációt tesz lehetővé. Nem mellesleg 24 órás reklámhordozó.

A hatékony digitális design messze túlmutat az esztétikán: tudatos problémamegoldás, amelynek célja a felhasználói viselkedés pozitív befolyásolása. A **jó design** nem szubjektív ízlés kérdése, hanem jól definiált elveken alapul.

## A webfejlesztés folyamata dióhéjban

Bár a kurzus a HTML, CSS és JavaScript technikai részleteire koncentrál, a kódolás egy nagyobb, több lépésből álló folyamat része. A sikeres weboldal titka a gondos előkészítésben rejlik, és az alábbi vázlat segít elhelyezni a programozói munkát a teljes projekt térképén.

**1. Stratégia és tervezés (A "Miért?")**
Mielőtt kódot írnánk, meg kell határozni a weboldal **célját** és **célközönségét**. Ekkor készül el a weboldal vázlatos szerkezete (**drótváz** vagy [wireframe](https://www.geeksforgeeks.org/websites-apps/wireframing/)), ami a későbbi fejlesztés alapját képezi.

**2. UI/UX Dizájn (A "Hogyan nézzen ki?")**
A drótvázakra építve a tervezők a *felhasználói élmény* (UX) és a *felhasználói felület* (UI) megtervezésével folytatják. A modern webdesign e két kulcsfontosságú pillére biztosítja, hogy a végeredmény ne csak szép, de hatékony és könnyen használható is legyen.
* **UX (User Experience) Design**: A felhasználói élmény stratégiai tervezése. A UX célja, hogy a weboldal használata logikus, intuitív és élvezetes legyen a felhasználó számára, miközben az üzleti célokat is maximálisan támogatja. Ez a folyamat a felhasználói kutatástól az információs architektúrán át a prototípus-tesztelésig terjed.
* **UI (User Interface) Design**: A felhasználói felület vizuális megtervezése. Ide tartozik az elrendezés, a színek, a tipográfia és a grafikai elemek egységes, esztétikus és következetes rendszere.

**3. Fejlesztés (A megvalósítás)**
Itt kel életre a terv. A fejlesztők leprogramozzák a vizuális terveket, és felépítik a weboldal működő, interaktív felületét. A két fő területéről (Frontend, Backend) már korábban olvashattunk az [Egy modern webalkalmazás anatómiája](../week01/01-fullstack.md) fejezetben.

**4. Tesztelés és optimalizálás (A finomhangolás)**
Az elkészült oldalt alaposan tesztelni kell, hogy minden hibátlanul működjön. Az indítás után a munka nem áll meg: **analitikai adatok** alapján folyamatosan figyelik és fejlesztik a weboldalt a még jobb eredményekért.

A webfejlesztés és a webdesign nem választható el élesen; a sikeres végtermék e szakterületek szoros együttműködésének eredménye.

>[!NOTE]
>Fenti felosztás egy lineáris ([vízesésszerű](https://www.geeksforgeeks.org/software-engineering/waterfall-model/)) felosztása a fejlesztési folyamatnak. Későbbi kurzusokon hallhattok még további, megközelítésekről is, mint az [Agilis módszertanról](https://www.geeksforgeeks.org/software-testing/what-is-agile-methodology/) vagy a [DevOpsról](https://www.geeksforgeeks.org/devops/introduction-to-devops/).

>[!NOTE]
>Több elmélet, modell is létezik, amely leírja, hogy "Mitől jó egy design?". Érdemes megemlíteni [Gestalt alapelveit](https://uxdesignblog.hu/articles/gestalt), valamint [Nielsen 10 heurisztikáját](https://innovationdesign.hu/ux/10-usability-heurisztika-nielsen/).

## CSS alapjai

CSS (Cascading Style Sheets) stílusleíró nyelv. Az első megjelenése 1994-ben volt Hakon Wium Lie ötlete alapján. Ehhez a csoporthoz csatlakozott később a W3C, és a Microsoft is, akik belátták ennek a jelentőségét. Korábban a CSS-nek különböző verzióit különböztethettük meg (pl. CSS 2.1), ma azonban a CSS-t modulokra bontották (színek, elrendezés, animációk stb.) és azokat külön-külön fejlesztik és verziózzák. Ezt nevezzük CSS3-nak.

A HTML önmagában struktúrát ad a dokumentumnak, de a böngészők alapértelmezett stílusai (pl. a címsorok nagyobb betűvel, a bekezdések új sorban és térközzel jelennek meg) csak nagyon alapvető olvashatóságot biztosítanak. A CSS-sel azonban sokkal többet tehetünk:
* Szöveg stílusozása (szín, méret, betűtípusok).
* Elrendezések létrehozása (pl. grid vagy többoszlopos elrendezések).
* Speciális effektek, például animációk hozzáadása.

### Stílusok definiálása

2 fő részből állnak:
* szelektor (`h1`)
* deklaráció (`color: red;`)

A deklaráció is 2 részből áll:
* tulajdonság (`color`)
* érték (`red`)

Pl.:
```css
h1 {
  color: red;
  font-size: 24px;
}
```

A CSS definiálása többféle módon lehetséges. HTML forráskódon belül
* `<style>` utasítás segítségével: a HTML `<head>` blokkjában definiáljuk a stílusokat
* Külső stíluslapok használata: külön fájlban, kiterjesztése: css, nincsenek benne HTML tagek, csak stílusok
* in-line, amikor HTML fájlon belül, az egyes HTML elemek tag-jeiben definiáljuk

#### **Stíluslap készítése `<style>` utasítás segítségével**

```html
<head>
   <style>
     h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
     h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
     h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
   </style>
</head>
```

Így néz ki a törzs rész

```html
<body>
   <h1>Repülőgépek</h1>
   <h2>Vitorlázó gépek</h2>
   <h3>R26 Góbé</h3>
</body>
```

Ez a megközelítés általában akkor lehet "kézenfekvő", ha egy adott HTML oldalhoz nagyon specifikus, vagy csak arra az egy oldalra vonatkozó stílusokat szeretnél alkalmazni. Így a stílusdefiníciók azonnal elérhetők az oldal betöltésekor, és azonnal hatással vannak a HTML elemek megjelenésére.

#### **Stíluslap használata külső stíluslapokkal**

A stíluslap külön, .css kiterjesztésű fájlban is létrehozható. Ilyenkor is a `<head>` részben hivatkozunk rá.

**Példa:**

```html
<head>
   <link rel="stylesheet" href="formazas1.css">
</head>
```

A törzsrész ugyanúgy néz ki, mint az első esetben:

```html
<body>
   <h1>Repülőgépek</h1>
   <h2>Vitorlázó gépek</h2>
   <h3>R26 Góbé</h3>
</body>
```

`link` utasítás paraméterei:
* rel - kapcsolat típusa ("stylesheet")
* href - stíluslap (vmi.css) helyének megadása

A `<link>` utasítást a HTML kód fejrészén belül (`<head>` utasítások között) kell megadni.
A külső stíluslap (formazas1.css) a következőképpen nézhet ki:

```css
h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
```

A külső stíiluslap előnyei
* **Könnyebben kezelhető**, hiszen HTML dokumentum módosítása nélkül változtathatjuk stílusbeállításokat.
* **Átlátható**, hiszen a stílus elkülönül a tartalomtól és struktúrától.
* **Gyorsabb betöltés** gyakori látogatás esetén. (cache)
* **Újrahasznosítható** stílus lapok, hiszen egy CSS fájl megadható több HTML oldalhoz is.

#### **Stíluslap készítése style paraméter segítségével, in-line CSS**

```html
<body>
   <h1 style="font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;">Repülőgépek</h1>
   <h2 style="font-size: 24px; color: red; font-family: Verdana, sans-serif;">Vitorlázó gépek</h2>
   <h3 style="font-size: 18px; color: blue; font-family: 'Courier New', monospace;">R26 Góbé</h3>
</body>
```

A style paraméter előnyei:
* **Közvetlen és azonnali hatás**: A stílusokat közvetlenül az adott HTML elemre alkalmazzuk. Ez azt jelenti, hogy azonnal látod az eredményt, és nem kell aggódnod a CSS szelektorok vagy a kaszkád (stílusok öröklődése és felülírása) bonyolultsága miatt. A böngésző ezt a stílust azonnal alkalmazza az elemre, amint eléri azt. Ez a legmagasabb szintű közvetlen befolyás, amit egyedi elemre gyakorolhatsz.
* **Magas prioritás (specifitás)**: Az inline stílusoknak van a legmagasabb prioritásuk a CSS hierarchiában. Ez azt jelenti, hogy ha egy elemet inline módon stílusozol, az felülír minden más stílust, ami belső (`<style>` tagben lévő) vagy külső `.css` fájlból érkezik, kivéve, ha azokban `!important` deklarációt használnak (amit általában kerülni szoktunk). Szóval, ha biztosra akarsz menni, hogy egy adott elem stílusa felülíródjon, akkor az inline módszer "gyors megoldásnak" tűnhet.
* **Egyszerűség nagyon specifikus, egyedi esetekben**: Ha tényleg csak egyetlen, nagyon specifikus elemet kell stílusozni egy oldalon, és tudod, hogy soha többé nem lesz szükséged ugyanarra a stílusra máshol, akkor elsőre egyszerűbbnek tűnhet közvetlenül a `style` attribútumba írni. Ilyenkor nincs szükség külön CSS fájlra vagy `<style>` blokkra.

>[!WARNING]
> **De most jön a "de"**: Fontos kiemelni, hogy bár ezek "előnyöknek" tűnhetnek, valójában az **inline CSS használata a legtöbb esetben rossz gyakorlatnak minősül a webfejlesztésben**. Miért?
>1.  **Rossz karbantarthatóság**: Képzeld el, hogy több száz HTML oldalból áll a webhelyed, és minden `<p>` tagnek egyedi stílusa van inline CSS-sel. Ha meg akarsz változtatni valamit (pl. az összes paragrafus betűszínét), akkor minden egyes HTML fájlt, minden egyes `<p>` tagjét át kellene írnod! Egy külső stíluslap esetén ez egyetlen CSS fájl egyetlen sorának módosítását jelentené.
>2.  **Nehéz újrahasznosíthatóság**: Az inline stílusok nem használhatók fel újra más elemeken vagy más oldalakon, hiszen be vannak ágyazva egy konkrét HTML elembe. Ez rontja a kódhatékonyságot.
>3.  **Szennyezi a HTML-t**: A HTML feladata a tartalom struktúrájának megadása, a CSS feladata pedig a vizuális megjelenésé. Az inline CSS összemossa ezt a két feladatkört, ami rontja a kód olvashatóságát és logikai elkülönítését. A JavaScript esetében sem javasolt a HTML kód "szennyezése", és ez a CSS-re is igaz.

Összességében tehát, bár az inline CSS gyorsan alkalmazható és magas prioritású, hosszú távon a karbantartás, az újrahasznosíthatóság és a kód tisztasága miatt **erősen javasolt külső stíluslapokat használni**.

### CSS szelektorok

A CSS szelektorok a CSS szabályok első részét képezik. Ezek elemek és más kifejezések mintái, amelyek megmondják a böngészőnek, hogy mely HTML elemeket kell kiválasztani, hogy a szabályban szereplő CSS tulajdonságértékeket alkalmazza rájuk. Az elem vagy elemek, amelyeket a szelektor kiválaszt, a szelektor *alanyát* képezik.

#### Típus-szelektorok (Element / Tag Name Selectors)
A típus-szelektorokat néha *tag név szelektoroknak* vagy *elem szelektoroknak* is nevezik. Az HTML elem nevével választják ki az elemeket a dokumentumból. Amikor egy ilyen szelektorhoz stílusokat rendelünk, az adott típusú összes HTML elem megkapja ezeket a stílusokat. A lenti `span` szelektor kiválasztja az összes `<span>` elemet és azok háttérszínét sárgára állítja.

```css
span { background-color: yellow; }
```

#### Osztály-szelektorok (Class Selectors)
Az osztály-szelektorok egy pont (`.`) karakterrel kezdődnek. Kiválasztanak mindent a dokumentumban, amire az adott osztályt alkalmazták. Az osztálynevek kis- és nagybetű érzékenyek. Egy elemhez több osztály is rendelhető, és ezekkel a stílusok rétegezhetők.

```html
<p class="highlight">Ez egy minta bekezdés a CSS osztály definíciójára.</p>
```

* **Alapvető használat**: Egyetlen osztály stílusozása.
    * Például egy `.highlight` nevű osztályt hozhatunk létre, és a `highlight` osztállyal ellátott összes elem kiemelt lesz. A lenti szabály sárga háttérszínt ad minden ilyen elemnek.

    ```css 
    .highlight { background-color: yellow; }
    ```

* **Osztályok célzása adott elemeken**: Létrehozhatunk egy szelektort, amely az adott osztállyal rendelkező konkrét elemeket célozza meg. Ezt úgy tesszük, hogy az elem típus-szelektorát használjuk, majd közvetlenül utána, szóköz nélkül hozzáfűzzük az osztályt egy ponttal. Ez a megközelítés csökkenti a szabály hatókörét, mivel csak az adott elem és osztály kombinációjára vonatkozik.
  * Például a `span.highlight { background-color: yellow; }` csak a `<span>` elemekre érvényes, amelyeknek van "highlight" osztályuk.
  * Az `h1.highlight { background-color: pink; }` pedig csak az `<h1>` elemekre, amelyeknek van "highlight" osztályuk.

  ```css
  span.highlight { background-color: yellow; }
  h1.highlight { background-color: pink; }
  ```

* **Több osztály együttes célzása**: Ha egy elemnek több osztálya van, és csak akkor szeretnénk stílusozni, ha *összes* megadott osztálya jelen van, az osztályneveket szóköz nélkül láncolhatjuk össze.
  * Például egy `.notebox.warning { border-color: orange; font-weight: bold; }` szabály csak azokra az elemekre vonatkozik, amelyeknek *mind* a "notebox", *mind* a "warning" osztályuk van. Ha egy elemnek csak a "danger" osztálya van, a `notebox` osztály hiányában nem kapja meg a stílust.

  ```css
  .notebox.warning { border-color: orange; font-weight: bold; }
  ```

#### ID-szelektorok (ID Selectors)
Az ID-szelektorok egy hash jellel (`#`) kezdődnek. Használatuk hasonló az osztály-szelektorokhoz, de fontos különbség, hogy egy `id` értéknek egyedinek kell lennie az egész HTML dokumentumban. Egyetlen ID csak egyetlen elemhez tartozhat az oldalon.

* **Használat**: Az ID-szelektor kiválasztja azt az elemet, amelyhez a megadott `id` tartozik. Egy típus-szelektorral is megelőzhető az ID, hogy csak akkor célozzunk, ha az elem típusa és az ID is megegyezik.
    *   Például az `#one { background-color: yellow; }` a "one" ID-vel rendelkező elem háttérszínét sárgára állítja.
    *   A `h1#heading { color: rebeccapurple; }` csak az `<h1>` elemre vonatkozik, amelynek "heading" az ID-je.

```css
#one { background-color: yellow; }
h1#heading { color: rebeccapurple; }
```

>[!WARNING]
>Az azonos ID többszöri használata érvénytelen kódot eredményez, és sok helyen furcsa viselkedést okozhat.

#### Szelektorkészletek (Selector Lists)
Ha több szelektorhoz azonos CSS stílusokat szeretnénk alkalmazni, akkor az egyedi szelektorokat egy *szelektorkészletbe* kombinálhatjuk, vesszővel elválasztva őket.

* **Példa**: A `h1, .special { color: blue; }` szabály a `<h1>` elemekre és a `.special` osztállyal rendelkező elemekre egyaránt alkalmazza a kék színt.
* **Olvashatóság**: Szóköz érvényes a vessző előtt vagy után. A szelektorokat új sorba is írhatjuk az olvashatóság javítása érdekében.
* **Érvénytelen szelektorok a listában**: Ha egy szelektorkészletben bármely szelektor szintaktikailag érvénytelen, az egész szabály figyelmen kívül marad. Ebben az esetben a böngésző egyik szelektorra sem alkalmazza a stílust.

```css
h1, .special { color: blue; }
```

#### Univerzális szelektor (Universal Selector)
Az univerzális szelektor egy csillaggal (`*`) jelölhető. Kiválasztja a dokumentum összes elemét. Ha leszármazott kombinátorral (pl. `article *`) láncolva használjuk, akkor az adott ős elemen belüli összes beágyazott elemet kiválasztja. Gyakran használják böngésző alapértelmezett stílusainak "resetelésére", például az összes elem külső és belső margójának eltávolítására. Ez a viselkedés gyakran látható a "reset stíluslapokban".

```css
* {
  margin: 0;
  padding: 0;
}

article * {
  border: 2px dotted red;
}
```

## Szöveg formázása

Fontos a szöveg formázásáról is külön szót ejteni, hisz a legtöbb információtartalmat a szöveg hordozza. Ez a tudományterület - **tipográfia** - már [Gutenberg](https://en.wikipedia.org/wiki/Johannes_Gutenberg) kora óta fejlődik. Azonban a honlapok estében elég speciális tulajdonságokra szoktunk hivatkozni:

* A tartalom állandó vagy dinamikusan frissülő információ.
* Felépítése többdimenziós mátrix.
* Fejezetek sajátos logikai kapcsolat alapján állnak össze.
* Csak a technika határozza meg a megjelenését.

Szöveg befogadása teljesen másként történik a honlapok esetében, mint egy papír alapú tartalom esetében. A szemünk eleve más módon dolgozza fel a bejövő információ tartalmat. Nem egymás utáni betűfeldolgozás van, hanem fixációs tartományokon belül elhelyezkedő információtartalmak feldolgozása. Ez azért van, mert a képernyőn közvetített tartalmakattartományokként értelmezi az agyunk.

Kiindulás: mekkora szöveget képes a szemünk egyszerre átlátni?

$v=\frac{(s-\delta)}{t_{f_{x}}}$ [betű/sec]; ahol
* $s=$ az egy pillantással átfogott betűk száma, **fixációs szélesség**;
* $\delta=$ túlfedés, a **kétszeresen fixált szövegrész**;
* $t=a$ **fixációs idő**;

Ez egy átlag magyar ember esetében 25 betű másodpercekénti feldolgozását jelenti. Mivel nem az egymás utáni betűket rakjuk össze szavakká, hanem a számítógépen a jeleket érzékeljük egy fixációval, és az agyunk ezt a képet kódolja és látja el tartalommal. Ez azt jelenti, hogy átlagosan 12-20 betűből álló szavakat vagyunk képesek egy fixációval az agyunkba juttatni.

### Szövegek használata a képernyőn

Az olvasási metódus jellegzetessége miatt fontos, hogy alapvető szövegelhelyezési szabályokat betartsunk. Minden szabály alapját a fixációs adatfeldolgozás indokolja.

Kétféle betűforma létezik. A betűformák különböző jelzéseket továbbítanak a felhasználóknak. Az emberek a **seriff** betűformákat klasszikusnak és elegánsnak tartják, ezzel szemben a **sans serif** betűformát modernnek és világosnak ítélik meg. Azonban a honlapok esetében célszerű a sans seriff formákat előnyben részesíteni, mert a szem könnyebben a fixációs tartományban lehatárolni a betűformákat.

Ha egy képernyő oldalon túl sok betűtípus található, akkor az oldal megjelenése zavaros. A sok betűtípus már csak azért is zavaró, mert a néző az oldal szerkezetének a „megfejtésével" törődik és nem összpontosít az üzenetre. Ha egy oldalon szövegelemeket meg kell különböztetni egymástól, célszerű különböző betűméretekkel és stílusokkal dolgozni vagy különböző háttereket használni.

A mondanivalót egyszerű, világos mondatokba kell sűríteni. A mondatok legyenek a lehető legrövidebbek. Ezt is fentebb említettük, miután a fixációs tartományok nem végtelenek, így megfelelő bit információ egyszeri felvétele és hatékonysága ezáltal biztosítható.

A használandó betűtípusok általában a megjelenítő képernyő méretétől függnek. Nagyobb felbontású képernyőn általában a betűméretek kisebbek. Egy számítógép képernyőjén bemutatott interaktív termék esetében természetes, hogy a néző a képernyő előtt ül. Mivel a képernyők felbontása jó, kisebb méretű betűk is jól olvashatók, azonban gondolnunk kell a mobil eszközökre is.

>[!WARNING]
>A csupa nagybetűből álló szöveg kevésbé olvasható, mint a nagy- és kisbetűt keverve használó. Csupa nagybetűből álló szövegbe beleolvadnak a nagybetűvel kezdődő szavak. Ilyen szövegben nem tűnik ki a mondatok kezdete, vagyis nem behatárolható a fixációs tartomány. A nagybetűs szöveg használatát rövid címekre és a szövegből kiemelni kívánt dolgokra kell korlátozni.
>Ha félkövér betűket korlátozottan használunk, a szöveg áttekinthető, olvasható lesz, ugyanakkor a félkövér szövegrész felhívja magára a figyelmet. Túl sok félkövér szövegrész a szöveget súlyossá teszi és elmarad a figyelemfelkeltő jellege.

### Betűtípusok használata (`font-family`)

A megfelelő betűtípus kiválasztása kulcsfontosságú a weboldal olvashatósága és hangulata szempontjából. Három alapvető módszer létezik a betűtípusok beállítására.

#### 1. Rendszer (biztonságos) betűtípusok
Ezek a leggyakoribb, a legtöbb operációs rendszeren előre telepített betűtípusok (pl. Arial, Helvetica, Times New Roman, Courier New). Mivel szinte minden eszközön elérhetők, megbízhatóan jelennek meg.

Érdemes mindig egy "fallback" listát (betűtípus-családot) megadni. A böngésző az első elérhető típust fogja használni a felsorolásból. A lista végén általában egy általános kategóriát adunk meg (pl. `sans-serif` vagy `serif`).

```css
p {
  font-family: Helvetica, Arial, sans-serif;
}
```

#### 2. Google Fonts és más webszolgáltatások
A **Google Fonts** egy ingyenes, hatalmas betűtípus-gyűjtemény. Használata egyszerű:
1.  Válaszd ki a kívánt betűtípust a [fonts.google.com](https://fonts.google.com) oldalon.
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
Bár a szolgáltatás stabil, elméletben fennáll a kockázata, hogy a link megváltozik vagy a szolgáltatás leáll.

#### 3. Saját, egyedi betűtípusok (`@font-face`)
Ha teljesen egyedi betűtípust szeretnél használni, azt a `@font-face` szabállyal teheted meg. Ehhez szükséged lesz a betűtípus fájljaira (pl. `.woff2`, `.woff`, `.ttf`).

**Lépései:**
1.  Helyezd a font fájlokat a projekted egy mappájába (pl. `/fonts`).
2.  Definiáld a betűtípust a CSS fájlod elején a `@font-face` szabállyal:

```css
@font-face {
  font-family: 'SajatBetutipusom'; /* Tetszőlegesen választott név */
  src: url('/fonts/sajatbetutipus.woff2') format('woff2'),
       url('/fonts/sajatbetutipus.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}
```
3.  Ezután a megadott `font-family` névvel már bárhol használhatod a weboldalon:

```css
body {
  font-family: 'SajatBetutipusom', Arial, sans-serif;
}
```

A `.woff2` formátum a legjobb választás a modern böngészőkhöz a hatékony tömörítése miatt, míg a `.woff` a régebbi böngészők számára biztosít kompatibilitást.

---

### Szövegstílus és méret

A szöveg kinézetét számos tulajdonsággal finomhangolhatjuk. A legfontosabbak egyetlen `font` rövidítéssel is megadhatók, de külön-külön is használhatók.

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

### Térközök és igazítás

A szöveg olvashatóságát nagyban befolyásolja a sorok, szavak és betűk közötti távolság, valamint a szöveg elrendezése.

| Tulajdonság | Leírás | Példa értékek |
| :--- | :--- | :--- |
| **`text-align`** | Vízszintes igazítás | `left`, `right`, `center`, `justify` (sorkizárt) |
| **`line-height`**| Sorköz (sortávolság)| `1.5`, `1.6em`, `24px` |
| **`letter-spacing`**| Betűköz | `1px`, `0.1em`, `-0.5px` (negatív is lehet) |
| **`word-spacing`** | Szóköz | `5px`, `0.4em` |
| **`text-indent`** | Első sor behúzása | `20px`, `2em` |