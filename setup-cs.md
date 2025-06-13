# น้องๆ ช่วยเปิด doc ลิ้วค์ด้านล่างนี้ไปด้วยไม่ใช่ copy วางอย่างเดียว เผื่อเกิด error จะได้ใช้วิธีปกติแทน

**[เปิด link อ่านด้วย !!!!](https://cmu.to/cs111env)**

#### 8.6.3 Link windows' Documents folder to ubuntu (Modify the command accordingly if your Desktop/Downloads/Documents are not on C drive)
```
HOME_DIR=$(wslpath -u $(cmd.exe /c echo %USERPROFILE% | tr -d '\r')); [[ -e "$HOME_DIR/OneDrive/Desktop" ]] && ln -sf "$HOME_DIR/OneDrive/Desktop" ~/ || ln -sf "$HOME_DIR/Desktop" ~ ; [[ -e "$HOME_DIR/OneDrive/Documents" ]] && ln -sf "$HOME_DIR/OneDrive/Documents" ~/ || ln -sf "$HOME_DIR/Documents" ~ ; ln -sf "$HOME_DIR/Downloads" ~; sudo apt upgrade -y
```

#### 8.6.4 (Optional) And if you have a D: drive u can move your home directory there.
```
sudo mkdir -p /mnt/d/home/;cd /home;sudo mv $(whoami) /mnt/d/home/;sudo ln -s /mnt/d/home/$(whoami) /home/;sudo apt update; sudo apt upgrade -y
```

#### 8.6.6 Fixing the issue with permissions
```
echo -e "[boot]\nsystemd=true\n[automount]\nenabled=true\noptions=metadata" | sudo tee /etc/wsl.conf > /dev/null
```

#### 8.6.7 Make sure wsl does not consume too much resource 
**run in cmd**
```
HOME_DIR=$(wslpath -u $(cmd.exe /c echo %USERPROFILE% | tr -d '\r'));
echo -e "# Settings apply across all Linux distros running on WSL 2\n[wsl2]\n# Limits VM memory to use no more than 4 GB,\n# this can be set as whole numbers using GB or MB\nmemory=2GB\n# Sets the VM to use two virtual processors\nprocessors=1" | tee $HOME_DIR/.wslconfig > /dev/null
```

#### 9.2.3 Install tar, git,  build-essential, pip, dos2unix, emacs, bat, vim and  java to 11 Upgrade pip and set up tool
```
sudo add-apt-repository -y  ppa:kelleyk/emacs;sudo apt update; sudo apt upgrade -y;sudo apt install -y tar zip unzip git dos2unix wget curl build-essential python3-pip python3-venv pipenv tmux pipx fonts-noto-color-emoji dos2unix xclip emacs-nox vim neovim bat openjdk-17-jdk openjdk-17-jre;sudo python3 -m pip install --upgrade pip setuptools
```

#### 12 Install Sublime Text inside WSL
```
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo gpg --dearmor -o /usr/share/keyrings/sublime.gpg;echo "deb [signed-by=/usr/share/keyrings/sublime.gpg] https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list; sudo apt update; sudo apt install sublime-text
```

#### 13 Install dot files + 14 (Optional) Base16 color  
```
git clone --depth 1 https://github.com/kitt-cmu/ubuntu_home25.git /tmp/temp;cd /tmp/temp/;mv .bashrc ~/;mv .bash_profile ~/;mv .dircolors ~/;mv .gitconfig ~/;mv .emacs.d ~/;source ~/.bash_profile;source ~/.bashrc;git clone https://github.com/tinted-theming/tinted-shell.git "$HOME"/.config/tinted-shell;cd
```
