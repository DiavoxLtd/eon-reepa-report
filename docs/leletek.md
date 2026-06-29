# Leletek

A talált eltérések egységes, követhető formátumban — **severity** (hatás) és **priority** (sürgősség) szerint súlyozva.

!!! success "1. teszt-kör — lezárva"
    **Vizsgálva:** a **teljes űrlap** — belépés → feltételek → kezdőoldal → **Céges adatok (1–6. lépés)** → **Termelőegység-ág** (Naperőmű · Szélerőmű · Energiatároló · Egyéb).
    **Böngésző:** Chromium ✅ · Firefox ✅ · Edge (Chromium-motor) ✅ · Safari: külön (következő kör).
    **Nézet:** desktop + **mobil** (390 px — nincs vízszintes túlcsordulás, kitölthető).
    **Eredmény: 19 lelet** + jelentős megerősített megfelelőség.

## Összefoglaló

| ID | Lelet | Sev | Prio |
|---|---|---|---|
| L-007 | HU→EN nyelvváltás nem fordít (a felület magyar marad) | <span class="sev-s1">S1</span> | <span class="prio-p1">P1</span> |
| L-002 | „KÁT-ba lépés ideje (ha releváns)" kötelezőként validál | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-006 | Validációs hibaüzenet a nyers technikai mezőnevet írja ki | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-008 | „Helyrajzi szám" kötelező a teljes cím mellett (hrsz↔cím XOR hiányzik) | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-016 | Naperőmű: „PV Panel orientáció (maximum)" hiányzik, „dőlésszög (maximum)" duplikált | <span class="sev-s2">S2</span> | <span class="prio-p2">P2</span> |
| L-001 | A „Nem" alapérték nincs előre kiválasztva a toggle-öknél | <span class="sev-s3">S3</span> | <span class="prio-p2">P2</span> |
| L-009 | „Származási garancia számlaszáma" feleslegesen kötelező | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-012 | „Vissza & Mentés" gomb — a követelmény szerint a Vissza nem ment | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-013 | Inkonzisztens default-kiválasztás (1. lépés toggle vs Képviselet módja) | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-015 | A tulajdonos „Név" mezője nem kötelező (a 3. lépésben kötelező) | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-018 | Kötelezőség-inkonzisztencia a cím-mezőknél termelőegység-típusonként | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-019 | Energiatároló: feltételes méret-mezők mindig láthatók (nem a toggle-ra) | <span class="sev-s3">S3</span> | <span class="prio-p3">P3</span> |
| L-003/004/005/010/011/014/017 | Kozmetikai / szöveg (%, dupla szóköz, hiányzó vessző, progress, hiányzó `*`…) | <span class="sev-s4">S4</span> | <span class="prio-p4">P3–P4</span> |

## Kiemelt leletek

!!! danger "L-007 — A HU→EN nyelvváltás nem működik · <span class='sev-s1'>S1</span> <span class='prio-p1'>P1</span>"
    - **Miért fontos?** A követelmény kétnyelvű (HU/EN) űrlapot ír elő.
    - **Mit látunk?** A nyelvválasztót „EN"-re állítva a teljes felület **magyar marad** (cím, mezők, gombok, hibaüzenetek).
    - **Hogyan javítsuk?** Az angol lokalizáció biztosítása minden szöveges elemre.

!!! warning "L-016 — Naperőmű: orientáció (maximum) hiányzik, dőlésszög (maximum) duplikált · <span class='sev-s2'>S2</span> <span class='prio-p2'>P2</span>"
    - **Miért fontos?** A panel-orientáció maximuma így **nem rögzíthető**, a dőlésszög maximuma kétszer kérdezett — hibás műszaki adatrögzítés.
    - **Mit látunk?** „PV Panel orientáció (minimum)" + „PV Panel dőlésszög (maximum)" egy sorban, majd lejjebb „PV Panel dőlésszög (minimum)" + „dőlésszög (maximum)" ismét.
    - **Hogyan javítsuk?** Az orientáció (maximum) mező pótlása; a dőlésszög (maximum) deduplikálása.

!!! warning "L-002 / L-006 / L-008 — validáció és kötelezőség · <span class='sev-s2'>S2</span>"
    - **L-002:** a „KÁT-ba lépés ideje (ha releváns)" opcionális mezőt kötelezőként kéri.
    - **L-006:** a hibaüzenet a belső azonosítót írja ki (pl. *„system_level_service"*) a magyar felirat helyett.
    - **L-008:** a „Helyrajzi szám" kötelező a teljes cím mellett — a „hrsz **vagy** cím" üzleti szabály hiányzik.

## ✅ Megerősített megfelelőség (a korábban feltételezett hibák az implementációban rendben)

Az élő teszt **cáfolta** a régi terv-/spec-feltevések jelentős részét — ezek a pontok rendben, a felület érettebb a dokumentumoknál:

- **Dátum-formátum helyes** (`éééé-hh-nn`); **Cégforma / Cégbejegyzés országa / Közterület jellege = legördülő** lista, alapérték „Magyarország"; **Cégbejegyzés dátuma** megvan.
- **Ismétlő blokkok** („+ további személy / tulajdonos / erőmű") és a **feltételes mezők** (Magánszemély/Cég) működnek.
- **Tracking szótár** rendben (1 tengelyes / 2 tengelyes / Fix); mező-magyarázatok (POD, %/°C, AC/DC) jól vezetik a kitöltést.
- **Kliensoldali validáció** beszédesen blokkol; **cross-browser** (Chromium↔Firefox) konzisztens; **mobil** nem törik szét.

!!! warning "Bizalmas leletek"
    A biztonsági és egyéb érzékeny jellegű megállapítások nem ebben a publikus riportban, hanem külön, bizalmas csatornán kerülnek átadásra.
