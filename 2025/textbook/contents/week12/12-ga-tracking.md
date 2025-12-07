# Google Analytics regisztráció és követőkódok

## Bevezetés

Ez az anyag a Google Analytics használatának első lépéseit mutatja be:
- Hogyan hozzunk létre Google Analytics fiókot
- Hogyan állítsunk be tulajdont
- Hogyan nyerjük ki és illesszük be a követőkódot
- Hogyan ellenőrizzük, hogy az adatgyűjtés működik

---

# 1. Előkészületek

A Google Analytics használatához szükséges:

- **Meglévő Google-fiók**
- Belépés: [https://analytics.google.com](https://analytics.google.com)
- Fontos: Google-fiókonként maximum **100 Analytics-fiók** hozható létre

Első lépés: kattintsunk a **Mérés indítása** gombra.

---

# 2. Analytics-fiók létrehozása

1. **Fiók név megadása**
- Célszerű cégnév vagy projekt neve

2. **Adatmegosztási beállítások kiválasztása**
- Opcionális, de érdemes elfogadni pl. *Hozzájárulások modellezése és üzleti statisztikák*

3. Kattintsunk a **Tovább** gombra

---

# 3. Tulajdon létrehozása

## Tulajdon alapadatok

- Tulajdon neve (pl. weboldal neve)
- Ország: **Magyarország**
- Időzóna: **Magyar idő**
- Pénznem: **Magyar forint (HUF)**

>[!WARNING]
A *Universal Analytics* tulajdon 2023. július 1. óta nem gyűjt adatokat. Csak GA4 tulajdont tudsz használni!

---

## Vállalkozás adatai

- Iparági besorolás
- Vállalatméret (lehet fiktív is)
- Következő gomb

---

## Üzleti célok

- Választható opciók, pl. Alapjelentések
- Kezdőknek javasolt az **Alapjelentések** választása
- Létrehozás gomb

>[!TASK]
Próbáld ki: állítsd be a saját üzleti céljaidat, majd nézd meg, hogyan változnak a jelentések az Analytics felületén!

---

## GDPR és szerződési feltételek

- Magyar GDPR elfogadása kötelező
- Ha adatmegosztásra is engedélyt adtunk (pl. Google-termékekkel), további feltételek jóváhagyása szükséges

---

# 4. Követőkód kinyerése

A követőkód beállítása után lesz mérhető a weboldal forgalma.

### Hozzáférés a kódhoz

1. Adminisztrálás fül

2. Tulajdonbeállítások

3. **Adatgyűjtés és -módosítás → Adatfolyamok**

---

## Platform kiválasztása

- Válasszuk ki a platformot: **Web**
- Mobil applikáció esetén iOS vagy Android is elérhető

---

## Adatfolyam létrehozása

- Weboldal **URL-címe** (pl. https://sajatoldal.hu)
- Adatfolyam neve (pl. Főoldal mérés)
- Ezután az adatfolyam létrejön

>[!TIP]
GitHub Pages oldalhoz is beállítható.

---

## Címke utasítások

- Ha nem nyílik meg automatikusan a telepítési ablak, kattintsunk a **Címke utasítások megjelenítése** gombra
- Két fő lehetőség:
    - **Támogatott webhelykészítő** (pl. WordPress, Wix)
    - **Kézi telepítés** → HTML-kód beillesztése

---

# 5. Követőkód telepítése

## Kézi telepítés

- Másoljuk ki a kapott kódot
- Illesszük be a weboldalunk `<head>` nyitótagja után

```html
<head>
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-XXXXXXXXXX');
    </script>
</head>
```

> [!TASK]
Próbáld ki: illeszd be a fenti kódot egy egyszerű HTML-oldaladba, majd nézd meg a Valós idejű riportot az Analytics-ben!

## Sikeres beállítás

- Ha mindent jól csináltunk:
    - 1–2 percen belül megjelennek az első látogatási adatok
    - Ellenőrizhető a **Valós idejű jelentések** menüpontban

 ---