# simple ssh setup

[video](https://www.youtube.com/watch?v=8X4u9sca3Io)
make your local machine can acess to github.

**1. make config for ssh:**

```
$ mkdir -p ~/.ssh | touch ~/.ssh/config | echo "Host *\nAddKeysToAgent yes\nIdentityFile ~/.ssh/id_ed25519 \n #UseKeychain yes # Passphrase" > ~/.ssh/config

```

**2. generate ssh key:**

```
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```
just press enter

**3. set ssh-agent:**

start ssh-agent
```
$ eval "$(ssh-agent -s)"
```

add ssh-key 
```
$ ssh-add ~/.ssh/id_ed25519
```

**4. add ssh to github:**

copy public key

```
$ cat ~/.ssh/id_ed25519.pub | xclip -selection clipboard
```
add key to [this.](https://github.com/settings/ssh/new) after that

```
$ yes|ssh -T git@github.com
```

**Next time if you clone something change it to ssh, if already exist repo is https change remote to ssh**
