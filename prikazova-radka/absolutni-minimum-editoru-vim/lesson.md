Na konci se podíváme na velmi mocný textový editor pro prostředí příkazové řádky.

Většina příkazů, které jsme si ukázali pracovala v režimu standardního textového vstupu a výstupu. Většinou něco vypsaly na terminál (`ls`, `pwd`) nebo něco udělaly (`cd`, `cp`, `mv`). Občas očekávaly nějaký standardní vstup poslaný rourou z jiného příkazu (např. `tr`) a jejich chování se obvykle řídilo parametry příkazové řádky.

Výjimku v tomto měly nástroje _less_ a _man_, které zabraly celé dostupné okno terminálu a zobrazily na něj soubor nebo manuálovou stránku. Program _less_ nám však dovoloval pouze soubor prohlížet. Pokud bychom potřebovali nějaký soubor upravit, popř. vytvořit nový soubor s nějakým obsahem, budeme potřebovat textový editor.

V profesionálním světe linuxové příkazové řádky se pro tyto případy nejčastěji používá editor _vim_. Důležité je vědět, že editor [VIM](https://www.vim.org/) se svým ovládáním významně liší běžných textových editorů, se kterými jste se doposud nejspíše setkali při psaní a editaci nějakého kódu (např. [Visual Studio Code](https://code.visualstudio.com/), [Atom](https://atom.io/) nebo [Sublime Text](https://atom.io/))

Editor VIM je profesionální nástroj a je nutné věnovat určitý čas naučení se s ním pracovat. Odměnou nám bude mnohem efektivnější a rychlejší editace textových souborů (požadované operace lze vykonat mnohem rychleji za použití menšího počtu úhozů). Výhody vznikají pouze při psaní 10 prsty bez sledování klávesnice.

Běžné textové editory obsahují jediný mód použití, a to režim vkládání textu (zmáčknutá posloupnost písmen daný text napíše do okna editoru). O pohyb kurzoru se v běžných editorech starají kurzorové šipky, navigační blok _Home_, _End_, _PageUP_, _PageDown_, popř. ještě s klávesou _Ctrl_. Mnoho činností lze vykonat pomocí myši.

Editor VIM vznikl jako následovník staršího editoru Vi, který se používal na UNIXových systémech vybavených monitorem. Klávesnice u terminálů tehdy běžně neměly kurzorové šipky ani navigační klávesy. Proto vznikl editor, která má oddělené režimy vkládání textu od režimu pohybu kurzoru a manipulace s textem.

U vimu rozlišujeme 3 hlavní režimy práce:

* Editační mód (Normal mode)
    * Slouží pohyb kurzoru, přesouvání částí textu
    * V tomto režimu není možné psát text
    * Výchozí mód při spuštění VIMu
    * Vstup do editačního módu: klávesa _Esc_
* INSERT mód
    * Vkládání znaků do souboru
    * Vstup do INSERT módu: klávesa _i_
    * Ukončení INSERT módu: klávesa _Esc_
* Příkazový mód
    * VIM zobrazí vlastní příkazovou řádku, kam je možné napsat složitější příkaz
    * Vstup do příkazového módu: klávesa _:_
    * Ukončení příkazového módu: klávesa _Esc_

## Jak to spustím a jak to vypnu

Editor VIM spustíme příkazem _vim_. Zobrazí se nám "Welcome screen", kde si můžeme povšimnout dobré rady jak editor vlastně ukončit. Editor zavřeme vstupem do příkazového módu pomocí dvojtečky _:_ následované příkazem _q_ a _Enter_.

Vyzkoušejte si několikrát otevřít a bezpečně zavřít prázdný editor VIM.

```shell
$ vim
```

```
  1                                                                             
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                              VIM - Vi IMproved                                
~                                                                               
~                               version 8.2.3512                                
~                           by Bram Moolenaar et al.                            
~                      Modified by <bugzilla@redhat.com>                        
~                 Vim is open source and freely distributable                   
~                                                                               
~                        Help poor children in Uganda!                          
~                type  :help iccf<Enter>       for information                  
~                                                                               
~                type  :q<Enter>               to exit                          
~                type  :help<Enter>  or  <F1>  for on-line help                 
~                type  :help version8<Enter>   for version info                 
~                                                                               
~                                                                               
~                                                                               
~                                                                               
utf-8 unix  [No Name]                                                   0/1   1
```

Pokud chceme v editoru něco napsat, zmáčkneme klávesu _i_, která nás přepne do INSERT módu. V tu chvíli klávesy dělají to co od nich očekáváme - text se zobrazuje v okně editoru. Znak tilda _~_ zde znamená prázdný řádek.

```
  1 Ahoj vime!                                                                  
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
utf-8 unix  [No Name] +                                                 1/1  11 
-- INSERT --                                                                   
```

Pokud jsme něco napsali, ale text nechceme ukládat do souboru, musíme VIM ukončit příkaze _:q!_, abychom dali najevo, že opravdu nechceme soubor ukládat.

```
  1 Ahoj vime!                                                                  
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
utf-8 unix  [No Name] +                                                 1/1  10 
:q!
```

V opačném případě musíme soubor uložit příkazem _:w <název souboru>_.

```
  1 Ahoj vime!                                                                  
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
utf-8 unix  [No Name] +                                                 1/1  10 
:w pozdrav.txt
```

Po ukončení editoru pomocí _:q_ si můžeme obsah souboru vypsat na terminál

```shell
$ cat pozdrav.txt
Ahoj vime!
```

Námi vytvořený soubor si můžeme opět otevřít ve VIMu tak, že název souboru zadáme jako parametr. Stejně můžeme otevřít ve VIMu i neexistující soubor a editor nám ho při uložení souboru vytvoří.

```shell
$ vim pozdrav.txt
```

Příkazy, které už umíme jako _:w_ a _:q_ je možné i zkombinovat do jednoho _:wq_.

## Další funkce VIMu

Vyhledávání zapneme klávesou lomítko _/_ v editačním módu a napíšeme text, který chceme v souboru vyhledat. Na další výskyt vyhledávaného řetězce se přesuneme pomocí _n_ a na předchozí pomocí _N_. Toto funguje stejně jako v programech _less_ a _man_.

VIM je profesionální editor pro editaci programů a konfiguračních souborů. Je velmi ergonomický, protože při jeho používání není nutné, aby prsty opustily prostřední řadu klávesnice. Není nutné používat kurzorové šipky, navigační blok nebo myš. Pohyb kurzoru a editace existujícího testu se provádí v editačním mód (Normal mode).

Pokud vám editor VIM přijde děsivý, je důležité vědět, že po vás nikdo nevyžaduje, abyste ho používali výlučně. Pro dobrou znalost práce v linuxové příkazové řádce je však velmi vhodné znát alespoň minimum editoru VIM. Je důležité znát alespoň:

* Otevřít soubor ve VIMu: `$ vim <název souboru>`
* Vyhledat text v souboru: _/_
* Upravit slovo nebo řádek v souboru: INSERT mód zapneme klávesou _i_
* Ukončit VIM: ukončíme INSERT mód pomocí _Esc_ a uložíme a ukončíme práci pomocí _:wq_

Pro zájemce doporučuji vestavěný tutoriál

```shell
$ vimtutor
```

Pokud vás editor VIM zaujme a naučíte se s ním pracovat, odměnou vám bude mnohem vyšší rychlost úprav textových souborů, zdravější ergonomie práce na klávesnici a doživotní závislost na vimovském způsobu ovládání textového editoru :-).
