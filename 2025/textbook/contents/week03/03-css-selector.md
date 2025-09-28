# CSS szelektorok

A CSS szelektorok mondják meg a böngészőnek, hogy mely HTML elemekre kell a stílusokat alkalmazni.

Induljunk ki a következő HTML-ből.

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Szelektorok Gyakorló</title>

</head>
<body>

    <h1 id="heading">CSS Szelektorok a gyakorlatban</h1>

    <h2>Típus-szelektor</h2>
    <p>Ez egy sima bekezdés, de van benne egy <span>span elem</span>, aminek sárga a háttere a típus-szelektor miatt.</p>
    
    <hr>
    
    <h2>Osztály-szelektorok</h2>
    <h1 class="highlight">Ez egy h1 elem "highlight" osztállyal (rózsaszín háttér).</h1>
    <p class="highlight">Ez egy bekezdés "highlight" osztállyal (sárgás háttér).</p>
    <div class="notebox">Ez egy sima "notebox". Nincs narancs kerete.</div>
    <div class="notebox warning">Ez a "notebox" megkapta a "warning" osztályt is, ezért vastag és narancs keretes.</div>
    
    <hr>
    
    <h2>ID-szelektor</h2>
    <p id="one">Ennek a bekezdésnek "one" az ID-ja, ezért kék a háttere.</p>
    
    <hr>
    
    <h2>Szelektorkészlet</h2>
    <p class="special">Ez a bekezdés a ".special" osztály miatt alá van húzva. (A h1 címek is aláhúzottak a szelektorkészlet miatt).</p>

    <hr>
    
    <h2>Kombinátorok</h2>
    
    <h3>Leszármazott szelektor (szóköz)</h3>
    <div id="leszarmazott-teszt">
        <p>Ez a bekezdés a div-en belül van, ezért zöld a bal oldali kerete.</p>
        <div>
            <p>Ez egy mélyebben beágyazott bekezdés, de mivel leszármazott, ez is megkapja a zöld keretet.</p>
        </div>
    </div>
    <p>Ez a bekezdés a div-en kívül van, nincs zöld kerete.</p>
    
    <h3>Gyermek szelektor (>)</h3>
    <div id="gyermek-teszt">
        <p>Ez a bekezdés a div <strong>közvetlen gyermeke</strong>, ezért piros a bal oldali kerete.</p>
        <div>
            <p>Ez egy mélyebben beágyazott bekezdés. Ő már nem közvetlen gyermek, így **nem kapja meg** a piros keretet.</p>
        </div>
    </div>
    
    <hr>
    
    <h2>Pszeudo-osztályok</h2>
    <p>Vidd az egeret a gombra, kattints a beviteli mezőbe, vagy tartsd lenyomva a gombot!</p>
    
    <button>Interaktív Gomb</button>
    <br><br>
    <input type="text" placeholder="Kattints ide a fókuszért!">

</body>
</html>
```

### Típus-szelektorok (Element Selectors)
A HTML elem nevével választják ki az elemeket. A lenti `span` szelektor az összes `<span>` elem háttérszínét sárgára állítja.
```css
span { background-color: yellow; }
```

### Osztály-szelektorok (Class Selectors)
Egy pont (`.`) karakterrel kezdődnek, és minden olyan elemet kiválasztanak, amely rendelkezik a megadott `class` attribútummal.

* **Alapvető használat**: A `.highlight` az összes `highlight` osztályú elemet célozza.
    ```css 
    .highlight { background-color: yellow; }
    ```
* **Célzás adott elemen**: A `h1.highlight` csak az `<h1>` elemekre érvényes, amelyeknek van "highlight" osztályuk.
    ```css
    h1.highlight { background-color: pink; }
    ```
* **Több osztály együttes célzása**: A `.notebox.warning` csak azokra az elemekre vonatkozik, amelyeknek *mind* a "notebox", *mind* a "warning" osztályuk meg van adva.
    ```css
    .notebox {font-weight: bold;}
    .warning { border: 10px solid orange;}
    ```

### ID-szelektorok (ID Selectors)
Egy hash jellel (`#`) kezdődnek. Fontos különbség, hogy egy `id` értéknek **egyedinek kell lennie** az egész HTML dokumentumban.
```css
#one { background-color: blue; color: white;}
h1#heading { color: rebeccapurple; }
```

>[!WARNING]
>Az azonos ID többszöri használata érvénytelen kódot eredményez, és hibás működést okozhat.

### Szelektorkészletek (Selector Lists)
Ha több szelektorhoz azonos stílust szeretnénk rendelni, vesszővel elválasztva felsorolhatjuk őket.
```css
h1, .special { text-decoration: underline; }
```

### Univerzális szelektor (Universal Selector)
A csillag (`*`) jelöli, és a dokumentum összes elemét kiválasztja. Gyakran használják böngésző stílusok "resetelésére".
```css
* {
  margin: 0;
  padding: 0;
}
```

### Kombinátorok és Pszeudo-osztályok

A szelektorokat kombinálhatjuk is, hogy még pontosabban célozhassunk.

* **Leszármazott szelektor (szóköz):** Egy elemen belüli *bármely* leszármazottat eléri. A `div p` minden `<p>` elemet kiválaszt, ami egy `<div>`-en belül van.
* **Gyermek szelektor (`>`):** Csak a *közvetlen* gyermek elemeket választja ki. A `div > p` csak azokat a `<p>` elemeket célozza, amelyek közvetlenül a `<div>` elemen belül vannak.

A **pszeudo-osztályok** egy elem speciális állapotát jelölik, és kettősponttal (`:`) kezdődnek. Elengedhetetlenek az interaktív felületekhez.
* `:hover`: Akkor lép érvénybe, amikor a felhasználó az egeret az elem fölé viszi.
* `:focus`: Akkor aktív, amikor egy elem (pl. egy űrlapmező) fókuszt kap (belekattintanak).
* `:active`: Egy elem aktív állapotát jelöli (pl. amíg a gombot lenyomva tartjuk).

**Példa:**
```css
/* Amikor az egeret a gomb fölé visszük */
button:hover {
    background-color: #555;
    color: white;
    cursor: pointer;
}

/* Amikor a beviteli mezőre kattintunk (fókuszba kerül) */
input:focus {
    border-color: dodgerblue;
    outline: 2px solid lightblue;
}

/* Amikor a gombot lenyomva tartjuk */
button:active {
    transform: scale(0.95);
}
```
