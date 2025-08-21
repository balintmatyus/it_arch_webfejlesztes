# HTML5 alapjai

##  Elemek, attribútumok és a dokumentum szerkezete

A **HTML** (HyperText Markup Language) egy leíró nyelv, amely a weboldalak tartalmának strukturálására szolgál. Nem egy programozási nyelv, hanem egy **jelölőnyelv**, amely megmondja a böngészőnek, hogyan jelenítse meg az egyes tartalmi részeket, például címeket, bekezdéseket vagy képeket. A HTML dokumentumok egyszerű szöveges fájlok, általában `.html` kiterjesztéssel.

A HTML alapvető építőkövei az **elemek**. Egy elem segítségével jelöljük meg, zárjuk körbe vagy csomagoljuk be a tartalom különböző részeit, hogy azok egy bizonyos módon jelenjenek meg vagy viselkedjenek. Például egy szövegrészt bekezdésként (`<p>`) vagy félkövérként (`<strong>`) jelölhetünk meg.

Minden HTML elem egy meghatározott anatómia szerint épül fel. Ez általában három részből áll: **a nyitó tagből** (pl. `<p>`), a **tartalomból** (a szöveg vagy más elem, amire a `<p>` vonatkozik) és a **záró tagből** (pl. `</p>`). A záró tag megegyezik a nyitóval, de egy perjel (`/`) található benne. A tag-ek nevei nem számítanak kis- és nagybetűérzékenynek, de a bevett gyakorlat a kisbetűs írásmód.

```html
<p>Ez egy bekezdés.</p>
<p>Ez egy másik bekezdés.</p>
```

Az elemek egymásba is ágyazhatók, ezt nevezzük **beágyazásnak** (nesting). Ha például egy bekezdésen belül egy szót különösen hangsúlyozni szeretnénk, a `<strong>` elemet a `<p>` elemen belül helyezhetjük el. A helyes beágyazás kulcsfontosságú: a belső elem záró tagjének meg kell előznie a külső elem záró tagjét. A helytelen sorrend hibás megjelenítéshez vezethet.

```html
<p>Ez egy <strong>kiemelt</strong> üzenet.</p>
```

Léteznek olyan elemek is, amelyek nem rendelkeznek záró taggel és tartalommal. Ezeket **üres elemeknek** (void elements) nevezzük. Tipikusan arra szolgálnak, hogy valamilyen tartalmat, például egy képet, beillesszenek a dokumentumba. A legismertebb példa az `<img>` elem, amely egy képfájlt jelenít meg az oldalon.

Az elemek rendelkezhetnek **attribútumokkal** is, amelyek további információkat hordoznak az elemről, de ezek az információk nem jelennek meg a tényleges tartalomban. Az attribútumok a nyitó tagben kapnak helyet, és egy névből, egy egyenlőségjelből, valamint idézőjelek közé zárt értékből állnak (pl. `class="kiemelt"`). Az `<img>` elem `src` (forrás) és `alt` (alternatív szöveg) attribútumai például megadják a kép elérési útját és egy rövid leírást róla.

```html
<img src="https://www.uni-corvinus.hu/contents/themes/corvinus-theme/library/img/corvinus_logo_2024.svg" alt="A Corvinus hivatalos logója" width="673">
```

Az attribútumok értékeit mindig idézőjelek közé kell tenni. Bár a böngészők bizonyos esetekben elfogadják az idézőjelek nélküli értékeket, ez könnyen hibához vezethet, különösen ha az érték szóközöket tartalmaz. Használhatunk szimpla vagy dupla idézőjeleket is, de fontos a következetesség. Ha egy idézőjelet szeretnénk megjeleníteni az attribútum értékén belül, karakterreferenciát kell használnunk.

> [!QUESTION]
> A böngésző az általa fel nem ismert elemeket jellemzően figyelmen kívül hagyja. Gondoljuk végig, ennek a megoldásnak milyen előnyei és hátrányai vannak? (Elgépelés a HTML-ben, kompatibilitás böngészőverziók között)

Egy teljes HTML dokumentum nem csak egyedi elemekből áll, hanem egy meghatározott alapstruktúrával is rendelkezik. Minden dokumentum a `<!doctype html>` deklarációval kezdődik, amely a böngészőnek jelzi a dokumentum típusát. Ezt követi a `<html>` elem, amely az egész oldalt körbeveszi. A `<html>` elemen belül található a `<head>` és a `<body>` rész.

A `<head>` szekció tartalmazza az oldal meta-információit, amelyeket a felhasználó közvetlenül nem lát. Ide tartozik például az oldal címe (`<title>`), amely a böngésző fülén jelenik meg, a karakterkódolás beállítása (`<meta charset="utf-8">`), valamint a stíluslapokra (CSS) és szkriptekre (JavaScript) mutató hivatkozások. Ezzel szemben a `<body>` elem tartalmazza az összes látható tartalmat: szövegeket, képeket, videókat és minden mást. A `<meta name="description" content="...">` egy rövid leírást ad az oldalról, amelyet a keresőmotorok (pl. Google) gyakran megjelenítenek a találati listában a cím alatt.

```html
<!doctype html>
<html lang="hu">
<head>
    <meta charset="utf-8">
    <title>Példa weboldalra</title>
    <meta name="description" content="Ez egy rövid, informatív leírás a weboldal tartalmáról.">
    <link rel="stylesheet" href="stilusok.css">
    <script src="script.js" defer></script>
</head>
<body>
    <p>Ez egy <strong>kiemelt</strong> üzenet.</p>
</body>
</html>
```

Végül fontos megemlíteni a **kommenteket** és a **speciális karaktereket**. A HTML-ben a `<!--` és `-->` jelek közé írt szöveg kommentnek minősül, amelyet a böngésző figyelmen kívül hagy. Ez hasznos jegyzetek elhelyezésére a kódban. Ha olyan speciális karaktereket szeretnénk megjeleníteni, mint a `<` vagy `&`, amelyek a HTML szintaxis részét képezik, **karakterreferenciákat** (pl. `&lt;` és `&amp;`) kell használnunk, hogy a böngésző ne kódként értelmezze őket. Teljes lista [itt](https://quickref.me/html-char.html) található.

```html
<p>Ha a '<' jelet szeretnénk megjeleníteni, akkor az &lt; kódot kell használnunk.</p>

<p>Például, a p-tagek használata így néz ki: &lt;p&gt;Ez egy paragrafus.&lt;/p&gt;</p>

<p>Az '&' jel megjelenítéséhez az &amp; kódot használjuk, például a Fekete &amp; Társa cégnévben.</p>
```

## Címsorok és bekezdések: A tartalom strukturálása

A HTML egyik legfontosabb feladata, hogy **struktúrát** adjon a szöveges tartalomnak. Ennek alapvető eszközei a címsorok és a bekezdések, amelyek nélkül a böngésző a teljes szöveget egyetlen, formázatlan szövegtömbként jelenítené meg. A helyes strukturálás nemcsak a vizuális megjelenést javítja, hanem a felhasználói élményt, a keresőoptimalizálást (SEO) és az akadálymentesítést is alapjaiban határozza meg.

A HTML hat különböző szintű címsort (`<h1>`-től `<h6>`-ig) és egy bekezdés elemet (`<p>`) kínál a tartalom tagolására. Az `<h1>` jelöli a legmagasabb szintű címsort, általában a dokumentum főcímét, míg az `<h2>` az alcímeket, az `<h3>` pedig az al-alcímeket jelöli, és így tovább. Minden bekezdést egy `<p>` elembe kell csomagolni. Ezek az elemek alkotják a dokumentum logikai vázát.

A címsorok használatakor kulcsfontosságú a **logikai hierarchia** betartása. Bevett gyakorlat, hogy egy oldalon csak egyetlen `<h1>` elemet használunk a főcímhez. A címsorok szintjeit nem szabad átugrani (pl. egy `<h2>` után nem következhet `<h4>`), mivel ez megzavarja a dokumentum szerkezetét. A címsorokat nem szabad pusztán vizuális céllal, a betűméret megváltoztatására használni; ez a feladat a CSS-re tartozik.

De miért van szükség erre a szigorú struktúrára? Először is, a felhasználók gyorsan átfuttatják a weboldalakat, és a címsorok segítenek nekik megtalálni a releváns információt. Másodszor, a keresőmotorok a címsorokban található kulcsszavakat fontosabbnak tekintik, így a helyes használat javítja az oldal **SEO** helyezését. Harmadszor, a látássérült felhasználók által használt **képernyőolvasó szoftverek** a címsorokat használják „útjelző táblaként” a tartalomban való navigáláshoz, így a címsorok hiánya szinte használhatatlanná teszi számukra az oldalt.

A strukturálás mögött meghúzódó legfontosabb elv a **szemantika**: a megfelelő HTML elem használata a megfelelő célra. Egy `<h1>` elem nemcsak nagyobbra formázza a szöveget, hanem közli a böngészővel és a segítő technológiákkal, hogy az a szöveg „az oldal legfontosabb címe”. Ezzel szemben a `<span>` egy általános, soron belüli (inline) konténer, amely önmagában nem hordoz jelentést. Arra használjuk, hogy egy szövegrészletet megjelöljünk, tipikusan azért, hogy CSS-sel stílust adjunk neki, vagy JavaScripttel célozzuk meg, anélkül, hogy a dokumentum szerkezetét megváltoztatnánk. Ha tehát egy `<span>` elemet formázunk úgy, hogy címsornak tűnjön, az elveszíti a szemantikai értékét, és nem fogja segíteni sem a SEO-t, sem az akadálymentesítést. A helyes elemek használata olyan, mint a közlekedési lámpák: a pirosnak azt kell jelentenie, hogy „állj” – ha más jelentést adnánk neki, káosz alakulna ki.

```html
<body>
    <!-- 1. HELYES HIERARCHIA -->
    <h1>A Webfejlesztés Alapjai (Főcím)</h1>
    <p>Ez a bekezdés a főcímhez tartozó bevezető szöveget tartalmazza.</p>

    <h2>HTML Alapok (Alcím)</h2>
    <p>Itt a HTML alapjairól esik szó, amely a weboldalak vázát adja.</p>

    <h3>Elemek és Attribútumok (Al-alcím)</h3>
    <p>Ez a rész részletesebben foglalkozik az elemekkel és attribútumokkal.</p>

    <h2>CSS Alapok (Másik alcím)</h2>
    <p>A CSS felel a weboldalak vizuális megjelenéséért, a színekért és elrendezésért.</p>

    <hr>

    <!-- 2. HELYTELEN HIERARCHIA (KERÜLENDŐ PÉLDA) -->
    <h1>Ez egy főcím</h1>
    <h4>Ez egy helytelenül használt címsor, mert átugrottuk a h2 és h3 szinteket.</h4>
    <p>Ez a gyakorlat megzavarja a dokumentum szerkezetét és rontja az akadálymentességet.</p>

    <hr>

    <!-- 3. SZEMANTIKUS VS. VIZUÁLIS CÍMSOR -->
    
    <!-- Helyes, szemantikus címsor -->
    <h2>Ez egy valódi, szemantikus alcím</h2>
    <p>A keresőmotorok és képernyőolvasók ezt alcímként fogják értelmezni.</p>

    <!-- Helytelen, csak vizuálisan formázott "címsor" -->
    <span style="font-size: 1.5em; font-weight: bold; display: block; margin-top: 1em;">
        Ez csak egy formázott szöveg, nem valódi címsor
    </span>
    <p>Bár kinézetre hasonlít egy alcímre, a böngésző és a segítő technológiák számára ez csak egy egyszerű szövegrészlet, jelentés nélkül.</p>
</body>
```

>[!NOTE]
> A `<hr>` utasítás egy horizontális vonalat ad hozzá az oldalhoz.

## Hangsúly és fontosság: Szemantikus kiemelés

A HTML nemcsak a tartalom strukturálására, hanem a szövegrészek **jelentésének finomítására** is lehetőséget ad. Erre szolgál a hangsúlyozás és a fontosság jelölése. A két legfontosabb szemantikus elem erre a célra az `<em>` (emphasis - hangsúly) és a `<strong>` (strong importance - erős fontosság). Az `<em>` elem a mondat jelentését megváltoztató hangsúlyt jelöl (ahogy a beszédben is hangsúlyozunk egy szót), és a böngészők alapértelmezetten dőlt betűvel jelenítik meg. A `<strong>` elem ezzel szemben a tartalom nagy fontosságát, sürgősségét vagy komolyságát jelöli (pl. egy figyelmeztetés), és általában félkövér stílust kap. Kulcsfontosságú, hogy ezeket az elemeket a szemantikai jelentésük miatt használjuk, nem pedig pusztán a vizuális stílus (dőlt vagy félkövér) eléréséért.

A helyzet bonyolultabb az `<i>`, `<b>` és `<u>` elemekkel. Ezeket eredetileg tisztán **prezentációs célokra** hozták létre (italic, bold, underline), egy olyan korban, amikor a CSS még nem volt elterjedt. Mivel a modern weben a szemantika kulcsfontosságú (a SEO és az akadálymentesítés miatt), az ilyen, jelentés nélküli prezentációs elemek használata elavulttá vált. A HTML5 azonban nem távolította el őket teljesen, hanem új, specifikus szemantikai jelentéssel ruházta fel őket.

A modern szabály szerint az `<i>`, `<b>` vagy `<u>` elemeket csak akkor helyénvaló használni, ha nincs náluk megfelelőbb szemantikus elem (mint az `<em>` vagy `<strong>`), és a jelentés hagyományosan dőlt, félkövér vagy aláhúzott stílust kíván. Az `<i>` elemet ma már olyan esetekben használjuk, mint **idegen szavak**, taxonómiai megnevezések vagy gondolatok jelölése. A `<b>` elem **kulcsszavak**, terméknevek vagy egy bekezdés bevezető mondatának kiemelésére szolgál, anélkül, hogy különösebb fontosságot adna neki. Az `<u>` használata a legritkább, mivel az aláhúzást erősen a hiperhivatkozásokhoz kötik; elsősorban **helyesírási hibák** vagy tulajdonnevek jelölésére javasolt, de a stílusát CSS-sel érdemes lehet módosítani.

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <title>Hangsúly és Fontosság Példa</title>
</head>
<body>
    <h1>Használati útmutató</h1>
    <p>
        Ez a kávéfőző <em>nem</em> játék. A használata előtt figyelmesen olvassa el az útmutatót!
    </p>
    <p>
        <strong>FIGYELEM:</strong> A forró részekhez ne érjen hozzá, mert súlyos égési sérülést okozhat!
    </p>
    <p>
        A gép egy speciális, <i>dekalcináló</i> folyadékot igényel a vízkőmentesítéshez.
        A <b>vízkőmentesítés</b> kulcsfontosságú a hosszú élettartamhoz.
    </p>
    <p>
        Ellenőrizze, hogy a <u class="helyesirasi-hiba">kapocsoló</u> ki van-e kapcsolva, mielőtt csatlakoztatja a hálózathoz.
    </p>
</body>
</html>
```

>[!NOTE]
>A CSS-ről (`<style>` tag) a későbbiekben lesz még szó.

A szövegek kiemelésén túl a HTML lehetőséget ad speciális tipográfiai jelölésekre is, amelyek elengedhetetlenek tudományos vagy matematikai tartalmak esetén.

- **Felső index** (`<sup>`): A `<sup>` (superscript) elem a tartalmát az alapszöveg fölé, kisebb méretben jeleníti meg. Tipikusan hatványkitevők (10<sup>3</sup>), mértékegységek (100 ⁰C), vagy sorszámok (pl. 1<sup>st</sup>) jelölésére használjuk.
- **Alsó index** (<sub>): A <sub> (subscript) elem a tartalmát az alapszöveg alá, kisebb méretben pozícionálja. Leggyakoribb felhasználási területe a kémiai képletek (pl. H₂O) vagy lábjegyzetek jelölése.

```html
<p>
    A víz (kémiai képlete: H<sub>2</sub>O) egy rendkívüli anyag.
    Forráspontja normál légköri nyomáson 100 <sup>o</sup>C.
</p>
```

## HTML Listák: A tartalom rendezése

A HTML három különböző típusú listát kínál a tartalmak logikus csoportosítására és strukturálására. A listák a weboldalak alapvető elemei, a navigációs menüktől a receptekig mindenhol megtalálhatók. A megfelelő lista típus kiválasztása kulcsfontosságú a szemantikus, jól strukturált és akadálymentes tartalom létrehozásához. A három fő típus a **rendezetlen (unordered)**, a **rendezett (ordered)** és a **leíró (description)** lista.

### Rendezett és Rendezetlen Listák

A **rendezetlen listát** (`<ul>` - unordered list) akkor használjuk, ha az elemek sorrendje nem számít. Tipikus példa erre egy bevásárlólista. A teljes listát egy `<ul>` elembe zárjuk, és minden egyes listaelem egy `<li>` (list item) elemen belül kap helyet. A böngészők ezeket alapértelmezetten valamilyen listajellel (pl. ponttal) jelenítik meg.

```html
<ul>
  <li>Tej</li>
  <li>Kenyér</li>
  <li>Tojás</li>
</ul>
```

Ezzel szemben a **rendezett listát** (`<ol>` - ordered list) akkor alkalmazzuk, ha az elemek sorrendje lényeges, például egy recept lépéseinél vagy egy útbaigazításnál. A szerkezete megegyezik a rendezetlen listáéval, azzal a különbséggel, hogy a `<ul>` helyett `<ol>` elemet használunk a `<li>` elemek körbezárására. A böngészők ezeket a listákat sorszámokkal (1, 2, 3...) jelölik.

```html
<ol>
  <li>Tedd a vizet forrni.</li>
  <li>Helyezd a teafiltert a csészébe.</li>
  <li>Öntsd rá a forró vizet.</li>
</ol>
```

### Listák egymásba ágyazása

A HTML lehetővé teszi a listák egymásba ágyazását is. Ez különösen hasznos, ha egy listaelemhez további alpontokat szeretnénk rendelni. Ezt úgy tehetjük meg, hogy egy teljes listát (legyen az `<ol>` vagy `<ul>`) egy másik lista `<li>` elemén belül helyezünk el. Egy recept utasításainál például egy lépéshez tartozó alternatívákat vagy pontosításokat egy beágyazott, rendezetlen listában adhatunk meg.

```html
<ol>
  <li>Reggeli teendők
    <ul>
      <li>Fogmosás</li>
      <li>Öltözködés</li>
    </ul>
  </li>
  <li>Indulás a munkába</li>
</ol>
```

### Leíró Listák

A **leíró lista** (`<dl>` - description list) egy speciálisabb lista típus, amely kifejezetten **kifejezések és azok definícióinak**, vagy kérdés-válasz párok megjelenítésére szolgál. Ez a lista három elemből épül fel:

* **`<dl>`:** Maga a leíró lista, amely körbeveszi a teljes szerkezetet.
* **`<dt>`:** (description term) A definiálandó kifejezés.
* **`<dd>`:** (description definition) A kifejezéshez tartozó leírás vagy definíció.

Egy `<dl>` listán belül több `<dt>`/`<dd>` pár is lehet. Arra is van lehetőség, hogy egyetlen kifejezéshez (`<dt>`) több definíciót (`<dd>`) is társítsunk. A böngészők a leíró listákat általában úgy jelenítik meg, hogy a definíciókat beljebb húzzák a kifejezésekhez képest, így vizuálisan is elkülönülnek.

```html
<dl>
  <dt>HTML</dt>
  <dd>HyperText Markup Language, a weboldalak vázának leírására szolgáló nyelv.</dd>
  <dt>CSS</dt>
  <dd>Cascading Style Sheets, a weboldalak vizuális stílusának definiálására szolgáló nyelv.</dd>
</dl>
```

## Képek hozzáadása

A képek beágyazásának alapvető eszköze a HTML-ben az `<img>` elem. Ez egy úgynevezett "üres elem", ami azt jelenti, hogy nincs záró tagje. A működéséhez két alapvető attribútumra van szükség: az `src`-re (source), amely a képfájl URL-címét (legyen az relatív vagy abszolút) tartalmazza, és az `alt`-ra, amely egy alternatív szöveges leírást ad a képről. Az `<img>` elemeket "helyettesített elemeknek" is nevezik, mivel a tartalmukat és méretüket egy külső erőforrás (a képfájl) határozza meg, nem pedig a HTML kód.

Az `alt` attribútum (alternatív szöveg) kritikus fontosságú az akadálymentesség és a felhasználói élmény szempontjából. Ez a szöveg jelenik meg, ha a kép valamilyen okból nem töltődik be (pl. elgépelt URL vagy lassú internetkapcsolat miatt). A képernyőolvasót használó látássérült felhasználók számára ez a leírás teszi "láthatóvá" a képet. A jó `alt` szöveg tömören leírja a kép tartalmát és funkcióját. Ha a kép pusztán dekoráció, az `alt` attribútumot üresen kell hagyni (`alt=""`), hogy a segítő technológiák átugorhassák.

A kép méretének megadása a `width` (szélesség) és `height` (magasság) attribútumokkal szintén kulcsfontosságú. Bár ezeket nem a kép átméretezésére kell használni (arra a CSS való), a kép eredeti méreteinek megadásával a böngésző már a kép letöltése előtt "lefoglalja" a helyét az oldalon. Ezzel elkerülhető az a zavaró jelenség, amikor a tartalom a kép betöltődésekor hirtelen "ugrik" egyet, ami rontja az olvashatóságot és a felhasználói élményt.

Amikor egy képhez képaláírást szeretnénk fűzni, a szemantikailag helyes megoldás a `<figure>` és `<figcaption>` elemek használata. A `<figure>` elem egy önálló tartalmi egységet (ami lehet kép, kódrészlet, diagram stb.) jelöl, a `<figcaption>` pedig a hozzá tartozó képaláírást tartalmazza. Ez a szerkezet egyértelműen összekapcsolja a képet a leírásával, ami a segítő technológiák és a keresőmotorok számára is hasznos információt nyújt.
```html
<h1>Budapest nevezetességei</h1>

<p>Az Országház a magyar főváros egyik legismertebb jelképe.</p>

<!-- Itt a példa a figure és figcaption használatára -->
<figure>
    <img 
        src="https://placehold.co/400x250/003366/FFFFFF?text=Orsz%C3%A1gh%C3%A1z" 
        alt="Az Országház épülete a Duna partján, esti kivilágításban."
        width="400" 
        height="250">
    
    <figcaption>
        Az Országház a Duna partján. Steindl Imre tervei alapján épült.
    </figcaption>
</figure>

<p>A fenti kép és a hozzá tartozó képaláírás szemantikailag összetartozik a `figure` és `figcaption` elemeknek köszönhetően.</p>
```

## Linkek létrehozása

A **hiperhivatkozások**, vagy röviden linkek, a web alapvető építőkövei; ezek teszik a webet egy valódi, összekapcsolt hálózattá. A linkek lehetővé teszik, hogy dokumentumokat más dokumentumokhoz vagy erőforrásokhoz (képekhez, videókhoz) kapcsoljunk, sőt, akár egy dokumentum egy adott részére ugorjunk. A linkek létrehozásának alapja az `<a>` (anchor) elem, amelynek legfontosabb attribútuma a `href` (Hypertext Reference), ami a cél webcímét (URL) tartalmazza.

```html
<p>
    Ez egy egyszerű mondat, amely tartalmaz egy linket a <a href="https://www.mozilla.org/hu/">Mozilla Kezdőlapra</a>.
</p>
```

Szinte bármilyen webes tartalom átalakítható linkké. Nemcsak egyszerű szövegrészeket, hanem akár komplett **blokk-szintű elemeket** is, mint például egy címsort (`<h1>`) vagy egy képet (`<img>`). Ehhez egyszerűen az adott elemet kell az `<a>` elemen belül elhelyezni. A `title` attribútummal kiegészítő információt adhatunk a linkhez, amely az egérkurzor fölé mozgatásakor egy kis buborékban jelenik meg, de fontos tudni, hogy ez az információ a billentyűzettel vagy érintőképernyővel navigáló felhasználók számára nehezen hozzáférhető.

```html
<a href="https://www.mozilla.org/hu/firefox/">
    <img 
        src="https://placehold.co/200x80/E66000/FFF?text=Firefox+Let%C3%B6lt%C3%A9se" 
        alt="Firefox böngésző letöltése">
</a>
```

A linkek céljának megértéséhez elengedhetetlen az **URL-ek és az útvonalak** ismerete. Az URL (Uniform Resource Locator) egy erőforrás címe a weben. Két fő típust különböztetünk meg: az abszolút URL a cél teljes webcímét tartalmazza (pl. https://www.example.com/oldal.html), és mindig ugyanoda mutat. Ezzel szemben a relatív URL a hivatkozó fájlhoz képest adja meg a cél helyét (pl. rolunk.html vagy kepek/logo.png), ami rövidebb és rugalmasabb, különösen a weboldal fejlesztése és költöztetése során.

```html
<!-- Abszolút URL: Teljes webcímet használ, ami egy külső oldalra mutat. -->
<p>
    Ez egy abszolút link a <a href="https://www.google.com">Google keresőre</a>.
</p>

<!-- Relatív URL: Csak a fájlnevet használja, mert a 'kapcsolat.html'
        ugyanabban a mappában van, mint ez a fájl. -->
<p>
    Ez pedig egy relatív link a <a href="kapcsolat.html">kapcsolati oldalunkra</a>.
</p>
```

Lehetőség van arra is, hogy egy dokumentum konkrét részére, úgynevezett **dokumentumrészletre** (document fragment) hivatkozzunk. Ehhez először a cél elemnek adnunk kell egy egyedi `id` attribútumot (pl. `<h2 id="fejezet2">`). A link `href` attribútumában ezt az azonosítót egy kettőskereszt (`#`) előzi meg (pl. `href="oldal.html#fejezet2"`). Ha ugyanazon az oldalon belüli részre ugranánk, elég csak a `#` és az azonosító használata.

```html
<h1>Hosszú Dokumentum Példa</h1>

<!-- TARTALOMJEGYZÉK: Ezek a linkek az oldal különböző pontjaira mutatnak -->
<nav>
    <h2>Tartalomjegyzék</h2>
    <ul>
        <!-- A href="#fejezet1" az oldal azon elemére ugrik, amelynek id="fejezet1" -->
        <li><a href="#fejezet1">Ugrás az 1. fejezethez</a></li>
        <li><a href="#fejezet2">Ugrás a 2. fejezethez</a></li>
        <li><a href="#fejezet3">Ugrás a 3. fejezethez</a></li>
    </ul>
    <p>
        <em>(Ha egy másik oldalra, pl. 'masik_oldal.html' második fejezetére hivatkoznánk, a link így nézne ki: 
        <code>&lt;a href="masik_oldal.html#fejezet2"&gt;</code>)</em>
    </p>
</nav>

<hr>

<!-- TARTALOM: A címsorok megkapják az egyedi 'id' attribútumot, amire a linkek hivatkoznak -->

<h2 id="fejezet1">1. Fejezet: A Kezdetek</h2>
<p>Ez az első fejezet tartalma. Ahhoz, hogy a link működését lássuk, szükség van elegendő szövegre, ami kitölti a képernyőt és görgetést tesz szükségessé.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam in dui mauris. Vivamus hendrerit arcu sed erat molestie vehicula. Sed auctor neque eu tellus rhoncus ut eleifend nibh porttitor. Ut in nulla enim. Phasellus molestie magna non est bibendum non venenatis nisl tempor. Suspendisse dictum feugiat nisl ut dapibus. Mauris iaculis porttitor posuere. Praesent id metus massa, ut blandit odio. Proin quis tortor orci. Etiam at risus et justo dignissim congue. Donec congue lacinia dui, a porttitor lectus condimentum laoreet. Nunc eu ullamcorper orci. Quisque eget odio ac lectus vestibulum faucibus eget in metus. In pellentesque faucibus vestibulum. Nulla at nulla justo, eget luctus tortor. Nulla facilisi. Duis aliquet egestas purus in blandit.</p>
<p>Curabitur vulputate, ligula lacinia scelerisque tempor, lacus lacus ornare ante, ac egestas est urna sit amet arcu. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Sed molestie augue sit amet leo consequat posuere. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Proin vel ante a orci tempus eleifend ut et magna. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer id quam. Morbi porta, sem quis iaculis ullamcorper, elit erat condimentum orci, vel interdum pid at nulla. Aliquam lorem ante, dapibus in, viverra quis, feugiat a, tellus.</p>

<h2 id="fejezet2">2. Fejezet: A Fejlődés</h2>
<p>Ez a második fejezet. Ha az "Ugrás a 2. fejezethez" linkre kattintottál, a böngészőnek ide kellett görgetnie az oldalt.</p>
<p>Phasellus viverra nulla ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies nisi vel augue. Curabitur ullamcorper ultricies nisi. Nam eget dui. Etiam rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper libero, sit amet adipiscing sem neque sed ipsum. Nam quam nunc, blandit vel, luctus pulvinar, hendrerit id, lorem. Maecenas nec odio et ante tincidunt tempus. Donec vitae sapien ut libero venenatis faucibus. Nullam quis ante. Etiam sit amet orci eget eros faucibus tincidunt. Duis leo. Sed fringilla mauris sit amet nibh. Donec sodales sagittis magna.</p>
<p>Sed consequat, leo eget bibendum sodales, augue velit cursus nunc, quis gravida magna mi a libero. Fusce vulputate eleifend sapien. Vestibulum purus quam, scelerisque ut, mollis sed, nonummy id, metus. Nullam accumsan lorem in dui. Cras ultricies mi eu turpis hendrerit fringilla. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; In ac dui quis mi consectetuer lacinia. Nam pretium turpis et arcu. Duis arcu tortor, suscipit eget, imperdiet nec, imperdiet iaculis, ipsum. Sed aliquam ultrices mauris. Integer ante arcu, accumsan a, consectetuer eget, posuere ut, mauris.</p>

<h2 id="fejezet3">3. Fejezet: A Befejezés</h2>
<p>Ez pedig a harmadik, egyben utolsó fejezet. A dokumentumrészletekre való hivatkozás nagyon hasznos hosszú oldalak, például GY.I.K. (Gyakran Ismételt Kérdések) vagy dokumentációk esetében a könnyebb navigáció érdekében.</p>
<p>Praesent blandit, eros vel aliquam blandit, enim est consectetur purus, ut ullamcorper nunc neque vitae tellus. Integer nec orci. Praesent eu pede. In hac habitasse platea dictumst. Nam sed est. Sed vel ipsum. Proin et est. Vivamus sed justo. Pellentesque ac nulla. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Aliquam bibendum, turpis eu mattis iaculis, ex lorem mollis sem, ut sollicitudin risus orci quis tellus. Cras ut dui. Morbi vitae diam. Nulla quis mi. Duis arcu. Praesent egestas. Curabitur lorem. Mauris et dolor. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</p>
<p>Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; In ac dui quis mi consectetuer lacinia. Nam pretium turpis et arcu. Duis arcu tortor, suscipit eget, imperdiet nec, imperdiet iaculis, ipsum. Sed aliquam ultrices mauris. Integer ante arcu, accumsan a, consectetuer eget, posuere ut, mauris. Praesent adipiscing. Phasellus ullamcorper ipsum rutrum nunc. Nunc nonummy metus. Vestibulum volutpat pretium libero. Cras id dui. Aenean ut eros et nisl sagittis vestibulum. Nullam nulla eros, ultricies sit amet, nonummy id, imperdiet feugiat, pede. Sed lectus. Donec mollis hendrerit risus. Phasellus nec sem in justo pellentesque facilisis. Etiam imperdiet imperdiet orci. Nunc nec neque.</p>
```

>[!NOTE]
>A jó linkek készítésének vannak bevált gyakorlatai. A legfontosabb a **világos és leíró link-szöveg** használata. Kerülni kell az olyan általános kifejezéseket, mint a "Kattints ide!", mert ezek nem informatívak sem a felhasználók, sem a keresőmotorok, sem a képernyőolvasót használók számára. Ehelyett a link szövegének tükröznie kell, hogy hová vezet (pl. "Firefox letöltése"). A link szövege legyen rövid, és ne ismételje meg magát az URL-t.

Amikor nem egy másik HTML oldalra, hanem egy letöltendő erőforrásra (pl. PDF, ZIP) hivatkozunk, érdemes ezt a link szövegében jelezni, és a `download` attribútumot is használni. Ez utóbbi jelzi a böngészőnek, hogy a fájlt töltse le, és akár alapértelmezett fájlnevet is megadhatunk neki. A `target="_blank"` attribútummal pedig elérhetjük, hogy a link egy új böngészőfülön nyíljon meg, ami külső hivatkozások esetén bevett gyakorlat, de használatát érdemes megfontolni a felhasználói élmény szempontjából.

```html
<h1>Erőforrások</h1>

<!-- 1. Példa: Link egy letölthető fájlhoz -->
<p>
    Kattints ide a legfrissebb jelentés letöltéséhez. A `download` attribútum
    biztosítja, hogy a böngésző a letöltést indítsa el, ahelyett, hogy megpróbálná
    megnyitni a fájlt.
</p>
<p>
    <a href="/eleresi/ut/egy/dokumentumhoz.pdf" download="eves_jelentes_2025.pdf">
        Éves jelentés letöltése (PDF, 2.5MB)
    </a>
</p>

<hr>

<!-- 2. Példa: Link, ami új fülön nyílik meg -->
<p>
    Külső hivatkozások esetén gyakran használjuk a `target="_blank"` attribútumot,
    hogy a felhasználó ne hagyja el az oldalunkat.
</p>
<p>
    <a href="https://www.mozilla.org/hu/" target="_blank">
        Látogass el a Mozilla hivatalos oldalára (új fülön nyílik meg)
    </a>
</p>
```

Végül, a linkek nemcsak weboldalakra mutathatnak. A `mailto:` séma segítségével olyan linkeket is létrehozhatunk, amelyekre kattintva a felhasználó alapértelmezett levelezőprogramja nyílik meg egy új üzenettel. A `mailto:` után megadhatjuk a címzett e-mail címét, és további paraméterekkel (pl. `?subject=...&body=...`) előre kitölthetjük a tárgyat vagy a levél törzsét is, ezzel megkönnyítve a felhasználó dolgát.

```html
<p>
    További paramétereket (pl. `body`) az '&' jellel fűzhetünk hozzá.
    Fontos, hogy a szóközöket és speciális karaktereket kódolni kell (pl. a szóköz helyett '%20'-t használunk).
</p>
<p>
    <a href="mailto:ajanlat@peldaoldal.hu?subject=Ajánlatkérés%20egy%20termékre&body=Tisztelt%20Cím!%0A%0AÉrdeklődni%20szeretnék%20a%20következő%20termékük%20iránt:%0A%0A">
        Ajánlatkérés küldése
    </a>
</p>
<p><em>(Megjegyzés: a `%0A` sortörést hoz létre a levél szövegében.)</em></p>
```

Forrás: https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content

A szöveg AI felhasználásával készült.