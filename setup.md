# Setup Machine

## Install Regolith
```
sudo add-apt-repository ppa:regolith-linux/release
sudo apt install regolith-desktop-mobile
```

## Install Terminator
`sudo apt install terminator`

## Install Zsh
```
sudo apt install zsh
chsh -s /bin/zsh
```

## Install Powerline Fonts
`sudo apt-get install fonts-powerline`

## Install Spaceship Prompt
`npm install -g spaceship-prompt`

## Install and config git/github
```
sudo apt-get install git

ssh-keygen -t ed25519 -C "murilooon@gmail.com"

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

sudo apt-get install xclip

xclip -selection clipboard < ~/.ssh/id_ed25519.pub

git config --global user.name "murilooon"
git config --global user.email murilooon@gmail.com
```

# Additional but important apps

## Install Postman
```
sudo apt install snapd
sudo snap install postman
```

## Install Brave
```
sudo apt install apt-transport-https curl gnupg

curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -

echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser
```

## Install Slack
```
sudo apt install snapd
sudo snap install slack --classic
```

## Install VSCode
```
sudo apt install snapd
sudo snap install code --classic
```

## Install Nvm
```
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

code ~/.zshrc

## print in the end of ./zshrc file
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

## Install Yarn
`npm install --global yarn`

## Install asdf
```
https://asdf-vm.com/#/core-manage-asdf

-- Node
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring'
asdf global nodejs 15.11.0
```

