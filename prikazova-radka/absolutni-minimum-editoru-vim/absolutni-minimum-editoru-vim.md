Na konci se podíváme na velmi mocný textový editor pro prostředí příkazové řádky.

Většina příkazů, které jsme si ukázali, pracovala v režimu standardního textového vstupu a výstupu. Většinou něco vypsaly na terminál (`ls`, `pwd`) nebo něco udělaly (`cd`, `cp`, `mv`). Občas očekávaly nějaký standardní vstup poslaný rourou z jiného příkazu (např. `tr`) a jejich chování se obvykle řídilo parametry příkazové řádky.

Výjimku v tomto měly nástroje `less` a `man`, které zabraly celé dostupné okno terminálu a zobrazily na něj soubor nebo manuálovou stránku. Program `less` nám však dovoloval pouze soubor prohlížet. Pokud bychom potřebovali nějaký soubor upravit, popř. vytvořit nový soubor s nějakým obsahem, budeme potřebovat textový editor.

V profesionálním světe linuxové příkazové řádky se pro tyto případy nejčastěji používá editor `vim`. Důležité je vědět, že editor [VIM](https://www.vim.org/) se svým ovládáním významně liší od běžných textových editorů, se kterými jste se doposud nejspíše setkali při psaní a editaci nějakého kódu (např. [Visual Studio Code](https://code.visualstudio.com/) nebo [Sublime Text](https://www.sublimetext.com/))

Editor VIM je profesionální nástroj a je nutné věnovat určitý čas naučení se s ním pracovat. Odměnou nám bude mnohem efektivnější a rychlejší editace textových souborů (požadované operace lze vykonat mnohem rychleji za použití menšího počtu úhozů). Výhody vznikají pouze při psaní 10 prsty bez sledování klávesnice.

Běžné textové editory obsahují jediný mód použití, a to režim vkládání textu (zmáčknutá posloupnost písmen daný text napíše do okna editoru). O pohyb kurzoru se v běžných editorech starají kurzorové šipky, navigační blok :kbd[Home], :kbd[End], :kbd[PageUP], :kbd[PageDown], popř. ještě s klávesou :kbd[Ctrl]. Mnoho činností lze vykonat pomocí myši.

Editor VIM vznikl jako následovník staršího editoru Vi, který se používal na UNIXových systémech vybavených monitorem. Klávesnice u terminálů tehdy běžně neměly kurzorové šipky ani navigační klávesy. Proto vznikl editor, která má oddělené režimy vkládání textu od režimu pohybu kurzoru a manipulace s textem.

U vimu rozlišujeme 3 hlavní režimy práce:

* Editační mód (Normal mode)
    * Slouží k pohybu kurzoru, přesouvání částí textu
    * V tomto režimu není možné psát text
    * Výchozí mód při spuštění VIMu
    * Vstup do editačního módu: klávesa :kbd[Esc]
* INSERT mód
    * Slouží ke vkládání znaků do souboru
    * Vstup do INSERT módu: klávesa :kbd[i]
    * Ukončení INSERT módu: klávesa :kbd[Esc]
* Příkazový mód
    * VIM zobrazí vlastní příkazovou řádku, kam je možné napsat složitější příkaz
    * Vstup do příkazového módu: klávesa :kbd[:]
    * Ukončení příkazového módu: klávesa :kbd[Esc]

## Jak to spustím a jak to vypnu

Editor VIM spustíme příkazem `vim`. Zobrazí se nám "Welcome screen", kde si můžeme povšimnout dobré rady, jak editor vlastně ukončit. Editor zavřeme vstupem do příkazového módu pomocí dvojtečky :kbd[:] následované příkazem :kbd[q] a :kbd[Enter].

Vyzkoušejte si několikrát otevřít a bezpečně zavřít prázdný editor VIM.

```shell
$ vim
```

```
  1                                                        
~                                                          
~                                                          
~                    VIM - Vi IMproved                     
~                                                          
~                     version 8.2.3512                     
~                 by Bram Moolenaar et al.                 
~            Modified by <bugzilla@redhat.com>             
~       Vim is open source and freely distributable        
~                                                          
~              Help poor children in Uganda!               
~      type  :help iccf<Enter>       for information       
~                                                          
~      type  :q<Enter>               to exit               
~      type  :help<Enter>  or  <F1>  for on-line help      
~      type  :help version8<Enter>   for version info      
~                                                          
~                                                          
utf-8 unix  [No Name]                              0/1   1
```

Pokud chceme v editoru něco napsat, zmáčkneme klávesu :kbd[i], která nás přepne do INSERT módu. V tu chvíli klávesy dělají to, co od nich očekáváme - text se zobrazuje v okně editoru. Znak tilda `~` zde znamená prázdný řádek.

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
utf-8 unix  [No Name] +                            1/1  11 
-- INSERT --                                               
```

Pokud jsme něco napsali, ale text nechceme ukládat do souboru, musíme VIM ukončit příkazem `:q!`, abychom dali najevo, že opravdu nechceme soubor ukládat.

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
utf-8 unix  [No Name] +                            1/1  10 
:q!
```

V opačném případě musíme soubor uložit příkazem `:w <název souboru>`.

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
utf-8 unix  [No Name] +                            1/1  10 
:w pozdrav.txt
```

Po ukončení editoru pomocí `:q` si můžeme obsah souboru vypsat na terminál

```shell
$ cat pozdrav.txt
Ahoj vime!
```

Námi vytvořený soubor si můžeme opět otevřít ve VIMu tak, že název souboru zadáme jako parametr. Stejně můžeme otevřít ve VIMu i neexistující soubor a editor nám ho při uložení souboru vytvoří.

```shell
$ vim pozdrav.txt
```

Příkazy, které už umíme jako `:w` a `:q` je možné i zkombinovat do jednoho `:wq`.

## Další funkce VIMu

Vyhledávání zapneme klávesou lomítko :kbd[/] v editačním módu a napíšeme text, který chceme v souboru vyhledat. Na další výskyt vyhledávaného řetězce se přesuneme pomocí :kbd[n] a na předchozí pomocí :kbd[N]. Toto funguje stejně jako v programech `less` a `man`.

VIM je profesionální editor pro editaci programů a konfiguračních souborů. Je velmi ergonomický, protože při jeho používání není nutné, aby prsty opustily prostřední řadu klávesnice. Není nutné používat kurzorové šipky, navigační blok nebo myš. Pohyb kurzoru a editace existujícího testu se provádí v editačním módu (Normal mode).

Pokud vám editor VIM přijde děsivý, je důležité vědět, že po vás nikdo nevyžaduje, abyste ho používali výlučně. Pro dobrou znalost práce v linuxové příkazové řádce je však velmi vhodné znát alespoň minimum editoru VIM. Je důležité znát alespoň:

* Otevřít soubor ve VIMu: `$ vim <název souboru>`
* Vyhledat text v souboru: :kbd[/]
* Upravit slovo nebo řádek v souboru: INSERT mód zapneme klávesou :kbd[i]
* Ukončit VIM: ukončíme INSERT mód pomocí :kbd[Esc] a uložíme a ukončíme práci pomocí `:wq`

Pro zájemce doporučuji vestavěný tutoriál

```shell
$ vimtutor
```

Pokud vás editor VIM zaujme a naučíte se s ním pracovat, odměnou vám bude mnohem vyšší rychlost úprav textových souborů, zdravější ergonomie práce na klávesnici a doživotní závislost na vimovském způsobu ovládání textového editoru 😄.
