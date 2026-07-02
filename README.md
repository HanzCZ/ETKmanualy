# ETK manuály

Návody „jak něco udělat v ETK" (administrace na `https://etkdev.ssgh.cz/admin/`).
Každý návod je Markdown soubor se screenshoty, na kterých je vyznačeno, kam kliknout.

Složka funguje zároveň jako **Obsidian vault** i jako **GitHub repozitář**.

## Struktura

```
ETKmanualy/
├── README.md
└── navody/
    └── <oblast>/
        ├── <nazev-navodu>.md
        └── assets/           # screenshoty k návodům v této oblasti
```

## Konvence pro psaní návodu

- Nadpis = co návod řeší.
- Sekce **Kdo to může udělat** (oprávnění/role).
- Číslované kroky, u každého kroku screenshot s vyznačením (rámeček/šipka), kam kliknout.
- Screenshoty se ukládají do `assets/` vedle návodu, pojmenované `nazev-navodu-01.png`, `-02.png`, …
- Na konci sekce **Proměnné / pole formuláře** s tabulkou (pole → popis → povinné?).

## Seznam návodů

- [Učebny — vytvoření a editace](navody/ucebny/ucebny-vytvoreni-a-editace.md)
