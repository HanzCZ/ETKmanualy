# Screenshoty — technický postup

Jak vznikají screenshoty do návodů, aby byly jednotné (rozměr, vzhled anotací). Slouží hlavně
jako připomínka postupu (i pro asistenta při ztrátě kontextu).

## Prostředí

- ETK admin: `https://etkdev.ssgh.cz/admin/` (testovací). Přihlášení superadmin účtem.
- Snímky se pořizují **z živé aplikace** přes Chrome (rozšíření / Chrome MCP), ne rekonstrukcí.
- Cílový rozměr snímku: **1288×939 px**.

## Pořízení snímku do souboru

Na tomto stroji nefungovalo přímé ukládání přes `computer-use` ani systémový `screencapture`
(chybí oprávnění). Funkční oklika přes Chrome (gif_creator), která uloží soubor na disk:

1. Nastav stránku do požadovaného stavu (naviguj, vyplň pole) — **bez** nahrávání.
2. Zapni nahrávání → proveď **jednu** akci (klik do prázdna / dvojklik na prvek). Jen akce
   vytvoří snímek; samotný „screenshot" snímek nepřidá.
3. Zastav nahrávání → exportuj jako GIF se **staženim** do `~/Downloads`, s vypnutými overlaye
   (watermark, click indicators, progress bar, action labels), kvalita max.
4. V Pythonu převeď GIF → PNG (`PIL`, poslední frame = ustálený stav).

## Anotace (jednotný vzhled)

Barva: **`#FF5C00`** (oranžová).

- **Rámeček** kolem cílového prvku, síla ~4 px, volitelně světle oranžová průhledná výplň.
- **Číslovaný odznak**: oranžové kolečko (r ≈ 20 px) s bílým číslem a bílým 3px obrysem,
  umístěné **vedle** prvku, ať nezakrývá text. Čísla odpovídají krokům v návodu.
- **Šipka** oranžová (~6 px) s hrotem – jen když ukazuje směr/souvislost.
- **Popiska**: oranžový zaoblený obdélníček s bílým textem u šipky, krátký text.

Anotace se dělají PIL skriptem (souřadnice z 1288×939 snímku sedí 1:1). Odznaky ⭕ v obrázku
musí číselně odpovídat číslovanému popisu pod obrázkem v návodu.

## Uložení

- Základ (bez anotace) je jen mezikrok; do repa se commituje **anotovaný** PNG.
- Název: `assets/NN-strucny-nazev.png`, číslováno v pořadí výskytu v návodu.
