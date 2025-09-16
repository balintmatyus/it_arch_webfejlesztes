# Táblázatok: Adatok strukturálása

A HTML táblázatok célja **táblázatos adatok** megjelenítése – vagyis olyan információké, amelyeket sorokba és oszlopokba lehet rendezni. Lehetővé teszik, hogy gyorsan és könnyen leolvassunk értékeket, amelyek különböző adattípusok között teremtenek kapcsolatot.

>[!NOTE]
> Régebben a webfejlesztők táblázatokat használtak weboldalak elrendezésének (layout) kialakítására. Ez ma már **helytelen gyakorlatnak számít**. A modern CSS technológiák (mint a Flexbox vagy a Grid) sokkal hatékonyabb és rugalmasabb megoldást kínálnak. A táblázatos elrendezés akadálymentesítési problémákat okoz, nehezen karbantartható kódot eredményez, és nem reszponzív.

## A táblázat alapjai

Egy táblázat alapvető elemei a következők:

* `<table>`: Maga a táblázat konténere, amely minden más táblázattal kapcsolatos elemet körbevesz.
* `<tr>`: A táblázat egy sorát jelöli (table row).
* `<td>`: A táblázat egy celláját jelöli (table data). Egy cella egy `<tr>`-en belül kap helyet.

Lássunk egy egyszerű példát:

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <title>HTML5 Oldalstruktúra - Egyszerű Példa</title>
    <style>
        tr, td, table {
            border:1px solid black; 
            border-collapse: collapse;
        }
    </style>
</head>
<body>

  <table>
  <tr>
    <td>1. sor, 1. cella</td>
    <td>1. sor, 2. cella</td>
  </tr>
  <tr>
    <td>2. sor, 1. cella</td>
    <td>2. sor, 2. cella</td>
  </tr>
  </table>
</body>
</html>
```

>[!NOTE]
>Egyelőre a stílusbeállításokat csak másoljuk át, nem kell megértenünk. Azért adtam hozzá `border`-t (szegély), hogy láthatóvá váljon a táblázat felépítése.

## Fejlécek (`<th>`)

A táblázatok olvashatóságát és értelmezhetőségét nagyban javítja, ha fejléceket használunk. A `<th>` (table header) elem ugyanúgy működik, mint a `<td>`, de szemantikailag jelöli, hogy az adott cella egy sor vagy egy oszlop fejléce. A böngészők alapértelmezetten félkövérre és középre igazítva jelenítik meg a `<th>` elemek tartalmát.

```html
<table>
  <tr>
    <th>Név</th>
    <th>Kor</th>
  </tr>
  <tr>
    <td>Anna</td>
    <td>32</td>
  </tr>
  <tr>
    <td>Béla</td>
    <td>45</td>
  </tr>
</table>
```

## Cellák összevonása: `colspan` és `rowspan`

Néha szükség van arra, hogy egy cella több oszlopot vagy sort is átfogjon. Erre szolgál a `colspan` (oszlopok átfogása) és a `rowspan` (sorok átfogása) attribútum. Mindkettő egy számértéket vár, amely megadja, hogy hány oszlopot vagy sort fogjon át a cella.

```html
<table>
  <tr>
    <th colspan="2">Termék</th>
    <th>Eladott darab</th>
  </tr>
  <tr>
    <td>Telefon</td>
    <td>iPhone 15</td>
    <td>120</td>
  </tr>
  <tr>
    <td rowspan="2">Laptop</td>
    <td>MacBook Air</td>
    <td>45</td>
  </tr>
  <tr>
    <td>Dell XPS</td>
    <td>60</td>
  </tr>
</table>
```

A komplexebb táblázatok esetében további elemeket és attribútumokat használhatunk a struktúra és az akadálymentesség javítására.

## Táblázatcím (`<caption>`)

A `<caption>` elem segítségével címet adhatunk a táblázatunknak. Ezt közvetlenül a nyitó `<table>` tag után kell elhelyezni. A táblázatcím segít a felhasználóknak (különösen a képernyőolvasót használóknak) gyorsan megérteni a táblázat tartalmát anélkül, hogy végig kellene olvasniuk a cellákat.

```html
<table>
  <caption>Havi kiadások</caption>
  <tr>
    <th>Tétel</th>
    <th>Összeg</th>
  </tr>
  <tr>
    <td>Lakbér</td>
    <td>150.000 Ft</td>
  </tr>
</table>
```

## Struktúra: `<thead>`, `<tbody>`, `<tfoot>`

A hosszabb, összetettebb táblázatokat tovább tagolhatjuk a fejléc (`<thead>`), a törzs (`<tbody>`) és a lábléc (`<tfoot>`) részekre. Bár ezek az elemek önmagukban nem változtatják meg a táblázat vizuális megjelenését, jobb strukturális alapot adnak a CSS stílusozáshoz és a JavaScript manipulációhoz. Például CSS segítségével elérhetjük, hogy egy hosszú táblázat görgetésekor a fejléc (`<thead>`) mindig látható maradjon.

A helyes sorrend: `<thead>`, majd `<tbody>`, majd `<tfoot>`.

```html
<table>
  <caption>Havi kiadások</caption>
  <thead>
    <tr>
      <th>Tétel</th>
      <th>Kategória</th>
      <th>Összeg (Ft)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Lakbér</td>
      <td>Lakhatás</td>
      <td>150000</td>
    </tr>
    <tr>
      <td>Élelmiszer</td>
      <td>Bevásárlás</td>
      <td>80000</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="2">Összesen</td>
      <td>230000</td>
    </tr>
  </tfoot>
</table>
```

Forrás:
- https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content

A szöveg AI felhasználásával készült.