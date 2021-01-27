Procházet si svůj domovský adresář může být na začátku nuda, obzvláště, pokud v něm nic není. Naučíme se jak adresáře a soubory vytvářet, mazat, přesouvat a kopírovat

## Nové adresáře a prázdné soubory
```shell
touch <soubor>
```

Příkazem `touch` (dotknout) vytvoříme prázdný soubor. Prozatím si nemusíme lámat hlavu k čemu nám je vytvářet prázdné soubory. Potřebujeme je jen, abychom viděli i něco jiného než adresáře. Za podivným názvem příkazu `touch` stojí jeho hlavní funkcionalita, a to aktualizace _timestamp_ (časového údaje posledního přístupu k souboru) existujícího souboru. Toto uvádím jen pro úplnost a více se tím zabývat nemusíme.

```shell
mkdir <adresář>
```

Podobně jako v předchozím příkladu můžeme vytvořit adresář pomocí příkazu `mkdir` (_Make Directory_). Nabízí se nám i možnost vložit jako parametr celou delší cestu složenou z více adresářů. Pokud bychom však napsali např. `mkdir faktury/2021`, ale žádný adresář `faktury` bychom v pracovním adresáři neměli, nefungovalo by to. Tento nedostatek se však hravě opraví doplněním parametru `-p`.

```shell
mkdir -p <adresář>/<podadresář>
```

## Mazání souborů a adresářů
**Pozor!** Příkazová řádka nemá žádný koš! Cokoliv smažeme pomocí následujících příkazů se nedá nijak obnovit.

```shell
rm <soubor>
```

Prostě odstraníme soubor (_remove_). V některých prostředích se však může příkaz `rm` volat ve skutečnosti jako `rm -i`, kde se nám zobrazí otázka, jestli opravdu chceme tento příkaz odstranit a my na ni musíme odpovědět `y` (_yes_).

```shell
rmdir <prázdný adresář>
```
Tímto odstraníme adresář (_remove directory_). Pozor - příkaz funguje pouze na prázdné adresáře. Je to taková pojistka, abychom si omylem neodstranili něco, čeho bychom litovali. Pokud se v adresáři, který chceme smazat něco nachází, musíme to smazat jako první.

```shell
rm -r <adresář se soubory>
```
Jistě se vám taková pojistka zdá dost omezující. Vyřešit se to dá příkazem `rm -r`, který aplikujeme na adresář se soubory, který chceme smazat. Parametr `-r` znamená _rekurzivně_. Pod tímto slovem si představme, že se mazací operace aplikuje nejprve na vše co je uvnitř a pak na adresář samotný. A pokud se v tomto adresář opět nachází adresář s nějakým obsahem? Operace se zas opakuje. To je význam slova _rekurze_.

Poslední věc z oblasti mazání souborů a adresářů je velmi silná kombinace:

```shell
rm -rf
```

Tento příkaz rekurzivně smaže vše co mu předhodíme a na nic se nás ptát nebude (`-f` znamená _force_)

Příkazy pro vytváření a mazání umí pracovat i s více parametry. Pokud chceme naráz vytvořit více souboru příkazem `touch` nebo více adresářů příkazem `mkdir`, můžeme jejich názvy naskládat jako parametry příkazové řádky za sebe spustit jedním stiskem klávesy _Enter_. Stejně funguje i jejich mazání pomocí `rm` či `rmdir`.

## Kopírování a přesun
Poslední základní znalost práce se soubory a adresáři v linuxové příkazové řádce spočívá v jejich kopírování a přesouvání.

```shell
cp <soubor> <cíl>
```

Kopírování provádíme příkaze `cp`, který má dva povinné parametry a to, soubor, který chceme kopírovat a _kam_ to chceme nakopírovat (do jakého adresáře).

Alternativně funguje tento příkaz k vytvoření kopie souboru, pokud jako parametr _cíl_ není zvolen existující adresář, ale nový název souboru.

```shell
cp -r <adresář> <cíl>
```

Podobně jako u mazání příkaz `cp` automaticky nepřesouvá celé adresářové struktury. Pokud toho chceme docílit musíme použít parametr `-r` (kopíruj rekurzivně).

```shell
mv <zdroj> <cíl>
```

Příkaz `mv` má dvě základní funkce:
* Přesun souboru nebo adresáře do jiného adresáře (_move_), pokud je _cíl_ existující adresář
* Přejmenování souboru nebo adresáře na cílové jméno

U příkazů pro kopírování a přesun může být parametrů _co_ se má kopírovat více, jak poslední musí být vždy cílový adresář.


## Jak to hezky zobrazit
```shell
tree
```

Pokud se vám zdá že práce se soubory a adresáři je v prostředí příkazové řádky nesmírně nepřehledná věc, vyzkoušejte příkaz `tree`, který vám vytiskne obsah všech adresářů v nižších úrovních do přehledné stromové struktury.

## Cvičení
Dostali jste za úkol vytvořit ve vašem domovském adresáři adresář _data_, v něm podadresáře s názvy posledních tří let: _2021_, _2020_, _2019_. V každém adresáři vytvořte podadresáře pro každý kvartál: _Q1_, _Q2_, _Q3_, _Q4_.

Obsah adresáře `data` má vypadat:

```shell
.
├── 2019
│   ├── Q1
│   ├── Q2
│   ├── Q3
│   └── Q4
├── 2020
│   ├── Q1
│   ├── Q2
│   ├── Q3
│   └── Q4
└── 2021
    ├── Q1
    ├── Q2
    ├── Q3
    └── Q4
```

Váš šéf si rozmyslel, že nechce sledovat data po kvartálech, ale podle pololetí. Upravte strukturu na:

```shell
.
├── 2019
│   ├── H1
│   └── H2
├── 2020
│   ├── H1
│   └── H2
└── 2021
    ├── H1
    └── H2
```
