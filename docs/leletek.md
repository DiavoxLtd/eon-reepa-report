# Leletek

A talált eltérések egységes, követhető formátumban — **severity** (hatás) és **priority** (sürgősség) szerint súlyozva, böngésző/nézet bontásban.

!!! info "1. teszt-kör — állapot"
    **Vizsgálva:** belépés → feltételek → kezdőoldal → **Céges adatok 1–2. lépés** (Szerződéses adatok, Céginformációk).
    **Böngésző:** Chromium ✅ · Firefox ✅ (vizuálisan konzisztens) · Edge = Chromium-motor · Safari (WebKit): folyamatban.
    **Nézet:** desktop (tablet/mobil + a 3–6. lépés + termelőegység: következő adag).

## Összefoglaló

| ID | Lelet | Severity | Priority |
|---|---|---|---|
| L-007 | HU→EN nyelvváltás nem fordít (a felület magyar marad) | <span class="sev-s1">S1</span> | <span class="prio-p1">P1</span> |
| L-002 | „KÁT-ba lépés ideje (ha releváns)" kötelezőként validál (opcionális helyett) | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-006 | Validációs hibaüzenet a nyers technikai mezőnevet írja ki | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-008 | „Helyrajzi szám" kötelező a teljes cím mellett (hrsz↔cím XOR hiányzik) | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-001 | A „Nem" alapérték nincs előre kiválasztva a toggle-öknél | <span class="sev-s3">S3</span> | <span class="prio-p2">P2</span> |
| L-009 | „Származási garancia számlaszáma" feleslegesen kötelező | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-012 | „Vissza & Mentés" gomb — a követelmény szerint a Vissza nem ment | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-011 | Duplikált „Számlaszám" mező a „Származási garancia számlaszáma" mellett | <span class="sev-s4">S4</span> | <span class="prio-p3">P3</span> |
| L-003 | Kitöltöttség-kör „%"-ot mutat „0%" helyett | <span class="sev-s4">S4</span> | <span class="prio-p3">P3</span> |
| L-004 | Szöveg-eltérés (feltételek↔kezdőoldal) + hiányzó vessző | <span class="sev-s4">S4</span> | <span class="prio-p3">P3</span> |
| L-010 | Dupla szóköz egyes mező-feliratokban | <span class="sev-s4">S4</span> | <span class="prio-p4">P4</span> |
| L-005 | Progress-jelző 15%-ot mutat üres űrlapnál | <span class="sev-s4">S4</span> | <span class="prio-p4">P4</span> |

## Kiemelt leletek (részletesen)

!!! danger "L-007 — A HU→EN nyelvváltás nem működik · <span class='sev-s1'>S1</span> <span class='prio-p1'>P1</span>"
    - **Miért fontos?** A követelmény kétnyelvű (HU/EN) űrlapot ír elő.
    - **Mit látunk?** A nyelvválasztót „EN"-re állítva a teljes felület **magyar marad** — cím, mezőnevek, gombok, hibaüzenetek egyaránt.
    - **Hogyan javítsuk?** Az angol fordítás (lokalizáció) biztosítása minden szöveges elemre.
    - **Forrás:** UKT (kétnyelvűség kötelező); reprodukálva az élő dev-en (desktop, Chromium).

!!! warning "L-002 — A „KÁT-ba lépés ideje (ha releváns)" kötelező · <span class='sev-s2'>S2</span> <span class='prio-p2'>P2</span>"
    - **Miért fontos?** Opcionális mezőt nem szabad kötelezőként kikényszeríteni — blokkolja a továbblépést.
    - **Mit látunk?** Üres „Tovább"-ra a validáció kimondja: *„A(z) „KÁT-ba lépés ideje (ha releváns)" mező kitöltése kötelező."*
    - **Hogyan javítsuk?** A mező kötelezőségének levétele (a „ha releváns" jelzésnek megfelelően).
    - **Forrás:** mező-validációs specifikáció (KÁT-ba lépés = nem kötelező).

!!! warning "L-006 — Hibaüzenet a nyers technikai mezőnevet mutatja · <span class='sev-s2'>S2</span> <span class='prio-p2'>P2</span>"
    - **Miért fontos?** A QA-elvárás szerint a hibaüzenetek legyenek beszédesek és érthetők.
    - **Mit látunk?** A toggle-mezőknél a hibaüzenet a belső azonosítót írja ki (pl. *„system_level_service" mező kitöltése kötelező*) a magyar felirat helyett.
    - **Hogyan javítsuk?** A felhasználóbarát mezőnév (label) használata a hibaüzenetekben.
    - **Forrás:** élő dev (1. lépés validáció).

!!! warning "L-008 — A „Helyrajzi szám" kötelező a teljes cím mellett · <span class='sev-s2'>S2</span> <span class='prio-p2'>P2</span>"
    - **Miért fontos?** Üzleti szabály: **vagy** helyrajzi szám, **vagy** címadatok adandók meg (XOR), nem mindkettő kötelezően.
    - **Mit látunk?** A 2. lépésben minden cím-mező (irányítószám, település, közterület, házszám) **és** a helyrajzi szám is kötelező.
    - **Hogyan javítsuk?** A „hrsz vagy cím" feltételes kötelezőség implementálása.
    - **Forrás:** mező-validációs specifikáció (hrsz XOR cím).

## ✅ Megerősített megfelelőség (a korábban feltételezett hibák az implementációban rendben)

A korábbi terv-/specifikáció-alapú feltételezések egy részét az élő teszt **cáfolta** — ezek a pontok rendben:

- **Dátum-formátum helyes** (`éééé-hh-nn`, magyar) — nem amerikai formátum.
- **Cégforma = legördülő lista**, **Cégbejegyzés országa** helyes felirattal + alapérték „Magyarország".
- **Cégbejegyzés dátuma** mező megvan (dátumválasztó).
- **Mező-feliratok megjelennek** (nem csak rákattintáskor); a kliensoldali validáció helyesen blokkol.
- **Cross-browser:** Chromium ↔ Firefox vizuálisan konzisztens.

!!! warning "Bizalmas leletek"
    A biztonsági és egyéb érzékeny jellegű megállapítások nem ebben a publikus riportban, hanem külön, bizalmas csatornán kerülnek átadásra.
