# Színek, hátterek és képek

## A színek szerepe

A design nem csak az esztétikai megjelenítés eszköze, hanem fontos gazdasági szerepe is van a cégek esetében. Egyik ilyen az identitás, vagyis a cégek arculatának segítése. Az image az arculat része, ami segíti a vállalatokat a saját vevőkörében a tudatosításban. 

A tudatosítás az arculat formai elemeinek megvalósítása révén következik be. Ennek fontos része például a színek, a logók és egyéb elemek (kép, táblázat..) a honlapon történő megjelenítése. Ezek szintén szabályokhoz köthetőek, melyeknek magyarázata sokféle kutatás eredményeként jött létre.

A színek esetében is meghatározó maga a tradíció, a színek pszichológiai hatása. Mindezek összefüggésben állnak a színek, mint elektromágneses hullámok fizikai tulajdonságaival. Valójában azonban a színeknek komoly fiziológiai és lélektani hatásuk van bennünk, sokszor tudatalatti reakciót váltanak ki, melyek befolyásolják döntéseinket és érzelmeinket. Honlapok esetében jellemzően a hangulati felosztás szerint alkalmazzuk a színeket.

* **Meleg színek**: kiemelnek, felhívják magukra a figyelmet, fellendítik a hangulatot és a védettség érzését keltik. Ide tartozik a **vörös**, ami a legrikítóbb szín, a vér, a láng színe. A **sárgával** együtt, aminek jellemzője a könnyedség és a jókedv, a legélénkebb színeket adják. Ezek mellett ide sorolható a **narancs** is. Fizikai oldalról nézve ezek a nagy hullámhosszúságú színek.
* **Hideg színek**: háttérbe tolnak, eltaszítanak, vagy elrejtenek, mindemellett nyugtatnak, pihentetnek. Ide tartoznak a fejlődést, harmóniát jelentő **zöld** színek egy része, az eget szimbolizáló **kék**, valamint a **lila**. Fizikai oldalról nézve ezek a kis hullámhosszúságú színek.

Összegezve a színek fényhullámokból (elektromágneses energia egy fajtája) jönnek létre. A fényhullámok maguk színtelenek, a színek az agyunkban állnak össze. A fénysugarak elérik a szemlencsét, s a fény a szemlencsén, mint fénytörő közegen keresztül a retinára vetülve alakulnak képpé, színekké. A szemünk a 400-700 nanométer (hullámhossz) közti fényhullámokat képes érzékelni.

A honlapok esetében alapszínekről beszélünk. Ez az **RGB**, amely három alapszín rövidítése. Az alapszínek megadhatók angol nevükkel is, egyébként RGB kóddal.

Példa:
RGB kód - pl.: `#89AF81` (hexadecimális)
* első két jegy piros, majd zöld, és kék
* `00` (nulla) a leggyengébb, `FF` a legerősebb
* `#88AA00` -> `#8A0` (ha mindhárom színkomponens ugyanabból a két karakterből áll)

Az alapszíneket azonban nem használjuk csak önmagukban. Az un. additív (összeadó) színkeverési módot alkalmazzuk, ami révén egyre inkább a fehér szín fele haladhatunk. Egy-egy alapszínnek 256-féle árnyalatot adhatunk. Ábrázolása hexadecimálisan történik ezeknek is, bár itt is használhatunk angol megfelelőket. Pl: purple (`#800080`). Miután a digitális környezetben közel 16,7 millió színárnyalat állítható elő, ezért kell néha a hexadecimális pontosítással dolgozni.

## A háttér szerepe

A háttér a képernyő egyik fontos eleme, amely előkészíti az információt, meghatározza a hangulatot. Fontos, hogy minden honlapkészítés előtt tisztázva legyen, hogy a képernyőnek milyen benyomást, érzést kell közvetíteni.

* Egyszerű ismertető jellegű szövegnél célszerű egyszerű hátterek használata. Ilyenkor érdemes tompa színeket használni.
* Ha lényeges, hogy a termék meghatározott légkört teremtsen, vagy szeretné a látogató figyelmét felhívni, akkor érdemes a háttérnek élénkebb színeket használni.
* Ha lehet a szövegek mögött, egyszínű háttér legyen, hogy az információtartalom minél kisebb veszteség nélkül legyen feldolgozható a látogató számára.

A színeket és ezen belül is a hátteret érdemes a stílusbeállításokkal együtt kezelni.

```css
p {
  color: rgba(255, 0, 0, 0.9);
  background-color: rgba(100, 100, 100, 0.2);
}
```

Az `rgba()` színmegadás lehetővé teszi, hogy a hagyományos RGB színekhez átlátszóságot (alpha csatornát) is rendeljünk. Ez különösen hasznos modern, rétegzett designok készítésénél.

A fenti példában egy majdnem teljesen átlátszatlan (0.9), élénk piros színt adtunk meg.

**A paraméterek jelentése:**

| Paraméter | Szerepe | Értéktartomány |
| :--- | :--- | :--- |
| **1-3. (R, G, B)** | A vörös, zöld és kék színösszetevők aránya. | `0`-tól `255`-ig terjedő egész szám. |
| **4. (Alpha)** | Az átlátszóság (opacitás) mértéke. | `0.0` (teljesen átlátszó) és `1.0` (átlátszatlan) közötti tizedes tört. |

>[!NOTE]
>Létezik egy `opacity` tulajdonság is a CSS-ben. Az `opacity` az egész elemet és tartalmát teszi átláthatóvá, míg az `rgba()` csak az adott színt.

```css
div {
  background-color: steelblue;
  opacity: 0.5;
}

/* vs */

div {
  background-color: rgba(70, 130, 180, 0.5);
}
```

Érdemes tájékozódni a trendekről mindig. Trendi színpaletták:
[https://coolors.co/palettes/trending](https://coolors.co/palettes/trending)

Mielőtt rátérnénk részletesen a leghatékonyabb, összefoglaló `background` parancsra, nézzük át röviden, milyen egyedi tulajdonságokból épül fel a háttér stílusozása. Ezeket ritkán használjuk külön-külön, de fontos ismerni a szerepüket.

| Tulajdonság | Szerepe | Leggyakoribb értékek |
| :--- | :--- | :--- |
| **`background-color`** | Háttérszín beállítása (pl. ha a kép nem tölt be). | `#333`, `rgba(0,0,0,0.5)` |
| **`background-image`** | Háttérkép megadása az `url()` függvénnyel. | `url("hero.jpg")` |
| **`background-repeat`** | A kép ismétlődésének szabályozása. | `no-repeat`, `repeat` |
| **`background-position`** | A kép igazítása az elemen belül. | `center`, `top right` |
| **`background-size`** | A kép méretezése (pl. a terület kitöltésére). | `cover`, `contain` |
| **`background-attachment`**| A kép görgetésének viselkedése. | `fixed`, `scroll` |

Ezeket az egyedi tulajdonságokat kombinálja a sokkal gyakrabban használt, összefoglaló `background` parancs. (Lásd lentebb.)

**Gyakorlati példa:**
Tegyük fel, hogy egy weboldal fejlécének szeretnénk egy háttérképet beállítani, ami nem ismétlődik, középre van igazítva, teljesen kitölti a rendelkezésre álló helyet, és görgetéskor a helyén marad.

```css
.hero-header {
  /* Hosszú, részletes módszer */
  background-color: #333; /* Sötét háttér, ha a kép nem tölt be */
  background-image: url("kep3.jpg");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  background-attachment: fixed;

  /* Ugyanaz a hatás az összefoglaló, profi módszerrel */
  background: #333 url("kep3.jpg") no-repeat fixed center/cover;
}
```

## Képek stílusbeállításai

A kép elhelyezése és vizuális stílusa (színvilág, kontraszt) tudatos tervezési döntés, amely a tartalom elrendezésének szerves része. A modern CSS eszközökkel a kép és a szöveg viszonya precízen szabályozható: a képet elhelyezhetjük a szövegblokkok között, mellettük, vagy akár szöveggel körbe is futtathatjuk a dinamikus és olvasóbarát elrendezés érdekében. A cél, hogy a vizuális elemek támogassák és tagolják a tartalmat, ne pedig elszigetelten álljanak mellette.

* **Ha a kép a fókuszpont, ami bemutatja a témát,** akkor érdemes a bal oldalra helyezni, mert az olvasó tekintete itt kezdi a pásztázást. A kép felkelti az érdeklődést, a mellette lévő szöveg pedig kifejti a részleteket. Ideális például egy cikk bevezetőjéhez vagy egy portfólió elem bemutatásához.

* **Ha a kép kiegészítő információt hordoz, illusztrál vagy lezár egy gondolatot,** akkor hatékony lehet a jobb oldalon elhelyezni. Miután a felhasználó már elkezdte olvasni a szöveget, a kép vizuális megerősítést, példát vagy egy kapcsolódó mellékinformációt nyújt anélkül, hogy megszakítaná az olvasás kezdeti lendületét.

A kép a honlapon leginkább a törzsben használatos. Ez az `<img>` tag segítségével lehetséges, ahol a kép forrását az `src` attribútummal kell megadni.
* `src="kep.gif"`: ugyanazon könyvtárban van
* `src="images/kep.gif"`: "eggyel lejjebb" van, az images könyvtárban
* `src="../../images/kep.gif"`: A kép és a html lap párhuzamos ágakon van, a kép 1, míg a html lap 2 szinttel lejjebb

>[!NOTE]
>Korábban említettük az `alt` attribútumot, amelynek az akadálymentesítésben van nagy szerepe. Pl. képernyőfelolvasó szoftver az `alt` értékét olvassa fel, de ez a szöveg jelenik meg, ha valamilyen okból kifolyólag nem sikerül a böngészőnek a képet betöltenie. Ha a kép csak díszítőelem, akkor üres érték adandó meg.

Figyelnünk kell azonban arra is, hogy a képek ne legyenek nagy méretűek. Sokszor fordul elő, ha a kép sokáig tölt be, akkor a látogató inkább elhagyja az oldalt. Ezért inkább tömörített képeket használjunk. A weben leginkább használható képfájl típusok: **gif, jpg, png, webp**.

**A képek beállításához használt paraméterek:**
* **border**: keret: vastagság típus szín
    * `border: 1px solid black;`
* **width**: px, pt
* **height**: px, pt

Ha a képeket más méretben szeretnénk használni, mint az eredeti mérete, akkor érdemes azt előtte egy képszerkesztő programmal átméretezni. A honlapon a méret megváltoztatásával nem csak az arányok változnak.

A weboldal elemeit, például a képeket vagy gombokat, **interaktívvá** és **dinamikussá** tehetjük CSS átmenetek (transitions) segítségével. Ezek a finom animációk, vagy mikrointerakciók, vizuális visszajelzést adnak a felhasználónak, amikor interakcióba lép egy elemmel (pl. ráviszi az egeret).

**Példa**: A kép 0.4 másodperc alatt nőjön meg 10%-kal és forduljon el 5 fokkal.

```css
/* Az alapállapotban megadjuk, hogy a 'transform' tulajdonság 
   változása 0.4 másodpercig tartson. */
img {
  transition: transform 0.4s ease-out;
}

/* A :hover állapotra megadjuk a cél animációt: 
   10%-os nagyítást és 5 fokos elforgatást. */
img:hover {
  transform: scale(1.1) rotate(-5deg);
}
```

>[!WARNING]
>A fenti példa érintőképernyőn nem működik. Mobilon az animáció vagy el sem indul, vagy egy érintés után „úgy marad”. Ezért ez a technika csak asztali gépekre ajánlott.

