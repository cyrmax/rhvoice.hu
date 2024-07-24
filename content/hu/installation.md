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
