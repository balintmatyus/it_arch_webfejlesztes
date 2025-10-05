# Táblázatok stílusbeállításai

Az HTML táblázatok stílusozása kulcsfontosságú a weboldalak olvashatóságának és esztétikájának javításához. Alapértelmezésben a böngészők által megjelenített táblázatok gyakran zsúfoltak és nehezen olvashatóak. A CSS segítségével azonban jelentősen javíthatunk a táblázatok megjelenésén.

Kezdjük a kiindulási HTML kóddal. A lenti táblázat "Negyedéves kütyü eladásokat" tartalmaz. Ennek a szerkezetnek a stílusát fogjuk a továbbiakban CSS-sel módosítani.

```html
<table>
  <caption>Negyedéves kütyü eladások</caption>
  <thead>
    <tr>
      <th>Termék neve</th>
      <th>Eladott darabszám</th>
      <th>Egységár (HUF)</th>
      <th>Leírás</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Okos Vízforraló 3000</td>
      <td>150</td>
      <td>25000</td>
      <td>Wi-Fi képes vízforraló, alkalmazás-vezérléssel.</td>
    </tr>
    <tr>
      <td>Kiber Kávéfőző</td>
      <td>95</td>
      <td>42000</td>
      <td>Programozható, beépített darálóval.</td>
    </tr>
    <tr>
      <td>Holo Projektor Mini</td>
      <td>210</td>
      <td>78000</td>
      <td>Hordozható, 4K felbontású mini projektor.</td>
    </tr>
    <tr>
      <td>Flexi Billentyűzet</td>
      <td>350</td>
      <td>12500</td>
      <td>Vízálló, feltekerhető szilikon billentyűzet.</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="4">Az adatok 2025 harmadik negyedévére vonatkoznak.</td>
    </tr>
  </tfoot>
</table>
```

## Alapvető táblázat stílusok

A táblázatok stílusbeállításánál az alábbi alapvető tulajdonságokat érdemes figyelembe venni:

* **Betűtípus frissítése:** Egy kevésbé formális megjelenés érdekében érdemes lehet az alapértelmezett betűtípust megváltoztatni az egész HTML dokumentumon.
    ```css
    html {
      font-family: Arial, Helvetica, sans-serif;
    }
    ```

* **Térköz és elrendezés:**
    * `table-layout: fixed`: Ez a tulajdonság biztosítja a táblázat kiszámítható viselkedését, és lehetővé teszi, hogy az oszlopszélességeket a fejléc elemein (`<th>`) keresztül állítsuk be.
    * `width`, `min-width`, `margin: 0 auto`: Ezekkel a beállításokkal a táblázat a szélesebb nézetablakokat (viewport) nagyrészt kitöltheti és vízszintesen középre igazítható. Szűkebb nézetablakok esetén a táblázat olvasható szélességű marad, és szükség esetén vízszintes görgetést tesz lehetővé, ami jobb felhasználói élményt nyújt mobil eszközökön.
    * `border-collapse: collapse`: Ezt az értéket javasolt beállítani a táblázat stílusozásakor, mivel megszünteti a táblázat elemei közötti alapértelmezett térközöket, és a határokat eggyé vonja össze, ami letisztultabb megjelenést eredményez.
    * `padding`: A `<th>` és `<td>` elemekre beállított belső térköz javítja az adatok olvashatóságát. (Erre később még visszatérünk a következő órán)

* **Példa:**
```css
table {
    table-layout: fixed;
    width: 80%;
    min-width: 1000px;
    margin: 0 auto;
    border-collapse: collapse;
}

th, td {
    padding: 0.6em;
}
```

## Adatok igazítása

Az adatok cellán belüli igazítása elengedhetetlen az olvashatóság szempontjából. Általános gyakorlat, hogy a szöveget balra, a számokat pedig jobbra igazítjuk.

* **Szöveg- és számigazítás:** Az `:nth-child` pszeudo-osztály segítségével kiválaszthatjuk a táblázat adott oszlopait, és beállíthatjuk azok igazítását, valamint szélességét. Fontos, hogy a több tartalmat tartalmazó oszlopok szélesebbek legyenek, mint a számokat tartalmazóak, hogy a szöveg elférjen egy sorban.
* **Függőleges igazítás:** A `vertical-align: top` tulajdonság biztosítja, hogy a cellák tartalma a cella tetejére igazodjon, ne pedig középre.

* **Példa:**
```css
th, td {
    vertical-align: top;
    padding: 0.3em; /* A jobb függőleges igazítás érdekében csökkentjük a padding-ot */
}

/* A 2. és 3. oszlop (számok) jobbra igazítása */
tr :nth-child(2),
tr :nth-child(3) {
    text-align: right;
    width: 15%;
}

/* Az 1. oszlop (termék neve) balra igazítása */
tr :nth-child(1) {
    text-align: left;
    width: 25%;
}

/* A 4. oszlop (leírás) balra igazítása és szélesítése */
tr :nth-child(4) {
    text-align: left;
    width: 45%;
}
```

## Keretek hozzáadása

A keretek vizuálisan elválasztják a táblázat `<caption>` elemét, az adatokat és a lábjegyzetet (`<tfoot>`).

* **Példa:**
```css
tfoot {
    border-top: 1px solid #999999;
}

table {
  /* ...egyéb táblázat stílusok */
    border-top: 1px solid #999999;
    border-bottom: 1px solid #999999;
}
```

## Zebra csíkozás

A zebra csíkozás, vagyis a váltakozó színű sorok, megkönnyítik a táblázatok adatainak értelmezését és olvasását. A `:nth-child` szelektor egy formulát is kaphat paraméterként (pl. `2n+1` vagy `odd` a páratlan, `2n` vagy `even` a páros sorokhoz).

* **Példa:**
```css
tbody tr:nth-child(odd) {
    background-color: #eeeeee;
}
```

## Felirat (caption) stílusozása

A táblázat felirata (`<caption>`) is testreszabható, például a `caption-side` tulajdonsággal, amely meghatározza a felirat elhelyezkedését (pl. `bottom` az aljára).

* **Példa:**
```css
caption {
    padding: 1em;
    font-style: italic;
    caption-side: bottom;
    letter-spacing: 1px;
}
```

## Gyors tippek táblázatok stílusozásához

* Legyen a táblázat HTML jelölése a lehető legegyszerűbb és rugalmas.
* Használja a `table-layout: fixed` tulajdonságot a kiszámíthatóbb elrendezés érdekében.
* Alkalmazza a `border-collapse: collapse` beállítást a letisztultabb keretekhez.
* Ossza fel a táblázatot logikai részekre (pl. `<thead>`, `<tbody>`, `<tfoot>`), hogy könnyebben lehessen stílusokat alkalmazni.
* Használjon zebra csíkozást a sorok jobb olvashatóságáért.
* Igazítsa a `<th>` és `<td>` szövegét a `text-align` tulajdonsággal a rendezettebb és könnyebben követhető megjelenés érdekében.


## Teljes kód egyben

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stílusozott Táblázat Példa</title>
    <style>
        /* Betűtípus frissítése */
        html {
            font-family: Arial, Helvetica, sans-serif;
            background-color: #f4f4f4; /* A jobb láthatóságért egy enyhe háttérszín */
            padding: 20px;
        }

        /* Alapvető táblázat stílusok: elrendezés, méretezés, középre igazítás */
        table {
            table-layout: fixed;
            width: 80%;
            min-width: 1000px;
            margin: 0 auto;
            border-collapse: collapse;
            /* Keretek hozzáadása a táblázat tetejére és aljára */
            border-top: 1px solid #999999;
            border-bottom: 1px solid #999999;
            background-color: #ffffff;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        /* Cella stílusok: térköz és függőleges igazítás */
        th, td {
            padding: 0.3em;
            vertical-align: top;
        }

        /* Fejléc stílusai */
        thead th {
            background-color: #333;
            color: #fff;
            padding: 0.8em 0.3em;
        }

        /* Adatok igazítása: számok jobbra, szöveg balra */
        /* Az 1. oszlop (termék neve) balra igazítása */
        tr :nth-child(1) {
            text-align: left;
            width: 25%;
        }

        /* A 2. és 3. oszlop (számok) jobbra igazítása */
        tr :nth-child(2),
        tr :nth-child(3) {
            text-align: right;
            width: 15%;
        }

        /* A 4. oszlop (leírás) balra igazítása és szélesítése */
        tr :nth-child(4) {
            text-align: left;
            width: 45%;
        }

        /* Zebra csíkozás a jobb olvashatóságért */
        tbody tr:nth-child(odd) {
            background-color: #eeeeee;
        }

        /* Lábjegyzet (tfoot) stílusai */
        tfoot {
            border-top: 1px solid #999999;
        }

        tfoot td {
            font-size: 0.9em;
            font-style: italic;
            text-align: center; /* A colspan miatt a lábjegyzetet középre igazítjuk */
            padding: 1em 0;
        }

        /* Felirat (caption) stílusozása */
        caption {
            padding: 1em;
            font-style: italic;
            caption-side: bottom;
            letter-spacing: 1px;
            color: #666;
        }
    </style>
</head>
<body>

    <table>
      <caption>Negyedéves kütyü eladások</caption>
      <thead>
        <tr>
          <th>Termék neve</th>
          <th>Eladott darabszám</th>
          <th>Egységár (HUF)</th>
          <th>Leírás</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Okos Vízforraló 3000</td>
          <td>150</td>
          <td>25 000</td>
          <td>Wi-Fi képes vízforraló, alkalmazás-vezérléssel.</td>
        </tr>
        <tr>
          <td>Kiber Kávéfőző</td>
          <td>95</td>
          <td>42 000</td>
          <td>Programozható, beépített darálóval.</td>
        </tr>
        <tr>
          <td>Holo Projektor Mini</td>
          <td>210</td>
          <td>78 000</td>
          <td>Hordozható, 4K felbontású mini projektor.</td>
        </tr>
        <tr>
          <td>Flexi Billentyűzet</td>
          <td>350</td>
          <td>12 500</td>
          <td>Vízálló, feltekerhető szilikon billentyűzet.</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td colspan="4">Az adatok 2025 harmadik negyedévére vonatkoznak.</td>
        </tr>
      </tfoot>
    </table>

</body>
</html>
```