# Termékszűrő Űrlap Készítése

A feladatod egy HTML űrlap (Form) elkészítése, amely képes kommunikálni a megadott webszerverrel. Az űrlap segítségével a felhasználó különböző feltételek (név, ár, kategória) alapján szűrheti a termékeket.

Kiinduló állomány:

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Termék Kereső</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            padding-top: 50px;
        }
        .container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            width: 400px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="text"],
        input[type="number"],
        select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box; /* Hogy a padding ne nyomja szét a keretet */
        }
        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .checkbox-group label {
            margin-bottom: 0;
            cursor: pointer;
        }
        input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Termék Szűrő</h1>

    <form>
        
        <div class="form-group">
            <!-- nev -->
        </div>

        <div class="form-group">
            <!-- kategoria -->
        </div>

        <div class="form-group">
            <!-- min_ar -->
        </div>

        <div class="form-group">
            <!-- max_ar -->
        </div>

        <div class="form-group checkbox-group">
            <!-- keszleten -->
        </div>

    </form>
</div>

</body>
</html>
```

A szerver címe (ahová az adatokat küldeni kell): **`https://7ulrq73p67t2h3lrkbzfjeb7y40rgooa.lambda-url.us-east-1.on.aws/`** (Ezt használd az `action` attribútumban).

## 1. Lépés: A kommunikációs csatorna megnyitása

Elsőként magát az űrlap keretet kell létrehoznod. Hozd létre a `<form>` elemet. Állítsd be a célpontot (`action`) a fenti szerver címre, és válaszd ki a megfelelő metódust (`method`). Mivel szűrésről van szó, javaslom a **GET** használatát, ahogy azt az elméletben is láttuk.

```html
<form action="HOVA_KÜLDÖM" method="HOGYAN_KÜLDÖM"> ... </form>
```

## 2. Lépés: Szöveges keresés és Ársávok

**A szerver által várt paraméterek:**
* `nev`: A termék neve (részleges egyezés is elég).
* `min_ar`: A minimum ár.
* `max_ar`: A maximum ár.

**Feladat:**
Hozd létre a szükséges `<input>` mezőket az űrlapon belül.
1.  A névhez használj egyszerű szöveges mezőt.
2.  Az árakhoz használj szám típusú mezőt.

>[!WARNING]
>A szerver **pontosan** ezeken a neveken (`nev`, `min_ar`, `max_ar`) keresi az adatokat. Ha az `<input>` elemed `name` attribútuma más (pl. `name="termekNeve"`), a szerver nem fogja megtalálni, és a szűrés nem működik!

## 3. Lépés: Kategória választó (A pontos egyezés)

A szerver működése alapján, ha van kategória szűrés, akkor annak **betűre pontosan** egyeznie kell. Ha a felhasználó kézzel írja be, könnyen elgépelheti.

**Feladat:**
Ahelyett, hogy gépelésre kényszerítenéd a felhasználót, használj egy legördülő listát (`<select>`).

Lehetséges kategóriák: Elektronika, Kiegészítők

* Készítsd el a legördülő listát a megfelelő `name` attribútummal (`kategoria`).
* Vedd fel opcióként (`<option>`) az adatbázisban szereplő kategóriákat.

## 4. Lépés: "Raktáron" szűrő

**Feladat:**
Hozz létre egy jelölőnégyzetet (`checkbox`), amivel a felhasználó jelezheti, hogy csak olyan terméket kér, ami van készleten. A paraméter neve: `keszleten`.

## 5. Lépés: A küldés gomb

Végül szükség van egy gombra, ami elindítja a folyamatot.

**Feladat:**
Helyezz el egy gombot az űrlap végén, ami elküldi (`submit`) az adatokat.

## Ellenőrzés és Tesztelés

Ha elkészültél, mentsd el a HTML fájlt és nyisd meg a böngészőben.

1.  Írj be egy nevet (pl. "kábel") -> Nyomd meg a gombot.
2.  Figyeld meg a böngésző címsorát (URL)! Ha jól dolgoztál és GET metódust használtál, valami ilyesmit kell látnod:
    `<szerver-címe>?nev=kabel&min_ar=&max_ar=&kategoria=...`
3.  Látod a paramétereket az URL-ben?
    * A `name` attribútumok (nev, min_ar) lettek a kulcsok?
    * Az általad beírt értékek lettek az értékek?
4.  Ha pipálod a készletet, megjelenik az URL végén, hogy `&keszleten=on`?

## Bónusz gondolkodnivaló

Próbáld ki, hogy átírod a `<form>`-ban a `method="GET"`-et `method="POST"`-ra.
* Frissítsd az oldalt és küldd el újra az űrlapot.
* Mi változott az URL-ben?

A szerver úgy van megírva, hogy kezelje a POST kéréseket is. :)