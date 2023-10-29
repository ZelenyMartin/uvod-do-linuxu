I když se jedná o workshop o Linuxu, pravděpodobně většina z vás přichází s operačním systémem Windows. Abychom však mohli pracovat s linuxovou příkazovou řádkou, potřebujeme ji mít k dispozici na našem počítači. Způsobem, jak toho můžeme snadno dosáhnout, je použití vestavěné funkcionality operačního systému Windows s názvem _Windows Subsystem for Linux (WSL)_.

:::warn
Je nezbytné mít nejaktuálnější updatované Windows. Na starších Windows než Windows 10 není funkcionalita _WSL_ přítomna.
:::

## Instalace WSL na Windows
Budeme následovat oficiální návod na [webu Microsoftu](https://learn.microsoft.com/en-us/windows/wsl/install) a nainstalujeme si nejvyšší verzi _WSL_.

### Automatická instalace

Otevřeme si příkazovou řádku Windows a spustíme příkaz

```
wsl --install
```

### Klíčové body manuální instalace

Pokud by se vám z jakéhokoliv důvodu nepodařilo nainstalovat WSL2 pomocí příkazu `wsl --install`, shrnul jsem zde kroky [manuálního postupu](https://learn.microsoft.com/en-us/windows/wsl/install-manual).

1. Zapněte funkcionalitu WSL a virtualizace (Step 1 a 3 v oficiálním návodu)

    ::fig[Zapnutí funkcionality WSL]{src=assets/01_terminal_screenshot.png size=100}

1. Restartujte počítač!
1. Stáhněte a nainstalujte WSL update Linuxového jádra (Step 4)
1. Nastavte WSL 2 jako výchozí verzi (Step 5)
1. Nainstalujte linuxovou distribuci z Microsoft Store (např. Debian je kompletní distribuce, která je zároveň nejmenší z nabízených a stažení nebude trvat dlouho)

    ::fig[Instalace distribuce z Microsoft Store]{src=assets/02_ms_store_debian_instalace.png size=100}

1. Po prvním spuštění distribuce vyžaduje vytvoření uživatele s heslem.

    :::warn
    Psaní hesla v linuxovém terminálu neposkytuje žádnou vizuální odezvu (žádné `*` nebo •). To, že se nic nezobrazuje, když zadáváte heslo, je účel.
    :::

    ::fig[Vytvoření linuxového uživatele]{src=assets/05_debian_vytvoreni_uzivatele.png size=100}

1. Od teď již budete moci kdykoliv spustit WSL zadáním tohoto příkazu v nabídce Start

::fig[Spouštění WSL]{src=assets/06_start_WSL.png size=100}


## MacOS a Linux

Pokud používáte Apple nebo už máte nainstalován Linux, stačí najít ve svém prostředí aplikaci _Terminal_. Nemůžete-li ji najít přímo, zkuste použít vyhledávání.

