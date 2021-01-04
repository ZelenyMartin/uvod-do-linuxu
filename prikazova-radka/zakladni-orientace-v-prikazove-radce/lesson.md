Pokud už před sebou vidíme spuštěné okno s terminálem, řekneme si něco málo o čem to vlastně budeme mluvit.

## Terminál == konzole == příkazová řádka == shell
Tyto výrazy mají k sobě velmi blízko a budeme je považovat za synonyma. V angličtině se jedná analogicky o výrazy: _Terminal_, _Console_ a _Command Line_ (často ve spojení _Command Line Interface_, zkráceně _CLI_). _Shell_ je označení typu programů pracujících jako interpret příkazové řádky. Konkrétně _Bash_ bývá častým linuxovým shellem.

Terminál realizuje textové vstupně/výstupní rozhraní s počítačem. Jednoduše řečeno počítači na klávesnici zadáme příkaz v podobě textu ukončený klávesou _Enter_. A výstupem bude text s výsledkem příkazu, který nám počítač vypíše.

## Prompt
První text, který v okně terminálu vidíme je tzv. _prompt_ (anglické slovo, které znamená _výzva_, _pobídka_). V _promptu_ nám operační systém sděluje nějaké základní důležité informace, abychom je měli vždy na očích. Formát _promptu_ není pevně dán a různé distribuce Linuxu a MacOS zde mohou vypisovat různé informace. Stejně tak si můžeme _prompt_ nastavit sami tak, aby nám vyhovoval. Nejčastěji je zde uživatelské jméno přihlášeného uživatele, název počítače a pracovní adresář (popř. celá cesta), kde se uživatel nachází. Znak `~` (tilda) je zástupný symbol pro náš domovský adresář.


## Nejdůležitější klávesy
Než se vrhneme na příkazy povíme si něco o velmi důležitých klávesách, které nám usnadní práci s terminálem.

* Enter - spuštění příkazu
* Šipka nahoru - vyvolání předchozího příkazu (opakovaným stisknutím je možné procházet historii)
* Tabulátor - doplňování příkazů nebo cesty

## První příkazy
**POZOR!** Symbol dolaru na začátku příkazu se do terminálu nepíše. Jedná se o všeobecně rozšířenou konvenci v psaní návodů a dokumentace, abychom odlišili, že se jedná o příkaz v terminálu.

### Kde se nacházím a co tam je?
```shell
$ pwd
```

Příkaz `pwd` vypíše absolutní cestu pro aktuální pracovní adresář (_Print Working Directory_). Často máme tuto informaci dostupnou přímo v _promptu_.

```shell
$ ls
$ ls -l
$ ls -la
```

Příkaz `ls` vypíše seznam souborů a adresářů v aktuálním pracovním adresáři (_list_). Jedná se o jeden z nejpoužívanějších příkazů při práci v příkazové řádce. Pokud se nám nelíbí, že se obsah vypsal vedle sebe, ale chtěli ho bychom viděl raději pod sebou, použijeme _parametr_ `-l` (_long_), který nám navíc vypíše spoustu další užitečných informací.

Parametr `-a` (_all_) navíc vypíše i takové podivné věci jako `.` (tečka) a `..` (dvě tečky). To jsou podobně jako `~` další zástupné symboly a značí

* `.` aktuální pracovní adresář
* `..` nadřazený adresář (adresář, který je o jednu úroveň nad našim pracovním adresářem)

Pro úplnost dodám, že parametr `ls -a` vypíše i soubory a adresáře začínající tečkou, což je konvence pro "skryté soubory a adresáře".

### Parametry == argumenty
Nyní jsme si ukázali, že můžeme chování nějakého příkazu upravit pomocí _parametrů_. Slova _parametry_ a _argumenty_ budeme opět považovat za synonyma. Pokud chceme zkombinovat parametry `-l` a `-a` příkazu `ls` ušetříme pár znaků zápisem `ls -la`. Na pořadí parametrů v tomto případě nezáleží, tzn. funguje i `ls -al`.


## Absolutní a relativní cesta

Nejprve si zopakujeme si speciální symboly, které se nám mohou v cestě vyskytovat

* `~` domovský adresář
* `.` aktuální pracovní adresář
* `..` nadřazený adresář

Jako novou věc si něco povíme o lomítku

* `/` začátek absolutní cesty

Rozlišení absolutní a relativní cesty ve velice jednoduché

* Začíná-li cesta lomítkem, jedná se o absolutní cestu
* Nezačíná-li cesta lomítkem, jedná se o relativní cestu

Cesta je hierarchická posloupnost adresářů na disku. Lomítko `/` se používá i na oddělení názvů těch adresářů. Základní rozdíly oproti Windows jsou ty, že Windows používá jako oddělovač zpětné lomítko `\` a na začátku absolutní cesty má název diskové jednotky, např. `C:\` nebo `D:\`. Linux toto nerozlišuje. Začátek je vždy jen jeden: `/` a diskové jednotky mohou být napojeny hierarchicky někam za toto lomítko.

Jak to přesně funguje se zatím nemusíte trápit. Budeme pracovat výhradně v našem domovském adresáři.

Když jsme si řekli, že _absolutní cesta_ začíná začátkem našeho kompletního hierarchického stromu adresářů (lomítkem `/`), je nutné zmínit, že _relativní cesta_ začíná našim pracovním adresářem.


## Procházení adresářů

Absolutní a relativní cestu zmiňujeme z toho důvodu, že pro mnoho příkazů očekává cestu jako svůj parametr na příkazové řádce.
