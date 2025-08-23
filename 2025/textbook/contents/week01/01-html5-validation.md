# Webfejlesztés Alapjai: Websztenderdek és HTML Validáció

## Mit értünk websztenderdek alatt és ki dönt a szabályokról?

A **websztenderdek** együttesen azoknak a technológiáknak és irányelveknek a gyűjteménye, amelyek biztosítják, hogy a weboldalak és webes alkalmazások egységesen, megbízhatóan és mindenki számára hozzáférhetően működjenek, függetlenül attól, hogy milyen böngészőt vagy eszközt használ a látogató.

Képzeld el, mi lenne, ha minden böngésző (Chrome, Firefox, Safari stb.) teljesen másképp értelmezné ugyanazt a HTML kódot. A fejlesztőknek minden egyes böngészőre külön weboldalt kellene készíteniük, ami egy rémálom lenne. Nem is beszélve a különböző eszközökről (PC, konzol, telefon, tablet stb.) A sztenderdek ezt a káoszt hivatottak megelőzni.

**Ki határozza meg a sztenderdeket?**

A websztenderdek fejlesztését és karbantartását nem egyetlen cég vagy kormány irányítja, hanem nemzetközi, független konzorciumok. A két legfontosabb szervezet:

1.  **World Wide Web Consortium (W3C):** A Tim Berners-Lee által alapított szervezet. Hagyományosan a W3C publikálja a HTML, CSS és más webes technológiák "ajánlásait" (Recommendations), amelyek de facto szabványnak minősülnek.
2.  **Web Hypertext Application Technology Working Group (WHATWG):** A nagyobb böngészőgyártók (Apple, Google, Mozilla, Microsoft) által alapított csoport. A WHATWG egy "élő szabvány" (Living Standard) modellt követ, ami azt jelenti, hogy a HTML specifikációját folyamatosan frissítik és fejlesztik a valós piaci igényeknek megfelelően. Ma már a WHATWG HTML Living Standardja számít az elsődleges referenciának.

Röviden: Ezek a szervezetek, a böngészőfejlesztők és a webes közösség közösen alakítják ki azokat a szabályokat, amiket a böngészők követnek a kódok megjelenítésekor.

## Mi az a HTML validáció és miért fontos?

A **HTML validáció** az a folyamat, amelynek során ellenőrizzük, hogy egy weboldal HTML kódja megfelel-e a hivatalos szabványoknak és a szintaktikai szabályoknak. Lényegében egy "helyesírás-ellenőrzés" a kódodra.

**Miért van rá szükség?**

* **Böngészőkompatibilitás:** Bár a modern böngészők nagyon "megbocsátóak" és megpróbálják a hibás kódot is értelmezni, a hibák eltérő megjelenítést eredményezhetnek a különböző böngészőkben. A valid kód biztosítja a konzisztens megjelenést.
* **Keresőoptimalizálás (SEO):** A keresőmotorok (mint a Google) könnyebben értelmezik a strukturált, hibátlan kódot, ami hozzájárulhat a jobb helyezés eléréséhez a találati listákon.
* **Akadálymentesség (Accessibility):** A valid kód alapvető fontosságú ahhoz, hogy a képernyőolvasó szoftverek és más segítő technológiák helyesen tudják értelmezni a weboldal tartalmát, így az mindenki számára elérhetővé válik.

## Hol és hogyan használjunk HTML validátort?

A legelfogadottabb és legszélesebb körben használt eszköz a **W3C hivatalos validátora**.

**Elérhetőség:** [https://validator.w3.org/](https://validator.w3.org/)

A használata rendkívül egyszerű. Három fő módon ellenőrizheted a kódodat:

1.  **Validate by URI:** Megadsz egy publikus weboldal URL-címét, és a validátor letölti és elemzi annak forráskódját.
2.  **Validate by File Upload:** Feltöltesz egy `.html` kiterjesztésű fájlt a saját számítógépedről.
3.  **Validate by Direct Input:** Közvetlenül bemásolod a HTML kódodat a szövegdobozba.

A validátor lefuttatása után egy riportot kapsz, amely pirossal jelöli a hibákat (Errors) és sárgával a figyelmeztetéseket (Warnings). A riport pontosan megmutatja, hogy melyik sorban mi a probléma, és gyakran javaslatot is tesz a javításra.

## Gyakorlati példa

Vegyünk egy egyszerű, de szándékosan hibás HTML kódot.

**Hibás kód:**

```html 
<!DOCTYPE html>
<html>
<head>
    <title>Gyakorló Oldal
</head>
<body>
    <h1>Üdv a weboldalon!
    <p>Ez egy bekezdés, amiben egy <b>kiemelt<i> rész van.</b></i>
    <img src="kep.jpg">
</body>
</html>
```

>[!TASK]
>Keresd meg a hibákat manuálisan a kódban, majd ellenőrizd a kódot a [validátor](https://validator.w3.org/) segítségével. Lehet, hogy egyes hibák kijavítása után a validátor újabbakat talál.