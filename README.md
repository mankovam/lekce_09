# Tvořím web A–Z: lekce 9

podzim 2020, Praha

<small>10. listopadu 2020</small>

---

#### Cvičení 1

1. Vlož ikonu letadla do stránky.
1. Zmenši ikonu na 20 % šířky stránky.
1. Vycentruj ikonu.
1. Změň barvu kruhového pozadí ikony.

note:

- otevři si cvičení O1_svg/
- Co kdybychom chtěli měnit barvu pozadí na při najetí myši?

---

#### Cvičení 2

1. Změň barvu letadla při najetí myši.
1. Otoč letadlo při najetí myši čumákem do prava.

note:

- **Pozor!** V případě transformací přímo na prvcích SVG, se hodí nastavit `transform-origin: center;`. Na rozdíl od HTML prvků, které mají tuto hodnotu výchozí, prvky SVG mají `transform-origin: left top`, tj. pokud je otáčíme, jako bychom je drželi za horní levý roh (a nikoli za střed).

---

#### Cvičení 3

1. Zjemni změny při najetí myši pomocí `transition`.

---

#### Cvičení 4

1. Obal ikonu nadpisem.
1. Text nadpisu: _Letiště Václava Havla_ umísti v kódu před ikonu.
1. Nadpis vespod orámuj 2px rámečkem.
1. Zmenši ikonu úměrně textu.
1. Ikonu a text umísti pod sebe, přičemž ikona bude první.
1. Obarvi nadpis i jeho rámování na `hotpink`.
1. Obarvi ikonu shodně s nadpisem

---

#### Cvičení 5

Úpravou složek HSLA vytvoř varianty tzv. primární barvy:

`--primary-light` => světlá
`--primary-lighter` => světlejší průsvitná
`--primary-dark` => tmavá

Vytvořené barvy použijeme na prvky

1. Pozadí stránky: světlejší průsvitnou
1. Písmo stránky: tmavou barvou
1. Hlavní nadpis: primární, stín tmavou
1. Nadpisy: tmavou
3. Odkazy v navigaci: písmo a orámování tmavou, podbarvit světlou; na hover změna pozadí (jak libo)
5. Sekce: podbarvit světlou, ohraničení tmavou
**Bonus**: Odstraň orámování poslední sekce.

---

#### Cvičení 6

1. Nastav barevné proměnné (pro `:root`).
2. Nahraď přímo nastavené barvy u jednotlivých prvků proměnnými.

note:

- v devTools při najetí myši nad hodnotu s funkcí `var()` se v bublině ukáže hodnota proměnné vlastnoti

---

#### Cvičení 7

Zjednodušíme zápis pro pozadí receptů.

1. Pro všechny recepty nastav jednotný obrázek na pozadí: gradient a proměnnou  `--bg-recipe` s výchozí hodnotou SVG obrázek kuchařky
2. Uprav kód jednotlivých receptů: odstraň vlastnost `background-image` a nastav pro každý recept hodnotu proměnné `--bg-recipe`.

---

#### Cvičení 8

1. Najdi vhodný emotikon pro komentář (bublina?).
2. Úpravou CSS umísti emotikon před počet komentářů

---
