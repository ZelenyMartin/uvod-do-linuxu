---
title: Zpracování souboru historie příkazů
demand: 3
---

Linuxový shell Bash ukládá všechny příkazy, které spouštíme do souboru `.bash_history` uložený v našem domovském adresáři. Využívá se např. pro příkaz `history`, který vypíše vše co jsme dříve do terminálu zadávali. Obsah souboru si můžete zobrazit pomocí:

```shell
$ cat ~/.bash_history
```

Vypište 10 vašich nejpoužívanějších příkazů (neuvažujte parametry příkazů - vyřízněte příkazy bez jejich parametrů). Výstup může vypadat např.

```shell
   1383 cd
   1167 git
    786 python
    759 cat
    398 gvim
    313 vim
    209 find
    203 sudo
    187 mv
    168 ls
```
