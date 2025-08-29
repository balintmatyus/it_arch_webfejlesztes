# Bevezetés a JavaScriptbe

## Mi a JavaScript és mire használható?

A JavaScript egy programozási nyelv, amelynek alapvető célja a weboldalak funkcionalitásának biztosítása és a felhasználói élmény gazdagítása. Míg a HTML a tartalom szerkezetét, a CSS pedig a vizuális megjelenését határozza meg, a JavaScript adja hozzá az interaktivitást és a dinamizmust. 1997-ben vált szabvánnyá, hivatalos neve **EcmaScript**. A JavaScript ennek a szabványnak az egyik implementációja.

Tim O'Reilly szavaival élve: 
> „Learning javascript used to mean you weren't a "serious software developer". Today, not learning javascript means the same thing.”

Vizsgáljuk meg a legfontosabb területeit.

### A böngészőben: Dinamikus és reszponzív weboldalak

A JavaScript teszi lehetővé, hogy egy weboldal ne csak egy statikus dokumentum, hanem egy intelligens, a felhasználói műveletekre azonnal reagáló alkalmazás legyen.

* **Valós idejű interakciók:** Kezeli a gombokra, menükre és más elemekre adott felhasználói kattintásokat. Lehetővé teszi az elegáns animációkat, felugró ablakokat és képnézegetőket anélkül, hogy az oldal minden alkalommal újratöltődne.
* **Azonnali űrlap-ellenőrzés:** Még az adatok elküldése előtt képes jelezni a felhasználónak, ha egy mezőt hibásan töltött ki (pl. érvénytelen e-mail formátum), ezzel időt spórolva és csökkentve a hibalehetőségeket.
* **Dinamikus tartalomkezelés:** Képes a weboldal bármely részét frissíteni anélkül, hogy a teljes oldal újratöltődne. Ez a technológia áll a modern hírfolyamok, a végtelen görgetés, az interaktív térképek és a keresési javaslatok mögött.

### A böngészőn túl: Univerzális fejlesztői platform

A **Node.js** futtatókörnyezet révén a JavaScript kilépett a böngészők keretei közül, és egy rendkívül sokoldalú, platformfüggetlen eszközzé vált.

* **Szerveroldali fejlesztés (Back-end):** Komplett, nagy teljesítményű webszerverek és API-k (alkalmazásprogramozási felületek) építhetők rá, amelyek az alkalmazások háttérlogikáját és adatbázis-műveleteit kezelik.
* **Mobilalkalmazások:** Olyan keretrendszerekkel, mint a **React Native**, a JavaScript-tudás felhasználható natív iOS és Android alkalmazások fejlesztésére, gyakran egyetlen közös kódbázisból.
* **Asztali szoftverek:** Számos ismert asztali alkalmazás (pl. **Visual Studio Code, Slack, Figma**) alapját az **Electron** keretrendszer adja, amely JavaScript, HTML és CSS technológiákra épül.

## A JavaScript elhelyezése és a helyes betöltési stratégia

Ahhoz, hogy a JavaScript kódunk életre kelthesse a weboldalt, a böngészőnek be kell töltenie és végre kell hajtania. A böngésző a HTML dokumentumot fentről lefelé haladva dolgozza fel, mint egy könyvet. **Ha egy `<script>` taggel találkozik, megáll, letölti és futtatja a kódot**, és csak utána olvassa tovább a HTML-t.

> [!QUESTION]
> Gondolj bele: mi történne, ha a színdarab rendezője (a JavaScript) már a díszlet felépítése (a HTML betöltődése) előtt elkezdené mozgatni a nem létező színészeket és tárgyakat a színpadon?

### A klasszikus módszer: Szkript a `<body>` végén

Ez a legegyszerűbb hagyományos megoldás. A `<script>` taget közvetlenül a záró `</body>` elem elé helyezzük. Mire a böngésző eléri a szkriptet, már a teljes HTML dokumentumot feldolgozta. Így a JavaScript garantáltan hozzáfér minden elemhez, például egy gombhoz vagy egy képhez.

**Példa:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Oldal címe</title>
</head>
<body>

    <h1 id="main-title">Helló Világ!</h1>
    <button id="color-changer">Válts színt!</button>

    <script src="app.js"></script> 
</body>
</html>
```

### A modern és javasolt módszer: `defer`

Ez a mai webfejlesztés de facto szabványa. A szkripteket a `<head>` szekcióban helyezzük el, ami logikailag is a helyes helyszín a "hozzávalók" listázására.

**A `defer` attribútum** azt mondja a böngészőnek: *"Kezdd el letölteni ezt a szkriptet a háttérben, de ne futtasd, amíg a teljes HTML oldalt fel nem dolgoztad."* A `defer`-rel ellátott szkriptek ráadásul megőrzik a sorrendjüket, ami fontos, ha az egyik a másikra épül (pl. előbb egy könyvtár, aztán a mi kódunk).

**Példa:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Modern oldal</title>
    <script src="photo-gallery-library.js" defer></script>
    <script src="main-logic.js" defer></script> 
</head>
<body>
    </body>
</html>
```

### Speciális esetekre: Az `async` attribútum

Az `async` (aszinkron) betöltés akkor hasznos, ha a szkript teljesen független a weboldal tartalmától, és a futási sorrendje sem számít.

* **Hogyan működik?** Az `async` azt jelenti: *"Töltsd le ezt a szkriptet a háttérben, és amint végeztél, azonnal futtasd, ne törődj semmivel!"* Ez megakaszthatja a HTML feldolgozását egy pillanatra, és a szkriptek semmilyen sorrendet nem tartanak.
* **Mikor használd?** Tipikusan külső, harmadik féltől származó szkriptekhez ideális, amelyek nem módosítják közvetlenül az oldalad elemeit.
    * **Példák:** Google Analytics mérőkódok, hirdetési szkriptek, külső chat-widgetek.

**Példa:**
```html
<head>
    <title>Oldal analitikával</title>
    <script src="app.js" defer></script> 
    <script src="https://www.google-analytics.com/analytics.js" async></script>
</head>
```

## Megjegyzések a kódban

A kódban elhelyezhetünk a program futását nem befolyásoló megjegyzéseket. Ezek célja az **olvashatóság javítása**, hogy segítséget nyújtson más (és a saját magunknak a jövőben) fejlesztőknek megérteni a kód működését, jelezheti egy kódrészlet eredetét **forrás megjelölésekor**, valamint **teszteléskor** ideiglenesen kikapcsolhatunk kódrészleteket tesztelés céljából.

Kétféle megjegyzés létezik:
*   **Egysoros megjegyzés**: **`//`** (két perjel után).
*   **Többsoros megjegyzés**: **`/* ... */`** (perjel és csillag között).

```javascript
/*
  Ez egy többsoros megjegyzés.
  A böngésző az ilyen blokkokat teljesen figyelmen kívül hagyja.
  Célja, hogy hosszabb magyarázatot fűzzünk a kódhoz.
*/

// Ez egy egysoros megjegyzés. Csak az adott sor végéig tart.
// A következő sor egy felugró ablakot fog mutatni a böngészőben.
alert('Helló Világ!');

// A megjegyzésekkel ideiglenesen ki is kapcsolhatunk kódot.
// Az alábbi sor nem fog lefutni, mert megjegyzés lett belőle:
// alert('Ez az üzenet nem fog megjelenni.');
```
## Változók és adattípusok

### Változók

A programozás során rengeteg információval dolgozunk: számokkal, szövegekkel, logikai értékekkel és bonyolultabb adatszerkezetekkel. Ahhoz, hogy ezeket az értékeket tárolni tudjuk, hivatkozni tudjunk rájuk, és szükség esetén módosítani is tudjuk, változókra van szükségünk. Egy **változó** lényegében egy elnevezett "konténer" vagy "doboz", amiben értékeket tárolhatunk.

#### Változók deklarálása: `let`, `const`, `var`

A JavaScriptben többféle módon is deklarálhatunk, vagyis létrehozhatunk változókat. A modern JavaScriptben két fő kulcsszóval dolgozunk: a `let` és a `const`. Régebben a `var` kulcsszót használtuk erre a célra, de erről mindjárt kiderül, miért érdemes elkerülni.

*   **`let`**: Ezt a kulcsszót akkor használjuk, ha egy olyan változót akarunk létrehozni, aminek az értékét **később megváltoztathatjuk** a program futása során.
    ```javascript
    let nev = "Anna"; // Deklarálás és inicializálás
    nev = "Béla";   // Érték újraadása lehetséges
    ```
    Ha egy `let`-tel deklarált változónak nem adunk kezdeti értéket, akkor az `undefined` típusú lesz.

*   **`const`**: Ez a "konstans" rövidítése, és olyan változókhoz használjuk, amelyeknek az értékét deklarálás után **nem akarjuk módosítani**. Gondolj rá úgy, mint egy egyszer beállítható dobozra.
    ```javascript
    const PI = 3.14159; // Deklarálás és inicializálás kötelező
    // PI = 3.14; // Hiba lenne: nem módosítható a const érték
    ```
    Fontos, hogy `const` esetén a deklarációkor **azonnal értéket kell adnunk** a változónak, különben hibát kapunk.

*   **`var`**: Ez a régi módszer változók deklarálására. **Kerüld el,** mivel számos hibalehetőséget rejt használata!

#### Névadási szabályok

A JavaScript változónevekben angol betűket, számokat és aláhúzásjelet (`_`) használhatsz, de a névnek mindenképpen **betűvel vagy aláhúzással kell kezdődnie**, számmal soha.

Fontos megjegyezni, hogy a JavaScript **megkülönbözteti a kis- és nagybetűket** (case sensitive), így a `felhasznalo`, `Felhasznalo` és `FELHASZNALO` három különböző változót jelöl. A nevek nem tartalmazhatnak szóközt, és kerülni kell a nyelv számára **foglalt kulcsszavak** (pl. `let`, `for`) használatát.

A tiszta és érthető kód írásához **ajánlott beszédes neveket** adni, amelyek utalnak a változó szerepére. Több szóból álló nevek esetén a **"lower camel case"** írásmód a bevett gyakorlat, ahol az első szó kisbetűvel kezdődik, a továbbiak pedig nagybetűvel (pl. `felhasznaloNev`, `termekAr`).

#### Hatókör (Scope)
A hatókör azt határozza meg, hogy egy változó **honnan érhető el** a programban. Ez egy nagyon fontos koncepció, ami segít elkerülni a névütközéseket és rendszerezettebben tartani a kódot.

*   **Blokkszintű hatókör (`let`, `const`)**: A `let` és `const` kulcsszavakkal deklarált változók csak abban a kódblokkban (`{}`) és az azon belüli beágyazott blokkokban érhetők el, ahol definiálták őket.
    ```javascript
    function peldaFuggveny() {
        let lokalisValtozo = 10;
        if (true) {
            const blokkValtozo = 20;
            console.log(lokalisValtozo); // Elérhető
            console.log(blokkValtozo);  // Elérhető
        }
        // console.log(blokkValtozo); // Hiba: blokkon kívül nem elérhető
    }
    // console.log(lokalisValtozo); // Hiba: függvényen kívül nem elérhető
    ```

*   **Globális hatókör**: Azok a változók, amelyeket a program legfelső szintjén, minden függvényen és blokkon kívül deklarálunk. Ezek a változók a program bármely pontjáról elérhetők.
    ```javascript
    const globalisValtozo = "Hello világ!";

    function mutasdGlobalist() {
        console.log(globalisValtozo); // Elérhető
    }
    mutasdGlobalist();
    console.log(globalisValtozo); // Elérhető
    ```

### Adattípusok: Milyen értékeket tárolhatunk?

A JavaScript egy **dinamikusan típusos nyelv**. Ez azt jelenti, hogy nem kell előre megmondanunk egy változónak, milyen típusú adatot fog tárolni (mint például C#-ban vagy Javában). A változó típusa az **értékadáskor** dől el, és akár a program futása során is megváltozhat.

Nézzük meg a leggyakoribb adattípusokat:

*   **`string` (szöveg)**: Karakterláncok, azaz szöveges adatok tárolására szolgál. A szöveget mindig **idézőjelek közé** kell tenni. Használhatunk egyszeres ( `''` ), kétszeres ( `""` ) idézőjeleket, vagy a modernebb **backtick** ( `` ` `` ) karaktert, ami a *template literal* nevet is viseli.
    ```javascript
    let nev = "Kovács Béla";
    let uzenet = 'Szia, hogy vagy?';
    let termek = `Laptop`; // Template literal
    ```
    A template literal különlegessége, hogy könnyen beágyazhatunk bele változókat és JavaScript kifejezéseket a `${}` szintaxissal, és több soros szöveget is egyszerűen kezel.
    ```javascript
    const felhasznalo = "Dani";
    console.log(`Üdv, ${felhasznalo}!`); // "Üdv, Dani!"
    ```

*   **`number` (szám)**: Egész számok (pl. 42) és lebegőpontos számok (pl. 3.14) tárolására szolgál. A JavaScriptben nincs külön típus az egész és tört számokra, mindkettő `number` típusú. Számok esetén **nem használunk idézőjeleket**.
    ```javascript
    let kor = 30;
    let ar = 1299.99;
    ```
>[!NOTE]
>Ha egy számot idézőjelek közé teszünk, az **string** típusúvá válik! (`"500"` az egy szöveg, nem szám). Ha számolni akarunk vele, előbb konvertálni kell.

*   **`boolean` (logikai)**: Két lehetséges értékkel rendelkezik: `true` (igaz) vagy `false` (hamis). Leginkább feltételek kiértékelésére használjuk.
    ```javascript
    let vanInternet = true;
    let bejelentkezve = false;
    ```

*   **`undefined` (nem definiált)**: Ez az adattípus azt jelzi, hogy egy változó létezik, de még **nem kapott értéket**.
    ```javascript
    let elsoValtozo;
    console.log(elsoValtozo); // undefined
    ```

Ezen kívül léteznek még más primitív típusok is, mint például a `bigint`, `symbol` és `null`, de ezekkel most nem foglalkozunk részletesebben. Az `object` (objektum) és `array` (tömb) típusokkal később foglalkozunk.

### A `typeof` operátor

Ha kíváncsi vagy egy változó aktuális adattípusára, a **`typeof` operátort** használhatod. Ez különösen hasznos hibakereséskor vagy amikor típusellenőrzést szeretnél végezni.

```javascript
let szam = 100;
console.log(typeof szam); // "number"

let szoveg = "Száz";
console.log(typeof szoveg); // "string"

let igazhamis = true;
console.log(typeof igazhamis); // "boolean"

let nemDefinialt;
console.log(typeof nemDefinialt); // "undefined"
```
Ezzel az operátorral könnyedén ellenőrizheted például, hogy egy felhasználótól kapott bemenet valóban szám-e, mielőtt matematikai műveleteket végeznél rajta.

## Operátorok

A JavaScriptben az **operátorok** olyan speciális szimbólumok, amelyek valamilyen műveletet végeznek el egy vagy több értéken (ezeket hívjuk operandusoknak). Gondolj rájuk úgy, mint a programozás "igéire" – ők teszik lehetővé, hogy a programunk csináljon is valamit az adatokkal.

### Értékadó operátorok

Az értékadó operátorok a leggyakrabban használt operátorok közé tartoznak, hiszen ők felelnek azért, hogy értékeket adjunk a változóinknak.

*   **`=` (egyenlőségjel)**: Ez a legegyszerűbb és leggyakoribb értékadó operátor. A jobb oldali kifejezés értékét adja a bal oldali változónak. Fontos: **ne keverd össze az összehasonlító `==` vagy `===` operátorokkal!**.

    ```javascript
    let szam = 10; // A 'szam' változó értéke 10 lesz
    let masikSzam = szam; // A 'masikSzam' értéke is 10 lesz
    ```

### Aritmetikai operátorok

Az aritmetikai operátorokkal matematikai számításokat végezhetünk.

*   A **négy alapműveletről** nem írunk részletesen.
    ```javascript
    let osszeg = 5 + 3; // 8
    let kulonbseg = 10 - 4; // 6
    let szorzat = 2 * 7; // 14
    let hanyados = 15 / 3; // 5
    ```
*   **`%` (maradékos osztás, modulo)**: Visszaadja az osztás maradékát. Ez nagyon hasznos lehet például annak ellenőrzésére, hogy egy szám páros-e (ha 2-vel való osztás maradéka 0).
    ```javascript
    let maradek = 10 % 3; // 1 (mert 10 / 3 = 3, maradék 1)
    let parosE = 8 % 2; // 0 (páros)
    ```
*   **`**` (hatványozás)**: Egy számot a megadott hatványra emel.
    ```javascript
    let hatvany = 2 ** 3; // 8 (mert 2 * 2 * 2)
    let pitagorasz = (3**2 + 4**2)**0.5; // 5 (gyökvonáshoz is használható, a 0.5-ik hatvány a négyzetgyök)
    ```

Sokszor fogsz találkozni speciális **rövidített értékadó operátorokkal** is, amelyekkel egyszerre végezhetünk aritmetikai műveletet és értékadást. Ez szép és hatékony kódot eredményez.

*   **`+=` (összeadás és értékadás)**: Hozzáadja a jobb oldali értéket a bal oldali változóhoz, majd az eredményt visszaírja a változóba.
    ```javascript
    let x = 5;
    x += 3; // Ugyanaz, mint x = x + 3; x értéke most 8
    ```
*   Ugyanez ismétlődik **a többi aritmetikai operátor** esetén.
    ```javascript
    let y = 10;
    y -= 4; // Ugyanaz, mint y = y - 4; y értéke most 6
    
    let z = 2;
    z *= 6; // Ugyanaz, mint z = z * 6; z értéke most 12
    
    let a = 20;
    a /= 4; // Ugyanaz, mint a = a / 4; a értéke most 5
    ```

### Inkrementáló és dekrementáló operátorok

Gyakran előfordul, hogy egy változó értékét pontosan eggyel szeretnénk növelni vagy csökkenteni. Erre valók az inkrementáló és dekrementáló operátorok.

*   **`++` (inkrementálás)**: Eggyel növeli a változó értékét.
*   **`--` (dekrementálás)**: Eggyel csökkenti a változó értékét.
    
```javascript
let szamlalo = 0;
szamlalo++; // szamlalo értéke most 1

let visszaszamlalo = 10;
visszaszamlalo--; // visszaszamlalo értéke most 9
```

>[!WARNING]
> Az `++` és `--` operátoroknak van egy "pre" és "post" formája, attól függően, hogy az operátor a változó előtt vagy után áll. Ha a változó *után* van (pl. `szamlalo++`), akkor az értékadás vagy kifejezés során először a változó **eredeti értékét** használja fel, majd *utána* növeli az értékét. Ha a változó *előtt* van (pl. `++szamlalo`), akkor először **növeli** az értékét, majd az *új* értéket használja fel. Kezdetben ez furcsának tűnhet, de a későbbiekben ciklusoknál vagy bonyolultabb kifejezéseknél látni fogod a jelentőségét!

### Logikai és összehasonlító operátorok

Ezek az operátorok segítenek nekünk feltételeket vizsgálni, és eldönteni, hogy egy kifejezés **`true` (igaz)** vagy **`false` (hamis)**-e, azaz logikai (boolean) értéket adnak vissza. Ez kulcsfontosságú a programvezérlésben, hiszen ezen alapulnak az elágazások és ciklusok.

#### Összehasonlító operátorok:

*   **`==` (egyenlő értékre)**: Azt ellenőrzi, hogy két érték megegyezik-e. **Nem veszi figyelembe a típust!**. (Pl. `5 == "5"` -> `true`).
*   **`! =` (nem egyenlő értékre, szóköz nélkül)**: Azt ellenőrzi, hogy két érték nem egyenlő-e. Szintén **nem veszi figyelembe a típust!**.
*   **`===` (szigorúan egyenlő)**: Azt ellenőrzi, hogy két érték **és a típusuk is** megegyezik-e. Ezt javasolt használni, mert kevesebb hibát okoz. (Pl. `5 === "5"` -> `false`, mert a típus eltér).
*   **`! ==` (szigorúan nem egyenlő, szóköz nélkül)**: Azt ellenőrzi, hogy két érték vagy a típusuk **nem** egyezik meg. Ezt is javasolt használni.
*   **`<` (kisebb mint)**: Azt ellenőrzi, hogy a bal oldali érték kisebb-e, mint a jobb oldali.
*   **`>` (nagyobb mint)**: Azt ellenőrzi, hogy a bal oldali érték nagyobb-e, mint a jobb oldali.
*   **`< =` (kisebb vagy egyenlő, szóköz nélkül)**: Azt ellenőrzi, hogy a bal oldali érték kisebb vagy egyenlő-e a jobb oldalival.
*   **`> =` (nagyobb vagy egyenlő, szóköz nélkül)**: Azt ellenőrzi, hogy a bal oldali érték nagyobb vagy egyenlő-e a jobb oldalival.

#### Logikai operátorok:

*   **`&&` (ÉS)**: Akkor ad vissza `true`-t, ha **mindkét** operandus `true`.
*   **`||` (VAGY)**: Akkor ad vissza `true`-t, ha **legalább az egyik** operandus `true`.
*   **`!` (NEM)**: Megfordítja egy logikai érték igazságát. `true`-ból `false`-t, `false`-ból `true`-t csinál.
    
    ```javascript
    let kor = 20;
    let jogositvany = true;
    let nagykoruEsJogsi = (kor >= 18 && jogositvany === true); // true

    let eso = true;
    let szel = false;
    let rosszIdo = (eso || szel); // true

    let vanPenz = false;
    let nincsPenz = !vanPenz; // nincsPenz értéke true lesz
    ```

### Operátorok precedenciája

Mint a matematikában, a JavaScript operátoroknak is van egy **precedencia sorrendjük**, ami meghatározza, milyen sorrendben értékelődnek ki egy komplex kifejezésben. Például a szorzás és az osztás mindig előbb hajtódik végre, mint az összeadás és a kivonás.

```javascript
let eredmeny = 5 + 10 * 3; // 10 * 3 = 30, majd 5 + 30 = 35.
                            // Nem (5 + 10) * 3 = 45!
```

Ha felül akarod írni a precedencia sorrendet, akkor **zárójeleket `()` kell használnod**. A zárójelben lévő kifejezések mindig először értékelődnek ki.

```javascript
let eredmeny2 = (5 + 10) * 3; // (5 + 10) = 15, majd 15 * 3 = 45
```

### Szöveg összefűzés

A `+` operátor nemcsak számokat tud összeadni, hanem **szövegeket is összefűz** (más néven *konkatenál*). Ha egy számot és egy szöveget akarsz összefűzni, a JavaScript automatikusan szöveggé alakítja a számot, és utána fűzi össze a két stringet.

```javascript
let nev = "Anna";
let koszones = "Szia " + nev + "!"; // "Szia Anna!"

let elsoSzam = 10;
let masodikSzam = "5";
let osszefuzott = elsoSzam + masodikSzam; // "105" (szöveg lesz!)
```
Ha a `+` operátort számokkal és szöveggel is használod egy sorban, és az eredményt egy figyelmeztető ablakban (`alert()`) akarod kiírni, akkor **csak a `+` operátor** fog működni az összefűzésre.

A modern JavaScriptben az **`összefűzés` (template literal)** sokkal elegánsabb és olvashatóbb megoldásokat kínál a backtick (`` ` ``) karakterekkel. Itt a `${változó}` szintaxissal könnyedén beágyazhatsz változókat és kifejezéseket a szövegbe.

```javascript
let nev = "Péter";
let kor = 25;
let uzenet = `Szia, ${nev}! ${kor} éves vagy.`; // "Szia, Péter! 25 éves vagy."
```

Ez sokkal szebb, mint a sok `+` jel! Ha teheted, inkább a template literaöket használd szöveg összefűzésére.

