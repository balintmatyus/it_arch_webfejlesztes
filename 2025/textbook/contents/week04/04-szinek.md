# Színek és hátterek

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

>[!NOTE]
>Számos színhez tartozik "név", amellyel közvetlenül is hivatkozhatunk színekre. Egy lista ezekről [itt](https://developer.mozilla.org/en-US/docs/Web/CSS/named-color) található.

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

>[!NOTE]
>Érdemes tájékozódni a trendekről mindig. Trendi színpaletták: [https://coolors.co/palettes/trending](https://coolors.co/palettes/trending)

