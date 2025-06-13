# Base - system
multilib => /etc/pacman.conf 
multicore-build => /etc/makepkg.cong MAKEFLAGS="-jX[cpu core]"
```
sudo pacman -Sy|sudo pacman -S base-devel git | git clone https://aur.archlinux.org/yay.git|cd yay/|makepkg -si;
yay --noconfirm -Syu;
yay --noconfirm -S binutils fakeroot zsh zsh-autosuggestions zsh-syntax-highlighting mkinitcpio-firmware libqalculate qalculate-gtk bc htop iftop filelight neofetch python nerd-fonts-inconsolata ttf-inconsolata ttf-vista-fonts ttf-ms-fonts noto-fonts-emoji xidlehook sxiv cmus harmonoid-bin playerctl pcmanfm ffmpeg yt-dlp bleachbit czkawka-gui-bin guvcview zathura zathura-cb zathura-djvu zathura-pdf-mupdf zathura-ps cups cups-pdf skanlite lib32-libpulse lib32-alsa-plugins zip unzip python-pywal cava tty-clock-git cbonsai rofi rofi-emoji vim neovim vim-plug brightnessctl pulsemixer pipewire pipewire-alsa pipewire-pulse pipewire-jack qlib32-pipewire qjackctl android-file-transfer alacritty termite lf-bin auto-cpufreq lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings betterlockscreen xarchiver xorg xorg-xset xorg-xinput openbox nitrogen tint2 volumeicon dunst xclip redshift scrot lxappearance lxappearance-obconf obmenu-generator obmenu picom noise-suppression-for-voice tenacity-git obsidian-appimage syncthing opentabletdriver kdeconnect tldr pyenv;
yay -c;yay -Scc;yay -Sc;
systemctl enable auto-cpufreq;systemctl enable betterlockscreen@USER --nowl
picom -b;
systemctl --user daemon-reload;systemctl --user enable opentabletdriver --now
```

# Nerdfonts
```
wget /tmp/Inconsolata.zip "https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/Inconsolata.zip";
cd /tmp/;
unzip Inconsolata.zip;
mv *.ttf /usr/share/fonts/;
```

# NvChad
```
git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim
```

vim ~/.config/nvim/lua/custom/chadrc.lua
https://github.com/NvChad/NvChad/discussions/1204
vim ~/.config/nvim/lua/core/init.lua -> opt.mouse = ""

*nvim nvchad cheatsheet space+ch*

# vim replace newline and stil want a newline
:% s/\n/a\r/g

# Home mode
yay -S steam firefox discord gimp krita kdenlive lutris mpv cmus libreoffice-still spotify notepadqq xournalpp qbittorrent handbreak obs-studio easytag mkvtoolnix-gui thokr-git zsh zsh-autosuggestions zsh-syntax-highlighting opentabletdriver alacritty neovim vim syncthing kdeconnect
  bash <(curl -sSL https://raw.githubusercontent.com/SpotX-CLI/SpotX-Linux/main/install.sh)
  git clone https://github.com/NvChad/NvChad ~/.config/nvim --depth 1 && nvim
  vim ~/.config/nvim/lua/custom/chadrc.lua
  https://github.com/NvChad/NvChad/discussions/1204
  vim ~/.config/nvim/lua/core/init.lua
  opt.mouse = ""

# Dev mode
yay -S neovim vim vscodium-bin libreolf-bin godot alacritty zsh zsh-autosuggestions zsh-syntax-highlighting 

# Reflector

sudo vim /etc/xdg/reflector/reflector.conf
sudo reflector --latest 15 --age 2 --fastest 15 --protocol https --sort rate --save /etc/pacman.d/mirrorlist

--save /etc/pacman.d/mirrorlist
--protocol https
--fastest 15
--latest 15
--sort rate

sudo vim /etc/pacman.conf

Server = http://mirror.archlinuxarm.org/archlinux/$repo/os/$arch
[core] 
Server = http://mirror.archlinuxarm.org/archlinux/$repo/os/$arch 
Include = /etc/pacman.d/mirrorlist
[extra] 
Server = http://mirror.archlinuxarm.org/archlinux/$repo/os/$arch 
Include = /etc/pacman.d/mirrorlist
[core] 
Server = http://mirror.archlinuxarm.org/archlinux/$repo/os/$arch 
Include = /etc/pacman.d/mirrorlist

# XFCE Switch language
xfce4-xkb-plugin

# Install didn't detect hard disk 
https://wiki.archlinux.org/title/Partitioning#Drives_are_not_visible_when_firmware_RAID_is_enabled
https://wiki.archlinux.org/title/EFI_system_partition#Check_for_an_existing_partition

# cmus slow quiting
```
cmus;exit
```

# cmus notification
https://github.com/dcx86r/cmus-notify

# rm -rf recover
yay -S testdisk
https://www.youtube.com/watch?v=EmG0wLcwVaM
https://www.youtube.com/watch?v=Kkt1-QeS9Qs

# Arch overwrite install
sudo pacman -S package-name --overwrite '*'
yay -S package-name --overwrite '*'

# Khinsider Bulk
Teamper Monkey
https://greasyfork.org/en/scripts/424015-vgmloaderx

# Angsana New Takeover
https://freefontsdownload.net/free-angsana_new-font-66184.htm
unzip and move it to /usr/share/fonts
fc-cache
sudo vim /etc/fonts/fonts.conf 
add :
        <alias>
                <family>sans-serif</family>
                <default>
                        <family>Noto Sans Thai</family>
                </default>
                </alias>
        <alias>
                <family>serif</family>
                <default>
                        <family>Noto Serif Thai</family>
                </default>
        </alias>

# Game ost
- yt : 
+ chapter : yt-dlp -f 140 --split-chapters -o "%(chapter_number)s.%(chapter)s.%(ext)s" "$(xclip -o)"
+ playlist :  yt-dlp -f 140 -o "%(playlist_index)s.%(title)s.%(ext)s" "$(xclip -o)"
+ video and audio : yt-dlp "$(xclip -o)"-f 400+140 --embed-subs

- https://downloads.khinsider.com/
- https://www.sittingonclouds.net/

# khinisder userscript download all
Tampermonkey -> https://codeberg.org/sun/userscripts/src/branch/main/user/VGMLoaderX.user.js#bypass=true -> remove all error line (librewolf)

# ffmpeg albumart extraction
ffmpeg -i input.xxx -an -vcodec copy cover.jpg

# ffmpeg mp3 to m4a (copy cover)
ffmpeg -i "$(ls *.mp3|head -1)" -an -vcodec copy cover.jpg;for i in *.mp3;do ffmpeg -i $i -i cover.jpg -c:a aac ${i%.*}.m4a;done;rm cover.jpg

# ffmpeg m4a to mp3 (copy cover)
ffmpeg -i "$(ls *.m4a|head -1)" -an -vcodec copy cover.jpg;for i in *.m4a;do ffmpeg -i $i -i cover.jpg -c:a libmp3lame ${i%.*}.mp3;done;rm cover.jpg

# ffmpeg audio merge
for a in *.ogg;do echo 'file '$a >> list.txt;done
ffmpeg -f concat -i list.txt -safe 0 -c copy a.ogg

# many directory
for x in */;do cd $x;mkdir m4a;for i in *.mp3;do ffmpeg -i $i -vn -c:a aac m4a/${i%.*}.m4a;done;notify-send "Done\!";cd ..;done
for x in */;do cd $x;mv m4a/* .;rm -rf *.mp3|rm -rf m4a/;cd ..;done

# ffmpeg img to vid
ffmpeg -loop 1 -framerate 1 -i a.jpg -c:v libx264 -t "time-duration-sec" x.mp4

# ffmpeg increase audio volume
ffmpeg -i a.mp4 -af volume=7 -vn x.mp4

# ffmpeg increase audio volume
ffmpeg -i a.mp4 -filter:a "volume=10dB" -c:v copy out.mp4

# Reduce image quality
Install imagemagick
convert a.jpg -quality '70%' b.jpg

# resize image
convert a.jpg -resize 1920x1080 b.jpg

# Batch convert img
for i in *.png;do convert $i ${i%.*}.jpg;done
mkdir re;for i in *;do convert  $i -resize 75% re/${i%.*}.jpg;done;rm *.png;mv re/* .;rm -rf re;cd ..
convert "$(xclip -o -selection clipboard)"  -resize 75%  "$(xclip -o -selection clipboard)"
for i in *.png;do convert $i ${i%.png}.jpg;done

# Batch rename char before file exts
https://askubuntu.com/questions/976368/how-to-remove-characters-from-file-names-using-command-line
renamed '01_1644787774.chess45_01.jpg' -> '01_1644787774.jpg'
renamed '02_1649091297.chess45_02a.jpg' -> '02_1649091297.jpg'
renamed '03_1649202160.chess45_02a.jpg' -> '03_1649202160.jpg'

for i in *.m4a;do mv $i "$(echo $i|cut -d\- -f3).m4a";done

# rename batch img in sub folder from text list
while read i;do cd $i;for j in *.jpg;do mv $j 0$j;done;cd ..;done < list2
for i in *;do cd $i;for j in {0..9};do mv $(find . -iname $j.jpg) 0$j.jpg;done;cd ..;done

# remove extra number
https://stackoverflow.com/questions/14928238/bash-remove-numbers-at-the-end-of-names
for i in *.jpg; do mv "$i" "${i%-*}.jpg"; done
'01_1644787774.jpg' -> '01.jpg'
'02_1649091297.jpg' -> '02.jpg'
'03_1649202160.jpg' -> '03.jpg'
'04_1653161177.jpg' -> '04.jpg'

# Img Scrapping
wget $(curl https://mangakakalot.com/chapter/toki_doki/chapter_0 |grep -Eo '<img src[^>]+>'|cut -d\" -f2)A
wget $(curl 'https://multmage.net/manga/a_suspiciously_childhood_friend'|grep -Eo 'https://multmage.net/sites/default/files/styles/beebox_4k/public/manga/others/gudl_a_suspiciously_childhood_friend/[^>]+'|cut -d\? -f1)
wget $(curl 'https://multmage.net/manga/koi' | grep -Eo 'https://multmage.net/sites/default/files/styles/beebox_4k/public/manga/others/jorori_koi/[^?]+')

# Get all url
curl 'https://www.mangaread.org/manga/love-advice-from-the-great-duke-of-hell/' | grep -Eo "https://www.mangaread.org/manga/love-advice-from-the-great-duke-of-hell/chapter-[^/]+"
for i in {1..5};do mkdir $i;cd $i;touch hello;cd ..;done
while read i;do echo $i|cut -d\/ -f6;done < list.txt
while read i;do mkdir $(echo "$i"|cut -d\/ -f6);cd $(echo "$i"|cut -d\/ -f6);wget $(curl "$i"|grep -Eo 'https://www.mangaread.org/wp-content/uploads/WP-manga/data/manga_63417195079b7/[^>]+'|cut -d\" -f1);cd ..;done < list.txt

curl https://mycomics.com/category/jackkit/ | grep -Eo "https://mycomics.com/a-complete-guide-to-succession-[^/]+" > list.txt
while read i;do mkdir $(echo "$i"|cut -d\/ -f4);cd $(echo "$i"|cut -d\/ -f4);wget $(curl "$i"|grep "pswp-width"|grep -Eo "https://mycomics.com/wp-content/uploads/[^\"]+");cd ..;done < list.txt

curl https://mangakatana.com/manga/kimi-wa-midara-na-boku-no-joou.9080|grep -Eo "https://mangakatana.com/manga/kimi-wa-midara-na-boku-no-joou.9080[^\"]+" >list.txt
while read i;do mkdir $(echo "$i"|cut -d\/ -f6);cd $(echo "$i"|cut -d\/ -f6);wget $(curl "$i"|sed -z 's/,/\n/g'|grep -Eo "https://i[^\"]+.jpg");cd ..;done < list.txt

for i in {1..3};do curl "https://modelth.com/onlyfan/" | grep -Eo "<a class=\"elementor-post__thumbnail__link\" href=\"https://modelsexyth.com/[^\"]+"|grep -Eo "https://modelth.com/[^\/]+" >> list;done
while read i;do mkdir $(echo "$i"|cut -d\/ -f4);cd $(echo "$i"|cut -d\/ -f4);wget $(curl -L $i|grep -Eo "https://www.mymypic.net/data/attachment/forum/[^\"]+");cd ..;done < list
for i in $(ls -d */);do for j in {1..3};do cd $i;rm *.$j;cd ..;done;done
du -h . | grep -E "0        "| awk '{print $2}'

for i in {1..11};do curl "https://youme.com/img/?_page=$i"| grep -Eo "<a href=\"https://youme.com/[^\"]+" >> list;done;sort -u list > listn;rm list;mv listn list
while read i;do mkdir $(echo "$i"|cut -d\/ -f5);cd $(echo "$i"|cut -d\/ -f5);wget $(curl "$i"|grep -Eo "https://youme.com/wp-content/uploads/[^\g]+"g);rm $(cat ../rm.txt|sed -z 's/\n/ /g');cd ..;done < list
for i in $(ls -d */);do for j in {1..3};do cd $i;rm *.$j;cd ..;done;done
for i in $(ls -d */);do cd $i;rm $(ls | grep x);cd ..;done

for i in {1..17};do curl https://www.jaekwarp.com/category/onlyfans/page/$i/ | grep -Eo "<a class=\"post-thumbnail d-block\" href=\"https://www.jaekwarp.com/[^\"]+" | grep -Eo "https://www.jaekwarp.com/[^\"]+" >> list;done
while read i;do mkdir $(echo "$i"|cut -d\/ -f4);cd $(echo "$i"|cut -d\/ -f4);wget $(curl "$i"|grep -Eo "href=\"https://www.jaekwarp.com/wp-content/uploads/[^?]+"|sed -z 's/href="//g';);cd ..;done < list
while read i;do mkdir $(echo "$i"|cut -d\/ -f4);cd $(echo "$i"|cut -d\/ -f4);wget $(curl "$i"|grep -Eo "href=\"https://www.jaekwarp.com/[^\"]+"|grep gid|cut -d\" -f2|cut -d\? -f1);cd ..;done < list

while read i;do mkdir $(echo "$i"|cut -d\/ -f5);cd $(echo "$i"|cut -d\/ -f5);wget $(curl $i|grep -Eo "https://multmage.net/sites/default/files/styles/beebox_2k/public/manga/others/peach_demon_king[^\?]+");cd ..;done<list

for i in {1..44};do curl "https://wallhaven.cc/search?categories=001&purity=010&topRange=1M&sorting=toplist&order=desc&ai_art_filter=1&page=$i"| grep -Eo "https://wallhaven.cc/w/[^\"]+";done > list
while read i;do wget -nc $(curl $i|grep -Eo "https://w.wallhaven.cc/full/[^\"]+");done < list
diff -c dupe2 dupe | grep "\- "|grep -v "\-\-\-"> lost
ls | cut -d- -f2|cut -d\. -f1 > dupe
cat list|cut -d\/ -f5 > dupe2
while read i;do wget $(curl $i|grep -Eo "https://w.wallhaven.cc/full/[^\"]+");done < lost
for i in *.png;do convert $i -resize "85%" -quality "75%" f/${i%.png}.jpg;done
for i in *.jpg;do convert $i -resize "85%" -quality "75%" f/$i;done

nf : f12 > network > cookie wtih cf_ & rem > curl --cookie "var" --limit-rate 10k
for i in {1..63};do curl --cookie "$(cat token)" --limit-rate 10k "https://wallhaven.cc/search?categories=001&purity=001&topRange=1M&sorting=toplist&order=desc&ai_art_filter=1&page=$i" | grep -Eo "https://wallhaven.cc/w/[^\"]+";done > list
while read i;do wget -nc $(curl --cookie "$(cat token)" --limit-rate 10k $i|grep -Eo "https://w.wallhaven.cc/full/[^\"]+");done < list
ls | cut -d- -f2|cut -d\. -f1 > dupe
cat list-tm_6-5-23|cut -d\/ -f5 > dupe2|sort -u dupe2 > dupe2
diff -c dupe2 dupe | grep "\- "|grep -v "\-\-\-"> lost;cat lost | sed -i 's/- /https://wallhaven.cc/w//g' lost # manully replace

for x in $(curl "https://www.wongnai.com/cooking/cookbooks/blood-sugar-control-recipes"|grep -Eo "recipes/[^\"]+" | sort -u);do echo "https://www.wongnai.com/$x";done | xclip -selection clipboard
for x in $(curl "https://www.wongnai.com/cooking/cookbooks/blood-sugar-control-recipes"|grep -Eo "recipes/[^\<]+" | sort -u|cut -d\> -f2);do echo "$x";done | xclip -selection clipboard

for i in {1..2};do curl "https://a-booru.org/g/2658654/b0ab307708/?p=$(($i-1))" |grep -Eo "\"https://e-hentai.org/s/[^\"]+"|cut -d\" -f2;done > list
for i in {1..2};do curl "$(xclip -o)/?p=$(($i-1))" |grep -Eo "\"https://e-hentai.org/s/[^\"]+"| cut -d\" -f2;done > list
while read i;do wget -nc "$(curl $i|grep -Eo "src=\"[^\"]+"|cut -d\" -f2|grep '.jpg')";done < list

curl "https://mangakakalot.com/manga/summer_ghost" | grep -Eo "https://mangakakalot.com/chapter/summer_ghost/chapter_[^\"]+" > list.txt
while read i;do mkdir "$(echo $i|cut -d\/ -f6)";cd "$(echo $i|cut -d\/ -f6)";wget -nc --user-agent="Mozilla/5.0 (Windows NT 10.0; rv:109.0) Gecko/20100101 Firefox/118.0" --referer="https://mangakakalot.com/" $(curl $i|grep -Eo "https://v12.mkklcdnv6tempv4.com[^\"]+");cd ..;done < list.txt

curl "https://projectmoon.postype.com/series/875159/leviathanprojectmooncomicsenglish" | grep -Eo "https://projectmoon.postype.com/post/[^\"]+" | sort -u > list
curl "https://projectmoon.postype.com/series/875159/page/2" | grep -Eo "https://projectmoon.postype.com/post/[^\"]+" | sort -u >> list

curl 'https://limbuscompany.fandom.com/wiki/Lobotomy_E.G.O::Regret_Faust/Voicelines' | grep -Eo 'https://static.wikia.nocookie.net/limbuscompany/images/[^\"]+'|grep -E "Lobo" > list
while read i;do wget $i;done<list;rm list

# Zathura gap
make sure in resize with same scale

# tranfer music to andriod no data loss
check coverart
zip it! and transfer
unknow artist -> tag editor in phone

# Switch language
sudo vim /etc/X11/xorg.conf.d/00-keyboard.conf
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "us,th"
        Option "XkbOptions" "grp:win_space_toggle"
EndSection

# Noise reduction Pipewire
https://medium.com/@gamunu/linux-noise-cancellation-b9f997f6764d

sudo vim /etc/systemd/user/pipewire-input-filter-chain.service
Change reduction vol "VAD Threshold(%)" 35.0 / line 42

# [Printer](https://wiki.archlinux.org/title/CUPS)
sudo systemctl enable cups

# [Scanner](https://wiki.archlinux.org/title/SANE)
yay -S skanlite

# Openbox custom bash script rc.xml
paste script in /bin/

# Wifi Terminal
nmcli

# Arduino can't upload to port ...
sudo chmod a+rw /dev/tty$(USB...)

# Discord update
https://wiki.archlinux.org/title/Discord#Discord_asks_for_an_update_not_yet_available_in_the_repository
https://www.youtube.com/watch?v=3OEfr7L-gUk [4:04]

# CUPS
get driver : https://www.openprinting.org/printers
yay system-config-printer cups cups-pdf
- disable banner
lpadmin -p <Printer Name> -o job-sheets-default=none
**check print option in programs [like gimp]**

# CUPS MP280
yay -S cnijfilter-mp280 scangearmp-mp280
first page print is secret page
not printing = reinstall driver and restart printer

# VPN
yay -S openvpn 
go to https://vpngate.net/en
choose server
download .ovpn
sudo openvpn /PATH/*.ovpn

# Firefox youtube fullscreen scrollbar (UBlockOrigin)
Ublock Origin -> Three cogwheels ("Open the dashboard") -> My Filters
www.youtube.com##ytd-app:style(overflow: hidden !important;)

# Warframe shuttering
proton GE 
Async

# Screnn share android
https://medium.com/android-news/wireless-debugging-through-adb-in-android-using-wifi-965f7edd163a
yay -S scrcpy sndcpy
Phone : Open debuginh via usb
scrcpy -M -K # allow mouse & sound on phone
sndcpy 192.168.0.200:5555 (need to install snd on phone)

# sndcpy mpv
sudo vim /opt/sndcpy/sndcpy
add
MPV=${MPV:-mpv}
"$MPV" --demuxer=rawaudio --demuxer-rawaudio-rate=48000 --no-cache --untimed --no-demuxer-thread --demuxer-cache-wait=no --player-operation-mode=cplayer tcp://localhost:"$SNDCPY_PORT"

# Tor
yay -S tor-browser
//yay -S torbrowser-launcher

# Audiobookbay magnet
hash info

# Libgen torrent
MD5

# Remove open with wine
~/.local/share/applications
rm -rf wine*

# Usb port loop
-unplug other usb
echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind;echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind;echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind;echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind

# pywal plugin
Zathura : https://github.com/GideonWolfe/Zathura-Pywal #no sudo
Librewolf : - https://addons.mozilla.org/en-US/firefox/addon/pywalfox/
- yay -S python-pywalfox;sudo pywalfox -g install;sudo mkdir /usr/lib/librewolf/native-messaging-hosts/;sudo cp /usr/lib/mozilla/native-messaging-hosts/pywalfox.json /usr/lib/librewolf/native-messaging-hosts/pywalfox.json;sudo rm -rf /usr/lib/mozilla/

# file in file
zip b.zip b.txt
cat a.jpg b.zip > c.jpg

# Steam
+ Crash at start
	- remove linux runtime soilder and reinstall proton + runtime
	- if can't > launch option = PROTON_USE_WINED3D11=1 %command%

# Steam connection error
1) ##temp| terminal steam -tcp
2) copy nameserve in '/run/systemd/resolve/stub-resolv.conf' to /etc/resolv.conf

# Steam Let me choose another location
yay -S xdg-desktop-portal

# Steam Warframe not launch
Move runtime to ext4
remove gamoderun in launch option

# SAM (Steam Achievements Manager)
yay -S samrewritten-git

# gamemode
yay -S gamemode lib32-gamemode 
gamemode -t

# lightdm failed after restart
sudo vim /etc/lightdm/lightdm.conf
[LightDM]
logind-check-graphical=true

# lightdm manual login
sudo vim /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-show-manual-login = true
greeter-hide-users = true

# laptop - touchpad scrolling 
vim /etc/X11/xorg.conf.d/30-touchpad.conf
Option "NaturalScrolling" "on"

# change mouse sensitivity
xinput set-float-prop $(xinput list | grep "Name of Mouse" | awk '{print $6}' | sed -e 's/id=//') 'libinput Accel Speed' "{0.00 - 0.99}" &
xinput set-float-prop $id $sub $val | xinput set-float-prop 12 300 0.65
xinput set-prop $id 303 "$x1 $x2" | xinput set-prop 21 303 "0.1 1" 

# bumpy scroll
check your mouse

# Power button action
sudo vim /etc/systemd/logind.conf
Or just >> https://unix.stackexchange.com/questions/50748/how-can-i-set-power-button-on-computer-case-to-power-off-system-with-systemd

# amd driver
yay -S mesa lib32-mesa xf86-video-amdgpu amdvlk vulkan-radeon lib32-vulkan-radeon lib32-amdvlk libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau #foss

# Screen tearing (amd) 
read archwiki amdgpu for more info >> https://wiki.archlinux.org/title/AMDGPU#Tear_free_rendering

install driver first
vim /etc/X11/xorg.conf.d/20-amdgpu.conf
Section "Device"
     Identifier "AMD"
     Driver "amdgpu"
     Option "TearFree" "true"
EndSection
yay -S mesa lib32-mesa #have to reinstall everytime you config anything related to screen/gpu (+ using lightdm)

# Screen tearing (nvidia)
https://www.youtube.com/watch?v=oYWer86A20s (Neon Cipher)
https://www.youtube.com/watch?v=0Ux9bz_Tfw0

# grub
GRUB_DEFAULT=saved #change to saved
GRUB_CMDLINE_LINUX_DEFAULT="resume=UUID=34c1700a-792b-41bf-9ceb-c2bc955932de loglevel=3 audit=0 nomodset" #remove quiet

# grub **fucked up**
boot to live usb
sudo mount /dev/sdax1 /mnt
sudo mount /dev/sdax2 /mnt/boot/efi
sudo arch-chroot /mnt
sudo os-prober
sudo grub-mkconfig -o /boot/grub/grub.cfg

# ntfs drive mounted but read only
boot to windows -> continue to windows 1 time

# Change disc lable
https://askubuntu.com/questions/1103569/how-do-i-change-the-label-reported-by-lsblk

# Bluetooth (low quality / mono / org.bluez.Error.Busy / org.bluez.Error.NotReady)
rfkill block bluetooth;rfkill unblock bluetooth;sudo systemctl stop bluetooth.service;sudo systemctl start bluetooth.service
repeat connect and disconnect : remove device and re-pair
pipewire : pactl set-card-profile [card_number] a2dp-sink # https://wiki.archlinux.org/title/PipeWire
if not :
	- boot to diffrent os ex: fedora , linux mint  , windows
	- reset bios

# Font cn/jp/kr/th (font blank error download font https://wiki.archlinux.org/title/Fonts#Font_packages)
yay -S adobe-source-han-sans-cn-fonts adobe-source-han-serif-cn-fonts
yay -S adobe-source-han-sans-jp-fonts adobe-source-han-serif-jp-fonts
yay -S adobe-source-han-sans-kr-fonts adobe-source-han-serif-kr-fonts
yay -S fonts-tlwg #th and optional

# firefox 
about:config
ui.key.menuAccessKeyFocuses false
browser.cache.disk.enable false
full-screen-api.transition-duration.enter 0 0
full-screen-api.transition-duration.leave 0 0
identity.fxaccounts.enabled false
https://www.userchrome.org/how-create-userchrome-css.html
https://www.reddit.com/r/firefox/comments/78pjz1/how_do_i_remove_this_microphone_indicator/

# mpv - ff2mpv
$ git clone https://github.com/woodruffw/ff2mpv
$ cd ff2mpv
$ vim ff2mpv 
insert :
librewolf)
     linux_path="$HOME/.librewolf"
     LINUX_NMH_DIR="native-messaging-hosts"
     JSON_FILE="ff2mpv.json"
     ;;

# Youtube conner problem ublockorigin
setting -> My filters -> www.youtube.com##ytd-app:style(overflow: hidden !important;)

# pip error :
- remove pip
curl 'https://bootstrap.pypa.io/get-pip.py' -o get-pip.py
python3 /tmp/get-pip.py
pip install --user pipenv
pip3 install --user pipenv
yay -S python-pip

# icons
gtk-update-icon-cache -f -t ~/.icons/<theme_name>
gtk-update-icon-cache -f -t /usr/share/icons/<theme_name>

# Pass word gen 
https://www.fosslinux.com/45609/ways-generate-random-password-linux.htm
openssl rand -base64 14
gpg --gen-random --armor 1 14

# find keyboard code/XF86..
xev or sudo showkey -a,k,s

# default app
xdg-mime default sxiv.desktop image/jpg
xdg-mime default sxiv.desktop image/jpeg
xdg-mime default sxiv.desktop image/png
xdg-mime default mpv.desktop audio/mp3
xdg-mime default mpv.desktop audio/mp4
xdg-mime default mpv.desktop video/mp4
xdg-mime default mpv.desktop video/mkv
xdg-mime default pcmanfm.desktop inode/directory
xdg-mime default notepadqq.desktop text/plain 
xdg-mime default nvim.desktop text/plain
xdg-mime default libreoffice-calc.desktop text/csv

# Add create new file option
paste file in ~/Template

# Notepad++ replace
https://www.winhelponline.com/blog/notepad-plus-find-and-replace-text/

    Find what: -.*
    Replace with:  leave it empty
    Set the Search mode to Regular expression
    Uncheck matches newline
    Click Replace All

::Before::
accesschk.exe - from Sysinternals
AccessEnum.exe - from Sysinternals
AddrView.exe - from NirSoft
activehotkeys.exe - from another vendor
::After::
accesschk.exe 
AccessEnum.exe 
AddrView.exe 
activehotkeys.exe

# One drive
Sing in windows > turn off deaman ... in onedrive setting

# The sims 4 mod location
	$HOME/.steam/steam/steamapps/compatdata/1222670/pfx/drive_c/users/steamuser/Documents/Electronic Arts/The Sims 4
	or
	/media/d/Steam/steamapps/compatdata/1222670/pfx/drive_c/users/steamuser
	/media/x/Steam/steamapps/compatdata/1222670/pfx/drive_c/users/steamuser/Documents/Electronic Arts/The Sims 4/Mods
	cd /media/x/Steam/steamapps/compatdata/1222670/pfx/drive_c/users/steamuser;rm -r Documents;ln -s -d /media/c/Users/Acer/OneDrive/Documents Documents

# Firefox about:config
identity.fxaccounts.enabled = false
ui.key.menuAccessKeyFocuses = false
browser.cache.disk.enable = false
full-screen-api.transition-duration.enter 0 0	
full-screen-api.transition-duration.leave 0 0
toolkit.telemetry.enabled = false
browser.download.useToolkitUI = true

# Take 2k screen shot in 1080p X11
xrandr --output eDP --scale 2x2 --panning 3840x2160;sleep 10;xrandr --output eDP --scale 1x1 --panning 1920x1080

# Web scraping (https://unix.stackexchange.com/questions/181254/how-to-use-grep-and-cut-in-script-to-obtain-website-urls-from-an-html-file)
wget $(curl https:\\www.web.com |grep -Eo '<img src[^>]+>'|cut -d\" -f2)

# Wine
ln -s -d /mnt/d/linux_game/.wine .wine

# Battery level
https://askubuntu.com/questions/69556/how-do-i-check-the-batterys-status-via-the-terminal
upower -e
upower -i /org/freedesktop/UPower/devices/battery_BAT1

# Pacman slow
sudo reflector --latest 15 --age 2 --fastest 15 --protocol https --sort rate --save /etc/pacman.d/mirrorlist

# Arduino 
sudo chmod a+rw /dev/ttyUSB0

# Update ungoogle chroium appimage
wget "$(curl https://ungoogled-software.github.io/ungoogled-chromium-binaries/|curl "https://ungoogled-software.github.io/$(curl https://ungoogled-software.github.io/ungoogled-chromium-binaries/| grep -Eo "/ungoogled-chromium-binaries/releases/appimage/64bit/[^\"]+")"|grep -Eo "https://github.com/clickot/ungoogled-chromium-binaries/releases/download/[^\"]+")";yes|mv ungoogled-chromium_112.0.5615.121-1.1.AppImage ~/.appimage/ungoogled-chromium.AppImage;chmod +x ~/.appimage/ungoogled-chromium.AppImage

# OpenDirectory
Open port 8000 or else in router
cd folder/
python -m http.server port #default 8000
python -m http.server 6958
find own public ip
publicip:port

# Syncthing
change default folder
https://docs.syncthing.net/v1.23.3/users/config.html?highlight=path#config-option-folder.path

# pyenv
pyenv install 3.1x.xx 
pyenv local 3.1x.xx # In that directory and subdirectory
pyenv shell <version> # In that shell
pyenv gobal <version> # Everywhere

# git change remote type https to ssh:
git remote set-url origin git@github.com:user/repo.git

# merge pdf cli
pdfunite *.pdf out.pdf

#troubleshoot slow bio boot
0) Swap windows boot to first -> reboot -> boot menu -> arch
0.1) Fastboot on
0.2) boot to live usb ejcect while core boot
0.3) check fstab swap
1) reset bios (slow boot to grub or boot entry)
	+ fix slow bios boot / long bios boot
	+ fix bluetooth in linux
2) reinstall linux linux-headers grub --overwrite
3) vim etc/default/grub  -> remove nomodeset
4) yay -S dkms -> sudo dkms autoinstall

# AUR reinstall all Dependencies
yay -S $(pacman -Qi spotdl | grep "Depends On" | cut -d: -f2)

# PTP Camera Storage
https://wiki.archlinux.org/title/GPhoto#Example_usage_with_GVfs
yay -S gphoto2 gvfs-gphoto2
