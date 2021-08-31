Prozatím jsme pracovali s adresářovou strukturou a prázdnými soubory. Teď se podíváme jak prozkoumat obsah souboru.

## Stažení a prohlížení ukázkového souboru
Jako ukázkový soubor si stáhneme zdrojový kód textu této lekce ve formátu Markdown. Budeme na tento soubor nahlížet jako na obyčejný textový soubor.

```shell
$ wget https://raw.githubusercontent.com/ZelenyMartin/uvod-do-linuxu/master/prikazova-radka/prohlizeni-textovych-souboru/lesson.md
```

Příkaz pro vypsání obsahu souboru se jmenuje _cat_.

```shell
$ cat lesson.md
```

Název příkazu `cat` nemá nic společného s kočkou. Jedná se o zkratku anglického výrazu _concatenate_, což znamená zřetězení. Příkaz `cat` umí nejen vypsat jeden soubor, ale všechny soubory, které jsou mu předány jako parametry příkazové řádky.

Pro ukázku k čemu je to dobré si stáhněme další testovací soubory.

```shell
$ wget https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/prohlizeni-textovych-souboru/assets/data1.txt
$ wget https://kodim.cz/czechitas/uvod-do-linuxu/prikazova-radka/prohlizeni-textovych-souboru/assets/data2.txt
```

Jednotlivě si zobrazme obsahy souborů.

```shell
$ cat data1.txt
31
15
86
10
82
24
$ cat data2.txt
69
21
13
20
24
71
```

Dohromady si soubory vypíšeme.

```shell
$ cat data1.txt data2.txt
```

S předchozí kapitoly můžeme použít i zástupné znaky.

```shell
$ cat data*
```

Pomocí znaku "větší než", který si nyní představme jako šipku, můžeme výpis přesměrovat do nového souboru.

```shell
$ cat data1.txt data2.txt > data_all.txt
```

## Přehlednější zobrazení souboru

Vrátíme-li se k příkladu vypsání obsahu souboru `lesson.md`, uvidíme, že pokud je počet řádků souboru větší než výška našeho terminálu, musím na začátek souboru scrollovat kolečkem. Někdy je tento způsob dost nepřehledný, protože se nám začátek textového souboru vizuálně smísí s předchozím textem v našem terminálu a nevidíme pořádně, kde soubor vlastně začíná.

Abychom si pomohli, představíme si další příkazy pro prohlížení souborů.

```shell
$ head lesson.md
```

Příkaz _head_ vypíše začátek souboru. Ve výchozím nastavení vypisuje prvních 10 řádků souboru. Toto je možné upravit parametrem _-n_.

```shell
$ head -n 5 lesson.md
```

Podobně funguje příkaz _tail_, který naopak vypisuje poslední řádky souboru.


```shell
$ tail lesson.md
```

```shell
$ tail -n 5 lesson.md
```

Posledním hezkým nástrojem pro zobrazení souboru je program _less_. Tento příkaz, podobně jako program _man_, funguje interaktivně a na celý terminál nám zobrazí obsah souboru. Také nám umožní souborem procházet pomocí šipky nahoru a dolu a kláves Home a End. Neméně důležitou funkcionalitou je interaktivní vyhledávání, které spustíme klávesou lomítko _/_, na další výskyt vyhledávaného textu se posuneme klávesou _n_ a na předchozí výskyt velkým _N_. Program `less` ukončíme opět klávesou _q_.

```shell
$ less lesson.md
```

