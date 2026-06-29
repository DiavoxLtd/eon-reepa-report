# Áttekintés

> **EON REEPA adatbekérő űrlap — tesztelési riport.** Ez az élő, verziózott dokumentum a tesztelés módszertanát, eredményeit és a leszállítandó tesztjegyzőkönyvet tartalmazza, az **ISO/IEC/IEEE 29119-3:2021** szabvány szerint.

## A tesztelt rendszer

A **REEPA** az E.ON megújuló energiás (nap-/szél-/energiatároló) partnerei számára készülő **webes adatbekérő űrlap**, amely a korábbi Excel-alapú adatbekérést váltja ki. A partner egy egyedi, tokenizált linken keresztül adja meg a céges és az erőművekre vonatkozó műszaki adatait, több lépésben, mellékletekkel, majd beküldi az űrlapot.

## A tesztelés célja és hatóköre

A tesztelés célja, hogy az **alapvető hibák ne a megrendelői átvételen (UAT) derüljenek ki**, hanem azt megelőzően kiszűrjük őket. A vizsgálat a következő szempontokra terjed ki (részletek: [Teszt-stratégia](teszt-strategia.md)):

- **Funkcionális** működés (teljes adatbekérési folyamat, mentés/folytatás, beküldés)
- **Mező-validáció** (kötelezőség, formátum, határértékek, üzleti szabályok)
- **Design-egyezés** a jóváhagyott tervhez (EON UI komponensek)
- **Böngésző-kompatibilitás** és **reszponzivitás** (asztali / tablet / mobil)
- **Akadálymentesség** (WCAG 2.2 AA — lásd [ACR](akadalymentesseg.md))
- **Tartalom és nyelvhelyesség**

## Módszertan

- A riport és a tesztjegyzőkönyv az **ISO/IEC/IEEE 29119-3:2021** *Test Completion Report* (7.4) struktúráját követi.
- A leletek egységes formátumban: **Miért fontos? → Mit látunk? → Hogyan javítsuk? → Forrás**, **severity (S1–S4)** és **priority (P1–P4)** súlyozással, böngésző/nézet bontásban.
- A követelmény→teszteset megfeleltetés a [Követhetőségi mátrixban (RTM)](rtm.md).

## Verziózás

Minden teszt-kör a riport **külön verziójaként** jelenik meg (a fejléc verzióválasztójában), így a megrendelő bármikor visszanézheti a korábbi köröket és a haladást — ez biztosítja az **audit-nyomonkövethetőséget**.

!!! note "Állapot"
    **1. teszt-kör folyamatban** — a Céges adatok 1–2. lépésének leletei feltöltve (lásd [Leletek](leletek.md)). Következik: a 3–6. lépés, a termelőegység-ág, valamint a tablet/mobil nézetek.
