---
title: Spojování CSV souborů
demand: 3
---

Stáhněte si v příkazové řádce do pracovního adresáře následující soubory:

```shell
https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/prohlizeni-textovych-souboru/assets/u202.csv
https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/prohlizeni-textovych-souboru/assets/u203.csv
https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/prohlizeni-textovych-souboru/assets/u302.csv
```

Soubory spojte do jednoho souboru. Bohužel ale není možné jednoduše použít `cat u*` - v datech by vám vadila hlavička z každého CSV. Ve výsledném souboru mějte hlavičku pouze jednou na prvním řádku. Můžete využívat různé dočasné pracovní soubory.
