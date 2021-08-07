Pokud se vám už ze všech příkazů a jejich parametrů točí hlava, v této kapitole si ukážeme kde hledat nápovědu.

## Manuálové stránky

Pokud se vám zatím zdá, že práce v linuxové příkazové řádce spočívá především v tom pamatovat si všechny příkazy a všechny jejich parametry, ujistím vám, že tak to rozhodně není. Příkazů v Linuxu existuje nesmírně velké množství a s každou novou verzí nějaké distribuce přichází nové programy a naopak zastaralé programy se přestávají používat.

Abychom v tom všem měli přehled, velká většina příkazů má i svou vlastní manuálovou stránku. Manuál zobrazíme programem `man`. Doposud všechny příkazy, které jsme zkoušeli fungovaly tak, že něco udělali (např. `cp`, `mv`, `mkdir`) popř. něco vypsali na terminál (`ls`, `pwd`). Program `man` funguje tak, že na celé okno terminálu zobrazí příslušnou manuálovou stránku a náš důvěrně známy prompt nám zmizí.

Vyzkoušejte si zobrazit manuálovou stránku některého příkazu, který jsme si dosud ukázali, např.

```shell
$ man ls
```

Zobrazí se nám

```
LS(1)                             User Commands                            LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about  the  FILEs  (the current directory by default).
       Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..
Manual page ls(1) line 1 (press h for help or q to quit)
```

Nejdůležitější je poslední řádek, který nám říká, že zobrazení manuálu ukončíme klávesou _q_. Pro pohyb dolů ve stránce můžeme použít šipku dolů.

Zcela přiznávám, že čtení a pochopení obsahu manuálových stránek je pro začátečníka náročná věc. Manuálové stránky jsou psané specifickou IT angličtinou plnou výrazů, které nikde nejsou vysvětleny a člověk musí jejich význam opět hledat.


### Výhody používání manuálových stránek

S největší pravděpodobností jako většina začátečníků nebudete mít manuálové stránky v oblibě. Proč používat textový manuál v terminálu, když existuje web a cokoliv si můžeme vygooglit? Pokusím se pár bodů na obhajobu manuálu uvést:

* Přesnost dokumentace - pokud si zobrazíte manuálovou stránku nějakého příkazu, můžete se spolehnout, že bude reflektovat skutečnost. Pokud tvůrce nějakého programu upraví chování nějakého přepínače nebo přidá novou funkcionalitu, vždy bude odpovídajícím způsobem upravena i manuálová stránka. Pokud byste řešení vašeho problému googlili, můžete najít odpovědi, které se budou vztahovat k úplně jiné verzi programu nebo k jiné distribuci a vám tyto rady nemusí fungovat.
* Rychlost - manuál je skutečně brán jako příručka, kterou berete do ruky a rychle v ní vyhledáte to, co potřebujete najít. Nemusíte opouštět terminál, protože si chcete jen zobrazit konkrétní část nějaké manuálové stránky, kterou jste si už zobrazili stokrát ještě tisíckrát si ji v budoucnu zobrazíte. Nikdo po vás nechce se něco učit nazpaměť, když máme manuál.
* Kompaktnost a úplnost - manuálová stránka není nikdy příliš dlouhá. Příklady použití bývají pouze u některých příkazů. Přesto se můžete spolehnout, že seznam argumentů bude kompletní.

I když budete možná s manuálem bojovat, dejte mu občas šanci. Pokud si přeci jen zjistíte co potřebujete přes Google na Stack Overflow, vraťte se do manuálu a pokuste se informaci ověřit i tam. Časem mu jistě přijdete na chuť.


### Ovládání manuálu

Zatím umíme manuál zobrazit, ukončit pomocí _q_ a "scrolovat" pomocí šipek. Velká výhoda toho manuál v počítači je vyhledávání. Chceme-li cokoliv na příslušné stránce najít, spustíme si vyhledávání pomocí lomítka _/_. Každý následující případ vyhledávaného slova dostaneme klávesou _n_ (next). Na předchozí výskyt použijeme velké _N_.

Velmi výhodné pro začátečníka je možnost vyhledávat přes _všechny manuálové stránky_ v počítači. V tom případě musíme manuál spustit s parametrem _-k_ pro seznam stránek, popř. _-K_ pokud chceme stránky rovnou zobrazovat.

```shell
$ man -k <slovo>
```

### Syntaxe příkazů podle manuálu

Na začátku každé manuálové stránky hned po názvu je odstavec _SYNOPSIS_. U této části popíšu obvyklou konvenci jak se příkazy zapisují. Některé příkazy vyžadují nějaký argument, jinak by jejich vykonání nemělo smysl, např. `touch` nebo `mkdir`. Tuto informaci se dozvíte v odstavci SYNOPSIS (nebo pokud příkaz chybně spustíte).

V jiných případech jsou zde uvedeny příklady volitelných argumentů:

* `[OPTION]` - volitelný parametr je uveden v hranatých závorkách `[` a `]`
* `[OPTION]...` - možnost více parametrů je znázorněno pomocí třech teček `...`

Zmínil jsem, že pokud nenastavíme příkaz dobře (např. vynecháme povinný argument), příkaz po spuštění nic neudělá, ale často nám vypíše nápovědu. Tuto nápovědu můžeme podle konvence zobrazit pomocí parametru _-h_ nebo _--help_.

