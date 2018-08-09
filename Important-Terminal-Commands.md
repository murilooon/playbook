# Terminal Commands

## GitHub

### Update files on your own GitHub

1. git add * ou git add nome-arquivo
2. git commit -m "comentário da alteração"
3. git push origin master

### Update local files updated on GitHub

1. git pull

### Create New Repository

* Create directly on GitHub

or

* git clone repository-link

### Make a Branch e Pull Request

1. git branch nova-branch
2. git checkout nova-branch

or

1. git checkout -b nova-branch (sai de uma branch, cria outra e entra nela)

3. git add *
4. git commit -m "alterei o arquivo x"
5. git push --set-upstream origin nova-branch
6. Ir no branch criado e criar o pull request

### Creating a feature branch and incorporating a finished feature on develop

1. git checkout -b myfeature develop
	- Switched to a new branch "myfeature"
2. git checkout develop
	- Switched to branch 'develop'
3. git merge --no-ff myfeature
	- Updating ea1b82a..05e9557 (Summary of changes)
4. git branch -d myfeature
	- Deleted branch myfeature (was 05e9557)
5. git push origin develop

### Clone Private Repository

* git clone git@github.com:magrathealabs/minions.git

### Change Your Git Default Editor to Sublime

* git config --global core.editor "subl3 -n -w"

### Skipping the Staging Area

Using -a option to the git commit command, you don't need to git add, it will automatically add all files that are tracked.

* git commit -a -m "text"

### Links

* [Git Commands](https://gist.github.com/leocomelli/2545add34e4fec21ec16)
* [Guia Prático](http://rogerdudler.github.io/git-guide/index.pt_BR.html)
* [Anaconda Config](https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-16-04)

## Install with pip in Windows

* py -m pip install module-name

## Install with conda in Ubuntu

* conda install module-name

## Add on PATH in Ubuntu

1. sudo nano /etc/profile
2. export PATH=$PATH:/home/murilo/anaconda3/bin on end of file
3. Ctrl+O to save
4. Ctrl+X to exit
5. Reinicialize the system

* "echo $PATH" to see all the PATH's 

## Python Important Stuffs

### Pipenv documentaton

* https://github.com/pypa/pipenv

### Command to active the virtual environment for tensorflow

	source ~/tensorflow/venv/bin/activate