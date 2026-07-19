> ⚠️ **Toto repo je archivované — obsah se přestěhoval.**
> Aktuální verze žije v privátním repu [HanzCZ/ssgh-dokumentace](https://github.com/HanzCZ/ssgh-dokumentace), složka [`etk-manualy/`](https://github.com/HanzCZ/ssgh-dokumentace/tree/main/etk-manualy). Historie commitů byla při sloučení zachována.

# ETK manuály

Návody „jak něco udělat v ETK" (administrace na `https://etkdev.ssgh.cz/admin/`).
Každý návod je Markdown soubor se screenshoty, na kterých je vyznačeno, kam kliknout.

Složka funguje zároveň jako **Obsidian vault** i jako **GitHub repozitář**.

## Jak psát návody

**➡️ Závazný styl a formát: [`STYL-NAVODU.md`](STYL-NAVODU.md)** — přečti si před psaním nového návodu.

- Prázdná šablona ke zkopírování: [`_sablona/navod-sablona.md`](_sablona/navod-sablona.md)
- Technický postup pořizování a anotace screenshotů: [`_sablona/screenshoty-postup.md`](_sablona/screenshoty-postup.md)

## Struktura

```
ETKmanualy/
├── README.md
├── STYL-NAVODU.md            # zdroj pravdy pro styl a formát
├── _sablona/                 # šablona návodu + postup na screenshoty
└── navody/
    └── <oblast>/
        ├── <nazev-navodu>.md
        └── assets/           # screenshoty k návodům v této oblasti
```

## Seznam návodů

- [Učebny — vytvoření a editace](navody/ucebny/ucebny-vytvoreni-a-editace.md)

## Diagramy

- [Směrování příchozích hovorů (SU / OSA / CSP)](diagramy/smerovani-prichozich-hovoru.md)
