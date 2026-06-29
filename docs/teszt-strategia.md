# Teszt-stratégia

A tesztelés rétegekre bontva, minden követelményt **pozitív és negatív** ágon is vizsgálva, az alábbi paraméterekkel.

## Teszt-rétegek

| Réteg | Tartalom |
|---|---|
| **Funkcionális** | Teljes folyamat: belépés → adatkezelés elfogadása → kitöltés → mentés/folytatás → ellenőrzés → beküldés |
| **Mező-validáció** | Kötelezőség, típus, formátum, határérték, üzleti szabályok, érték-konverziók |
| **Design-egyezés** | A jóváhagyott tervtől (EON UI komponensek) való eltérések |
| **Böngésző-kompatibilitás** | Lásd a böngésző-mátrixot |
| **Reszponzivitás** | Asztali / tablet / mobil nézet |
| **Akadálymentesség** | WCAG 2.2 AA → [ACR](akadalymentesseg.md) |
| **Teljesítmény** | Válaszidők, terhelés alatti viselkedés |
| **Tartalom / nyelvhelyesség** | Szövegek, hibaüzenetek, lokalizáció |

## Böngésző-mátrix

A leletek minden megjelölt böngészőn ellenőrzöttek; a javítás-ellenőrzés is mindegyiken megtörténik (hogy ne maradjon „egyik böngészőben jó, másikban nem" állapot).

| Böngésző | Motor | Verzió |
|---|---|---|
| Google Chrome | Blink | aktuális + 1 korábbi |
| Mozilla Firefox | Gecko | aktuális + 1 korábbi |
| Microsoft Edge | Blink | aktuális + 1 korábbi |
| Apple Safari | WebKit | aktuális + 1 korábbi |

## Nézetek

**Asztali · tablet · mobil** — a felület mindegyik nézetben funkcionálisan és vizuálisan vizsgált; a leletek nézetenként bontva.

## Akadálymentesség

**WCAG 2.2 AA** — automatikus (axe-core) és manuális ellenőrzés; az eredmény az [ACR](akadalymentesseg.md)-ben.

## Hiba-súlyozás (ISO/IEC/IEEE 29119-3)

A hibák **severity** (hatás) és **priority** (sürgősség) szerint külön súlyozottak:

| Severity | Jelentés | | Priority | Jelentés |
|---|---|---|---|---|
| <span class="sev-s1">S1</span> | Blokkoló — használhatatlan | | <span class="prio-p1">P1</span> | Azonnal javítandó |
| <span class="sev-s2">S2</span> | Kritikus — fő funkció sérül | | <span class="prio-p2">P2</span> | Soron kívül |
| <span class="sev-s3">S3</span> | Jelentős — kerülőúttal működik | | <span class="prio-p3">P3</span> | Ütemezetten |
| <span class="sev-s4">S4</span> | Kisebb / kozmetikai | | <span class="prio-p4">P4</span> | Ráérő |

## Teszt-eset szerkezet

Minden teszt-eset egységes mezőkkel készül: **azonosító · réteg · előfeltétel · lépések · bemenet · elvárt eredmény · böngésző/nézet · eredmény (PASS/FAIL + bizonyíték) · prioritás**. A követelmény-megfeleltetés a [Követhetőségi mátrixban](rtm.md).
