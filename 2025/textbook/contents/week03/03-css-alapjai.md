# CSS alapjai

CSS (Cascading Style Sheets) stílusleíró nyelv. Ötlete 1994-ben fogalmazódott meg Hakon Wium Lie-ben. Bár korábban verziókat (pl. CSS 2.1) különböztettünk meg, ma már a CSS-t modulokra bontva (színek, elrendezés, animációk stb.) fejlesztik és verziózzák. Ez a moduláris felépítés a modern CSS.

A HTML önmagában struktúrát ad a dokumentumnak, de a böngészők alapértelmezett stílusai csak nagyon alapvető olvashatóságot biztosítanak. A CSS-sel azonban sokkal többet tehetünk:
* Szöveg stílusozása (szín, méret, betűtípusok).
* Elrendezések létrehozása (pl. grid vagy többoszlopos elrendezések).
* Speciális effektek, például animációk hozzáadása.

## Stílusok definiálása

2 fő részből állnak: szelektorból (`h1`) és deklarációból (`color: red;`). A deklaráció is 2 részből, tulajdonságból (`color`) és értékből áll (`red`).

```css
h1 {
  color: red;
  font-size: 24px;
}
```

A CSS definiálása többféle módon lehetséges. HTML forráskódon belül:
* `<style>` utasítás segítségével a HTML `<head>` blokkjában,
* külső stíluslapok használatával külön `*.css` kiterjesztésű fájlként kezelve
* in-line, amikor az egyes HTML elemek tag-jeiben definiáljuk

### **Stíluslap készítése `<style>` utasítás segítségével**
```html
<head>
   <style>
     h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
     h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
     h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
   </style>
</head>
<body>
   <h1>Repülőgépek</h1>
   <h2>Vitorlázó gépek</h2>
   <h3>R26 Góbé</h3>
</body>
```
Ez a megközelítés általában akkor lehet "kézenfekvő", ha egy adott HTML oldalhoz nagyon specifikus, vagy csak arra az egy oldalra vonatkozó stílusokat szeretnél alkalmazni.

### **Stíluslap használata külső stíluslapokkal**

A stíluslap külön, .css kiterjesztésű fájlban is létrehozható. Ilyenkor is a `<head>` részben hivatkozunk rá.

**Példa:**
```html
<head>
   <link rel="stylesheet" href="style.css">
</head>
```

A törzsrész ugyanúgy néz ki, mint az első esetben.

A külső stíluslap (`style.css`) a következőképpen nézhet ki:
```css
h1 {font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;}
h2 {font-size: 24px; color: red; font-family: Verdana, sans-serif;}
h3 {font-size: 18px; color: blue; font-family: 'Courier New', monospace;}
```

A külső stíluslap előnyei:
* **Könnyebben kezelhető:** A HTML módosítása nélkül változtatható a stílus.
* **Átlátható:** A stílus elkülönül a tartalomtól és a struktúrától.
* **Gyorsabb betöltés:** A böngésző gyorsítótárazza (cache) a fájlt.
* **Újrahasznosítható:** Egy CSS fájl több HTML oldalhoz is csatolható.

### **Stíluslap készítése style paraméter segítségével, in-line CSS**
```html
<body>
   <h1 style="font-size: 32px; color: darkgreen; font-family: Arial, sans-serif;">Repülőgépek</h1>
   <h2 style="font-size: 24px; color: red; font-family: Verdana, sans-serif;">Vitorlázó gépek</h2>
   <h3 style="font-size: 18px; color: blue; font-family: 'Courier New', monospace;">R26 Góbé</h3>
</body>
```
Az inline stílusoknak magas a prioritásuk és azonnal hatnak, de használatuk a legtöbb esetben **rossz gyakorlatnak** minősül.

>[!WARNING]
> **Miért kerülendő az inline CSS?**
>1.  **Rossz karbantarthatóság:** Több száz oldalas webhelyen egy apró módosítás (pl. a betűszín megváltoztatása) több száz fájl szerkesztését igényelné. Külső stíluslap esetén ez egyetlen sor módosítása.
>2.  **Nem újrahasznosítható:** A stílus egy konkrét HTML elembe van "égetve", máshol nem használható fel.
>3.  **Szennyezi a HTML-t:** A HTML feladata a struktúra leírása, a CSS-é a megjelenés. Az inline CSS összemossa ezt a két feladatkört, rontva a kód olvashatóságát.

## Deklarációk eredettípusai

A CSS deklarációk három fő **eredettípusból** származnak, amelyeket a kaszkádolási algoritmus (lásd lentebb) a tulajdonságértékek meghatározására használ. Ezek az eredettípusok a következők: a **Felhasználói ügynök stíluslapok** (*User-agent stylesheets*), amelyeket a böngészők (user-agents) biztosítanak az alapvető, alapértelmezett stílusokhoz, a **Szerzői stíluslapok** (*Author stylesheets*), melyeket a webfejlesztők írnak az oldal dizájnjának és kinézetének meghatározására, beleértve az **inline stílusokat** is, amelyeket a `style` attribútummal definiálnak, valamint a **Felhasználói stíluslapok** (*User stylesheets*), melyekkel az olvasó felülírhatja a stílusokat a saját kívánságaihoz igazított böngészési élmény érdekében. A kaszkádolási algoritmus határozza meg, hogy ezen különböző eredetekből származó stílusok közül melyik kap precedenciát.

>[!NOTE]
>Mi a kurzus során **szerzői stíluslapokat** hozunk létre.

### A kaszkád elve: Ki nyer a végén?

A **kaszkád** (cascade) egy alapvető algoritmus, amely a CSS (Cascading Style Sheets) nevében is szerepel. Ez az algoritmus határozza meg, hogy a felhasználói ügynökök (böngészők) hogyan kombinálják a különböző forrásokból származó CSS tulajdonságértékeket egy adott elemhez. A kaszkád megértése kulcsfontosságú, mert a legmagasabb precedenciájú eredetből származó tulajdonságérték érvényesül, még akkor is, ha egy alacsonyabb precedenciájú réteg vagy eredet szelektora specifikusabb lenne.

A CSS deklarációk három fő **eredettípusból** származnak: a **felhasználói ügynök stíluslapokból** (User-agent stylesheets, a böngésző alapértelmezett stílusai), a **szerzői stíluslapokból** (Author stylesheets, a fejlesztők által írt stílusok), és a **felhasználói stíluslapokból** (User stylesheets, az olvasó által beállított stílusok).

A kaszkádoló algoritmus öt lépésben dönti el a prioritást:
1. **Relevancia (Relevance):** Kiszűri azokat a szabályokat, amelyek az elemre vonatkoznak.
2. **Eredet és fontosság (Origin and importance):** A szabályokat az `!important` jelölés és az eredet (Origin) szerint rendezi. Ez a lépés megelőzi a specifikussági algoritmust. Például a normál szerzői stílusok magasabb precedenciájúak, mint a normál felhasználói és a normál felhasználói ügynök stílusok.

| Prioritás | Eredet | Fontosság |
| :---: | :---: | :---: |
| 1 | user-agent (böngésző) | normal |
| 2 | user (felhasználó) | normal |
| 3 | author (fejlesztő) | normal |
| 4 | author (fejlesztő) | !important |
| 5 | user (felhasználó) | !important |
| 6 (legfontosabb) | user-agent (böngésző) | !important |

3. **Specifikusság (Specificity):** Azonos eredet és fontosság esetén a legmagasabb specifikusságú szelektor nyer.
4. **Megjelenési sorrend (Order of appearance):** Ha minden más azonos, az utolsóként deklarált stílus érvényesül.

A normál **inline stílusok** minden más normál szerzői stílusnál magasabb precedenciával rendelkeznek.
