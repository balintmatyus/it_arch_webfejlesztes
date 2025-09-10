---
marp: true
theme: uncover
paginate: true
backgroundColor: #f8f9fa
color: #212529
style: |
  section {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  }
  h1 {
    color: #0066cc;
    font-size: 2em;
    font-weight: 600;
  }
  h2 {
    color: #333;
    font-size: 1.5em;
    border-bottom: 2px solid #0066cc;
    padding-bottom: 0.3em;
  }
  code {
    background-color: #f4f4f4;
    border-radius: 4px;
    padding: 2px 6px;
  }
  blockquote {
    border-left: 4px solid #0066cc;
    padding-left: 1em;
    color: #666;
  }
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2em;
  }
  ul {
    text-align: left;
  }
  strong {
    color: #0066cc;
  }
---

# **Informatika és IT architektúra alapjai**
## 1. előadás

Gazdaságinformatikus BSc
2025/2026/1. félév

---

## Agenda

- 🌐 **Internet és WWW**
- 🔄 **Kliens-szerver architektúra**  
- 🏗️ **Full-stack fejlesztés**
- 📝 **HTML5 alapok**
- ✅ **Websztenderdek és validáció**

---

# **1. rész**
## Hogyan működik a web?

---

## 🤔 Nyitókérdés

> **Mi a különbség az Internet és a World Wide Web között?**

---

## Internet vs. WWW

<div class="columns">
<div>

### **Internet**
- Fizikai infrastruktúra
- "Hálózatok hálózata"
- Kábelek, routerek, szerverek
- TCP/IP protokoll

</div>
<div>

### **WWW**
- Információs rendszer
- Az Interneten fut
- HTML, URL, HTTP
- Tim Berners-Lee (1989)

</div>
</div>

---

## Fejlődési mérföldkövek

**1969** → ARPANET (4 egyetem)
**1983** → TCP/IP protokoll
**1989** → WWW megszületése
**1993** → Mosaic böngésző
**2000+** → Web 2.0 korszak

---

## TCP/IP protokoll

### **Postai analógia**

- **TCP** = Gondos postai ügyintéző
  - Szétszedi a könyvet lapokra
  - Megszámozza őket
  - Ellenőrzi a kézbesítést

- **IP** = Postás
  - Címzés (IP-címek)
  - Útvonalválasztás

---

## Kliens-szerver modell

**Kliens**: Kérelmező (böngésző, app)
**Szerver**: Kiszolgáló (adatok, logika)

### Előnyök
- Központosított menedzsment
- Skálázhatóság
- Erőforrás-megosztás

---

## 🎯 Közös feladat

**Rajzoljuk fel együtt egy weboldal betöltődésének folyamatát!**

Főbb lépések:
1. URL beírása
2. DNS lekérdezés
3. TCP kapcsolat
4. HTTP kérés/válasz
5. Renderelés

---

## Egy oldal betöltődése

1. **DNS feloldás** → `https://www.uni-corvinus.hu` → `146.110.3.100`
2. **TCP handshake** → Kapcsolat létrehozása
3. **HTTP kérés** → `GET / HTTP/1.1`
4. **Szerver feldolgozás** → HTML generálás
5. **HTTP válasz** → `200 OK` + HTML
6. **Renderelés** → Vizuális megjelenítés

---

## HTTPS és biztonság

### 🔒 **Titkosítás**
SSL/TLS protokoll

### ✅ **Integritás**
Adatok sértetlensége

### 🏢 **Hitelesítés**
Tanúsítványok

---

# **2. rész**
## Full-stack fejlesztés

---

## A modern webalkalmazás anatómiája

**Frontend** (kliens oldal)
↕️
**Backend** (szerver oldal)
↕️
**Adatbázis**

---

## Frontend hármasság

### 🏗️ **HTML** = Struktúra
A ház váza és falai

### 🎨 **CSS** = Stílus
Festék, tapéta, díszítés

### ⚡ **JavaScript** = Viselkedés
Elektromos hálózat, kapcsolók

---

## Szemléltető példa

```html
<button>Kattints!</button>  <!-- HTML -->
```

```css
button { color: blue; }      /* CSS */
```

```javascript
button.onclick = () => {...} // JS
```

---

## Separation of Concerns

### **Miért válasszuk szét?**
- ✅ Karbantarthatóság
- ✅ Csapatmunka
- ✅ Újrahasznosíthatóság
- ✅ Skálázhatóság

---

## Backend felelősségek

- **Üzleti logika** végrehajtása
- **Adatbázis** interakciók
- **Hitelesítés** és biztonság
- **API** szolgáltatás

> ⚠️ **Kritikus műveletek mindig a szerveren!**

---

# **3. rész**
## HTML5 alapok

---

## Mi az a HTML?

**H**yper**T**ext **M**arkup **L**anguage

- Nem programozási nyelv!
- Jelölőnyelv (markup)
- Struktúra leírása
- `.html` fájlok

---

## HTML elemek anatómiája

```html
<p class="kiemelt">Tartalom</p>
```

- **Nyitó tag**: ``<p>``
- **Attribútum**: ``class="kiemelt"``
- **Tartalom**: ``Tartalom``
- **Záró tag**: ``</p>``

---

## 💻 Gyakorlat

**Írjuk meg együtt az első HTML oldalunkat!**

```html
<!DOCTYPE html>
<html lang="hu">
<head>
    <meta charset="UTF-8">
    <title>Első oldalam</title>
</head>
<body>
    <h1>Hello World!</h1>
</body>
</html>
```

---

## Dokumentum struktúra

- ``<!DOCTYPE html>`` → HTML5 deklaráció
- ``<html>`` → Gyökérelem
- ``<head>`` → Meta információk
- ``<body>`` → Látható tartalom

---

## Szemantikus címsorok

``<h1>`` **Főcím** (csak 1 oldalanként!)
``<h2>`` Alcím
``<h3>`` Al-alcím
...
``<h6>`` Legalsó szint

### ⚠️ Hierarchia fontossága!
SEO + Akadálymentesség

---

## Szövegformázás

### **Szemantikus kiemelés**
- ``<strong>`` → Fontos
- ``<em>`` → Hangsúlyos

### **Vizuális formázás** (kerülendő)
- ``<b>`` → Félkövér
- ``<i>`` → Dőlt

---

## Listák típusai

<div class="columns">
<div>

### **Rendezett**
```html
<ol>
  <li>Első</li>
  <li>Második</li>
</ol>
```

</div>
<div>

### **Rendezetlen**
```html
<ul>
  <li>Alma</li>
  <li>Körte</li>
</ul>
```

</div>
</div>

---

## Képek beágyazása

```html
<img src="kep.jpg" 
     alt="Leíró szöveg"
     width="400" 
     height="300">
```

### 📌 **Alt attribútum kötelező!**
Akadálymentesség + SEO

---

## Linkek létrehozása

```html
<a href="https://example.com">Külső link</a>
<a href="about.html">Belső link</a>
<a href="#section1">Ugrás részhez</a>
```

### 💡 **Tipp**: Kerüld a "Kattints ide!" szöveget

---

# **5. rész**
## Websztenderdek és validáció

---

## Ki dönt a szabályokról?

### **W3C**
World Wide Web Consortium
Tim Berners-Lee alapította

### **WHATWG**
Böngészőgyártók csoportja
"Living Standard" modell

---

## Miért fontos a validáció?

- ✅ **Böngésző-kompatibilitás**
- ✅ **SEO optimalizálás**
- ✅ **Akadálymentesség**
- ✅ **Hibák korai észlelése**

---

## HTML Validátor

### 🔧 **W3C Validator**
[validator.w3.org](https://validator.w3.org)

**Használati módok:**
1. URL megadása
2. Fájl feltöltése
3. Kód bemásolása

---

## 🏆 Gyakorlati feladat

**Találjuk meg a hibákat!**

```html
<!DOCTYPE html>
<html>
<head>
    <title>Teszt oldal
</head>
<body>
    <h1>Címsor
    <p>Bekezdés <b>félkövér<i> dőlt</b></i>
</body>
</html>
```

---

## Tipikus validációs hibák

1. ❌ Hiányzó záró tagek
2. ❌ Rossz beágyazási sorrend
3. ❌ Hiányzó kötelező attribútumok
4. ❌ Érvénytelen attribútum értékek
5. ❌ Duplikált ID-k

---

## Összefoglalás

### **Ma megtanultuk:**
- 🌐 Internet vs. WWW különbség
- 🔄 Kliens-szerver kommunikáció
- 🏗️ Frontend/Backend szerepek
- 📝 HTML5 alapok
- ✅ Validáció fontossága

---

## Gyakorlat

Telepítsd fel a VS Code-ot a saját számítógépedre, ha azon szeretnél dolgozni.

## Következő előadás

GitHub fiók regisztrálása (https://www.github.com) és Git telepítése (https://git-scm.com/downloads)