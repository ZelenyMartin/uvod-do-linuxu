## Vyhledávání souborů

V další kapitole si ukážeme řešení situací, pro které by nám jednoduché použití hvězdiček a otazníků v shellu už nestačilo.

Pokud budeme potřebovat specifikovat soubory, které se nachází jinde než v aktuálním pracovním adresáři, např. ve složitější adresářové struktuře, můžeme použít program `find`. Tento program nám vyhledá soubory podle našeho zadání a vypíše nám jejich absolutní cesty na terminál.

```shell
$ find <kde vyhledávám> <co hledám>
```

Základní dva parametry, které příkaz `find` akceptuje, jsou:

1. Adresář, kde chceme vyhledávat - pokud tento parametr vynecháme, vyhledává se v aktuálním pracovním adresáři
1. Co hledáme - tady je to trochu složitější, protože zdaleka nemusíme vyhledávat pouze podle názvu souboru. Pokud chceme vyhledávat podle názvu, použijeme parametr `-name` následovaný již známým způsobem cesty specifikovaným pomocí hvězdiček a otazníků. Tento výraz ale musí být v jednoduchých nebo dvojitých uvozovkách! Pro jednoduchost si ukážeme vyhledávání pouze podle názvu, ale dodám jen, že je možné vyhledávat soubory například i podle stáří nebo velikosti.

Abychom si vše prakticky ukázali, budeme muset mírně odbočit do jiné části.

## Stažení a rozbalení pracovních dat

Pro stažení souboru [data.zip](assets/data.zip), který je uložen někde na webu, můžeme v prostředí příkazové řádky použít program `wget`.


```shell
$ wget https://kodim.cz/cms/assets/devops/uvod-do-linuxu/prikazova-radka/specifikace-cesty/vyhledavani-souboru/data.zip
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
