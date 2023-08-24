Procházet si svůj domovský adresář může být na začátku nuda, obzvláště, pokud v něm nic není. Naučíme se jak adresáře a soubory vytvářet, mazat, přesouvat a kopírovat

## Nové adresáře a prázdné soubory
Následující ukázky příkazů obsahují ukázku parametru mezi `<` a `>`. To je opět konvence. Při zkoušení příkazů si tam doplňte sami vhodný název.

```shell
$ touch <soubor>
```

Příkazem `touch` (dotknout) vytvoříme prázdný soubor. Prozatím si nemusíme lámat hlavu, k čemu nám je vytvářet prázdné soubory. Potřebujeme je jen, abychom viděli i něco jiného než adresáře. Za podivným názvem příkazu `touch` stojí jeho hlavní funkcionalita, a to aktualizace _timestamp_ (časového údaje posledního přístupu k souboru). Toto uvádím jen pro úplnost a více se tím zabývat nemusíme.

```shell
$ mkdir <adresář>
```

Podobně jako v předchozím příkladu můžeme vytvořit adresář pomocí příkazu `mkdir` (make directory). Nabízí se nám i možnost vložit jako parametr celou delší cestu složenou z více adresářů. Pokud bychom však napsali např. `mkdir faktury/2021`, ale žádný adresář `faktury` bychom v pracovním adresáři neměli, nefungovalo by to. Tento nedostatek se však hravě opraví doplněním přepínače `-p`.

```shell
$ mkdir -p <adresář>/<podadresář>
```

## Mazání souborů a adresářů
**Pozor!** Příkazová řádka nemá žádný koš! Cokoliv smažeme pomocí následujících příkazů, se nedá nijak obnovit.

```shell
$ rm <soubor>
```

Prostě odstraníme soubor (remove). V některých prostředích se však může příkaz `rm` volat ve skutečnosti jako `rm -i`, kde se nám zobrazí otázka, jestli opravdu chceme tento příkaz odstranit, a my na ni musíme odpovědět `y` (yes).

```
$ rmdir <prázdný adresář>
```
Tímto odstraníme adresář (remove directory). Pozor - příkaz funguje pouze na prázdné adresáře. Je to taková pojistka, abychom si omylem neodstranili něco, čeho bychom litovali. Pokud se v adresáři, který chceme smazat, něco nachází, musíme to smazat jako první.

```shell
$ rm -r <adresář se soubory>
```
Jistě se vám taková pojistka zdá dost omezující. Vyřešit se to dá příkazem `rm -r`, který aplikujeme na adresář se soubory, který chceme smazat. Parametr `-r` znamená _rekurzivně_. Pod tímto slovem si představme, že se mazací operace aplikuje nejprve na vše, co je uvnitř, a pak na adresář samotný. A pokud se v tomto adresář opět nachází adresář s nějakým obsahem? Operace se zas opakuje. To je význam slova _rekurze_.

Poslední věc z oblasti mazání souborů a adresářů je velmi silná kombinace:

```shell
$ rm -rf <adresář se soubory>
```

Tento příkaz rekurzivně smaže vše, co mu předhodíme, a na nic se nás ptát nebude (`-f` znamená force)

Příkazy pro vytváření a mazání umí pracovat i s více parametry. Pokud chceme naráz vytvořit více souboru příkazem `touch` nebo více adresářů příkazem `mkdir`, můžeme jejich názvy naskládat jako parametry příkazové řádky za sebe spustit jedním stiskem klávesy :kbd[Enter]. Stejně funguje i jejich mazání pomocí `rm` či `rmdir`.

## Kopírování a přesun
Poslední základní znalost práce se soubory a adresáři v linuxové příkazové řádce spočívá v jejich kopírování a přesouvání.

```shell
$ cp <soubor> <cíl>
```

Kopírování provádíme příkaze `cp`, který má dva povinné parametry, a to soubor, který chceme kopírovat, a kam to chceme nakopírovat (do jakého adresáře).

Alternativně funguje tento příkaz k vytvoření kopie souboru, pokud jako parametr _cíl_ není zvolen existující adresář, ale nový název souboru.

```shell
$ cp -r <adresář> <cíl>
```

Podobně jako u mazání příkaz `cp` automaticky nepřesouvá celé adresářové struktury. Pokud toho chceme docílit, musíme použít parametr `-r` (kopíruj rekurzivně).

```shell
$ mv <zdroj> <cíl>
```

Příkaz `mv` má dvě základní funkce:
* Přesun souboru nebo adresáře do jiného adresáře (move), pokud je cíl existující adresář
* Přejmenování souboru nebo adresáře na cílové jméno

U příkazů pro kopírování a přesun může být parametrů, co se má kopírovat, více, jako poslední musí být vždy cílový adresář.


## Jak to hezky zobrazit
```shell
$ tree
```

Pokud se vám zdá že práce se soubory a adresáři je v prostředí příkazové řádky nesmírně nepřehledná věc, vyzkoušejte příkaz `tree`, který vám vytiskne obsah všech adresářů v nižších úrovních do přehledné stromové struktury. Pokud příkaz `tree` ve svém prostředí nemáte, budete si ho muset doinstalovat.

## Cvičení
::exc[excs/vytvareni]
::exc[excs/presouvani]
