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
