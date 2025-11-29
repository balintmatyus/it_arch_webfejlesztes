# Gyakorló Feladat: Felhasználók Kezelése (AJAX)

## A feladat célja

Készíts egy egyszerű webalkalmazást, amely:
1. Lekéri a felhasználókat a JSONPlaceholder API-ról
2. Megjeleníti őket egy listában
3. Lehetővé teszi új felhasználó hozzáadását

---

## Előkészületek

**API végpont:** `https://jsonplaceholder.typicode.com/users`

Egy felhasználó objektum struktúrája:
```javascript
{
    id: 1,
    name: "Leanne Graham",
    email: "Sincere@april.biz",
    phone: "1-770-736-8031"
}
```

> [!NOTE]
> A JSONPlaceholder egy teszt API – a POST kérés "működik" (visszaad egy választ), de valójában nem ment az adatbázisba.

---

## 1. lépés: HTML struktúra

Hozz létre egy `index.html` fájlt az alábbi elemekkel:

- [ ] Egy `<header>` a cím számára (pl. "👥 Felhasználók")
- [ ] Egy `<form>` három beviteli mezővel:
  - Név (`type="text"`)
  - Email (`type="email"`)
  - Telefon (`type="text"`)
  - Küldés gomb
- [ ] Egy `<div>` a státusz üzenetek megjelenítésére (`id="status"`)
- [ ] Egy `<ul>` a felhasználók listájának (`id="user-list"`)

**Tipp:** Használd a tananyagban látott Todo alkalmazás HTML struktúráját mintaként!

---

## 2. lépés: CSS stílusok

Adj hozzá alapvető stílusokat:

- [ ] A `.container` legyen középre igazítva, fehér háttérrel
- [ ] A form mezői legyenek egymás alatt, megfelelő padding-gel
- [ ] A státusz div háttérszíne változzon a típus szerint:
  - `.loading` – kékes háttér
  - `.error` – pirosas háttér  
  - `.success` – zöldes háttér
- [ ] A lista elemek legyenek kártyaszerűek, elválasztó vonallal

---

## 3. lépés: JavaScript – Változók és segédfüggvények

Hozd létre a szükséges változókat és segédfüggvényeket:

- [ ] Mentsd el az API URL-t egy konstansba
- [ ] Szerezd meg a DOM elemek referenciáit:
  - A lista (`#user-list`)
  - A státusz div (`#status`)
  - Az űrlap és a beviteli mezők
- [ ] Írj egy `showStatus(message, type)` függvényt, ami:
  - Beállítja a státusz div szövegét
  - Beállítja a megfelelő CSS osztályt
- [ ] Írj egy `createUserHTML(user)` függvényt, ami:
  - Kap egy user objektumot
  - Visszaad egy HTML stringet (pl. `<li>...</li>`)
  - Jelenítse meg a nevet, emailt és telefont

---

## 4. lépés: GET kérés – Felhasználók betöltése

Írj egy `async function loadUsers()` függvényt:

- [ ] Jelenítsd meg a "Betöltés..." státuszt
- [ ] Használj `try/catch` blokkot
- [ ] A `try` ágban:
  - Küldj GET kérést a `/users` végpontra (használd a `?_limit=5` paramétert)
  - Várd meg a választ (`await`)
  - Alakítsd JSON-né (`await response.json()`)
  - Járd végig a kapott tömböt
  - Minden elemhez generálj HTML-t a segédfüggvénnyel
  - Illeszd be a listába
  - Jelenítsd meg a sikeres státuszt
- [ ] A `catch` ágban:
  - Írd ki a hibát a konzolra
  - Jelenítsd meg a hiba státuszt
- [ ] Hívd meg a függvényt az oldal betöltésekor

**Ellenőrzés:** Nyisd meg az oldalt böngészőben – látnod kell 5 felhasználót!

---

## 5. lépés: POST kérés – Új felhasználó hozzáadása

Írj egy `async function addUser(name, email, phone)` függvényt:

- [ ] Jelenítsd meg a "Mentés..." státuszt
- [ ] Használj `try/catch` blokkot
- [ ] A `try` ágban:
  - Küldj POST kérést az API-ra
  - Állítsd be a `method`-ot "POST"-ra
  - Állítsd be a `headers`-ben a `Content-Type`-ot
  - A `body`-ban küldd el az adatokat `JSON.stringify()`-jal
  - Várd meg és dolgozd fel a választ
  - Add hozzá az új felhasználót a lista **elejére**
  - Ürítsd ki az űrlap mezőit
  - Jelenítsd meg a sikeres státuszt
- [ ] A `catch` ágban kezeld a hibát

---

## 6. lépés: Űrlap eseménykezelő

Kösd össze az űrlapot a POST függvénnyel:

- [ ] Adj hozzá `submit` eseménykezelőt az űrlaphoz
- [ ] Akadályozd meg az oldal újratöltését (`event.preventDefault()`)
- [ ] Olvasd ki a beviteli mezők értékeit
- [ ] Ellenőrizd, hogy a név mező nem üres-e
  - Ha üres, jelenítsd meg a hibaüzenetet és állj meg (`return`)
- [ ] Hívd meg az `addUser()` függvényt a megfelelő paraméterekkel

---

## 7. lépés: Tesztelés

Ellenőrizd az alkalmazás működését:

- [ ] Az oldal betöltésekor megjelennek a felhasználók?
- [ ] A "Betöltés..." üzenet látszik rövid ideig?
- [ ] Új felhasználó hozzáadása működik?
- [ ] Az új felhasználó a lista elején jelenik meg?
- [ ] Üres név esetén hibaüzenet jelenik meg?
- [ ] Az űrlap kiürül sikeres hozzáadás után?
- [ ] A konzolban nincsenek hibák?

---

## Bónusz feladatok (opcionális)

Ha elkészültél, próbáld ki ezeket:

1. **Validáció bővítése:** Ellenőrizd, hogy az email mező tartalmaz-e `@` karaktert!

2. **Törlés gomb:** Adj hozzá minden felhasználóhoz egy törlés gombot, ami eltávolítja az elemet a listából (csak a DOM-ból, API hívás nélkül)!

3. **Keresés:** Adj hozzá egy kereső mezőt, ami szűri a megjelenített felhasználókat név alapján!

---

## Segítség, ha elakadtál

**GET kérés alapstruktúra:**
```javascript
async function loadData() {
    try {
        const response = await fetch(/* URL ide */);
        const data = await response.json();
        // feldolgozás...
    } catch (error) {
        // hibakezelés...
    }
}
```

**POST kérés alapstruktúra:**
```javascript
async function sendData() {
    try {
        const response = await fetch(/* URL */, {
            method: /* ??? */,
            headers: {
                /* ??? */
            },
            body: /* ??? */
        });
        const result = await response.json();
        // feldolgozás...
    } catch (error) {
        // hibakezelés...
    }
}
```

**Elem hozzáadása a lista elejére:**
```javascript
lista.insertAdjacentHTML("afterbegin", html);
```