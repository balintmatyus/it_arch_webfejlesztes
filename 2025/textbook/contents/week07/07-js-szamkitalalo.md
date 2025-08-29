# Számkitaláló játék készítése

>[!TASK]
>Írj programot, amely "gondol" egy számra, a felhasználónak pedig korlátozott számú lehetősége van kitalálni azt. A program minden tipp után segíti a játékost azzal, hogy megmondja, a gondolt szám kisebb vagy nagyobb-e.

## 1. Lépés: A játék előkészítése

Mielőtt a játék elindulna, meg kell határoznunk a játékszabályokat és a kezdőállapotot.

**Változók és konstansok létrehozása:** 
* Először is, szükséged lesz egy helyre, ahol tárolod a **titkos számot**, amit ki kell találni. 
* Ezen kívül rögzítened kell, hogy a játékosnak **maximum hány próbálkozása** lehet. 
* Érdemes egy harmadik változót is létrehozni, ami egyfajta "flagként" működik, és azt jelzi, hogy a játékos **eltalálta-e már a számot**. Ennek a kezdőértéke hamis legyen, hiszen a játék elején még nem nyert.
* A játék indulásakor egy felugró ablakkal tájékoztasd a játékost a játékszabályokról: mondd el neki, hogy gondoltál egy számra, és hány lehetősége van kitalálni.

## 2. Lépés: A tippelési folyamat megvalósítása

A játék központi eleme a tippelés, aminek meghatározott számban kell ismétlődnie.

* Használj egy ciklust (például egy `for` ciklust), ami pontosan annyiszor fog lefutni, amennyi a próbálkozások maximális száma. Ez a ciklus fogja kezelni az egyes tippelési köröket.
* A cikluson belül minden körben kérd be a játékos tippjét egy felugró ablak segítségével. Fontos, hogy a bekért adatot **szövegből számmá alakítsd**, hogy később matematikai összehasonlításokat végezhess vele.

>[!NOTE]
>Ezt a lépést a `Number(szamSzovegkent)` függvény segítségével hajthatod végre.

## 3. Lépés: A Tipp Kiértékelése

Miután a játékos tippelt, és az adatot számmá alakítottad, a programnak reagálnia kell.

* **Elágazás használata:** Egy `if...else` szerkezettel vizsgáld meg a játékos tippjét.
    * **Első eset (győzelem):** Ha a tipp **egyezik** a titkos számmal, gratulálj a játékosnak egy üzenetben. Nagyon fontos, hogy ekkor állítsd át az "eltalálta-e" jelzőváltozót igazra, majd azonnal **szakítsd meg a ciklust**, hiszen a játéknak vége.
    * **Második eset (túl alacsony tipp):** Ha a tipp **kisebb**, mint a titkos szám, egy üzenettel tudasd a játékossal, hogy egy nagyobb számra gondoltál.
    * **Harmadik eset (túl magas tipp):** Ha a tipp **nagyobb**, mint a titkos szám, akkor pedig jelezd, hogy a keresett szám kisebb.

---

## 4. Lépés: A Játék Végének Kezelése

Miután a ciklus befejeződött (akár azért, mert a játékos nyert, akár azért, mert elfogytak a próbálkozásai), le kell zárni a játékot.

* **Végeredmény ellenőrzése:** A ciklus után vizsgáld meg az "eltalálta-e" jelzőváltozó értékét.
* **Vesztes állapot közlése:** Ha a változó értéke továbbra is hamis, az azt jelenti, hogy a játékosnak nem sikerült kitalálnia a számot a megadott próbálkozások alatt. Ebben az esetben egy utolsó üzenetben tudasd vele, hogy vesztett, és áruld el, mi volt a titkos szám. Ha a változó igaz, akkor nincs teendő, hiszen a győzelmet már a cikluson belül kezelted.