# ARTIX INSTALLAZIONE
[![](https://img.shields.io/badge/Artix-Linux%20OS-blue?style=for-the-badge&logo=Artix+Linux)](https://artixlinux.org/)

## Installazione via shell del sistema base
- Avviare il boot da Artix live usb (LOGIN & PASS = artix) | Usate una iso con grafica integrata
- Connettere il sistema ad internet
- Aprire gparted o disks e formattare il sistema
- Avviare il terminale ed evitare l'auto installazione buggata

### Aquisire lo script di installazione, estrarre ed entrare nella cartella estratta
```
curl -OL https://github.com/ayaneechan/artix_installazione/archive/Installazione-artix-ita-1.0.tar.gz
```
```
tar xzf Installazione-artix-ita-1.0.tar.gz.tar.gz
```
```
cd Installazione-artix-ita-1.0.tar.gz
```
### Avviare lo script
```
sudo ./install.sh
```

## Quando si aprono i comandi: (la guida segue openrc)
### (openrc/dinit)
```
openrc
```
### Mettere il disco dove volete installare la distro es. /dev/sda
```
/dev/sda
```
### Partizione di swap (0=senza)
```
4
```
### Filesystem (quello che preferite es. ext4)
```
ext4
```
### Cryptazione (si o no)
```
y
```
### Timezone
```
Europe/Rome
```
### hostname (es. fag-army)
```
fag-army
```
### password di root (voi mettetene una sicura)
```
1234
```
### ora aspettate (deve scaricare tutti i pacchetti), infine riavviate
```
sudo reboot
```
### togliere immediatamente la chiavetta usb *consigliato

# Configurazione post-installazione

### Modificare il file e aggiungere le repo dopo [galaxy] | basta un server solo
```
[universe]
Server = https://universe.artixlinux.org/$arch
Server = https://mirror1.artixlinux.org/universe/$arch
Server = https://mirror.pascalpuffke.de/artix-universe/$arch
Server = https://artixlinux.qontinuum.space/artixlinux/universe/os/$arch
Server = https://mirror1.cl.netactuate.com/artix/universe/$arch
Server = https://ftp.crifo.org/artix-universe/
```
### Aggiornare le repo
```
sudo pacman -Syu 
```
### Aggiungere il supporto ad arch
```
sudo pacman -S artix-archlinux-support
```
## aggiungere le repo di https://wiki.artixlinux.org/Main/Repositories
```
sudo nano /etc/pacman.conf
```
### aggiungere in fondo al file o dopo le repo #Artix per non creare confusione
```
#Archlinux
[extra]
Include = /etc/pacman.d/mirrorlist-arch

[community]
Include = /etc/pacman.d/mirrorlist-arch
```
### Aggiornare le repo
```
sudo pacman -Syu 
```
### Installare un text editor (artix consiglia 'nano')
```
sudo pacman -S nano
```
### Per sicurezza installare questi pacchetti
```
sudo pacman dialog dosfstools 
```
### Installare le utility audio
```
pacman -S pipewire pipewire-pulse alsa-utils
```
### Aggiungere proprio utente (es. sonozoccola)
```
useradd -mG wheel sonozoccola
```
```
passwd sonozoccola
```
### Aggiungere i permessi di root
```
EDITOR=nano visudo
```
### Togliere il cancelletto da %wheel ALL=(ALL) ALL

### Installiamo la parte grafica; se sapete cosa state facendo potete non installare alcuni paccheti inutili (altrimenti no)
```
sudo pacman -S xorg xf86-video-amdgpu lightdm-openrc lightdm-gtk-greeter mate mate-extra system-config-printer connman-gtk
```
### Attivate il vostro display manager
```
sudo rc-update add lightdm default
```

# Riavviate e divertitevi
## Alcuni programmi utili:
### Gnome disks (gestione dischi)
```
sudo pacman -S gnome-disk-utility
```
### Pamac (gestore software)
```
sudo pacman -S pamac
```
### Dino (xmpp client)
```
sudo pacman -S dino
```
### Kleopatra (chiavi openPGP)
```
sudo pacman -S kleopatra
```
### Telegram
```
sudo pacman -S telegram-desktop
```
### Libreoffice (office)
```
sudo pacman -S libreoffice
```
### Mpv (video player)
```
sudo pacman -S mpv
```
### Freetube (client YT privato)
```
sudo pacman -S freetube
```
### Evolution (mail manager)
```
sudo pacman -S evolution
```
### Librewolf (Browser privato)
```
sudo pacman -S librewolf
```
