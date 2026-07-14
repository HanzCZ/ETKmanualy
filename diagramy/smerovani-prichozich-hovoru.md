---
oblast: Telefonie
aktualizovano: 2026-07-02
stav: návrh k odsouhlasení
---

# Směrování příchozích hovorů (SU / OSA / CSP)

Jak se rozřazují příchozí hovory mezi oddělení podle toho, v jakém stavu je volající
v našem číselníku. Platí pro volání na kteroukoli z těchto klapek:

| Oddělení | Klapka |
|---|---|
| **SU** – studijní oddělení | `11` |
| **OSA** | `49` |
| **CSP** | `00` |

---

## Hlavní rozřazení podle stavu volajícího

```mermaid
flowchart TD
    START([Příchozí hovor na 11 / 49 / 00])
    START --> KNOWN{Volající je<br>v číselníku?}
    KNOWN -- "ne" --> DEFAULT["Běžné vyzvánění na volané klapce<br>(k ověření)"]
    KNOWN -- "ano" --> STAV{Stav volajícího<br>v číselníku}

    STAV -- "před podáním přihlášky" --> SU["SU – studijní oddělení (11)"]
    STAV -- "přihláška podaná,<br>zatím nepřijat" --> OSA["OSA (49)"]
    STAV -- "přijat a dále" --> CSP["CSP (00)"]

    style SU fill:#d9e8ff,stroke:#3b6fd4
    style OSA fill:#dff2e0,stroke:#3f9c46
    style CSP fill:#fde8d9,stroke:#e07a2f
```

> ⚠️ **Dnes platí:** kdo je „přijat a dále", padá **vždy rovnou na CSP**.
> IVR rozcestník níže zatím neexistuje.

## Plánované rozšíření: IVR rozcestník pro přijaté

Až bude rozcestník nasazen, přijatí volající nespadnou rovnou na CSP, ale nejdřív
uslyší volbu:

```mermaid
flowchart TD
    PRIJAT["Volající: přijat a dále"] --> IVR{{"IVR rozcestník<br>(zatím NENÍ nasazen)"}}
    IVR -- "volba 1 – školné / platba /<br>splátkový kalendář" --> SU["SU (11)"]
    IVR -- "volba 2 – cokoli jiného" --> CSP["CSP (00)"]

    style IVR fill:#fff4cc,stroke:#c9a227,stroke-dasharray: 5 5
    style SU fill:#d9e8ff,stroke:#3b6fd4
    style CSP fill:#fde8d9,stroke:#e07a2f
```

## Nedovolání na OSA — přepad na SU a evidence zmeškaného hovoru

Když se volající na OSA nedovolá, hovor se přepojí na SU (to už dnes funguje).
**Změna:** pokud hovor nezvedne ani SU, zmeškaný hovor se musí evidovat **u OSA**, ne u SU.

```mermaid
flowchart TD
    CALL([Hovor směrovaný na OSA]) --> Q1{Zvedne OSA?}
    Q1 -- "ano" --> DONE1[Hovor vyřízen na OSA]
    Q1 -- "ne" --> FWD["Přepojení na SU<br>(děje se už dnes)"]
    FWD --> Q2{Zvedne SU?}
    Q2 -- "ano" --> DONE2[Hovor vyřízen na SU]
    Q2 -- "ne" --> MISS["Zmeškaný hovor se eviduje u OSA<br>(NE u SU) — požadovaná změna"]

    style MISS fill:#ffe3d1,stroke:#ff5c00,stroke-width:2px
```

---

## Shrnutí pravidel

1. Volající **v číselníku** se rozřazuje podle stavu: před podáním přihlášky → **SU**,
   podaná a nepřijat → **OSA**, přijat a dále → **CSP**.
2. **Zatím** jdou všichni přijatí rovnou na CSP; **plán** je IVR rozcestník
   (1 = školné/platby → SU, 2 = ostatní → CSP).
3. Nedovolání na OSA → přepad na SU; když nezvedne ani SU, zmeškaný hovor
   **zůstává evidovaný u OSA**.

## Otevřené otázky (k ověření)

- **Hranice SU/OSA:** zadání říkalo „stav nižší než *přihláška přijata* → SU" a zároveň
  „*přihláška podaná* a nepřijat → OSA". Diagram předpokládá, že OSA pravidlo má přednost,
  tedy SU dostává jen stavy **před podáním přihlášky**. Potvrdit.
- **Volající mimo číselník:** co se s nimi děje? (Diagram zatím předpokládá běžné
  vyzvánění na volané klapce.)
- Platí přepad „nedovolání → SU" i pro hovory na **CSP**, nebo jen pro OSA?
