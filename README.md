[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/matteoiervasi)
[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/dell-xps-9570-ubuntu-respin/Lobby?utm_source=share-link&utm_medium=link&utm_campaign=share-link)

# DELL XPS 15 9570 Ubuntu post installation script (18.04,19.04 and 19.10)

### Table of Contents
1. [Post-install script](#post-install-script)
2. [Switching from one graphic card to the other](#how-to-switch-from-one-graphic-card-to-the-other)
3. [Troubleshooting](#troubleshooting)

Collection of scripts and tweaks to make Ubuntu 18.04/19.04/19.10 run smooth on Dell XPS 15 9570.
I suggest everyone to use the post install method, the respun ISO is no longer supported nor neeeded for booting Ubuntu on 9570 as the stock one contains the needed fixes.

All informations, tips and tricks was gathered from:

- [tomwwright gist for DELL XPS 15 9560](https://gist.github.com/tomwwright/f88e2ddb344cf99f299935e1312da880)
- [Atheros wifi card fix](https://ubuntuforums.org/showthread.php?t=2323812&page=2)
- [Respin script and info](http://linuxiumcomau.blogspot.com/)
- Myself xD

Kudos and all the credits for things not related to my work go to developers and users on those pages!

### What works out-of-the-box
 - ✅ Atheros Wifi
 - ✅ Audio
 - ✅ Audio on HDMI
 - ✅ HDMI ( even on lid closed )
 - ✅ Nvidia/Intel graphic cards switch
 - ✅ Keyboard backlight
 - ✅ Display brightness
 - ✅ Sleep/wake on Intel

### What does't work properly
 - ➖ Sleep/wake on nVidia

### What doesn't work
 - ❌ Goodix Fingerprint sensor

## Post-install script
If you already have a standard Ubuntu install, you can try applying basic tweaks with the `xps-tweaks.sh` script.
You can run it directly without cloning the repository with the following command (requires `curl`):
```shell
bash -c "$(curl -fsSL https://raw.githubusercontent.com/JackHack96/dell-xps-9570-ubuntu-respin/master/xps-tweaks.sh)"
```

If you want touchpad gestures using X11, check https://github.com/bulletmark/libinput-gestures or better https://github.com/iberianpig/fusuma.

## How to switch from one graphic card to the other
Starting from nVidia 435 drivers, we can finally offload apps like on Windows without having to use very complicated setups with Bumblebee.
If during the script you chose to not enabling offloading, you can use the classic `prime-select` command:

**Intel**:
```
sudo prime-select intel
```
**Nvidia**:
```
sudo prime-select nvidia
```

**Nvidia**:
```
sudo prime-select nvidia
```

**kernel params**:
```
Kernel Boot Options:. loglevel=0 pcie_aspm=force acpi_rev_override=1 mem_sleep_default=deep acpi_osi=Linux scsi_mod.use_blk_mq=1 nouveau.modeset=0 acpi_sleep=nonvs systemd.show_status=false nouveau.runpm=0 splash quiet drm.vblankoffdelay=1 apm=on apm=power-off
```

**Note: A full reboot could be required when switching graphic cards.**

## Troubleshooting

Check the [wiki page](https://github.com/JackHack96/dell-xps-9570-ubuntu-respin/wiki/Troubleshooting) about it.

## Beautify
[Gnome login change](https://www.ostechnix.com/how-to-change-gdm-login-screen-background-in-ubuntu/)  
[theme](https://www.gnome-look.org/p/1241688/)  
[icon pack](https://www.gnome-look.org/p/1102582/)  
[wine chinese input](https://www.lulinux.com/archives/359)  
[Sound-fix](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)  
[docker-fix](https://stackoverflow.com/questions/48957195/how-to-fix-docker-got-permission-denied-issue)  
[virtualbox](https://www.virtualbox.org/wiki/Download_Old_Builds_6_0)  
[k2](https://github.com/Kurgol/keychron/blob/master/k2.md)  
numlock: sudo gedit /usr/share/X11/xkb/keycodes/evdev, change NMLK to 770  
