# AJAX és a Fetch API – Szerverkommunikáció JavaScriptben

## Bevezetés: Miért van erre szükség?

Az előző leckében megtanultuk, hogyan küldjük el az űrlapokat a szerverre. De mi történik ilyenkor? **Az egész oldal újratöltődik!** 

Gondolj arra, amikor a Facebookon görgetés közben új posztok jelennek meg, vagy amikor a Google már gépelés közben javaslatokat mutat. Ezek a funkciók nem töltik újra az oldalt – ez az **AJAX** lényege.

### Mi az AJAX?

Az AJAX (Asynchronous JavaScript and XML) egy **megközelítés**, ami lehetővé teszi adatok küldését és fogadását a háttérben:

* **Asynchronous (Aszinkron):** A kérés a háttérben fut, nem blokkolja az oldalt.
* **JavaScript:** A böngészőben futó kód küldi és fogadja az adatokat.
* **JSON:** Az adatformátum, amiben a szerver válaszol (régen XML volt, ma JSON).

## A `fetch()` API

A modern JavaScriptben a **`fetch()` függvényt** használjuk szerverkommunikációra, az **`async/await`** szintaxissal.

### Alapszintaxis

```javascript
async function adatokLetoltese() {
    try {
        const response = await fetch(url);    // Várunk a szerver válaszára
        const data = await response.json();   // JSON-né alakítjuk
        console.log(data);                    // Feldolgozzuk az adatokat
    } catch (error) {
        console.error("Hiba:", error);        // Hiba esetén ide kerül
    }
}
```

### Hogyan működik?

1. **`async function`** – Jelzi, hogy a függvény aszinkron műveleteket tartalmaz.
2. **`await fetch(url)`** – Elindít egy kérést és **megvárja** a választ.
3. **`await response.json()`** – A szerver válaszát JSON-né alakítja.
4. **`try/catch`** – Hiba esetén (pl. nincs internet) a `catch` ágba kerül.

## A JSONPlaceholder API

A gyakorlathoz a **JSONPlaceholder** API-t használjuk – ez egy ingyenes, nyilvános "teszt szerver", ami hamis adatokat ad vissza.

**Alap URL:** `https://jsonplaceholder.typicode.com`

| Végpont | Mit ad vissza? |
| :--- | :--- |
| `/todos` | Teendők listája |
| `/posts` | Blog bejegyzések |
| `/users` | Felhasználók |

> [!NOTE]
> A JSONPlaceholder egy **szimulált** API. A POST kérések "működnek" (visszaadják a várt választ), de nem módosítják ténylegesen az adatbázist. Ez tökéletes tanuláshoz!

---

## Gyakorlat: Todo Alkalmazás

Építsünk egy egyszerű teendő-listát, ami:
1. Betölti a teendőket a szerverről (GET)
2. Új teendőt küld a szerverre (POST)

### 1. lépés: HTML váz

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo App</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f0f0f0;
            padding: 40px 20px;
            margin: 0;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        header {
            background: #5a67d8;
            color: white;
            padding: 20px;
            text-align: center;
        }

        header h1 {
            margin: 0;
            font-size: 1.5em;
        }

        /* Űrlap stílusok */
        .add-form {
            padding: 15px;
            background: #f7f7f7;
            display: flex;
            gap: 10px;
        }

        .add-form input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 14px;
        }

        .add-form button {
            padding: 10px 20px;
            background: #48bb78;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
        }

        .add-form button:hover {
            background: #38a169;
        }

        /* Státusz üzenet */
        #status {
            padding: 10px;
            text-align: center;
            font-size: 14px;
        }

        #status.loading { background: #e6f3ff; color: #0066cc; }
        #status.error { background: #ffe6e6; color: #cc0000; }
        #status.success { background: #e6ffe6; color: #006600; }

        /* Lista stílusok */
        #todo-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .todo-item {
            padding: 12px 15px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .todo-item:last-child {
            border-bottom: none;
        }

        .todo-id {
            background: #eee;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 12px;
            color: #666;
        }

        .todo-title {
            flex: 1;
        }

        .todo-status {
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 4px;
        }

        .todo-status.done {
            background: #e6ffe6;
            color: #006600;
        }

        .todo-status.pending {
            background: #fff3e6;
            color: #cc6600;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>📝 Todo Lista</h1>
    </header>

    <!-- Új teendő űrlap -->
    <form class="add-form" id="add-form">
        <input type="text" id="new-todo" placeholder="Új teendő..." required>
        <button type="submit">Hozzáad</button>
    </form>

    <!-- Státusz jelző -->
    <div id="status"></div>

    <!-- Teendők listája -->
    <ul id="todo-list">
        <!-- IDE KERÜLNEK A TEENDŐK -->
    </ul>
</div>

<script>
    // A JavaScript kód ide kerül
</script>

</body>
</html>
```

---

### 2. lépés: Adatok lekérése (GET)

Kérjük le a teendőket a szerverről és jelenítsük meg őket!

```javascript
// API cím
const API_URL = "https://jsonplaceholder.typicode.com/todos";

// DOM elemek
const todoList = document.getElementById("todo-list");
const statusDiv = document.getElementById("status");

// Státusz üzenet megjelenítése
function showStatus(message, type) {
    statusDiv.textContent = message;
    statusDiv.className = type;
}

// Egy teendő HTML-jének létrehozása
function createTodoHTML(todo) {
    const statusClass = todo.completed ? "done" : "pending";
    const statusText = todo.completed ? "Kész" : "Folyamatban";
    
    return `
        <li class="todo-item">
            <span class="todo-id">#${todo.id}</span>
            <span class="todo-title">${todo.title}</span>
            <span class="todo-status ${statusClass}">${statusText}</span>
        </li>
    `;
}

// Teendők betöltése a szerverről
async function loadTodos() {
    showStatus("⏳ Betöltés...", "loading");

    try {
        const response = await fetch(API_URL + "?_limit=10");
        const todos = await response.json();
        
        // Sikerült! Megjelenítjük a teendőket
        let html = "";
        
        for (let i = 0; i < todos.length; i++) {
            html += createTodoHTML(todos[i]);
        }
        
        todoList.innerHTML = html;
        showStatus("✅ Betöltve!", "success");
        
    } catch (error) {
        // Hiba történt
        console.error("Hiba:", error);
        showStatus("❌ Nem sikerült betölteni!", "error");
    }
}

// Indítás
loadTodos();
```

#### Mi történik itt?

1. `await fetch(API_URL + "?_limit=10")` – Kérést küldünk, max 10 elemet kérünk.
2. `await response.json()` – A választ JSON-né alakítjuk.
3. `for` ciklussal végigmegyünk a teendőkön és HTML-t készítünk.
4. `todoList.innerHTML = html` – Beillesztjük a listába.

---

### 3. lépés: Új teendő küldése (POST)

Most tegyük lehetővé új teendők hozzáadását!

```javascript
// Űrlap elemek
const addForm = document.getElementById("add-form");
const newTodoInput = document.getElementById("new-todo");

// Új teendő küldése a szerverre
async function addTodo(title) {
    showStatus("⏳ Mentés...", "loading");

    try {
        const response = await fetch(API_URL, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                title: title,
                completed: false,
                userId: 1
            })
        });
        
        const newTodo = await response.json();
        
        // Sikerült! Hozzáadjuk a listához
        console.log("Szerver válasza:", newTodo);
        
        const html = createTodoHTML(newTodo);
        todoList.insertAdjacentHTML("afterbegin", html);
        
        newTodoInput.value = "";  // Űrlap ürítése
        showStatus("✅ Hozzáadva!", "success");
        
    } catch (error) {
        console.error("Hiba:", error);
        showStatus("❌ Nem sikerült menteni!", "error");
    }
}

// Űrlap beküldése
addForm.addEventListener("submit", function(event) {
    event.preventDefault();  // Ne töltse újra az oldalt!
    
    const title = newTodoInput.value.trim();
    
    if (title === "") {
        showStatus("⚠️ Írj be valamit!", "error");
        return;
    }
    
    addTodo(title);
});
```

#### A POST kérés felépítése

```javascript
const response = await fetch(url, {
    method: "POST",                    // HTTP metódus
    headers: {
        "Content-Type": "application/json"  // JSON-t küldünk
    },
    body: JSON.stringify({             // Az adat JSON stringként
        title: "Bevásárlás",
        completed: false
    })
});
```

> [!WARNING]
> A `body`-ban **mindig** `JSON.stringify()`-t kell használni! A `fetch()` nem tudja automatikusan átalakítani az objektumot.

---

## A teljes kód

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo App</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            background: #f0f0f0;
            padding: 40px 20px;
            margin: 0;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        header {
            background: #5a67d8;
            color: white;
            padding: 20px;
            text-align: center;
        }

        header h1 {
            margin: 0;
            font-size: 1.5em;
        }

        .add-form {
            padding: 15px;
            background: #f7f7f7;
            display: flex;
            gap: 10px;
        }

        .add-form input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 14px;
        }

        .add-form button {
            padding: 10px 20px;
            background: #48bb78;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
        }

        .add-form button:hover {
            background: #38a169;
        }

        #status {
            padding: 10px;
            text-align: center;
            font-size: 14px;
        }

        #status.loading { background: #e6f3ff; color: #0066cc; }
        #status.error { background: #ffe6e6; color: #cc0000; }
        #status.success { background: #e6ffe6; color: #006600; }

        #todo-list {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .todo-item {
            padding: 12px 15px;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .todo-item:last-child {
            border-bottom: none;
        }

        .todo-id {
            background: #eee;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 12px;
            color: #666;
        }

        .todo-title {
            flex: 1;
        }

        .todo-status {
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 4px;
        }

        .todo-status.done {
            background: #e6ffe6;
            color: #006600;
        }

        .todo-status.pending {
            background: #fff3e6;
            color: #cc6600;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>📝 Todo Lista</h1>
    </header>

    <form class="add-form" id="add-form">
        <input type="text" id="new-todo" placeholder="Új teendő..." required>
        <button type="submit">Hozzáad</button>
    </form>

    <div id="status"></div>

    <ul id="todo-list"></ul>
</div>

<script>
// ==========================================
// GLOBÁLIS VÁLTOZÓK
// ==========================================
const API_URL = "https://jsonplaceholder.typicode.com/todos";

const todoList = document.getElementById("todo-list");
const statusDiv = document.getElementById("status");
const addForm = document.getElementById("add-form");
const newTodoInput = document.getElementById("new-todo");

// ==========================================
// SEGÉDFÜGGVÉNYEK
// ==========================================

function showStatus(message, type) {
    statusDiv.textContent = message;
    statusDiv.className = type;
}

function createTodoHTML(todo) {
    const statusClass = todo.completed ? "done" : "pending";
    const statusText = todo.completed ? "Kész" : "Folyamatban";
    
    return `
        <li class="todo-item">
            <span class="todo-id">#${todo.id}</span>
            <span class="todo-title">${todo.title}</span>
            <span class="todo-status ${statusClass}">${statusText}</span>
        </li>
    `;
}

// ==========================================
// GET - TEENDŐK BETÖLTÉSE
// ==========================================

async function loadTodos() {
    showStatus("⏳ Betöltés...", "loading");

    try {
        const response = await fetch(API_URL + "?_limit=10");
        const todos = await response.json();
        
        let html = "";
        for (let i = 0; i < todos.length; i++) {
            html += createTodoHTML(todos[i]);
        }
        
        todoList.innerHTML = html;
        showStatus("✅ Betöltve!", "success");
        
    } catch (error) {
        console.error("Hiba:", error);
        showStatus("❌ Nem sikerült betölteni!", "error");
    }
}

// ==========================================
// POST - ÚJ TEENDŐ HOZZÁADÁSA
// ==========================================

async function addTodo(title) {
    showStatus("⏳ Mentés...", "loading");

    try {
        const response = await fetch(API_URL, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify({
                title: title,
                completed: false,
                userId: 1
            })
        });
        
        const newTodo = await response.json();
        console.log("Szerver válasza:", newTodo);
        
        const html = createTodoHTML(newTodo);
        todoList.insertAdjacentHTML("afterbegin", html);
        
        newTodoInput.value = "";
        showStatus("✅ Hozzáadva!", "success");
        
    } catch (error) {
        console.error("Hiba:", error);
        showStatus("❌ Nem sikerült menteni!", "error");
    }
}

// ==========================================
// ESEMÉNYKEZELŐ
// ==========================================

addForm.addEventListener("submit", function(event) {
    event.preventDefault();
    
    const title = newTodoInput.value.trim();
    
    if (title === "") {
        showStatus("⚠️ Írj be valamit!", "error");
        return;
    }
    
    addTodo(title);
});

// ==========================================
// INDÍTÁS
// ==========================================

loadTodos();
</script>

</body>
</html>
```

---

## Összefoglaló

| Művelet | HTTP metódus | `fetch()` használat |
| :--- | :--- | :--- |
| Adatok lekérése | `GET` | `await fetch(url)` |
| Új adat küldése | `POST` | `await fetch(url, { method: "POST", body: ... })` |

### Az `async/await` működése

```
async function  →  await fetch(url)  →  await response.json()  →  feldolgozás
      ↓                  ↓                      ↓                     ↓
  Aszinkron fv.    Kérés + várakozás       JSON parse          Megjelenítés
```

### Fontos tudnivalók

1. **`async function`** – Jelzi, hogy a függvényben `await`-et használunk.
2. **`await`** – Megvárja, amíg a művelet befejeződik.
3. **`try/catch`** – Hibakezelés (pl. nincs internet).
4. **`event.preventDefault()`** – Megakadályozza az oldal újratöltését.
5. **`JSON.stringify()`** – Objektumot JSON stringgé alakít (POST-nál kötelező).

---

## Házi feladat

1. Módosítsd az alkalmazást úgy, hogy a `/posts` végpontot használja a `/todos` helyett!
2. Adj hozzá egy második input mezőt a post "body" tartalmának!
3. Jelenítsd meg a postok szerzőjét is (`userId`)!