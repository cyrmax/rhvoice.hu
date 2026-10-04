+++
title = 'Installation'
date = 2024-07-20T19:15:34+03:00
menu = "nav"
draft = false
weight = 30
+++

# Installation instructions

## For NVDA

For any voice to work with NVDA, you need the RHVoice driver add-on, which can be downloaded from the [official RHVoice website](https://rhvoice.org) or using the link below.

[Download RHVoice driver NVDA add-on]({{<param "urls.nvdaDirectLink">}})

Notice: consider downloading the driver from the official website, as the link above points to a specific version which may be not the latest one.

When the driver is installed, you can download one of Hungarian voice add-ons on the [voices page]({{<relref "voices">}}).

## For SAPI-compatible software

SAPI voices do not require any driver software and can be installed with the corresponding setup files on the [voices page]({{<relref "voices">}}).

### For JAWS

SAPI voices also can be used with JAWS screenreader, but additional steps are needed for the best experience.

Unfortunately, by default JAWS tries to communicate with RHVoice synthesizer in a very old manner.
To fix this, you need to alter the SAPI configuration file for JAWS.
You can download the properly altered configuration file [here](https://hlas.ondrosik.sk/sapi5x.ini).

After you have downloaded the file, you need to copy it to the `C:\Program Files\Freedom Scientific\JAWS\xxxx` folder. If your system asks to replace the file, you should agree.

After updating the configuration, simply restart your JAWS screenreader and switch to RHVoice synthesizer.

## For Android

RHVoice also can be installed to any Android device including smartphones, tablets and even some smart TVs or TV boxes.

Currently, the RHVoice Android application is not available in Google Play and is only distributed as an APK file.

You can download the Android application on the [voices page]({{<relref "voices">}}) under a dedicated heading.

After the application installation, you have immediate access to all Hungarian (and not only Hungarian) voices including English, Russian and other languages.

In the languages list you should find the language you are interested in, select it and install the voice you want.

## For Linux (Beta voices) {#linux}

The Hungarian beta voices Anna, Imre and Katalin are available from the [RHVoice package repository on axelek.pl]({{<param "urls.linuxRepository">}}).

These packages support Debian 13, Ubuntu 24.04 and 26.04 LTS, Linux Mint 22.3, and Fedora 44 on 64-bit x86 computers (`amd64` or `x86_64`). The engine requires glibc 2.39 or newer; Debian 12 is not supported.

The commands below install all three Hungarian voices and the RHVoice module for Speech Dispatcher. The required engine and Hungarian language data are installed automatically. To install just one voice, keep only its voice package in the installation command.

| Voice | Package | Name in Speech Dispatcher |
| --- | --- | --- |
| Anna | `rhvoice-voice-anna-hun` | `Anna-Beta` |
| Imre | `rhvoice-voice-imre` | `Imre-Hun` |
| Katalin | `rhvoice-voice-katalin` | `Katalin` |

Run the commands in a terminal as your regular user. Commands starting with `sudo` require administrator privileges.

The repository signing-key fingerprint is `A263 A416 C89A D771 63AC 16C0 7CE0 7DB3 9AD2 DB61`.

### Debian, Ubuntu and Linux Mint

Install the download tool and add the repository signing key:

```sh
sudo apt update
sudo apt install wget ca-certificates
sudo install -d -m 0755 /etc/apt/keyrings
sudo wget -O /etc/apt/keyrings/rhvoice.asc https://axelek.pl/asael/rhvoice/rhvoice.asc
```

Add the repository using the command for your distribution. For Debian 13 or Ubuntu 24.04/26.04 LTS:

```sh
sudo wget -O /etc/apt/sources.list.d/rhvoice.sources https://axelek.pl/asael/rhvoice/rhvoice.sources
```

For Linux Mint 22.3, use the `.list` file, which also appears in Mint's Software Sources tool:

```sh
sudo wget -O /etc/apt/sources.list.d/rhvoice.list https://axelek.pl/asael/rhvoice/rhvoice.list
```

After adding the source for your distribution, refresh the package list and install the voices:

```sh
sudo apt update
sudo apt install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

### Fedora 44

Add the repository and install the voices:

```sh
sudo dnf install curl
sudo curl --fail --location --output /etc/yum.repos.d/rhvoice.repo https://axelek.pl/asael/rhvoice/rhvoice.repo
sudo dnf install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

When DNF asks to import the signing key, compare its fingerprint with the one above before accepting. It may ask separately for the repository metadata and the packages.

### Using the voices with Orca

In Orca preferences, select Speech Dispatcher as the speech system, RHVoice as the synthesizer, and one of the installed Hungarian voices. The voices are detected automatically.

If you use a personal Speech Dispatcher configuration at `~/.config/speech-dispatcher/speechd.conf`, run the following command as your regular user, without `sudo`:

```sh
rhvoice-configure-speech-dispatcher --reload
```

This adds RHVoice to your configuration and saves a backup with the `.before-rhvoice` suffix before making changes.

You can list the available voices and try Katalin from a terminal:

```sh
spd-say -o rhvoice -L
spd-say -o rhvoice -y Katalin "Szia! Ez egy magyar próbamondat."
```

### Updates

New versions arrive through your distribution's normal update manager. To update from a terminal on Debian, Ubuntu or Linux Mint:

```sh
sudo apt update
sudo apt upgrade
```

On Fedora:

```sh
sudo dnf upgrade
```
