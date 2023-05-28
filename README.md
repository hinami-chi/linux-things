# arch-linux-things
This is for personal use :) if you understand something, you can use it. (Arch linux)

# sudo ./gosumemory --path /ubicación/donde/esta/tu/carpeta/songs/del/osu/XD

# mysql
```
sudo pacman -Syu
yay -S mariadb mysql-workbench
sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql
sudo systemctl start mariadb
sudo mysql_secure_installation
Enter
n
n
Y
Y
Y
Y
sudo mysql -u root
```
# bancho.py
```
CREATE DATABASE banchopydev;
CREATE USER 'hinami'@'localhost' IDENTIFIED BY 'hinami';
GRANT ALL PRIVILEGES ON banchopydev.* TO 'hinami'@'localhost';
FLUSH PRIVILEGES;
sudo mysql -u hinami -p
yay -S nginx
sudo systemctl start nginx
yay -S redis
sudo systemctl start redis
yay -S python39
mysql -u hinami -p banchopydev < migrations/base.sql
```

# yuzu EA

```
sudo pacman -Syu --needed base-devel boost catch2 cmake ffmpeg fmt git glslang libzip lz4 mbedtls ninja nlohmann-json openssl opus python-pip python2 qt5 sdl2 zlib zstd
```

# flameshot

```
yay -S flameshot
Settings > Keyobard > Hotkeys > Programs > flameshot gui
```
![](https://i.imgur.com/v1OPuEg.png)

# T-Launcher Minecraft

```
yay -S jre8
https://dl2.tlauncher.org/f.php?f=files%2FTLauncher-2.8.zip
```

# oldsu osu! 2009

```
yay -S dotnet-runtime
```

# EpicGames
```
sudo pacman -Syu cabextract cups faudio lib32-acl lib32-faudio lib32-fontconfig lib32-freetype2 lib32-gettext lib32-giflib lib32-gnutls lib32-gst-plugins-base-libs lib32-gtk3 lib32-harfbuzz lib32-lcms2 lib32-libjpeg-turbo lib32-libldap lib32-libnl lib32-libpcap lib32-libpng lib32-libtasn1 lib32-libtiff lib32-libusb lib32-libxcomposite lib32-libxinerama lib32-libxrandr lib32-libxslt lib32-libxss lib32-mpg123 lib32-nspr lib32-nss lib32-opencl-icd-loader lib32-p11-kit lib32-sqlite lib32-v4l-utils lib32-vkd3d lib32-vulkan-icd-loader libimagequant lsof opencl-icd-loader python-distro python-evdev python-pillow sane vkd3d zenity icoutils xterm wget curl libudev0-shim python2 wxgtk-common wxgtk3 gnu-netcat lib32-libudev0-shim python2-wxpython3 vulkan-tools gamemode lib32-gamemode
```
```
wget -T 2 https://portwine-linux.ru/ftp/portwine/PortEpic-26 && sh "./PortEpic-26" && rm -f "./PortEpic-26"
```

# RetroArch

```
sudo pacman -S retroarch retroarch-assets-xmb retroarch-assets-ozone retroarch-assets-glui
sudo pacman -S libretro
sudo pacman -Ss libretro | grep "emu" # in emu you can put snes, mupen, etc.
```

# GatariServer
First edit `sudo leafpad /etc/hosts` and put theses IPs:
```
163.172.255.42 osu.ppy.sh
163.172.255.42 c.ppy.sh
163.172.255.42 c1.ppy.sh
163.172.255.42 c2.ppy.sh
163.172.255.42 c3.ppy.sh
163.172.255.42 c4.ppy.sh
163.172.255.42 c5.ppy.sh
163.172.255.42 c6.ppy.sh
163.172.255.42 ce.ppy.sh
163.172.255.42 a.ppy.sh
163.172.255.42 i.ppy.sh
163.172.255.42 s.ppy.sh
```
[this](http://storage.gatari.pw/ce.crt) file and put it `sudo cp /home/hinami/Descargas/ce.crt /etc/ca-certificates/trust-source/anchors/`, later update certifies with `sudo trust extract-compat`, later do: 
```
wine control # Preferencias de Internet -> Contenido -> Certificados -> Importar -> Sigues los pasos para importar, pero lo importas dos veces (primero por el automatico, y luego por Autoridades de Certificación de Raíz de Confianza)
export WINEPREFIX="$HOME/.wine_osu" 
export PATH=/opt/wine-osu/bin:$PATH
wine control
sudo su
cat /home/hinami/Descargas/ce.crt >> /etc/ssl/certs/ca-certificates.crt
```

# BetterDiscord

```
yay -S discord
yay -S betterdiscordctl-git
betterdiscordctl install
betterdiscordctl reinstall
```
+ [MessageLogger](https://cdn.discordapp.com/attachments/788296417251950593/800944412258729984/MessageLoggerV2.plugin.js)

# OpenTabletDriver

```
yay -S opentabletdriver
echo "blacklist wacom" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo rmmod wacom
sudo chmod 0666 /dev/uinput
systemctl --user enable opentabletdriver --now
systemctl --user restart opentabletdriver
```

# /etc/X11/xorg.conf.d/20-amdgpu.conf

```
Section "Device"
        Identifier "AMD"
        Driver  "amdgpu"
	Option "DRI" "3" 
        Option "TearFree" "true"
	Option "VariableRefresh" "true"
	Option "AccelMethod" "glamor"
	Option "SwapBuffersWait" "false"
EndSection
```

# yay

```
sudo pacman -S yay base-devel
```

# osu!
+ Video drivers, wine, winetricks
```
sudo pacman -S wine-staging winetricks giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama ncurses lib32-ncurses opencl-icd-loader lib32-opencl-icd-loader libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader lib32-mesa vulkan-intel lib32-vulkan-intel xorg xorg-server -y
```
+ For enable ACO
```
sudo nano /etc/environment
RADV_PERFTEST=aco
```
+ Install osu-wine

Download [wine-osu](https://drive.google.com/drive/folders/17MVlyXixv7uS3JW4B-H8oS4qgLn7eBw5) or the build I [use](https://1drv.ms/u/s!AgTOhQ7V3TN8j3CguPol4TOAXOdS?e=j7YdCH), for install:
```
cd Download
yay -U wine-osu-5.14-2-x86_64.pkg.tar.zst OR yay -U old_wine-osu-6.8-1-x86_64.pkg.tar.zst
```
+ Creating osu-wine prefix
```
export WINEPREFIX="$HOME/.wine_osu"
export WINEARCH=win32
export PATH=/opt/wine-osu/bin:$PATH
winetricks --force dotnet40 # do not install mono or gecko
winetricks gdiplus
```
+ osu! installation
```
wget https://m1.ppy.sh/r/osu\!install.exe # you can skip this step if you want use an older instalation
wine osu\!install.exe

# for wine internet issues:
sudo setcap cap_net_raw+epi /usr/bin/wine-preloader 
sudo setcap -r /usr/bin/wine-preloader
```
+ Low latency

Copy and paste these files with `sudo` in `/etc/pulse` : [daemon.conf](https://cdn.discordapp.com/attachments/787140086151774248/798790395537784855/daemon.conf), [default.pa](https://cdn.discordapp.com/attachments/787140086151774248/798790398126063636/default.pa), later put this [file](https://cdn.discordapp.com/attachments/862792192388497408/871246685127458836/limits.conf) in `/etc/security/` and put `pulseaudio -k` in terminal for restart pulse.


+ WindowsFonts

Download [this](https://1drv.ms/u/s!AgTOhQ7V3TN8jlZ1TL0afz19rgTS?e=7SrxGy) and put it in `/usr/share/fonts/WindowsFonts`

+ osu! Script
```
#!/bin/sh
export WINEPREFIX="$HOME/.wine_osu" 
export PATH=/opt/wine-osu/bin:$PATH 
export STAGING_AUDIO_DURATION=100000 # value will depend of your cpu, lower value is lower latency, I recommend 150000 for a low-end cpu like pentium from 2015
cd /your/osu/directory/xd/
wine osu!.exe "$@"
```
If you cannot execute osu!, try enabling AudioCompatibility in `osu!/osu!.<user>.cfg` and search AudioCompatibility, it will be in 0, change it to 1
```
AudioCompatibility = 1
```

# Refresh rate change (use ```xrandr``` for show proprieties)

```
cvt <horizontal resolution> <vertical resolution> <refresh rate>
xrandr --newmode <copypaste for cvt> 
xrandr --addmode <output video> <resolution_hertz>
xrandr --output <output video> --mode <resolution_hertz>
```
+ 143Hz example
```
cvt 1920 1080 143
xrandr --newmode "1920x1080_143.00"  449.00  1920 2088 2296 2672  1080 1083 1088 1176 -hsync +vsync
xrandr --addmode HDMI-A-0 1920x1080_143.00
xrandr --output HDMI-A-0 --mode 1920x1080_143.00 
```
+ Dual monitors example
```
#!/bin/bash
xrandr --newmode "1920x1080_143.00"  449.00  1920 2088 2296 2672  1080 1083 1088 1176 -hsync +vsync
xrandr --addmode HDMI-A-0 1920x1080_143.00
xrandr --newmode "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync   
xrandr --addmode DisplayPort-1 1024x768_75.00
xrandr --output HDMI-A-0 --mode 1920x1080_143.00 --right-of DisplayPort-1
xrandr --output DisplayPort-1 --mode 1024x768_75.00
```

# osr2mp4
```
sudo pacman -S python-pip
git clone https://github.com/uyitroa/osr2mp4-app
cd osr2mp4-app
pip install -r requirements.txt
python install.py
python main.py
```
+ Script
```
#!/bin/bash

export PYENV_VERSION=3.6.8
python '/home/<user>/osr2mp4-app/main.py'

# Reset version
unset PYENV_VERSION
```
