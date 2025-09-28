# Szöveg formázása

Fontos a szöveg formázásáról is külön szót ejteni, hisz a legtöbb információtartalmat a szöveg hordozza. Ez a tudományterület - **tipográfia** - már [Gutenberg](https://en.wikipedia.org/wiki/Johannes_Gutenberg) kora óta fejlődik.

A képernyőn való olvasás gyökeresen eltér a nyomtatott szöveg befogadásától. A szemünk nem folyamatosan halad, hanem ugrásokkal (fixációkkal) pásztázza a tartalmat. A kutatások azt mutatják, hogy egyszerre egy 12-20 karakteres blokkot vagyunk képesek hatékonyan feldolgozni. A jó web-tipográfia célja, hogy segítse ezt a folyamatot, és a szöveget könnyen "szkennelhetővé" tegye. Emiatt részesítjük előnyben a *sans-serif* betűtípusokat, a rövid, tömör mondatokat és a megfelelő sortávolságot.

## Szövegek használata a képernyőn

Kétféle betűforma létezik. Az emberek a **serif** betűformákat klasszikusnak és elegánsnak tartják, ezzel szemben a **sans serif** betűformát modernnek és világosnak ítélik meg. Honlapok esetében célszerű a sans serif formákat előnyben részesíteni, mert a szem könnyebben behatárolja a betűformákat a képernyőn.

Ha egy oldalon túl sok betűtípus található, a megjelenés zavaros lesz. A néző a szerkezet megfejtésével törődik, és nem összpontosít az üzenetre. A szövegelemek megkülönböztetésére használjunk inkább különböző betűméreteket, stílusokat vagy háttereket.

>[!WARNING]
>A csupa nagybetűből álló szöveg kevésbé olvasható, mint a nagy- és kisbetűt keverve használó. A szem nehezebben ismeri fel a szavakat, és a mondatok kezdete sem tűnik ki. A nagybetűs szöveg használatát rövid címekre és kiemelésekre korlátozzuk.
>A **félkövér** betűket is korlátozottan használjuk. Túl sok félkövér szövegrész a szöveget súlyossá teszi és elvész a figyelemfelkeltő jellege.

## Betűtípusok használata (`font-family`)

### 1. Rendszer (biztonságos) betűtípusok
Ezek a legtöbb operációs rendszeren előre telepített betűtípusok (pl. Arial, Helvetica, Times New Roman). Érdemes mindig egy "fallback" listát (betűtípus-családot) megadni. A böngésző az első elérhető típust fogja használni. A lista végén általában egy általános kategóriát adunk meg (pl. `sans-serif`).
```css
p {
  font-family: Helvetica, Arial, sans-serif;
}
```

### 2. Google Fonts és más webszolgáltatások
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

### 3. Saját, egyedi betűtípusok (`@font-face`)
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

## Szövegstílus és méret

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

## Térközök és igazítás

A szöveg olvashatóságát nagyban befolyásolja a sorok, szavak és betűk közötti távolság.

| Tulajdonság | Leírás | Példa értékek |
| :--- | :--- | :--- |
| **`text-align`** | Vízszintes igazítás | `left`, `right`, `center`, `justify` (sorkizárt) |
| **`line-height`**| Sorköz (sortávolság)| `1.5`, `1.6em`, `24px` |
| **`letter-spacing`**| Betűköz | `1px`, `0.1em`, `-0.5px` (negatív is lehet) |
| **`word-spacing`** | Szóköz | `5px`, `0.4em` |
| **`text-indent`** | Első sor behúzása | `20px`, `2em` |