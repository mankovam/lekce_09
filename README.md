# Tvořím web A–Z: lekce 9

podzim 2020, Praha

<small>10. listopadu 2020</small>

note:

- bitmapy vs vektory (křivky):
    - bitmapy jsou de facto mozaiky barevných bodů, nelze je škálovat do nekonečna (body jednou dojdou)
    - vektory: geometrické útvary vyjádřené matematickými rovnicemi (analytická geometrie)
- Hlavní výhodou vektorové grafiky je možnost pružně měnit rozměry bez ztráty kvality, přičemž si vystačíme s jediným souborem. Fotky je naproti tomu obvyklé mít v různých velikostech a servírovat je podle rozlišení obrazovky.

---

# SVG

[Scalable Vector Graphics](https://cs.wikipedia.org/wiki/Scalable_Vector_Graphics)

note:

- odbornice na SVG: [Sara Soueidan](https://www.sarasoueidan.com/about/) – inspirace pro tebe

---

## Úvod do SVG

- vektorový formát obrázků (tzv. obrázek v křivkách)
- SVG se zapisuje pomocí značek podobně jako HTML => lze ho upravovat v textovém editoru (VS Code).
- Upravit se dá i v grafických editorech:
    - [Adobe Illustrator](http://www.adobe.com/cz/products/illustrator.html) ‒ zpoplatněný
    - [Inkscape](https://inkscape.org/cs/) ‒ zdarma
    - různé generátory tvarů: [Squircley](https://squircley.app/), [Getwaves](https://getwaves.io/), [Blobmaker](https://www.blobmaker.app/)

note:

- Lze jej stylovat pomocí CSS.
- Hodí se k animování.
- Případný text v obrázku je čitelný i pro roboty.

---

## Použití SVG

- ikony
- loga
- grafy

**Pozor!** SVG není alternativou k bitmapovým obrázkům (JPG, PNG, GIF), ty jsou naopak ideální k zobrazení fotografií.

---

## Vložení SVG na stránku

---

### Pomocí prvku `<img>`

- stejně jako jiný obrázek, tj. do atributu `src` zadáme cestu k SVG souboru:

```html
<h2>
    <img src="letadlo.svg" alt="">
    Letiště Václava Havla
</h2>

```

note:

Takto vložené SVG lze stylovat jen pomocí CSS, které je zapsáno přímo v daném SVG souboru (inline styly). Zajímavější je proto druhá metoda, která nám dovolí stylovat SVG (a jeho části) přímo ve stylopise dané stránky.

---

#### Cvičení 1

1. Vlož ikonu letadla do stránky.
1. Zmenši ikonu na 20 % šířky stránky.
1. Vycentruj ikonu.
1. Změň barvu kruhového pozadí ikony.

note:

- Co kdybychom chtěli měnit barvu pozadí na při najetí myši?

---

### Vložení přímo do HTML

```html

<h2>
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 70 70">
        <circle fill="#48418e" cx="35" cy="35" r="35" />
        <path fill="#fff" d="M44.7,39.9l-6.9-6.9l16.7-12.5l-4.9-4.9l-20.8,8.3l-6.6-6.6c-1.9-1.9-4.5-2.3-5.9-1c-1.3,1.3-0.9,4,1,5.9 l6.6,6.6l-8.3,20.8l4.9,4.9l12.5-16.7l6.9,6.9v9.7h4.9l2.4-7.3l7.3-2.4v-4.9L44.7,39.9L44.7,39.9z" />
    </svg>
    Letiště Václava Havla
</h2>
```

note:

- K takto vloženému obrázku můžeme přisupovat v našem stylopise jako ke kterémukoli jinému prvku na stránce. Vhodné je přidat prvku `<svg>` třídu a tu použít jako selektor, ale není to nutné.
- **Lze stylovat i části obrázku:** v devTools si zjistíme, který prvek uvnitř SVG představuje část obrázku, kterou chceme stylovat a přes jeho selektor můžeme změnit jen část ikony.
- Ukázka:
    - Prozkoumat ikon v devTools.
    - Přidat třídu prvku `circle`.
    - Změnit mu barvu na `:hover`.

---

#### Cvičení 2

1. Změň barvu letadla při najetí myši.
1. Otoč letadlo při najetí myši čumákem do prava.

note:

- **Pozor!** V případě transformací přímo na prvcích SVG, se hodí nastavit `transform-origin: center;`. Na rozdíl od HTML prvků, které mají tuto hodnotu výchozí, prvky SVG mají `transform-origin: left top`, tj. pokud je otáčíme, jako bychom je drželi za horní levý roh (a nikoli za střed).

---

##### Vlastnost `transform-origin`

```css
.icon-plane {
    transform-origin: center;
}
```

---

#### Cvičení 3

1. Zjemni změny při najetí myši pomocí `transition`.

note:

- Vlastnost `transition` lze nastavit jen vybraným vlastnostem. Výchozí hodnota je `all`, tj. všechny přecházejí nám všechny vlastnosti, které nastavujeme.

---

####  Nastavujeme `transition` pro více vlastností

```css
:hover {
    transition: fill 400ms, transform 600ms;
}
```

note:

- případný druhý časový údaj v hodnotě transition, je `transition-delay`, tj. zpoždění přechodu.

---

#### Cvičení 4

1. Obal ikonu nadpisem.
1. Text nadpisu: _Letiště Václava Havla_ umísti v kódu před ikonu.
1. Nadpis vespod orámuj 2px rámečkem.
1. Zmenši ikonu úměrně textu.
1. Ikonu a text umísti pod sebe, přičemž ikona bude první.
1. Obarvi nadpis i jeho rámování na `hotpink`.
1. Obarvi ikonu shodně s nadpisem

note:

- Abychom drželi shodnou barvu v rámci jednoho prvku, můžeme využít hodnotu `currentColor`.

---

##### Hodnota `currentColor`

- nastaví barvu podle aktuální hodnoty `color` daného prvku

```css
p {
    color: purple;
    border-color: currentColor; /* rovněž purple */
}
```

---

# HSLA barvy

- **h**ue <small>~ odstín</small> <span class="fragment fade-in">0–360</span>
- **s**aturation <small>~ sytost</small> <span class="fragment fade-in">0%–100%</span>
- **l**ightness <small>~ tmavost</small> <span class="fragment fade-in">0%–100%</span>
- **a**lpha channel <small>~ průsvitnost</small> <span class="fragment fade-in">0–1</span>

<span class="fragment fade-in">`background-color: hsla(120, 50%, 50%, 0.5)`</span>

note:

- obdobně RGBA barvy s alfa kanálem

---

## Odstín (hue)
<style>.reveal section img { width: auto; }</style>
![](https://ishadeed.com/assets/color-css/color-wheel-1.jpg)

<small>zdroj: https://ishadeed.com/article/css-color/</small>

---

## Sytost, tmavost, alfa kanál

- sytost: 0% => šedá, 100% plná barva
- tmavost: 0% => černá, 100% => bílá
- průsvitnost: 0 => zcela průhledná, 1 => neprůsvitná

note:

- průsvitnost: desetinná tečka
- popis barev lidským jazykem (oproti RGBA)
- hned si ukážeme další výhodu tohoto zápisu

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

note:

- podbarvení odkazů: bude to chtít přidat padding
- primární barva je v komentáři
- Trochu se nám ty barvy opakují. Hodilo by se je hodit do proměnné, ne?

---

# Proměnné vlastnosti
# (CSS Custom Properties)

note:

- mají mnohem širší použití, ale nám zatím postačí využít je jako prosté proměnné
- vytvoříme si barevné schéma

---

## Proměnné vlastnosti

```css
:root {
    --primary: hsla(160, 50%, 50%, 1); /* nastavení */
}

h1 {
    color: var(--primary); /* užití */
}

p {
    color: var(--text-color, #222); /* #222 je výchozí hodnota */
}
```


note:

- název uvozen vždy dvěma `--` název autorský (jako u tříd)
- jsou to vlastnosti, takže je nastavujeme vždy pro nějaký selektor
- `:root` je pseudotřída pro kořenový prvek, tj. `html`, má však vyšší specificitu, proto se hodí na základní nastavení „proměnných“, přebije případné výchozí hodnoty
- protože jsou to vlastnosti, podléhají kaskádě a dědičnosti, čehož využijeme k vytvoření barevného schématu
- lze nastavit i výchozí hodnotu pro případ, že proměnná zůstane z nějakého důvodu není nastavena

---

#### Cvičení 6

1. Nastav barevné proměnné (pro `:root`).
2. Nahraď přímo nastavené barvy u jednotlivých prvků proměnnými.

note:

- v devTools při najetí myši nad hodnotu s funkcí `var()` se v bublině ukáže hodnota proměnné vlastnoti

---

## Proměnné vlastnosti: zanořování

Funkci `var()` lze zanořovat do deklarace jiné proměnné:

```css
p {
    --primary-hue: 120;
    --primary: hsla(var(--hue), 50%, 50%, 1)
}
```
note:

- **ukázat**: vytvořit barevné schéma => výhoda HSLA zápisu barev

---

#### Cvičení 7

Zjednodušíme zápis pro pozadí receptů.

1. Pro všechny recepty nastav jednotný obrázek na pozadí: gradient a proměnnou  `--bg-recipe` s výchozí hodnotou SVG obrázek kuchařky
2. Uprav kód jednotlivých receptů: odstraň vlastnost `background-image` a nastav pro každý recept hodnotu proměnné `--bg-recipe`.

---

## Praktické využití pseudoelementů

Vylepšíme recepty!

note:

- za název rubriky doplníme emotikon _label_
- vhodně ostylujeme (ztučnit, kurzíva)

---

#### Cvičení 8

1. Najdi vhodný emotikon pro komentář (bublina?).
2. Úpravou CSS umísti emotikon před počet komentářů

---

# CSS animace

```css
.icon {
    animation-name: spin; /* název shodný s názvem za @keyframes */
    animation-duration: 2s; /* trvání animace */
    animation-iteration-count: infinite; /* počet opakování */
    animation-timing-function: linear; /* průběh animace */
}

@keyframes spin {
    from { /* výchozí stav prvku */ }

    to { /* koncový stav prvku */ }
}

```