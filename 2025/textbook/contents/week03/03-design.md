# Felhasználói felület tervezése
 
 ## Mi a design?
 
 A honlapszerkesztés és a webdesign némileg átfedésben van egymással, de nem ugyanazt jelentik. A honlapszerkesztés maga a folyamat, a webdesign pedig a végtermékre vonatkozó elvárások gyűjtőfogalma. A honlapszerkesztéshez tartoznak a különböző programozási nyelvek és a grafika ismerete. Ez az a váz, ami végül megteremti az interneten keresztül is elérhető és használható felületet, a honlapot.
 
 A design egy olyan fogalom, amely magába foglalja a következő fogalmakat: esztétikai érzék, egyensúly, egységesség, harmónia, finomság, meglepetés... Szótár szerint jelent tervet, koncepciót, szándékot és mintát is. De ki lehet vele fejezni a készítést, kreálást és a szerkesztést is. Valahogy mégis több jelentést gondolunk a szó mögött. A szótár fordításai mellett valamilyen összhatást is jelent az emberek számára. A nyers jelentésben tehát egyféle előrelátó teremtés ez, ahol folyamatosan szem előtt kell tartani a végcélt. Erre nem úgy kell tekinteni, mind egy szükségtelen dolog, hanem mint a mindennapi munkánk szükséges része.
 
 Egy nagy látogatottságú weboldal jelentős értékkel bír. Miután növeli a cég imidzsét, láthatóvá teszi a céget akár távoli régiókban is, növeli a piacot, gyors és megbízható kommunikációt tesz lehetővé. Nem mellesleg 24 órás reklámhordozó.
 
 ## Honlap készítés előkészületei, menete
 
 Szedjük össze amink van (szöveg, kép, állományok, e-mail címek, linkek), majd tegyük meg a technikai előkészületeket (digitalizálás, szövegek gépelése, fényképezés, filmfelvételek elkészítése). A legfontosabb, hogy a kezdőlapunk minden - direkt- és indirekt kommunikációs szerepet betöltsön, miután a kezdőlapnak van a legfontosabb szerepe. (bemutat, eligazít, vezérel, definiál...)
 
 A következő lépés a tervezés, ami a logikai felépítés megtervezésével kell hogy foglalkozzon. A tervezés után az operatív részben a stílusok kialakítása az első feladat, ez magába foglalja a szövegek stílusainak kialakítását, a grafikák elhelyezésének, aktív elemek képének kialakítását és a színvilág meghatározását. Végül jön maga a programozási feladat, amiben fontos hangsúlyt kell fektetnünk a szerveroldali szolgáltatások kialakítására, reklámokra...
 
 ## CSS alapjai
 
 CSS (Cascading Style Sheets) stílusleíró nyelv. Az első megjelenése 1994-ben volt Hakon Wium Lie ötlete alapján. Ehhez a csoporthoz csatlakozott később a W3C, és a Microsoft is, akik belátták ennek a jelentőségét. A Stílus szerkesztésének természetesen voltak verziói is, ahogy mindennek az informatikában. Azonban a klasszikus verziók helyett manapság már csak különálló modulok (flexbox, grid...) léteznek.
 
 ### Stílusok definiálása
 
 2 fő részből állnak:
 * szelektor (h1)
 * deklaráció (color: red)
 
 A deklaráció is 2 részből áll:
 * tulajdonság (color)
 * érték (red)
 
 Pl.:
 ```css 
h1 {
  color: red;
}
 
 /* vagy */
 
h1 {
  color: red; 
  font-size: 4;
}
 ```
 
 A CSS definiálása többféle módon lehetséges. HTML forráskódon belül
 * `<style>` utasítás segítségével: a HTML sorok között adunk meg minden paramétert.
 * Külső stíluslapok használata: külön fájlban, kiterjesztése: css, nincsenek benne, HTML tagek, csak stílusok
 * in-line, amikor HTML fájlon belül, az egyes HTML elemek tag-jeiben definiáljuk
 
A CSS előnyei közé tartozik, hogy a megjelenés a dokumentum tartalmának és struktúrájának módosítása nélkül is megváltoztatható, valamint egy stíluslap megosztható több HTML dokumentum között is.
 
#### **Stíluslap készítése `<style>` utasítás segítségével**
 
 ```html
 <head>
   <style>
     h1 {font-size:7; color:darkgreen; font:arial}
     h2 {font-size:5; color:red; font:verdana}
     h3 {font-size:4; color: blue; font:courier}
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
 
 A `<style>` utasítás előnyei:
 * A fejrészben (`<head>` blokkban) adjuk meg a használni kívánt stílusokat.
 * Gyorsabb a hibakeresés, mivel egy fájlban található meg a stílus és a dokumentum tartalma.
 
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
 h1 {font-size:7; color:darkgreen; font:arial}
 h2 {font-size:5; color:red; font:verdana}
 h3 {font-size:4; color: blue; font:courier}
 ```
 
 A külső stíiluslap előnyei
 * HTML dokumentum forrásának módosítása nélkül változtathatjuk stílusainkat.
 * A `<link>` utasítás segítségével kapcsoljuk a HTML dokumentumunkhoz a megírt stíluslapot (formazas1.css).
 * Ha módosítani kell vmit, akkor csak a css állományon változtatunk.
 * A HTML kód törzsrésze a lehető legegyszerűbb.
 
#### **Stíluslap készítése style paraméter segítségével, in-line CSS**
 
 ```html
 <body>
   <h1 style="font-size:7; color:darkgreen; font:arial">Repülőgépek</h1>
   <h2 style="font-size:5; color:red; font:verdana">Vitorlázó gépek</h2>
   <h3 style="font-size:4; color:blue; font:courier">R26 Góbé</h3>
 </body>
 ```
 
 A style paraméter előnyei:
 * A HTML kód törzsrészébe kerülnek egyszerűen paraméterként a használni kívánt stílusok. Oda, abba az utasításba, ahol éppen szeretnénk alkalmazni azt.
 * A fejrészben (`<head>` utasítások között!) nem kell változtatni semmit.
 
 Nem igazán szoktuk használni, mert nehéz a hibakeresés.
 
 **Felmerül a kérdés!! Külső vagy belső stíluslap készítése?**
 
 Természetesen mindegy, hogy melyiket alkalmazzuk. Ami megvalósítható külső stíluslappal az megvalósítható belső stíluslappal is! Ha külső stíluslapot készítünk, a HTML kód átláthatóbb marad és könnyebb lesz a hibakeresés.
 
 ## Szöveg formázása
 
 Fontos a szöveg formázásáról is külön szót ejteni, hisz a legtöbb információtartalmat a szöveg hordozza. Ez a tudományterület - tipográfia - már Gutenberg kora óta fejlődik. Azonban a honlapok estében elég speciális tulajdonságokra szoktunk hivatkozni:
 
 * A tartalom állandó- friss vagy időtálló információ.
 * Felépítése többdimenziós mátrix.
 * Fejezetek sajátos logikai kapcsolat alapján állnak össze.
 * Csak a technika határozza meg a megjelenését.
 
 Szöveg befogadása teljesen másként történik a honlapok esetében, mint egy papír alapú tartalom esetében. A szemünk eleve más módon dolgozza fel a bejövő információ tartalmat. Nem egymás utáni betűfeldolgozás van, hanem fixációs tartományokon belül elhelyezkedő információtartalmak feldolgozása. Ez azért van, mert a képernyőn közvetített tartalmakattartományokként értelmezi az agyunk.
 
 Kiindulás: mekkora szöveget képes a szemünk egyszerre átlátni?
 
 $v=\frac{(s-\delta)}{t_{f_{x}}}$ [betű/sec];
 
 ahol $s=az$ egy pillantással átfogott betűk száma, fixációs szélesség; $\delta=$ túlfedés, a kétszeresen fixált szövegrész; $t=a$ fixációs idő;
 
 Ez egy átlag magyar ember esetében 25 betű másodpercekénti feldolgozását jelenti. Mivel nem az egymás utáni betűket rakjuk össze szavakká, hanem a számítógépen a jeleket érzékeljük egy fixációval, és az agyunk ezt a képet kódolja és látja el tartalommal. Ez azt jelenti, hogy átlagosan 12-20 betűből álló szavakat vagyunk képesek egy fixációval az agyunkba juttatni.
 
 ## Szövegek használata a képernyőn
 
 Az olvasási metódus mássága miatt fontos, hogy alapvető szövegelhelyezési szabályokat betartsunk. Minden szabály alapját a fixációs adatfeldolgozás indokolja.
 
 Kétféle betűforma létezi. A betűformák különböző jelzéseket továbbítanak a felhasználóknak. Az emberek a seriff betűformákat klasszikusnak és elegánsnak tartják, ezzel szemben a sans serif betűformát modernnek és világosnak ítélik meg. Azonban a honlapok esetében célszerű a sans seriff formákat előnyben részesíteni, mert a szem könnyebben a fixációs tartományban lehatárolni a betűformákat.
 
 Ha egy képernyő oldalon túl sok betűtípus található, akkor az oldal megjelenése zavaros. A sok betűtípus már csak azért is zavaró, mert a néző az oldal szerkezetének a „megfejtésével" törődik és nem összpontosít az üzenetre. Ha egy oldalon szövegelemeket meg kell különböztetni egymástól, célszerű különböző betűméretekkel és stílusokkal dolgozni vagy különböző háttereket használni.
 
 A mondanivalót egyszerű, világos mondatokba kell sűríteni. A mondatok legyenek a lehető legrövidebbek. Ezt is fentebb említettük, miután a fixációs tartományok nem végtelenek, így megfelelő bit információ egyszeri felvétele és hatékonysága ezáltal biztosítható.
 
 A használandó betűtípusok általában a megjelenítő képernyő méretétől függnek. Nagyobb felbontású képernyőn általában a betűméretek kisebbek. Egy számítógép képernyőjén bemutatott interaktív termék esetében természetes, hogy a néző a képernyő előtt ül. Mivel a képernyők felbontása jó, kisebb méretű betűk is jól olvashatók, azonban gondolnunk kell a mobil eszközökre is.
 
 ### Gyakori hiba
 
 A csupa nagybetűből álló szöveg kevésbé olvasható, mint a nagy- és kisbetűt keverve használó. Csupa nagybetűből álló szövegbe beleolvadnak a nagybetűvel kezdődő szavak. Ilyen szövegben nem tűnik ki a mondatok kezdete., vagyis nem behatárolható a fixációs tartomány. A nagybetűs szöveg használatát rövid címekre és a szövegből kiemelni kívánt dolgokra kell korlátozni.
 
 Ha félkövér betűket korlátozottan használunk, a szöveg áttekinthető, olvasható lesz, ugyanakkor a félkövér szövegrész felhívja magára a figyelmet. Túl sok félkövér szövegrész a szöveget súlyossá teszi és elmarad a figyelemfelkeltő jellege.
 
 ## Szövegek a CSS-el
 
 A betűtipusok megadás a következő módokon lehetséges:
 * Hagyományos megoldás
 * Google webfonts
 * Saját fontkészlet
 
 **Google webfonts:**
 
 Google szerver küldi a fontot, amit egy linken keresztül kérünk le. Ez a link változhat idővel!
 
 **Péda:**
 
 ```html
 <html>
   <head>
     <title>Title</title>
     <link
       href="https://fonts.googleapis.com/css?family=Roboto&display=swap"
       rel="stylesheet">
     <style>h3{font-family: 'Roboto', Helvetica';}</style>
   </head>
   <body>
     <h3>Repülógépek</h3>
   </body>
 </html>
 ```
 
 **Hagyományos megoldás:**
 
 Ilyenkor a HTML kódban mi határozzuk meg a paramétereket.
 * **font-style** - betű stílus
   * értéke lehet: italic (dőlt), normal
 * **font-weight**- betű vastagság
   * értéke lehet: bold (félkövér), normal, 100, 200, 300, 400 (=normal), 500, 600, 700 (bold), 800, 900
 * **font-variant** - betű variáns
   * értéke lehet: normal, small-caps (kiskapitális)
 * **font-size**- betűméret beállítás
   * értéke lehet:
   * abszolút (pt, px)
   * % (hierachikusan felette lévőhöz képest)
   * xx-small, x-small, small, medium, large, x-large, xx-large
   * larger, smaller (viszonyított)
 * **text-decoration** - szöveg "díszítés"
   * none (nincs - link aláhúzását meg lehet szüntetni)
   * underline (aláhúzás - csak indokolt esetben)
   * overline (föléhúzás)
   * line-through (áthúzás)
 * **text-align** - szöveg igazítás vízszintesen
   * értéke lehet: left (alapértelmezett), right, center, justify
 * **line-height** - sorköz
   * px, pt, em
   * pl.: line-height: 1.5em; (másfeles)
 * **word-spacing** - szóköz
   * px, pt, em
 * **letter-spacing** - betűköz
   * px, pt, em
 * **text-indent** - első sor behúzása
   * px, em