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

# **Felhasználói felület tervezése**
## 3. előadás

Gazdaságinformatikus BSc
2025/2026/1. félév

---

## Agenda

- 🎨 **Design alapok**
- 📝 **CSS alapjai**  
- 🔤 **Szövegformázás**

---

# **1. rész**
## Mi a design?

---

## Design ≠ Honlapszerkesztés

<div class="columns">
<div>

### **Honlapszerkesztés**
- Folyamat
- Programozási nyelvek
- Technikai megvalósítás

</div>
<div>

### **Webdesign**
- Végtermék
- Vizuális koncepció
- Felhasználói élmény

</div>
</div>

---

## Design jelentése

- **Esztétika** + **Funkció**
- Terv, koncepció, minta
- Harmónia és egyensúly
- Előrelátó teremtés

> 💡 **"A design a mindennapi munkánk része"**

---

## Weboldal értéke

### **Miért fontos?**
- 🏢 Cég imázs növelése
- 🌍 Regionális láthatóság
- 📈 Piacbővítés
- ⏰ 24 órás reklámhordozó

---

## Honlap készítés lépései

1. **Gyűjtés** → Tartalom, képek, linkek
2. **Előkészítés** → Digitalizálás, szövegek
3. **Tervezés** → Logikai felépítés
4. **Stílusok** → Színvilág, tipográfia
5. **Programozás** → Implementáció

---

# **2. rész**
## CSS alapjai

---

## Mi az a CSS?

**C**ascading **S**tyle **S**heets

- **1994** → Hakon Wium Lie
- **W3C** + **Microsoft** támogatás
- **Moduláris** fejlődés (flexbox, grid)

---

## CSS anatómia

```css
h1 {
  color: red;
  font-size: 24px;
}
```

**Szelektor** → `h1`
**Deklaráció** → `color: red;`
- **Tulajdonság** → `color`
- **Érték** → `red`

---

## CSS beágyazási módok

### **3 lehetőség**

1. 🏷️ **Inline** → `style` attribútum
2. 📄 **Belső** → `<style>` tag
3. 📁 **Külső** → `.css` fájl

---

## 1. Belső stíluslap

```html
<head>
  <style>
    h1 { 
      color: darkgreen; 
      font-size: 32px;
    }
  </style>
</head>
```

### ✅ Egyszerű, gyors
### ❌ Csak egy oldalra

---

## 2. Külső stíluslap

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

### ✅ Újrahasznosítható
### ✅ Cache-elhető
### ✅ Tiszta kód

---

## 3. Inline CSS

```html
<h1 style="color: red;">Címsor</h1>
```

### ⚠️ **Kerülendő!**
- ❌ Rossz karbantarthatóság
- ❌ Nem újrahasznosítható
- ❌ HTML "szennyezés"

---

# **3. rész**
## Szövegformázás

---

## Tipográfia a weben

### **Speciális tulajdonságok**
- Dinamikus tartalom
- Többdimenziós szerkezet
- Technikai korlátok
- Képernyő vs. papír

---

## Olvasási fixáció

### **Szemünk működése**

$v=\frac{(s-\delta)}{t_{f_{x}}}$ [betű/sec]

- **12-20 betű** / fixáció
- **25 betű** / másodperc
- Tartományok feldolgozása

---

## Betűtípusok

<div class="columns">
<div>

### **Serif** 
- Klasszikus
- Elegáns
- Nyomtatott

</div>
<div>

### **Sans-serif**
- Modern
- Tiszta
- Képernyőre optimális

</div>
</div>

---

## Szövegszervezési szabályok

### ⚠️ **Kerülendő**
- ❌ Túl sok betűtípus
- ❌ CSUPA NAGYBETŰ
- ❌ Túl sok félkövér

### ✅ **Ajánlott**
- Rövid mondatok
- Egyszerű nyelvezet
- Fixációs tartományok

---

## Betűtípus beállítások

### **1. Rendszer betűk**
```css
font-family: Arial, Helvetica, sans-serif;
```

### **2. Google Fonts**
```html
<link href="--fonts.googleapis.com/..." rel="stylesheet">
```

### **3. Saját betűk**
```css
@font-face { ... }
```

---

## Szöveg tulajdonságok

| Tulajdonság | Példa |
|:--- |:--- |
| `font-size` | `16px`, `1.2rem` |
| `font-weight` | `normal`, `bold`, `700` |
| `color` | `#333`, `rgb(51,51,51)` |
| `text-align` | `left`, `center`, `justify` |
| `line-height` | `1.5`, `24px` |

---

## Mértékegységek

### **Abszolút**
- `px` → Pixel (fix)
- `pt` → Point (nyomtatás)

### **Relatív**
- `rem` → Root elem (ajánlott!)
- `em` → Szülő elem
- `%` → Százalék
- `vw/vh` → Viewport

---

## Mikor mit használjunk?

| Egység | Használat |
|:--- |:--- |
| **`rem`** | Betűméret, térközök |
| **`px`** | Szegélyek, árnyékok |
| **`%`** | Rugalmas layoutok |
| **`vw/vh`** | Hero szekciók |

---

## Összefoglalás

### **Ma megtanultuk:**
- 🎨 Design alapelvek
- 📝 CSS beágyazási módok
- 🔤 Tipográfia a weben