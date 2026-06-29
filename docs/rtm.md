# Követhetőségi mátrix (RTM)

A **követelmény → teszteset → eredmény → defekt** megfeleltetés, amely biztosítja, hogy minden követelmény tesztelve legyen, és minden lelet visszavezethető legyen a forrásához.

| Követelmény ID | Forrás | Teszteset ID | Státusz | Defekt |
|---|---|---|---|---|
| _(feltöltés alatt)_ | | | | |

**Oszlopok:**

- **Követelmény ID** — a követelmény azonosítója (üzleti/műszaki specifikációból)
- **Forrás** — a követelmény dokumentum-hivatkozása
- **Teszteset ID** — a lefedő teszt-eset(ek)
- **Státusz** — <span class="status-pass">PASS</span> / <span class="status-fail">FAIL</span> / <span class="status-wip">folyamatban</span>
- **Defekt** — a kapcsolódó [lelet](leletek.md) hivatkozása (ha van)

!!! note "Lefedettség"
    A követelmény-lefedettségi mutató (tesztelt / összes követelmény) a teszt-körök előrehaladtával frissül.
