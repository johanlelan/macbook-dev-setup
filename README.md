# macbook-dev-setup

Collection of useful commands to setup you macbook pro

## Git

```sh
# Install Git
brew install git
```

```sh
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

## iTerm2

```sh
# Install iterm2 instead of terminal.app
brew install iterm2 --cask
```

## Oh-my-Zsh

```sh
# install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
# add powerlevel10k theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
# Re-run your term to configure the terminal prompt
...

```

## Homebrew

### Install homebrew commands

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Disable auto update brew

```sh
# add into your .bashrc or .zshrc these variables

# disable auto update brew
export HOMEBREW_NO_AUTO_UPDATE=TRUE
export HOMEBREW_NO_INSTALL_CLEANUP=TRUE
```

## Node.js

Install a NodeJS manager. You have `fnm` or `nvm`.

```sh
brew install nvm
nvm ls-remote
nvm install 14
nvm ls
nvm use 14
```

## Docker

Sources
- [Replace Docker Desktop by minikube](https://medium.com/rahasak/replace-docker-desktop-with-minikube-and-hyperkit-on-macos-783ce4fb39e3)
- [Exposing ports](https://itnext.io/goodbye-docker-desktop-hello-minikube-3649f2a1c469)

### Clean old Docker Desktop installation [Optional]

```sh
sudo rm -Rf /Applications/Docker.app
sudo rm -f /usr/local/bin/docker
sudo rm -f /usr/local/bin/docker-machine
sudo rm -f /usr/local/bin/docker-compose
sudo rm -f /usr/local/bin/docker-credential-desktop
sudo rm -f /usr/local/bin/docker-credential-ecr-login
sudo rm -f /usr/local/bin/docker-credential-osxkeychain
sudo rm -Rf ~/.docker
sudo rm -Rf ~/Library/Containers/com.docker.docker
sudo rm -Rf ~/Library/Application\ Support/Docker\ Desktop
sudo rm -Rf ~/Library/Group\ Containers/group.com.docker
sudo rm -f ~/Library/HTTPStorages/com.docker.docker.binarycookies
sudo rm -f /Library/PrivilegedHelperTools/com.docker.vmnetd
sudo rm -f /Library/LaunchDaemons/com.docker.vmnetd.plist
sudo rm -Rf ~/Library/Logs/Docker\ Desktop
sudo rm -Rf /usr/local/lib/docker
sudo rm -f ~/Library/Preferences/com.docker.docker.plist
sudo rm -Rf ~/Library/Saved\ Application\ State/com.electron.docker-frontend.savedState
sudo rm -f ~/Library/Preferences/com.electron.docker-frontend.plist
```

### Install Minikube

```sh
# intall hyperkit
brew install hyperkit
# install minikube
brew install minikube
# install docker cli
brew install docker
# install kubectl
brew install kubectl
# install docker-compose
brew install docker-compose
```

### Start Minikube

```sh
# start minikube
minikube start

# if error occues when starting the minikube use bleow command to clean the minikube
# and then restart 
minikube delete --all --purge

# start minikube again
minikube start

# this will start single node kubernets cluster on minikube vm
# docker deamon run inside the minikube vm with k8s cluster
kubectl get nodes

NAME       STATUS   ROLES                  AGE     VERSION
minikube   Ready    control-plane,master   3h45m   v1.22.2
```

### Configure Minikube

```sh
# add this entry to ~/.bashrc or ~/.zshrc to work in all terminal sessions
eval $(minikube docker-env)

# find minikube vm ip address, this ip use as the docker host ip
minikube ip 
>> 192.168.64.3

# add minikube ip to /etc/hosts if want
echo "`minikube ip` docker.local" | sudo tee -a /etc/hosts > /dev/null

# minikube configurations will be stored in the following config file 
~/.minikube/machines/minikube/config.json
```

### Espose Services outside Minikube

```sh
# add ingress controller to open ports
minikube addons enable ingress
# display the current cluster ip
minikube ip
192.168.64.12
# try to query the cluster
curl http://192.168.64.12

<html><head><title>404 Not Found</title></head><body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx</center></body></html>
```
#### Want DNS lookup into cluster

```sh
minikube addons enable ingress-dns
```

### Login to a remote registry

```sh
brew install docker-credential-helper
# log to your register
docker login
```

## Visual Studio Code

Go to the [Download page](https://code.visualstudio.com/docs?dv=osx)

```sh
cat << EOF >> ~/.zprofile
# Add Visual Studio Code (code)
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
EOF
```

### Extensions

- Better Comments
- codeMetrics
- Community Material Theme
- DotENV
- ESLint
- Fluent Icons
- French Language Pack for Visual Studio Code
- Git History
- GitHub Theme
- GitLens
- Import Cost
- Jest
- markdownlint
- Materiel Icon Theme
- Materiel Theme
- Materiel Theme Icons
- Node.js Extension Pack
- npm
- npm intellisense
- Prettier - Code formatter
- REST Client

## IntelliJ IDEA

For JAVA dev, the great `IntelliJ IDEA` is the best event if `VS Code` is useful.

Download the latest version [here](https://www.jetbrains.com/idea/download/#section=mac).

## HTTP Client

If you use `VSCode` then you know the [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client).
You just need to create a file with `.http` or `.rest` extension. VSCode will query you HTTP server and display the response.

### Desktop app for HTTP Request

Insomnia or Paw are two great HTTP clients. I prefer [Insomnia](https://insomnia.rest/download) for its free of use.

## Windows manager

There are two well-known `MACOS` window manager : `rectangleapp` or `spectacle`.

Let's install `Rectangle` [app](https://rectangleapp.com/)

## Light Web browser

I often use [mint](https://minbrowser.org/) to share websites throught instant Messaging. It is compact, light and efficient.

## iStats Menu

The Mac system monitor into your menubar. I love [iStats Menus](https://bjango.com/mac/istatmenus/)

```sh
brew install --cask istat-menus
```

## TODOs

- Office 365 apps (Excel, Outlook, Powerpoint, Remote Desktop, Teams, Word)
- Decompressor
- Discord
- Draw.io
- Google chrome
- Garmin express
- MacDown
- RDM (for redis)
- Robo 3T
- The unarchiver
- Tunnelblick
- VLC
- WeTranfer
- Zwift
