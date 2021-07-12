# Setup Machine

1. Install VSCode: `sudo apt install snapd` them `sudo snap install code --classic`
2. Create config.sh file and add the code below
3. Run `chmod +x config.sh`
4. Run `./config.sh`
5. Add the `~/.zshrc` example below to your zsh file

## config.sh
```
# Regolith
sudo add-apt-repository ppa:regolith-linux/release
sudo apt install regolith-desktop-mobile

# Terminator
sudo apt install terminator

# Zsh
sudo apt install zsh
chsh -s /bin/zsh

# Brave
sudo apt install apt-transport-https curl gnupg
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser

# Git
sudo apt-get install git

# oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Powerline Fonts
sudo apt-get install fonts-powerline

# SpaceShip Prompt
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"

# Slack
sudo apt install snapd
sudo snap install slack --classic

# asdf
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.8.1
. $HOME/.asdf/asdf.sh

# asdf-node
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring'
asdf install nodejs 14.13.1
asdf global nodejs 14.13.1

# asdf-ruby
sudo apt-get install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev
asdf plugin add ruby
asdf install ruby 2.7.3

# yarn
npm install --global yarn

# Github
ssh-keygen -t ed25519 -C "murilooon@gmail.com"

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519

git config --global user.name "murilooon"
git config --global user.email murilooon@gmail.com

echo "Add the response below to your github SSH config"
cat ~/.ssh/id_ed25519.pub

## Docker
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

## docker-compose
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## ~/.zshrc
```
export ZSH="/home/murilo/.oh-my-zsh"

ZSH_THEME="spaceship"

plugins=(git)

source $ZSH/oh-my-zsh.sh

alias zshconfig="code ~/.zshrc"
alias ohmyzsh="code ~/.oh-my-zsh"

#asdf
. $HOME/.asdf/asdf.sh
fpath=(${ASDF_DIR}/completions $fpath)
autoload -Uz compinit
compinit
```
