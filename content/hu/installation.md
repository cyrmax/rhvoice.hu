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

Csak akkor add hozzá a csomagtárolót, ha megbízol benne: mint bármely csomagtároló, ez is telepíthet rendszergazdai jogosultsággal futó programokat.

A csomagtárolót egyetlen csomag adja hozzá, amely telepíti az aláírókulcsot és a csomagforrást. A kulcs későbbi változásai ezzel a csomaggal, a szokásos frissítésekkel érkeznek.

### Debian, Ubuntu és Linux Mint

Töltsd le és telepítsd a csomagtároló csomagját:

```sh
wget -O /tmp/rhvoice-archive-keyring.deb https://axelek.pl/asael/rhvoice/rhvoice-archive-keyring.deb
sudo apt install /tmp/rhvoice-archive-keyring.deb
```

Ha a `wget` parancs nem található, előbb telepítsd: `sudo apt install wget`.

Frissítsd a csomaglistát, és telepítsd a hangokat:

```sh
sudo apt update
sudo apt install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

Ha szeretnéd, ellenőrizheted a telepített kulcsot. A kimenetnek tartalmaznia kell az `A263A416C89AD77163AC16C07CE07DB39AD2DB61` ujjlenyomatot:

```sh
gpg --show-keys /usr/share/keyrings/rhvoice-archive-keyring.pgp
```

### Fedora 44

Add hozzá a csomagtárolót, és telepítsd a hangokat:

```sh
sudo dnf install https://axelek.pl/asael/rhvoice/rhvoice-release.rpm
sudo dnf install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

Az első parancs hozzáadja a csomagtárolót és annak aláírókulcsát. A DNF jelzi, hogy egy csomagnál kihagyta az OpenPGP-ellenőrzést („skipped OpenPGP checks for 1 package”); ez a figyelmeztetés várható.

Amikor a második parancs az aláírókulcs importálását kéri, elfogadás előtt hasonlítsd össze az ujjlenyomatát a fent megadottal. Általában kétszer kér megerősítést: egyszer a csomagtároló metaadataihoz, egyszer a csomagokhoz.

### Ha a korábbi útmutató szerint adtad hozzá a csomagtárolót

Ha az útmutató korábbi változata szerint adtad hozzá a csomagtárolót (kulcs az `/etc/apt/keyrings` mappában és egy `rhvoice.sources` vagy `rhvoice.list` fájl, illetve Fedorán egy letöltött `rhvoice.repo` fájl), telepítsd a csomagtároló csomagját, hogy a kulcs jövőbeli változásai is eljussanak hozzád.

Debian, Ubuntu és Linux Mint esetén:

```sh
sudo apt update
sudo apt install rhvoice-archive-keyring
```

Fedora esetén:

```sh
sudo dnf install rhvoice-release
```

Debian, Ubuntu és Linux Mint rendszeren a csomag eltávolítja a korábbi útmutató változatlan fájljait, és a saját fájljaival helyettesíti őket. Ha valamelyiket módosítottad, az a helyén marad, és a csomag kiírja, hol szerepel még a csomagtároló. Ezt a fájlt töröld kézzel, különben az APT a `Conflicting values set for option Signed-By` hibát jelzi.

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

Az új verziók a disztribúciód szokásos frissítéskezelőjén keresztül érkeznek. Az aláírókulcs változásai is így, a csomagtároló csomagjával érkeznek. Debian, Ubuntu vagy Linux Mint rendszeren terminálból így frissíthetsz:

```sh
sudo apt update
sudo apt upgrade
```

Fedora esetén:

```sh
sudo dnf upgrade
```

### A hangok eltávolítása

Az alábbi parancsok az összes RHVoice csomagot eltávolítják, nem csak a magyar hangokat. A csomagtároló csomagját is eltávolítják, és vele együtt az aláírókulcsot és a csomagforrást.

Debian, Ubuntu és Linux Mint esetén:

```sh
sudo apt purge '~nrhvoice'
sudo apt update
```

Fedora esetén:

```sh
sudo dnf remove '*rhvoice*'
sudo rpmkeys --delete a263a416c89ad77163ac16c07ce07db39ad2db61
```

A második Fedora-parancs törli az importált aláírókulcsot az RPM adatbázisából.

Ha a korábbi útmutató szerint kézzel adtad hozzá a csomagtárolót, és nem telepítetted a csomagtároló csomagját, töröld a hozzáadott fájlokat is. Debian, Ubuntu és Linux Mint esetén:

```sh
sudo rm -f /etc/apt/sources.list.d/rhvoice.sources /etc/apt/sources.list.d/rhvoice.list /etc/apt/keyrings/rhvoice.asc
```

Fedora esetén:

```sh
sudo rm -f /etc/yum.repos.d/rhvoice.repo
```
