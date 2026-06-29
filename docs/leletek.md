# Leletek

A talált eltérések egységes, követhető formátumban. Minden lelet **bizonyítékkal** (képernyőkép / reprodukciós lépések) és **súlyozással** dokumentált.

## Lelet-formátum

Minden lelet az alábbi négy blokkból áll:

1. **Miért fontos? Mit jelent?** — a vizsgált szempont és jelentősége
2. **Mit látunk a felületen?** — a konkrét megfigyelés (képernyő, reprodukció, bizonyíték)
3. **Hogyan javítsuk?** — javasolt megoldás
4. **Forrás** — a követelmény/terv hivatkozás

…kiegészítve: **réteg · severity · priority · böngésző/nézet · státusz**.

!!! example "Lelet-sablon"
    **[L-000] Lelet címe** — <span class="sev-s3">S3</span> <span class="prio-p3">P3</span> · _réteg_ · _böngésző/nézet_

    - **Miért fontos?** …
    - **Mit látunk?** … _(képernyőkép)_
    - **Hogyan javítsuk?** …
    - **Forrás:** …

## Összefoglaló

| Lelet | Réteg | Severity | Priority | Státrusz |
|---|---|---|---|---|
| _(az első teszt-kör után töltődik)_ | | | | |

!!! note "Állapot"
    A leletek az **első teszt-kör** során kerülnek ide, az élő dev-környezeten végzett vizsgálat alapján.

!!! warning "Bizalmas leletek"
    A **biztonsági** és egyéb érzékeny jellegű megállapítások **nem** ebben a publikus riportban, hanem külön, bizalmas csatornán kerülnek átadásra a megrendelőnek és a fejlesztőnek.
