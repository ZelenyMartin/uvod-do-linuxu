Nyní si ukážeme první podstatné zrychlení a zjednodušení práce při použití příkazové řádky.

## Specifikace cesty
Pro další ukázku si vytvoříme nový pracovní adresář `soubory` a v něm několik prázdných souborů:

```shell
$ mkdir soubory
$ cd soubory
$ touch data1.csv data1.json dataA.csv dataA.json moje_data.txt
```

Vytvořili jsme si soubory různých přípon. Pokud chceme nyní vylistovat pouze soubory s příponou csv, můžeme to udělat pomocí:
```shell
$ ls *.csv
```

Hvězdičku jsme použili jako zástupný znak, který vyjadřuje libovolnou posloupnost znaků (0-N). Další příklady specifikace souborů:
```shell
ls data1*
ls *data*
```

Další speciální symbol je otazník _?_. Ten specifikuje přesně jeden zástupný znak. Vytvořme si v pracovním adresáři další testovací soubory:
```shell
$ touch data10.csv data100.csv dataAAA.csv dataBBB.csv
```

Pomocí následujícího příkazu vylistujeme pouze ty soubory, které mají mezi názvem _data_ a příponou přesně jeden znak:
```shel
$ ls data?.*
data1.csv  data1.json  dataA.csv  dataA.json
```

Tento způsob nahrazování znaků v názvech souborů a adresářů se nazývá _glob_.

[[[ excs Cvičení
- glob
]]]

## Vyhledávání souborů

V další kapitole si ukážeme řešení situací, pro které by nám jednoduché použití hvězdiček a otazníků v shellu už nestačilo.

Pokud budeme potřebovat specifikovat soubory, které se nachází jinde než v aktuálním pracovním adresáři, např. ve složitější adresářové struktuře, můžeme použít program `find`. Tento program nám vyhledá soubory podle našeho zadání a vypíše nám jejich absolutní cesty na terminál.

```shell
$ find <kde vyhledávám> <co hledám>
```

Základní dva parametry, které příkaz `find` akceptuje je:

1. Adresář, kde chceme vyhledávat - pokud tento parametr vynecháme, vyhledává se v aktuálním pracovním adresáři
1. Co hledáme - tady je to trochu složitější, protože zdaleka nemusíme vyhledávat pouze podle názvu souboru. Pokud chceme vyhledávat podle názvu, použijeme parametr `-name` následovaný již známým způsobem cesty specifikovaným pomocí hvězdiček a otazníků. Tento výraz ale musí být v jednoduchých nebo dvojitých uvozovkách! Pro jednoduchost si ukážeme vyhledávání pouze podle názvu, ale dodám jen, že je možné vyhledávat soubory například i podle stáří nebo velikosti.

Abychom si vše prakticky ukázali, budeme muset mírně odbočit do jiné části.

## Stažení a rozbalení pracovních dat

Pro stažení souboru, který je uložen někde na webu, můžeme v prostředí příkazové řádky použít program `wget`.

```shell
$ wget https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/specifikace-cesty/assets/data.zip
```

Následně si soubor s příponou `.zip` rozbalíme. Použijeme k tomu program `unzip`.

```shell
$ unzip data.zip
```

## Příklady použití příkazu find

```shell
$ find -name '*.json'
```

```shell
$ find -name 'Q1*'
```

```shell
$ find -name '*CZ*'
```

```shell
$ find -name '*CZ*' -or -name '*SK*'
```

