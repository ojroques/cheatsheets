# ArchLinux Installation and Configuration Guide (2017.12.01)


## Pre-installation

#### Keyboard layout
    loadkeys fr-pc

#### Internet connection
    wifi-menu

#### Update the system clock
    timedatectl set-ntp true
    timedatectl set-timezone Europe/Paris

#### Partition the disks
    fdisk /dev/sda
        /dev/sda1: boot  (~256MB)
        /dev/sda2: swap  (~2GB)
        /dev/sda3: /     (~20GB)
        /dev/sda4: /home (>1GB)

#### Format the partitions
    mkfs.ext2 /dev/sda1
    mkfs.ext4 /dev/sda3
    mkfs.ext4 /dev/sda4
    mkswap /dev/sda2

#### Mount the file systems
    mount /dev/sda3 /mnt
    mkdir /mnt/home && mount /dev/sda4 /mnt/home
    mkdir /mnt/boot && mount /dev/sda1 /mnt/boot
    swapon /dev/sda2


## Installation

#### Install the base packages
    pacstrap /mnt base base-devel


## Configure the system

#### Fstab
    genfstab -U -p /mnt >> /mnt/etc/fstab

#### Chroot
    arch-chroot /mnt

#### Hostname
    echo <myhostname> > /etc/hostname
    echo '127.0.1.1 <myhostname>.localdomain <myhostname>' >> /etc/hosts

#### Locale and keyboard layout
Uncomment needed localizations in `/etc/locale.gen`, and generate them with:

    locale-gen

Then for keyboard layout and locale execute:

    echo LANG="en_US.UTF-8" > /etc/locale.conf
    echo KEYMAP=fr > /etc/vconsole.conf

#### Initramfs
    mkinitcpio -p linux

#### Root password
    passwd

#### Boot loader
    pacman -Syu grub
    grub-install --target=i386-pc --no-floppy --recheck /dev/sda
    grub-mkconfig -o /boot/grub/grub.cfg

#### WiFi connection
    pacman -S iw wpa_supplicant dialog wpa_actiond

#### Reboot
    exit
    umount -R /mnt
    reboot


## Post-installation

#### Add new users
    useradd -m -g users <user>
    passwd <user>

#### Network connection
    wifi-menu
    systemctl enable netctl-auto@<interface>.service

#### Xorg installation
    pacman -Syu xorg-server xorg-xinit xorg-xrdb

#### Window manager (i3wm with rofi)
    pacman -S i3 rofi

Open `~/.xinitrc` and add:

    exec i3

#### Display manager (lightdm)
    pacman -S lightdm lightdm-gtk-greeter
    systemctl enable lightdm.service

Change `user-session` to `user-session=i3` in `/etc/lightdm/lightdm.conf`

Change `background` to `background=#2b83a6` in `/etc/lightdm/lightdm-gtk-greeter.conf`

#### Terminal emulator (termite)
    pacman -S termite

#### Keyboard configuration in console
    localectl --no-convert set-x11-keymap fr

#### Privilege escalation
    pacman -S sudo

Execute `visudo` and add `<user> ALL=(ALL) ALL`

#### Volume
    pacman -S alsa-utils

#### Brightness
    pacman -S xf86-video-intel
    pacman -S xorg-xbacklight

#### Touchpad
    pacman -S xf86-input-synaptics

#### File management and USB devices (thunar)
    pacman -S thunar gvfs thunar-volman

#### Other applications
    pacman -S gcc git openssh zip unzip
    pacman -S chromium atom vim vlc
    pacman -S scrot feh xautolock
    pacman -S qt4 gtk3 gnome-themes-standard

#### Reboot
    reboot


## Configure the environment

#### Fonts
    pacman -S ttf-inconsolata adobe-source-sans-pro-fonts
    git clone https://aur.archlinux.org/ttf-font-awesome.git
    makepkg -si

#### Apps configuration
Clone the dotfiles repository into `~/`:

    git clone https://github.com/ojroques/dotfiles.git

Copy `~/dotfiles/i3/config` into `~/.config/i3/`

Copy `~/dotfiles/i3status/config` into `~/.config/i3status/`

Copy `~/dotfiles/rofi/config` into `~/.config/rofi/`

Copy `~/dotfiles/termite/config` into `~/.config/termite/`

Copy `~/dotfiles/.gitconfig` into `~/`

Copy `~/dotfiles/70-synaptics.conf` into `/etc/X11/xorg.conf.d/`

Change `/path/` in `~/.config/i3/config` with a wallpaper path

Reboot

#### SSH key
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    eval $(ssh-agent -s)
    ssh-add ~/.ssh/id_rsa


## Troubleshooting
Boot ArchLinux from the `.iso` file, then execute:

    loadkeys fr-pc
    mount /dev/sda3 /mnt
    mount /dev/sda1 /mnt/boot
    mount /dev/sda4 /mnt/home
    arch-chroot /mnt
    (...)
    exit
    umount -R /mnt
    reboot