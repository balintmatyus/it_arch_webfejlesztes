# Részletes megoldás - Sakk weboldal készítése

Ez a dokumentum részletesen bemutatja a sakk weboldal elkészítésének folyamatát, a tervezéstől a megvalósításig.

## Tervezési koncepció

Ezen weboldal célja a sakkjáték bemutatása egy egyszerű, letisztult felületen. A központi elem egy sakktábla, amelyen néhány sakk figurát helyezünk el. Az oldal tartalmaz rövid ismertetőt a játékról, és egy összegző gondolatot a sakk szellemi értékeiről.

Az elkövetkezendőkben az alábbi weboldalt készítjük el:

![Megoldás](./megoldas.png)

## A projekt előkészítése

> [!IMPORTANT]
> Hozzuk létre a következő mappastruktúrát:
>
> ```
> web/
> ├── index.html
> ├── styles/
> │   └── style.css
> └── images/
>     ├── favicon.ico
>     ├── feher_bastya.png
>     ├── feher_kiraly.png
>     ├── fekete_huszar.png
>     └── fekete_kiralyno.png
> ```

## HTML struktúra felépítése

### Alap HTML váz

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sakk bemutatása</title>
    <link rel="stylesheet" href="./styles/style.css">
    <link rel="icon" type="image/x-icon" href="./images/favicon.ico">
</head>
<body>
    <!-- Itt lesz a tartalom -->
</body>
</html>
```

### Header szakasz

A header részben elhelyezzük a főcímet és egy bevezető bekezdést a sakkról:

```html
<header>
    <h1>A sakk játék lényege</h1>
    <p id="bekezdes">A sakk ősi, perzsa-arab eredetű stratégiai táblajáték két személy részére, és egyben sportág is. A „sakk" szó – amely nemcsak a játékot jelenti, hanem azt a helyzetet is, amikor az ellenfél királya „ütésben van" – a perzsa „shāh" (شَاه) szóból ered, melynek jelentése király.</p>
</header>
```

### Main szakasz - A sakktábla és navigáció

A fő tartalmi részben először egy navigációs menüt helyezünk el, majd egy 9×9-es táblázatot, amely egy sakktáblát reprezentál. A táblázat első sora és első oszlopa a sakkban használt koordinátákat tartalmazza:

```html
<main>
        <nav>
            <h2>Tartalom</h2>
            <ul>
                <li><a href="#bekezdes">A sakk fogalma</a></li>
                <li><a href="#befejezes">Összefoglalás</a></li>
            </ul>
        </nav>
        <table>
            <tbody>
                <tr>
                    <td></td>
                    <td>A</td>
                    <td>B</td>
                    <td>C</td>
                    <td>D</td>
                    <td>E</td>
                    <td>F</td>
                    <td>G</td>
                    <td>H</td>
                </tr>
                <tr>
                    <td>1</td>
                    <td></td>
                    <td><img src="./images/fekete_kiralyno.png" alt="Kép egy fekete királynő sakkbábúról."></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                    <td></td>
                </tr>
                <!-- További sorok a 2-8. sorig -->
            </tbody>
        </table>
    
    <p id="befejezes">Összegzésként elmondható, hogy a <a href="https://hu.wikipedia.org/wiki/Sakk" target="_blank">sakk</a> nem csupán egy játék, hanem igazi szellemi kihívás, amely fejleszti a logikát, a türelmet és a stratégiai gondolkodást. Akár kezdőként, akár tapasztalt játékosként ülünk a tábla mellé, minden parti új lehetőséget kínál a fejlődésre és az önmegismerésre. A sakk világa végtelen – és éppen ez teszi olyan izgalmassá.</p>
</main>
```

### Footer szakasz

Az oldal alján egy egyszerű láblécet helyezünk el, amely tartalmazza a szerzői jogi információkat:

```html
<footer>
    <p>2025 &copy; Minden jog fenntartva</p>
</footer>
```

## CSS stílusok kialakítása

### Alap stílusok

Az egész oldal alapértelmezett beállításait egy univerzális szelektor segítségével állítjuk be:

```css
* {
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
}

nav {
    float: left;
    width: fit-content;
    padding: 0 40px;
}
```

### Táblázat stílusok

A sakktábla megjelenését különféle CSS szelektorok és tulajdonságok kombinációjával állítjuk be:

```css
table {
    border-collapse: collapse;
    margin: 20px auto;
}

td, th {
    border: 1px solid black;
    width: 100px;
    height: 100px;
}

tbody tr:first-child td, tbody td:first-child {
    background-color: lightblue;
    font-weight: bold;
}

tbody tr:nth-child(n+2):nth-child(odd) td:nth-child(n+2):nth-child(even),
tbody tr:nth-child(n+2):nth-child(even) td:nth-child(n+2):nth-child(odd) {
    background-color: black;
}

tbody tr td {
    padding: 10px;
    text-align: center;
}

tbody tr:first-child td:first-child {
    background-color: white;
}
```

### Képek stílusai

A bábukat ábrázoló képek méretezését és igazítását az alábbi stílusokkal biztosítjuk:

```css
img {   
    height: 100%;      
}
```

### Szöveges elemek stílusai

A címsorok és bekezdések formázása:

```css
h1 {
    text-align: center;
    font-size: 36px;
    margin: 20px;
}

h2 {
    font-size: 24px;
    margin-bottom: 15px;
}

p#bekezdes {
    margin: 15px;
    font-style: italic;
    font-size: 1.2em;
}

p#befejezes {
    margin: 15px;
    color: red;
}

p#bekezdes, p#befejezes {
    line-height: 1.5;
}

footer p {
    color: yellow;
    background-color: brown;
    font-size: 1.5em;
    text-align: center;
    padding: 20px;
}
```

### Link stílusok

A láblécben lévő link különböző állapotainak formázása:

```css
p a {
    color: darkred;
    text-decoration: none;
}

p a:hover {
    text-decoration: underline;
}

p a:visited {
    color: black;
}
```

## Navigáció megvalósítása

Az oldalon egy egyszerű, balra igazított navigációs menüt alakítottunk ki. A navigációs menü a tartalom elején jelenik meg, és két belső hivatkozást tartalmaz:

```css
nav {
    float: left;
    width: fit-content;
    padding: 0 40px;
}

h2 {
    font-size: 24px;
    margin-bottom: 15px;
}
```

>[!NOTE]
>A `float: left` tulajdonság biztosítja, hogy a navigáció balra igazodjon, és a tartalom körbefolyja azt. A `width: fit-content` tulajdonság azt jelenti, hogy a navigációs menü csak annyi helyet foglal el, amennyi szükséges a tartalmának megjelenítéséhez.