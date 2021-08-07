Než se vrhneme na praktickou část, povíme si něco o motivaci k používání příkazové řádky a její historii.

## Unix a GNU/Linux
Příkazová řádka v podobě jakou používáme dnes v Linuxu vznikla na přelomu šedesátých a sedmdesátých let v operačním systému Unix. Ten umožňoval, aby na jednom počítači mohlo pracovat naráz více uživatelů, kteří se připojovali z textových terminálů. Operačních systémů unixového typu vzniklo více. Byly velmi používané a licence byly drahé.

![Historie Unixu](assets/unix_history.jpg){.fig .fig-100}

Později vznikl projekt GNU, který si dal za cíl nabídnou unixové prostředí ve formě _free software_ (dnes se jedná o _open source_ model a svobodné licence). V kombinaci s jádrem Linux vzniká GNU/Linux, který se velmi rozšířil ve formě mnoha distribucí.


## Terminál == konzole == příkazová řádka == shell
Tyto výrazy mají k sobě velmi blízko a budeme je považovat za synonyma. V angličtině se jedná analogicky o výrazy: _Terminal_, _Console_ a _Command Line_ (často ve spojení _Command Line Interface_, zkráceně _CLI_). _Shell_ je označení typu programů pracujících jako interpret příkazové řádky. Často používaný linuxový shell je například _Bash_. Jedná se o program, který pochopí, co na příkazovou řádku napíšeme, podle toho se zachová a vypíše nám výsledek.

Terminál realizuje textové vstupně/výstupní rozhraní s počítačem. Jednoduše řečeno počítači na klávesnici zadáme příkaz v podobě textu ukončený klávesou _Enter_. A výstupem bude text s výsledkem příkazu, který nám počítač vypíše.


## Jak vypadá Linux
Je důležité si uvědomit, že dnešní Linux rozhodně není pouze příkazová řádka. Je však mnoho případů, kdy rozhraní terminálu zcela dostačuje a je i vhodnější. Linux bývá často nasazován na servery, u kterých chcete, aby pracovaly samy a bez nutnosti zásahu. Připojování k serverům se často řeší dálkové přes internet, kde textové rozhraní Linux je rychlejší a pohodlnější než režim vzdálené plochy u Windows serveru.

Linux dále pracuje ve spoustě elektroniky téměř skrytě bez přímé uživatelské interakce jako např. síťové routery, chytré televize, mobilní telefony s Androidem a spousty vestavěných zařízení realizovaných jednodeskovými počítači (např. RaspberryPi).

Kromě _WSL_ je možnost na počítač nainstalovat Linux přímo ve formě některé linuxové distribuce. Pokud nechceme instalovat Linux přímo "na železo" např. v režimu _dual-boot_ s Windows, můžeme využít virtualizaci (např. _VirtualBox_) a Linux nainstalovat do virtuálního počítače běžícího jako program v operačním systému.


## Distribuce a grafická prostředí
Distribuce je kompletní linuxový operační systém, který si můžete stáhnout ve formě ISO obrazu bootovacího flash disku, rozběhnout na počítači a nainstalovat. Distribuce nabízí kromě jádra Linux a podpůrných nástrojů GNU mnoho programů ve formě balíčků (např. Firefox, Thunderbird, LibreOffice, VLC, Gimp, Inkscape, Audacity). Různé distribuce ze sebe navzájem vychází nebo alespoň sdílí stejný balíčkovací systém. Podle nejčastěji používaných balíčkovacích systémů můžeme rozlišit Debian-based distribuce ([Debian](https://www.debian.org/), [Ubuntu](https://ubuntu.com/), [Linux Mint](https://linuxmint.com/)) a RPM-based distribuce ([Red Hat Enterprise Linux](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux), [CentOS](https://www.centos.org/), [Fedora](https://getfedora.org/), [openSUSE](https://www.opensuse.org/)).

V neposlední řadě každá distribuce často nabízí více grafických prostředí ([Gnome 3](https://www.gnome.org/), [KDE Plasma 5](https://kde.org/), [Xfce](https://xfce.org/), [MATE](https://mate-desktop.org/), [Cinnamon](https://cinnamon-spices.linuxmint.com/), [LXDE](http://www.lxde.org/), [LXQt](https://lxqt-project.org/)).


## Proč používat příkazovou řádku?
Ovládání přes příkazovou řádku je v každé linuxové distribuci téměř totožné. Kromě historického aspektu, že něco existuje desítky let a stále se používá je hlavní výhodou práce v příkazové řádce rychlost některých úkonů, malý objem přenášených dat a rychlá latence při vzdálené práci a automatizace činností ve formě skriptování.

