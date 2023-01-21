## Čtení na doma

Ve zbytku kapitoly uvedu další ukázky, které je možné v linuxové příkazové řádce provádět s textem.

### Další možnosti příkazů head a tail

Vraťme se zpět k filtrování řádků. Víme, že k tomu můžeme použít program `grep`, pokud chceme vyhledat nějaký výskyt řetězce na řádku. Pokud chceme filtrovat podle čísla řádku, můžeme využít `head` nebo `tail`. Doposud jsme specifikovali, kolik chceme nechat řádků za začátku souboru nebo na konci souboru. Můžeme však i opačně říct, že chceme smazat určitý počet řádků z konce (`head` a číslo s prefixem `-`) nebo vypsat vše od určitého řádku do konce (`tail` a číslo s prefixem `+`).

Ekvivalentem k příkazu `sed '1d'` pro smazání hlavičky CSV souboru je také `tail -n +2`. Tento příkaz nám říká: vypiš konec souboru od řádku 2 dál. Co to znamená a jak to funguje si ukážeme na řadě čísel:

Výpis prvního řádku

```shell
$ seq 10 | head -n 1
1
```

Smazání posledního řádku

```shell
$ seq 10 | head -n -1
1
2
3
4
5
6
7
8
9
```

Výpis posledního řádku

```shell
$ seq 10 | tail -n 1
10
```

Smazání prvního řádku:

```shell
$ seq 10 | tail -n +2
2
3
4
5
6
7
8
9
10
```

Důležité je si zapamatovat, že `head` vždy vypisuje začátek souboru a `tail` vypisuje konec souboru. Pomocí prefixů `+` a `-` lze zpřesňovat toto chování.

### awk

Nejpokročilejším nástrojem, který si zde představíme, je program `awk`. Z doposud představených nástrojů má nejdelší manuálovou stránku. Jedná se interpret programovacího jazyka, který je určen pro práci s tabulkovými daty. Nástroje jako `sed` a `awk` už jsou pokročilejší věci, ale jejich použití pro složité problémy nemusí být vždy nejlepší volba. Dnes jdou některé úkoly řešit snadněji pomocí jazyka Python a jeho knihovny Pandas.

Výhoda `awk` podobně jako programu `sed` je však ta, že pracuje jako filtr a využívá unixový způsob práce se standardním textovým vstupem a výstupem a jeho propojení rourami. Tím se může plně integrovat se všemi ostatními nástroji, které jsme prozatím probrali.

Pro následující ukázku si vezměme sloupeček čísel a příkazů, které nám vyprodukovalo předchozí cvičení

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

Tyto data jsou hezky zarovnány, aby se dobře četly, ale pokud bychom si chtěli sloupce vyříznout, tak příkaz `cut` zde neuspěje. Jednotlivá pole totiž nejsou oddělena přesně jedním znakem.

```shell
$ awk '{print $1}' data.txt
1383
1167
786
759
398
313
209
203
187
168
```

```shell
$ awk '{print $2}' data.txt
cd
git
python
cat
gvim
vim
find
sudo
mv
ls
```

Příklad použití jazyka `awk` pro počítání s daty

```shell
$ awk 'BEGIN {sum = 0} {sum += $1} END {print sum}' data.txt
5573
```

Vytiskni řádky pouze pro třípísmenné příkazy

```shell
$ awk 'length($2) == 3 {print $0}' data.txt
   1167 git
    759 cat
    313 vim
```

Číslo uvozená znakem dolar `$` značí příslušné políčko v řádku (čísluje se zde od 1). `$0` znamená celý řádek.

Důležité je vědět, že síla programů `sed`, `awk` (a např. i `grep`) vyzní až s použitím regulárních výrazů. Nevadí, pokud jste programem `awk` spíše zmateni. Stačí si zapamatovat, že něco takového existuje. Programovací úsilí směřujte více např. k jazyku Python.
