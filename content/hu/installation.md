+++
title = 'Telepítés'
date = 2024-07-22T16:24:34+02:00
menu = "nav"
draft = false
weight = 30
+++

# Telepítési útmutató

## NVDA

Ahhoz, hogy bármelyik RHVoice hang működjön az NVDA képernyőolvasóval, szükséged lesz az RHVoice bővítményre, amely letölthető az [RHVoice hivatalos honlapjáról](https://rhvoice.org) vagy az alábbi linken.

[Az RHVoice bővítmény letöltése]({{<param "urls.nvdaDirectLink">}})

Figyelem: érdemes a drivert a hivatalos weboldalról letölteni, mivel a fenti link egy adott verzióra mutat, ami lehet, hogy nem a legfrissebb.

Amint a bővítmény telepítve van, letöltheted a magyar hangokat a [hangok oldalon]({{<relref "voices">}}).

## SAPI-kompatibilis szoftverekhez

A SAPI hangok nem igényelnek semmilyen driver szoftvert, és a megfelelő fájlokkal telepíthetőek a [hangok oldalról]({{<relref "voices">}}).

### A Jaws for Windows képernyőolvasóhoz

A SAPI hangok a JAWS képernyőolvasóval is használhatók, de a legjobb élmény érdekében további lépések szükségesek.

Sajnos alapértelmezés szerint a JAWS nagyon régi módon próbál kommunikálni az RHVoice szintetizátorral.
Ennek javításához módosítani kell a SAPI konfigurációs fájlt.
A megfelelően módosított konfigurációs fájlt [innen töltheted le](https://hlas.ondrosik.sk/sapi5x.ini).

Miután letöltötted a fájlt, másold be a C:\Program Files\Freedom Scientific\JAWS\xxxx mappába. Az xxxx a telepített JAWS verzióját jelöli. Ha a rendszer kéri a fájl cseréjét, fogadd el.

A konfiguráció frissítése után egyszerűen indítsd újra a JAWS képernyőolvasót és válts az RHVoice szintetizátorra.

## Android

Az RHVoice bármely Android eszközre telepíthető, beleértve az okostelefonokat, táblagépeket és még néhány okos TV-t vagy TV boxot is.

Jelenleg az RHVoice Android alkalmazás nem érhető el a Google Play áruházban, és csak APK fájlként terjesztjük.

Az alkalmazás letölthető a [hangok oldalon]({{<relref "voices">}}) a megfelelő szekcióban.

Az alkalmazás telepítését követően azonnal hozzáférhetsz az összes magyar (és nem csak magyar) hanghoz, beleértve az angol, orosz és egyéb nyelveket is.

A nyelvek listájában meg kell találnod a kívánt nyelvet, kiválasztanod és telepítened a számodra legmegfelelőbb hangot.

## Linux (Béta hangok) {#linux}

Az Anna, Imre és Katalin magyar hangok bétaverziói az [axelek.pl RHVoice csomagtárolójából]({{<param "urls.linuxRepository">}}) érhetők el.

A csomagok Debian 13, Ubuntu 24.04 és 26.04 LTS, Linux Mint 22.3, valamint Fedora 44 rendszeren használhatók, 64 bites x86 számítógépeken (`amd64` vagy `x86_64`). A motorhoz legalább glibc 2.39 szükséges; a Debian 12 nem támogatott.

Az alábbi parancsok mindhárom magyar hangot és a Speech Dispatcher RHVoice modulját telepítik. A szükséges motor és a magyar nyelvi adatok automatikusan települnek. Ha csak egy hangot szeretnél használni, a telepítési parancsban csak annak a hangnak a csomagját hagyd meg a hangcsomagok közül.

| Hang | Csomag | Név a Speech Dispatcherben |
| --- | --- | --- |
| Anna | `rhvoice-voice-anna-hun` | `Anna-Beta` |
| Imre | `rhvoice-voice-imre` | `Imre-Hun` |
| Katalin | `rhvoice-voice-katalin` | `Katalin` |

A parancsokat terminálban, a saját felhasználói fiókoddal futtasd. A `sudo` kezdetű parancsokhoz rendszergazdai jogosultság szükséges.

A csomagtároló aláírókulcsának ujjlenyomata: `A263 A416 C89A D771 63AC 16C0 7CE0 7DB3 9AD2 DB61`.

### Debian, Ubuntu és Linux Mint

Telepítsd a letöltéshez szükséges eszközt, és add hozzá a csomagtároló aláírókulcsát:

```sh
sudo apt update
sudo apt install wget ca-certificates
sudo install -d -m 0755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/rhvoice.asc https://axelek.pl/asael/rhvoice/rhvoice.asc
```

A disztribúciódnak megfelelő paranccsal add hozzá a csomagtárolót. Debian 13 vagy Ubuntu 24.04/26.04 LTS esetén:

```sh
sudo wget -O /etc/apt/sources.list.d/rhvoice.sources https://axelek.pl/asael/rhvoice/rhvoice.sources
```

Linux Mint 22.3 esetén a `.list` fájlt használd, amelyet a Mint Szoftverforrások alkalmazása is megjelenít:

```sh
sudo wget -O /etc/apt/sources.list.d/rhvoice.list https://axelek.pl/asael/rhvoice/rhvoice.list
```

Miután hozzáadtad a disztribúciódnak megfelelő forrást, frissítsd a csomaglistát, és telepítsd a hangokat:

```sh
sudo apt update
sudo apt install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

### Fedora 44

Add hozzá a csomagtárolót, és telepítsd a hangokat:

```sh
sudo dnf install curl
sudo curl --fail --location --output /etc/yum.repos.d/rhvoice.repo https://axelek.pl/asael/rhvoice/rhvoice.repo
sudo dnf install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

Amikor a DNF az aláírókulcs importálását kéri, elfogadás előtt hasonlítsd össze az ujjlenyomatát a fent megadottal. A csomagtároló metaadataihoz és a csomagokhoz külön is kérhet megerősítést.

### A hangok használata az Orcával

Az Orca beállításaiban válaszd a Speech Dispatcher beszédrendszert, az RHVoice szintetizátort és az egyik telepített magyar hangot. A telepített hangokat a rendszer automatikusan felismeri.

Ha saját Speech Dispatcher konfigurációt használsz a `~/.config/speech-dispatcher/speechd.conf` fájlban, futtasd az alábbi parancsot a saját felhasználói fiókoddal, `sudo` nélkül:

```sh
rhvoice-configure-speech-dispatcher --reload
```

Ez hozzáadja az RHVoice modult a konfigurációdhoz, és a módosítás előtt `.before-rhvoice` végződésű biztonsági másolatot készít.

A következő parancsokkal kilistázhatod az elérhető hangokat, és kipróbálhatod Katalint a terminálból:

```sh
spd-say -o rhvoice -L
spd-say -o rhvoice -y Katalin "Szia! Ez egy magyar próbamondat."
```

### Frissítések

Az új verziók a disztribúciód szokásos frissítéskezelőjén keresztül érkeznek. Debian, Ubuntu vagy Linux Mint rendszeren terminálból így frissíthetsz:

```sh
sudo apt update
sudo apt upgrade
```

Fedora esetén:

```sh
sudo dnf upgrade
```
