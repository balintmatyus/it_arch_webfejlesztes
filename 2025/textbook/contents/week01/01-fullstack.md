# Egy modern webalkalmazás anatómiája

A **full-stack fejlesztő** szerepe messze túlmutat a puszta kódoláson. A full-stack megbízatás nem (csak) azt jelenti, hogy minden egyes létező technológia mesterének kell lenni, hanem sokkal inkább egy olyan építészmérnöki szemléletet követel meg, amely átlátja a teljes rendszert, a kliens böngészőjétől egészen a szerver adatbázisáig. Ez a szerepkör holisztikus rálátást igényel arra, hogyan kommunikálnak és lépnek kölcsönhatásba egy alkalmazás különböző részei.

Egy modern webalkalmazás két alapvető területe különíthető el:
- A **kliensoldal** (frontend): Minden, amit a felhasználó a böngészőjében lát és amivel interakcióba lép. Ez a felhasználói élményért, a megjelenítésért és az azonnali interaktivitásért felel.
- A **szerveroldal** (backend): Az alkalmazást működtető láthatatlan motor. Ez kezeli az alapvető üzleti logikát, az adatkezelést, a biztonságot és a hitelesítést.

## A Frontend Hármassága – Struktúra, Stílus és Viselkedés

A webfejlesztés alapjait három, egymást kiegészítő technológia alkotja. A köztük lévő kapcsolat megértéséhez gyakran használják a „házépítés” analógiáját, amely egy erős mentális modellt biztosít a szerepük megértéséhez.

### Az alaprajz: HTML

A HTML (**HyperText Markup Language**) biztosítja egy weboldal alapvető szerkezetét. Ez a weboldal csontváza vagy váza, amely meghatározza az oldalon található elemeket, mint például a címsorokat, bekezdéseket, listákat, képeket és hivatkozásokat.

A házépítési analógiát követve a HTML dönti el, hogy egy háznak van-e alapja, falai és teteje. Meghatározza, hogy vannak-e benne olyan helyiségek, mint a konyha vagy a hálószoba, és hogy az étkezőben asztalok és székek állnak. A HTML nélkül egyszerűen nincs struktúra, ami a tartalmat befogadná. Ha egy weboldal egy ház, akkor a HTML határozza meg például, hogy hány hálószoba van a házban, és hány asztal és szék kerül az étkezőbe.

### Az esztétika: CSS

A CSS (**Cascading Style Sheets**) a stílus és a megjelenítés nyelve. Ez szabályozza, hogy a HTML által meghatározott szerkezet hogyan jelenik meg vizuálisan a felhasználó számára. A ház analógiájánál maradva, ha a HTML a váz, akkor a CSS a belső és külső dizájn. Ez határozza meg a falak színét, a díszléceket, a nappali méretét, a „welcome” lábtörlő betűtípusát, és hogy a padló szőnyeggel vagy parkettával van-e borítva. A CSS nélkül egy weboldal funkcionális, de sivár és barátságtalan, mint egy csupasz házkeret.

A CSS felelős az elrendezésért (az elemek elhelyezése az oldalon), a térközökért, a színekért, a betűtípusokért és a reszponzív tervezésért, biztosítva, hogy a „ház” minden eszközön jól nézzen ki, a nagy asztali monitortól a kis telefon képernyőjéig.

### A funkcionalitás: JavaScript

A **JavaScript** (JS) az a nyelv, amely életre kelti a weboldalt, irányítva annak dinamikus viselkedését és interaktivitását.

Az analógiánkat teljessé téve a JavaScript a ház funkcionális közműveit képviseli: az elektromos vezetékeket, a vízvezeték-rendszert, a fűtési-hűtési rendszert (HVAC), valamint minden interaktív elemet, mint például az automata ajtókat vagy a villanykapcsolóra felgyulladó lámpákat. A JavaScript kezeli, mi történik, amikor egy felhasználó csinál valamit. Ez a technológia felelős az interaktív elemekért, például a gombokért és űrlapokért, és szabályrendszert használ annak meghatározására, hogy mi történjen a felhasználói interakció hatására.

A JavaScript teszi lehetővé, hogy a felhasználó egy gombra kattintva egy felugró ablakot lásson, egy űrlapot az oldal újratöltése nélkül küldjön el, vagy valós időben frissülő tartalmat figyeljen meg. Lényegében a JavaScript alakítja át a statikus dokumentumot (HTML és CSS) egy teljes értékű, interaktív alkalmazássá.

### A szétválasztás filozófiája: A rend melletti érvek

A **Separation of Concerns** (SoC), vagyis az „aggodalmak szétválasztása” egy tervezési alapelv, amely egy programot különálló részekre bont, ahol minden rész egy-egy külön „aggodalmat” kezel. A klasszikus webfejlesztésben ez azt jelenti, hogy a HTML-t (struktúra), a CSS-t (stílus) és a JS-t (viselkedés) különálló fájlokban tartjuk.

Néhány előny:
- **Karbantarthatóság és érthetőség**: A szétválasztott kód könnyebben olvasható, hibakereshető és frissíthető. Egy logikai hibát javító fejlesztőnek nem kell a stíluskódon átrágnia magát, ami csökkenti a kognitív terhelést. A kód tisztasága és olvashatósága jelentősen javul, ami időt takarít meg a csapatnak, hiszen nem kell napokkal korábban írt, nehezen értelmezhető kódot megfejteniük.
- **Csapatmunka és párhuzamos fejlesztés**: Az SoC lehetővé teszi a specializációt. Egy UI/UX tervező dolgozhat a CSS fájlokon, egy tartalmi stratéga a HTML-en, egy programozó pedig a JavaScripten, mindezt párhuzamosan, anélkül, hogy egymás munkáját zavarnák. Ez a modularitás felgyorsítja a fejlesztést, mivel az egyes modulok izolálása segít felmérni, hogy egy változtatás mely területeket érintheti.
- **Újrahasznosíthatóság és skálázhatóság**: A moduláris kód természeténél fogva újrahasznosíthatóbb. Egy jól definiált CSS stíluslapot egy teljesen más HTML struktúrára is alkalmazni lehet, vagy egy JavaScript funkciót több oldalon is újra lehet használni. Ez a modularitás kulcsfontosságú a nagy, skálázható rendszerek építésében, mivel csökkenti a karbantartási költségeket; egy hiba javítása vagy egy funkció bővítése sokkal kevésbé fájdalmas, ha az csak egy helyen jelenik meg.

> [!NOTE]
> Fenti felbontás elsősorban a klasszikus, statikus weboldalakra igaz. A gyakorlatban azonban legtöbbször a szeparációs határok nem egyértelműek. Ilyen példákat ebben a kurzusban nem vizsgálunk meg, de a képzés során találkozhattok majd ilyen helyzetekkel.

## A láthatatlan gépezet: A szerveroldal alapvető felelősségei

A backend (vagy szerveroldal) a szerverek, alkalmazások és adatbázisok kombinációja, amely a webalkalmazás gerincét alkotja. Ez minden, ami a „színfalak mögött” történik.

Alapvető felelősségei a következők:
- **Üzleti logika**: Az alkalmazás alapvető szabályainak és munkafolyamatainak végrehajtása (pl. egy végösszeg kiszámítása, egy rendelés feldolgozása, felhasználói jogosultságok meghatározása).   
- **Adatbázis-interakció**: Az összes alkalmazásadat tárolása, lekérdezése, frissítése és kezelése (pl. felhasználói profilok, termékkatalógusok, bejegyzések).   
- **Hitelesítés és biztonság**: A felhasználói identitások ellenőrzése, a munkamenetek kezelése, valamint az érzékeny adatok és erőforrások védelme az illetéktelen hozzáféréstől.   
- **API szolgáltatás**: Egy tiszta, stabil interfész (API) biztosítása, amellyel a frontend kommunikálhat.

>[!WARNING]
> **Miért kell ezeket a feladatokat a szerveroldalon kezelni?**
> A kliensoldali kód (HTML, CSS, JS) természeténél fogva a felhasználó gépére kerül letöltésre és ott fut le. Ezért ez a kód alapvetően nem megbízható. Egy rosszindulatú vagy akár csak kíváncsi felhasználó megvizsgálhatja és manipulálhatja a kliensoldali kódot.
> Ezért minden kritikus műveletet, amely biztonságot és adatintegritást igényel – mint például a jogosultságok ellenőrzése, a fizetések feldolgozása vagy az adatbázis-hozzáférés –, a backend szerveren kell végrehajtani, amely egy biztonságos, megbízható környezet, amit az alkalmazás tulajdonosa felügyel. **A backend az igazság végső döntőbírája.**

> [!NOTE]
> A félév során kizárólag a kliens oldallal fogunk foglalkozni. A szerver oldalról későbbi kurzusokon (pl. Software Engineering) lesz szó részletesen.

🌐

Források:
- https://www.bsd.education/html-css-javascript-an-overview/
- https://blog.codeanalogies.com/2018/05/09/the-relationship-between-html-css-and-javascript-explained/
- https://www.newtarget.com/web-insights-blog/separation-of-concerns-in-web-design-and-development/
- https://www.geeksforgeeks.org/software-engineering/separation-of-concerns-soc/
- https://www.upwork.com/resources/beginners-guide-back-end-development

A szöveg AI felhasználásával készült.
