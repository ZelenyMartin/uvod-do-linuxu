V této kapitole se vrhneme na pokročilejší zpracování textových souborů.

## Řazení řádků a zpracování duplicit

Pro další práci si stáhneme nová pracovní data

```shell
$ wget https://kodim.cz/cms/assets/kurzy/uvod-do-linuxu/prikazova-radka/zpracovani-textu/names.txt
```

Využijme známé příkazy, abychom se s daty seznámili: `head`, `tail`, `wc -l`, `cat`, `less`

### Řazení příkazem sort

Příkazem `sort` si můžeme daný seznam jmen seřadit podle abecedy.

```shell
$ sort names.txt
```

Jak dosáhneme seřazení od Z do A? Hledej v manuálu.

### Řazení čísel

Pro další ukázku si vygenerujeme soubor deseti čísel pomocí příkazu `seq`

```shell
$ seq 10 > cisla.txt
$ cat cisla.txt
1
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

Zamícháme si řádky pomocí příkazu `shuf`.

```shell
$ shuf cisla.txt > nahodna_cisla.txt
```

Obecné textové řazení na číslech bohužel nefunguje, tak jak bychom si přáli

```shell
$ sort nahodna_cisla.txt
1
10
2
3
4
5
6
7
8
9
```

Jakým parametrem dosáhneme toho, aby se čísla seřadila správně? Hledej v manuálu.


### uniq

Příkaz `uniq` slouží k vyřazení duplicitních řádků. Funguje ale pouze, pokud se jedná o duplicitní řádky hned po sobě. Abychom dosáhli požadováného chování, musíme tento filtr aplikovat na seřazený soubor.

Počet jmen

```shell
$ sort names.txt | wc -l
100
```

Počet unikátních jmen

```shell
$ sort names.txt | uniq | wc -l
93
```

Zobrazení duplicitních hodnot

```shell
$ sort names.txt | uniq -d
Appleton
Campbell
Dempsey
Kelly
Reynolds
Ulyatt
Webster
```

Velmi užitečný je u příkazu `uniq` parametr `-c` - vytiskne nám počet výskytů daného řádku. Můžeme si pak seznam pomocí tohoto čísla seřadit

```shell
$ sort names.txt | uniq -c | sort -n | tail
      1 Widdows
      1 Wilkinson
      1 Willson
      2 Appleton
      2 Campbell
      2 Dempsey
      2 Kelly
      2 Reynolds
      2 Ulyatt
      2 Webster
```

## Nahrazování v textu

Další pracovní soubor obsahuje jména i příjmení.

```shell
$ wget https://kodim.cz/cms/assets/kurzy/uvod-do-linuxu/prikazova-radka/zpracovani-textu/fullnames.txt
```

### tr

Jednoduchý příkaz `tr` (translate) slouží k nahrazování znaků z množiny prvního parametru znaky z druhé množiny.

Náhrada mezer za tečky

```shell
$ cat fullnames.txt | tr ' ' '.'
Violet.Nielson
Adela.Flynn
Jenna.Turner
Ronald.Trent
Analise.Cooper
Doris.Leigh
Harry.Allen
Marie.Greenwood
Taylor.Murphy
Owen.Vass
```

Smazání určitých znaků dosáhneme použitím parametru `-d` následovaným množinou znaků, které chceme smazat (v tomto případě mezera).

```shell
$ cat fullnames.txt | tr -d ' '
VioletNielson
AdelaFlynn
JennaTurner
RonaldTrent
AnaliseCooper
DorisLeigh
HarryAllen
MarieGreenwood
TaylorMurphy
OwenVass
```

Program `tr` má více užitečných funkcí, např. náhrada všech velkých písmen malými.

```shell
$ cat fullnames.txt | tr '[[:upper:]]' '[[:lower:]]'
violet nielson
adela flynn
jenna turner
ronald trent
analise cooper
doris leigh
harry allen
marie greenwood
taylor murphy
owen vass
```

Nejdůležitější je si uvědomit, že program `tr` funguje podle jednotlivých znaků. Pro další ukázku si vytvoříme testovací soubor s tímto obsahem:

```
tým 1
tým 2
tým 3
```

Jak na to? Napíšeme-li příkaz
```shell
$ cat > tymy.txt
```

program bude čekat na standardní vstup, který přesměruje do souboru `tymy.txt`. Zkopírujte si text výše a vložte do čekajícího terminálu a zadávání textu ukončete klávesovou zkratkou :kbd[Ctrl+D].

Pokud budeme nyní chtít čísla týmu změnit na písmena bude fungovat

```shell
$ cat tymy.txt | tr '123' 'ABC'
tým A
tým B
tým C
```

### sed

Předchozí příklad použití programu `tr` je svou funkcionalitou omezen tím, že nahrazuje vždy pouze jeden znak. Co když budeme potřebovat v našich datech nahradit celé slovo jiným slovem? V tom nám pomůže jedna z funkcí pokročilejšího nástroje - programu `sed` (Stream EDitor).

Program `sed` využívá něco jako vlastní komplexní jazyk, díky kterému je ovšem i velmi mocný a lze jej využít na spoustu úkolů. My si ukážeme velmi častý příklad, a to využití příkazu `s` (substitute).

Budeme-li chtít nahradit v datech `fullnames.txt` mezeru za tečku pomocí sedu, napíšeme:

```shell
$ sed 's/ /./' fullnames.txt
Violet.Nielson
Adela.Flynn
Jenna.Turner
Ronald.Trent
Analise.Cooper
Doris.Leigh
Harry.Allen
Marie.Greenwood
Taylor.Murphy
Owen.Vass
```

První znak je požadovaný příkaz `s` (substitute), následuje oddělovač lomítko `/`, potom co chceme najít (mezeru) a za dalším lomítkem napíšeme, na co ji chceme změnit (tečka). Na konci nezapomeneme na uzavírací lomítko.

Lepší příklad bude nahrazení celého slova _tým_ za anglické _team_

**Pozor!** Parametr `-i` příkazu `sed` přepíše soubor, se kterým pracuje (in-place).

```shell
$ sed -i 's/tým/team/' tymy.txt
```


## Řezání sloupců

V této části si povíme něco o zjednoduššení možné práce např. s CSV soubory. Pro ukázku využijeme pracovní data z předchozího cvičení.

Pro vyřezávání sloupců slouží příkaz `cut`. Pro práci s CSV se nejčastěji využívá v kombinaci s parametry `-d` (delimiter) udávající oddělovač polí v CSV a `-f` (field) s číslem pole pro výřez.

```shell
$ cut -d ',' -f 1 u202.csv
jméno
Jana Zbořilová
Lukáš Jurčík
Pavel Horák
Lukáš Jurčík
Pavel Kysilka
Kateřina Novotná
Marie Krejcárková
Vasil Lácha
Alexey Opatrný
Petr Valenta
Miroslav Bednář
Pavel Horák
Ivana Dvořáková
Lenka Jarošová
Miroslav Bednář
```

Využijme pipe a vyextrahujme si dále pouze příjmení studentů

```shell
$ cut -d, -f1 u202.csv | cut -d' ' -f2
jméno
Zbořilová
Jurčík
Horák
Jurčík
Kysilka
Novotná
Krejcárková
Lácha
Opatrný
Valenta
Bednář
Horák
Dvořáková
Jarošová
Bednář
```

## Filtrování řádků

Hlavičky CSV souboru se zbavíme pomocí příkazu `sed`. V jeho jazyce lze použít příkaz `d` (delete), kterému předchází číslo řádku, které chceme ze vstupu smazat.

```shell
$ seq 10 | sed '1d'
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

Výsledkem této části může být např. seřazený seznam příjmení studentů

```shell
$ cut -d, -f1 u202.csv | cut -d' ' -f2 | sed '1d' | sort | uniq
Bednář
Dvořáková
Horák
Jarošová
Jurčík
Krejcárková
Kysilka
Lácha
Novotná
Opatrný
Valenta
Zbořilová
```

## Cvičení
::exc[excs>history]
