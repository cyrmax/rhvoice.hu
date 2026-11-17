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

Add the repository only if you trust it: like any package repository, it can install software that runs with administrator privileges.

The repository is added by a single package that installs the signing key and the package source. Later changes to the key arrive with this package in regular updates.

### Debian, Ubuntu and Linux Mint

Download and install the repository package:

```sh
wget -O /tmp/rhvoice-archive-keyring.deb https://axelek.pl/asael/rhvoice/rhvoice-archive-keyring.deb
sudo apt install /tmp/rhvoice-archive-keyring.deb
```

If the `wget` command is not found, install it first with `sudo apt install wget`.

Refresh the package list and install the voices:

```sh
sudo apt update
sudo apt install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

Optionally, you can check the installed key. The output should contain the fingerprint `A263A416C89AD77163AC16C07CE07DB39AD2DB61`:

```sh
gpg --show-keys /usr/share/keyrings/rhvoice-archive-keyring.pgp
```

### Fedora 44

Add the repository and install the voices:

```sh
sudo dnf install https://axelek.pl/asael/rhvoice/rhvoice-release.rpm
sudo dnf install speech-dispatcher-rhvoice \
    rhvoice-voice-anna-hun rhvoice-voice-imre rhvoice-voice-katalin
```

The first command adds the repository and its signing key. DNF reports that it skipped OpenPGP checks for 1 package; this warning is expected.

When the second command asks to import the signing key, compare its fingerprint with the one above before accepting. It usually asks twice: once for the repository metadata and once for the packages.

### If you added the repository using the earlier instructions

If you followed the earlier version of these instructions (a key in `/etc/apt/keyrings` and a `rhvoice.sources` or `rhvoice.list` file, or a `rhvoice.repo` file downloaded on Fedora), install the repository package so that future key changes reach you.

On Debian, Ubuntu and Linux Mint:

```sh
sudo apt update
sudo apt install rhvoice-archive-keyring
```

On Fedora:

```sh
sudo dnf install rhvoice-release
```

On Debian, Ubuntu and Linux Mint, the package removes the unchanged files of the earlier instructions and puts its own in their place. If you edited one of those files, it stays in place and the package tells you where else the repository is listed. Remove that file yourself, otherwise APT reports the error `Conflicting values set for option Signed-By`.

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

New versions arrive through your distribution's normal update manager. Changes to the signing key arrive the same way, in the repository package. To update from a terminal on Debian, Ubuntu or Linux Mint:

```sh
sudo apt update
sudo apt upgrade
```

On Fedora:

```sh
sudo dnf upgrade
```

### Removing the voices

The commands below remove all RHVoice packages, not only the Hungarian voices. They also remove the repository package, and with it the signing key and the package source.

On Debian, Ubuntu and Linux Mint:

```sh
sudo apt purge '~nrhvoice'
sudo apt update
```

On Fedora:

```sh
sudo dnf remove '*rhvoice*'
sudo rpmkeys --delete a263a416c89ad77163ac16c07ce07db39ad2db61
```

The second Fedora command removes the imported signing key from the RPM database.

If you added the repository by hand using the earlier instructions and never installed the repository package, also delete the files you added. On Debian, Ubuntu and Linux Mint:

```sh
sudo rm -f /etc/apt/sources.list.d/rhvoice.sources /etc/apt/sources.list.d/rhvoice.list /etc/apt/keyrings/rhvoice.asc
```

On Fedora:

```sh
sudo rm -f /etc/yum.repos.d/rhvoice.repo
```
