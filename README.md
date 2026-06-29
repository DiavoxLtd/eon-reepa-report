# EON REEPA — Tesztriport

Az **E.ON REEPA** adatbekérő űrlap tesztelésének élő, verziózott riportja — az **ISO/IEC/IEEE 29119-3:2021** (Software Test Documentation) szabvány szerint.

Tesztelő: **Diavox Kft.** · Megbízó: **E.ON**.

## Technológia

- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) + [mike](https://github.com/jimporter/mike) (verziózás → audit-nyomonkövethetőség)
- GitHub Actions → GitHub Pages (`gh-pages` branch)

## Helyi futtatás

```bash
pip install -r requirements.txt
mkdocs serve
```

## Felépítés

| Szekció | Tartalom |
|---|---|
| Áttekintés | Rendszer, scope, módszertan, környezet |
| Teszt-stratégia | Rétegek, böngésző-mátrix, mobil, WCAG 2.2 AA |
| Leletek | 3-blokkos leletek (severity/priority, nézet/böngésző bontás) |
| Követhetőség (RTM) | Követelmény → teszteset → státusz → defekt |
| Akadálymentesség (ACR) | VPAT 2.5 / WCAG 2.2 AA konformitás |
| Tesztjegyzőkönyv | Test Completion Report (29119-3, 7.4.1–7.4.10) |

> A részletes teszt-tudástár és a nyers (esetenként bizalmas) leletek a privát munka-repóban kezeltek; ez a **publikus** riport kizárólag a megrendelő felé megosztható, nem-érzékeny tartalmat tartalmaz.
