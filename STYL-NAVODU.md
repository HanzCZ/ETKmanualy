# Styl a formát návodů ETK

Závazná pravidla, jak psát návody v tomto repu, aby byly **jednotné**. Platí pro každý
soubor v `navody/`. Vzorový hotový návod: [Učebny — vytvoření a editace](navody/ucebny/ucebny-vytvoreni-a-editace.md).
Prázdná šablona ke zkopírování: [`_sablona/navod-sablona.md`](_sablona/navod-sablona.md).

> Tento dokument je „zdroj pravdy". Když se styl někdy změní, upraví se **nejdřív tady**
> a pak se podle toho sjednotí ostatní návody.

---

## 1. Struktura repozitáře a pojmenování

```
navody/<oblast>/<nazev-navodu>.md      ← jeden návod = jeden .md
navody/<oblast>/assets/                 ← screenshoty k návodům té oblasti
```

- **Oblast** = sekce ETK (např. `ucebny`, `tridy`, `klasifikace`, `etesty`). Malá písmena, bez diakritiky, slova spojená pomlčkou.
- **Název souboru** = krátký a popisný, malá písmena, bez diakritiky, pomlčky: `ucebny-vytvoreni-a-editace.md`.
- **Screenshoty**: `NN-strucny-nazev.png`, číslované od `01`, v pořadí, v jakém jsou v návodu. Např. `01-prehled-menu.png`.
- Každý nový návod přidej do seznamu v [`README.md`](README.md).

---

## 2. Kostra návodu (pořadí sekcí)

Každý návod má tuto kostru. Sekce, které nedávají smysl, se **vynechají** (ne že zůstanou prázdné).

1. **YAML frontmatter** (metadata, viz níže)
2. **`# Nadpis`** — co návod řeší (H1, jen jeden)
3. **Krátký úvod** — 1–2 věty co se čtenář naučí + poznámka o prostředí
4. **`## Kde to najdu`** — cesta v levém menu + přímý odkaz (`/admin/...`) + screenshot
5. **`## Kdo to může udělat`** — role/oprávnění
6. **`## Jak <akce>`** — číslované kroky se screenshoty (hlavní část; může jich být víc)
7. **`## Proměnné (pole formuláře)`** — tabulka, pokud je formulář
8. **`## Jak <to> edituji`** — pokud se editace liší od vytvoření
9. **`## Přehled sloupců v tabulce`** — u agend s výpisem/gridem
10. **Upozornění / omezení** — blockquote `> ⚠️` tam, kde to patří (klidně uvnitř sekcí)
11. **`## Rychlé shrnutí`** — 2–4 odrážky na konci (TL;DR)

### YAML frontmatter (na začátku souboru)

```yaml
---
oblast: Učebny
modul: eTesty → Nastavení
aktualizovano: RRRR-MM-DD
prostredi: etkdev.ssgh.cz (testovací)
---
```

---

## 3. Styl psaní

- **Jazyk:** čeština.
- **Oslovení čtenáře:** tykání, přímo („klikni", „vyplň", „potvrď"). Ne „uživatel klikne".
- **Kroky:** rozkazovací způsob, jeden krok = jedna akce. Číslované seznamy (`1.`, `2.`, …).
- **Stručnost:** krátké věty. Žádná omáčka. Čtenář chce vědět *kam kliknout a co se stane*.
- **Konzistentní pojmy:** prvky UI pojmenovávej **přesně tak, jak jsou v aplikaci** (včetně diakritiky a velkých písmen): *Vytvořit učebnu*, *Reálná kapacita*, *Je aktivní*.
- **Prostředí:** screenshoty jsou z testovacího `etkdev.ssgh.cz`; když se ostrý provoz liší (např. chybí červený pruh „testovací režim"), zmiň to jednou v úvodu.

---

## 4. Formátování (Markdown)

| Prvek | Zápis | Použití |
|---|---|---|
| Nadpis návodu | `# …` | jednou na začátku |
| Sekce | `## …` | hlavní sekce |
| Podsekce | `### …` | jen když je opravdu potřeba |
| **Tlačítka / názvy polí / položky menu** | `**Vytvořit učebnu**` | tučně |
| Cesty, URL, názvy sloupců v DB, klávesy | `` `/admin/classrooms/` ``, `` `Enter`, `name` `` | kód (backticky) |
| Poznámka / tip / omezení | `> …` blockquote, s prefixem emoji | viz níže |
| Odkaz na jiný návod | `[text](../oblast/soubor.md)` | relativní cesta |
| Tabulka | standardní MD tabulka | proměnné, přehledy |

**Blockquote poznámky** — používej jednotné prefixy:
- `> ⚠️` — **omezení / na co si dát pozor** (např. „tohle z UI nejde").
- `> 💡` — tip nebo doplňující info.
- Běžné upřesnění bez emoji (např. poznámka o testovacím prostředí) taky jako `>`.

Nezapomeň, že co **nejde ověřit v aplikaci**, se označí jako *k ověření* — nikdy si nevymýšlej
chování. Radši napiš „*(k ověření se správcem ETK)*".

---

## 5. Screenshoty — jak je popisovat a anotovat

### 5.1 Vkládání do textu

- Screenshot vlož **hned za krok/odstavec, kterého se týká**, ne na konec.
- Formát: `![Výstižný alt popis](assets/NN-nazev.png)`. Alt text je stručná věta, co je na obrázku.
- **Pod screenshot** dej **číslovaný seznam**, který vysvětluje očíslované odznaky na obrázku
  (viz níže). Čísla v seznamu = čísla ⭕ na obrázku = pořadí kroků. Musí sedět 1:1.

Příklad:

```markdown
![Prázdný formulář pro vytvoření učebny](assets/02-formular-prazdny.png)

1. **Název učebny** – označení místnosti (např. `A101`).
2. **Aktivní** – zda se učebna nabízí (výchozí **Ano**).
3. **Kapacita** – počet míst.
4. **Vytvořit učebnu** – uloží.
```

### 5.2 Vizuální styl anotace (jednotný vzhled)

Do screenshotů se dokresluje **oranžová** (`#FF5C00`):

- **Rámeček** kolem prvku, na který se má kliknout / který je důležitý: síla ~4 px,
  volitelně světle oranžová průhledná výplň.
- **Číslovaný odznak** = oranžové kolečko s bílým číslem, umístěné tak, aby **nezakrývalo text**
  prvku (vedle, ne přes). Čísla jdou v pořadí kroků.
- **Šipka** oranžová – jen když je potřeba ukázat směr/souvislost (např. „sem se to uloží").
- **Popiska** (label) – oranžový obdélníček s bílým textem u šipky, jen krátce (např. `Odeslat`,
  `Dvojklik → uprav → Enter`).
- Nepřeplácávej to – radši **méně, ale jasně**. Jeden obrázek = jedna myšlenka.

### 5.3 Technika pořízení (jak snímky vznikají)

Snímky se pořizují z živé aplikace přes Chrome a anotují skriptem. Detailní postup (včetně
řešení, když nejdou běžné cesty) je v [`_sablona/screenshoty-postup.md`](_sablona/screenshoty-postup.md).
Rozměr snímků: **1288×939 px**.

---

## 6. Checklist před „hotovo"

- [ ] Frontmatter vyplněný, `aktualizovano` = dnešní datum.
- [ ] Sekce v pořadí dle kap. 2, nepotřebné vynechané.
- [ ] Názvy prvků UI přesně podle aplikace.
- [ ] Každý screenshot má alt text a (kde má odznaky) číslovaný popis, čísla sedí 1:1.
- [ ] Anotace oranžová, odznaky nezakrývají text.
- [ ] Co nejde ověřit = označeno *k ověření*.
- [ ] Návod přidán do seznamu v `README.md`.
