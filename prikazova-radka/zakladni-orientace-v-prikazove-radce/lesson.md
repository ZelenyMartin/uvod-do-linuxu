Pokud už před sebou vidíme spuštěné okno s terminálem, řekneme si co si v něm můžeme přečíst a hlavě co do něj můžeme napsat.

## Prompt
První text, který v okně terminálu vidíme je tzv. _prompt_ (anglické slovo, které znamená _výzva_, _pobídka_). V _promptu_ nám operační systém sděluje nějaké základní důležité informace, abychom je měli vždy na očích. Formát _promptu_ není pevně dán a různé distribuce Linuxu a MacOS zde mohou vypisovat různé informace. Stejně tak si později můžeme _prompt_ nastavit sami tak, aby nám vyhovoval. Nejčastěji je zde uživatelské jméno přihlášeného uživatele, název počítače a pracovní adresář (popř. celá cesta), kde se uživatel nachází. Znak `~` (tilda) je zástupný symbol pro náš domovský adresář.


## Nejdůležitější klávesy
Než se vrhneme na příkazy povíme si něco o velmi důležitých klávesách, které nám usnadní práci s terminálem.

* Enter - spuštění příkazu
* Šipka nahoru - vyvolání předchozího příkazu (opakovaným stisknutím je možné procházet historii)
* Tabulátor - doplňování příkazů nebo cesty (napíšeme část příkazu nebo cesty a tabulátor nám doplní zbytek)


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

Tyto nejjednodušší jednopísmenné parametry příkazů se uvozují pomlčkou/minusem a jedná se opět o konvenci napříč všemi příkazy a programy v linuxové příkazové řádce.


## Jak _shell_ pozná co má spustit?
V této části si také povíme co to vlastně jsou ty příkazy, které do příkazové řádky píšeme. Z pohledu linuxového shellu se totiž jedná o samostatné spustitelné programy, které se mohou doplnit o příslušné parametry a po spuštění něco udělají. A jak _shell_ pozná jestli to slovo, které v něm spustíme je název nějakého programu? Musí si ho totiž v počítači vyhledat.

Takové vyhledávání programu je naštěstí docela rychlé, a jednoduché. V běžícím _shellu_ je definovaná tzn. _proměnná prostředí_ s názvem `PATH` a ta obsahuje absolutní cesty k adresářům, kde se v systému nachází spustitelné programy. Shell se automaticky podívá do všech těchto adresářů a první program, který vyhovuje hledanému názvu, spustí. Pro zájemce navíc dodám, že tyto cesty si můžeme zobrazit pomocí příkazu `echo $PATH` (jedná se o seznam absolutních cest oddělený dvojtečkou `:`).


## Absolutní a relativní cesta

Nejprve si zopakujeme speciální symboly, které se nám mohou v cestě vyskytovat

* `~` domovský adresář
* `.` aktuální pracovní adresář
* `..` nadřazený adresář

Jako novou věc si něco povíme o lomítku

* `/` začátek absolutní cesty

Rozlišení absolutní a relativní cesty ve velice jednoduché

* Začíná-li cesta lomítkem, jedná se o absolutní cestu
* Nezačíná-li cesta lomítkem, jedná se o relativní cestu

Cesta je hierarchická posloupnost adresářů na disku. Lomítko `/` se používá i na oddělení názvů těchto adresářů. Základní rozdíly oproti Windows jsou ty, že Windows používá jako oddělovač zpětné lomítko `\` a na začátku absolutní cesty má název diskové jednotky, např. `C:\` nebo `D:\`. Linux toto nerozlišuje. Začátek je vždy jen jeden: `/` a diskové jednotky mohou být napojeny hierarchicky někam za toto lomítko.

Jak to přesně funguje se zatím nemusíte trápit. Budeme pracovat výhradně v našem domovském adresáři.

Když jsme si řekli, že _absolutní cesta_ začíná začátkem našeho kompletního hierarchického stromu adresářů (lomítkem `/`), je nutné zmínit, že _relativní cesta_ začíná našim pracovním adresářem.

Uvedeme si pár příkladů:
* `~` relativní cesta k našemu domovskému adresáři
* `/home/martin` absolutní cesta k domovskému adresáři uživatele `martin`
* `..` relativní cesta k nadřazenému adresáři
* `Dokumenty` relativní cesta k adresáři `Dokumenty` v našem pracovním adresáři
* `~/Dokumenty` relativní cesta k adresáři `Dokumenty` v našem domovském adresáři
* `Dokumenty/faktury` delší ukázka cesty
* `Dokumenty/faktury/2021` ještě delší ukázka cesty


## Procházení adresářů

Absolutní a relativní cestu zmiňujeme z toho důvodu, že mnoho příkazů očekává cestu jako svůj parametr na příkazové řádce.

Jedním z těchto příkazů je i již zmíněný příkaz `ls`, který umí zobrazit obsah adresáře na dané cestě. Tato cesta může být uvedena jak absolutní, tak relativní. Pouze pokud tento parametr není uveden, zobrazí se obsah pracovního adresáře.

Samotnou změnu pracovního adresáře provedeme příkazem `cd` (_Change Directory_), kde jako parametr příkazu napíšeme cestu k adresáři kam se chceme přesunout. Pokud toto vynecháme a spustíme příkaz `cd` bez parametru, přesuneme se do našeho domovského adresáře (jako kdybychom napsali `cd ~`).

Uvedeme si pár příkladů:
* `cd Dokumenty` přesun do adresáře `Dokumenty`
* `cd Dokumenty/faktury` přesun do adresáře `faktury`, který se nachází v adresáři `Dokumenty`
* `cd ..` přesun do nadřazeného adresáře (přesun o jednu úroveň nahoru)
* `cd ../..` přesun o dvě úrovně nahoru

Všechny přesuny si můžeme kontrolovat tak, že se nám aktuální pracovní adresář zobrazí v _promptu_, popř. použijeme příkaz `pwd`.

Zmíním ještě hezký tip, který nám pomůže, pokud uděláme v cestě chybu a pracovní adresář se nám změní na nějaký, který jsme nechtěli: pro přesun do adresáře, který byl našim předchozím pracovním adresářem napíšeme `cd -`.


## Cvičení
* Vyzkoušejte si samostatně příkazy `pwd`, `ls` a `cd`
* Ověřte jak funguje šipka nahoru a tabulátor
