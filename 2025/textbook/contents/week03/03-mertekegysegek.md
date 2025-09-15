# Mértékegységek a CSS-ben: px, rem, em, % és a többiek

A CSS-ben a méretek megadásakor (legyen az betűméret, elem szélessége vagy térköz) elengedhetetlen a mértékegység használata. Ezeket két fő csoportba sorolhatjuk: **abszolút** és **relatív** mértékegységekre.

## 1. Abszolút mértékegységek

Ezek a mértékegységek fix, állandó méretet jelölnek, nem függnek sem a képernyő méretétől, sem más elemek tulajdonságaitól. Főként olyan esetekben hasznosak, ahol a kimenet fizikai mérete ismert, például nyomtatásnál.

* `px` (pixel): A leggyakrabban használt abszolút egység webdesignban. Egy képpontot jelöl a képernyőn. Bár technikailag a képernyő felbontásától függ, a gyakorlatban egy kis, fix egységként tekintünk rá. **Jó választás lehet `border` (szegély) vastagságának vagy más, pixelpontosan megadandó értéknek.**
* `pt` (point, pont): Nyomdai mértékegység. 1 pt = 1/72 inch. Webes felületen ritkán használjuk.

## 2. Relatív mértékegységek

Ezek a mértékegységek valami máshoz viszonyítanak, ami rendkívül hasznossá teszi őket a **reszponzív (responsive) webdesign** során. Méretük a környezetük változásával (pl. böngészőablak átméretezése) együtt változik.

* **`em`**: Az elem **szülőjének `font-size` (betűméret)** értékéhez viszonyít.
    * Ha egy `div` elem betűmérete `16px`, akkor egy benne lévő `p` elem `font-size: 1.5em` értéke `16px * 1.5 = 24px` lesz.
    * **Hátránya**: Ha több egymásba ágyazott elemnél használjuk, a méretek "összeszorzódnak", ami nehezen követhetővé teheti a végső méretet.

* **`rem`** (root em): A dokumentum **gyökér (`<html>`) elemének `font-size`** értékéhez viszonyít.
    * Ez a modern webdesign egyik legfontosabb mértékegysége. Mivel mindig ugyanahhoz az alapértékhez (a gyökérhez) viszonyít, a méretek kiszámíthatóak és könnyen skálázhatóak. A böngészők alapértelmezett `font-size`-a általában `16px`, így `1rem = 16px`, `2rem = 32px`, stb.
    * **Előnye**: A felhasználó a böngésző beállításaiban megváltoztathatja az alap betűméretet, és a `rem`-mel megadott méretek arányosan igazodnak ehhez, javítva az **akadálymentességet (accessibility)**.

* **`%`** (százalék): A **szülő elem egy adott tulajdonságához** viszonyít.
    * Ha egy `div` szélessége `800px`, és egy benne lévő elem `width: 50%`, akkor az elem szélessége `400px` lesz.
    * Nagyon hasznos rugalmas elrendezések (layoutok) készítéséhez.

* **`vw` és `vh`** (viewport width / height): A **nézetablak (viewport) szélességéhez vagy magasságához** viszonyítanak.
    * `1vw` = a nézetablak szélességének 1%-a.
    * `1vh` = a nézetablak magasságának 1%-a.
    * Például egy `height: 100vh` tulajdonsággal rendelkező elem mindig pontosan kitölti a képernyő magasságát, mérettől függetlenül.

## Mikor melyiket használjuk? – Ökölszabályok

| Mértékegység | Javasolt felhasználás | Miért? |
| :--- | :--- | :--- |
| **`rem`** | `font-size`, `margin`, `padding` (térközök), `width`, `height` | Könnyen skálázható, kiszámítható és akadálymentes. A teljes felület arányosan növelhető/csökkenthető egyetlen alapérték (`html` `font-size`) módosításával. |
| **`px`** | `border-width` (szegélyvastagság), `box-shadow` értékek | Amikor egy vékony, fix, nem skálázódó méretre van szükség. |
| **`%`** | Elemek szélessége egy tárolón belül (pl. grid oszlopok) | Rugalmas, a szülő elemhez igazodó elrendezések készítésére. |
| **`em`** | Olyan elemeknél, amiknek a méretét a közvetlen szülőjükhöz akarjuk igazítani (pl. egy ikon mérete egy gomb szövegéhez képest). | Kontextusfüggő méretezést tesz lehetővé, de óvatosan kell vele bánni. |
| **`vw`, `vh`** | Teljes képernyős "hero" szekciók, a nézetablakhoz igazodó betűméretek. | A böngésző ablakának méretéhez kötött, dinamikus méretezéshez. |