# Gyakorló feladatok

## Téglalap kerülete és területe

Definiálj két változót, oldalA és oldalB néven, és adj nekik számértéket. Számítsd ki a téglalap kerületét és területét a tanult aritmetikai operátorokkal. Az eredményeket írasd ki a console.log() segítségével, magyarázó szöveggel.

## Köszönés

Írj egy JavaScript programot, amely egy aktualisOra nevű, egész számot tároló változó alapján a napszaknak megfelelő üdvözlést írja ki a konzolra. Használj if...else if...else szerkezetet, ami eldönti, hogy ha az óra 10-nél kisebb, akkor "Jó reggelt!", ha 18-nál kisebb, akkor "Jó napot!", egyébként pedig "Jó estét!" üzenetet jelenítsen meg. Az üdvözlés előtt a program írja ki a változó aktuális értékét is egy informatív szöveggel. Használd a `console.log(aktualisOra)` utasítást a megfelelő köszöntés megjelenítésére. Ha ezzel megvagy, módosítsd a kódodat, hogy a felhasználó neve is megjelenjen a köszöntésben. (Amennyiben nem adott meg a felhasználó nevet, legyen a neve Vendég.)

## Mini-kalkulátor

Írj egy programot, ami a `prompt()` segítségével bekér a felhasználótól két számot, majd egy matematikai operátort (`+`, `-`, `*`, `/`). Használj **`switch` utasítást** az operátor kiértékelésére!
* Ha az operátor `+`, add össze a két számot.
* Ha az operátor `-`, vond ki a másodikat az elsőből.
* Ha az operátor `*`, szorozd össze őket.
* Ha az operátor `/`, oszd el az elsőt a másodikkal.
* Az eredményt írasd ki az `alert()` segítségével.
* A `switch` szerkezetben használj `default` ágat is, ami akkor fut le, ha a felhasználó érvénytelen operátort ad meg (pl. "x"). Ekkor írasd ki: `"Hibás operátor!"`.

## FizzBuzz

Írj egy programot, ami egy for ciklussal végigmegy a számokon 1-től 100-ig.
* Ha a szám osztható 3-mal, írja ki, hogy "Fizz".
* Ha a szám osztható 5-tel, írja ki, hogy "Buzz".
* Ha a szám osztható 3-mal és 5-tel is, írja ki, hogy "FizzBuzz".
* Minden más esetben írja ki magát a számot.

## Számlálás

Írj ciklust, ami kiírja a konzolra a számokat szóközzel elválasztva egymás mellé 1-től egy, a felhasználó által meghatározott számig.

Miután ez sikerült, módosítsd a kódot úgy, hogy visszafele számoljon és ha elérte a 0-t, írd ki a konzolra, hogy "BUÉK!".

## Összeadó

Írj egy programot, ami addig kér be számokat a felhasználótól egy while ciklusban, amíg a felhasználó a "stop" szót nem írja be. A program számolja össze a beírt számok összegét. Amikor a ciklus véget ér, írja ki az alert() segítségével a végeredményt. A break utasítással lépj ki a ciklusból, ha a felhasználó a "stop" szót adja meg.

## Számkitaláló

Írj programot, amely "gondol" egy számra, a felhasználónak pedig korlátozott számú lehetősége van kitalálni azt. A program minden tipp után segíti a játékost azzal, hogy megmondja, a gondolt szám kisebb vagy nagyobb-e.

Ha ezzel megvagy módosítsd a "Számkitaláló játék" kódját! A cikluson belül, miután bekérted a felhasználó tippjét és átalakítottad `Number()`-rel, **végezz ellenőrzést!**
* Használd az **`isNaN()`** függvényt annak vizsgálatára, hogy a bemenet valóban számmá alakult-e.
* Ha a `isNaN(tipp)` értéke `true` (tehát a felhasználó nem számot írt be, pl. "abc"), akkor egy `alert()` üzenetben jelezd a hibát ("Kérlek, számot adj meg!"), és **ne pazarolj el egy próbálkozást**. (Tipp: a `continue` itt nem feltétlen jó megoldás, gondold át, hogyan tudnád a ciklusváltozót kezelni, hogy a próbálkozás ne vesszen el.)

## Faktoriális

Írj programot, ami 1) rekurzió segítségével, valamint 2) ciklussal kiszámítja egy szám faktoriálisát. A két számítási módot külön függvényként implementáld.
