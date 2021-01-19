# Setup Machine

## Install regolith
```
sudo add-apt-repository ppa:regolith-linux/release
sudo apt install regolith-desktop-mobile
```

## Install terminator
`sudo apt install terminator`

## Install Zsh
`sudo apt install zsh`

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
`sudo snap install postman`
