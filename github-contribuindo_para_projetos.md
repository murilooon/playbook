# GitHub - Como Contribuir Para Um Projeto

### Clonar o reposit�rio remoto

```sh
git clone git@github.com:murilooon/UDESC.git
```

### Criar uma branch e entrar nela

```sh
git branch nome-branch
git checkout nome-branch
```
Obs: Colocar um nome que faz sentido na branch

Obs2: Toda modifica��o feita aqui n�o complicar� o c�digo principal

### Adicionar os arquivos, commitar e mandar para o reposit�rio remoto na branch indicada

```sh
git add nome-arquivo
git commit -m "alguma-coisa"
git push origin nome-branch
```

### Voltar para a master e atualizar com o reposit�rio remoto

```sh
git checkout master
git pull origin master
```

Obs: sempre voltar pra master e atualizar antes de criar uma nova branch

### Excluir uma branch

```sh
git branch -D nome-branch
```

Obs: depois de criar um PR e ele for juntado ao c�digo principal, excluir a branch