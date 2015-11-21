---
layout: post
category : Xorg config
tagline: "How to configure the keyboard to alternate beetween 'us' and 'intl' layouts"
tags : [Xorg, keyboard, configuration, arch, arch linux]
---
{% include JB/setup %}

In my Arch Linux the keyboard configurations are in the `/usr/share/X11/xorg.conf.d/10-evdev.conf` file.

I just added the following lines to the `Section "InputClass"` with `Identifier "evdev keyboard catchall"`:

	Option  "XkbLayout" "us"
        Option  "XkbVariant" "altgr-intl"
