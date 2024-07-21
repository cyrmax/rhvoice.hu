+++
title = 'Installation'
date = 2024-07-20T19:15:34+03:00
menu = "nav"
draft = false
weight = 2
+++

# Installation instructions

## For NVDA

For any RHVoice voice to work with NVDA you need an RHVoice driver add-on which can be downloaded from the [official RHVoice website](https://rhvoice.org) or using the link below.

[Download RHVoice driver NVDA add-on]({{<param "urls.nvdaDirectLink">}})

Notice: consider downloading the driver from the official website as the link above points to a specific version which may be not the latest one.

When the driver is installed you can download one of Hungarian voice add-ons on the [voices page]({{<relref "voices">}}).

## For SAPI-compatible software

SAPI voices do not require any driver software and can be installed with corresponding setup files on the [voices page]({{<relref "voices">}}).

### For JAWS

SAPI voices also can be used with JAWS screenreader, but additional steps are needed for the best experience.

Unfortunately, by default JAWS tries to communicate with RHVoice synthesizer in a very old maner.
To fix this you need to alter SAPI configuration file for JAWS.
You can download properly altered configuration file [here](https://hlas.ondrosik.sk/sapi5x.ini).

After you have downloaded the file, you need to copy it to `` folder. If your system asks to replace the file, you should agree.

After updating the configuration simply restart your JAWS screenreader and switch to RHVoice synthesizer.

## For Android

RHVoice also can be installed to any Android device including smartphones, tablets and even some smart TVs or TV boxes.

Currently RHVoice Android application is not available in Google Play and is only distributed as an APK file.

You can download the Android application on the [voices page]({{<relref "voices">}}) under a dedicated heading.

After the application installation you have immediate access to all Hungarian (and not only Hungarian) voices including English, Russian and other languages.

In the languages list you should find the language you are interested in, select it and install the voice you want.
