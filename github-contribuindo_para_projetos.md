# GitHub - Como Contribuir Para Um Projeto

### Clonar o repositório remoto

```sh
git clone git@github.com:murilooon/UDESC.git
```

### Criar uma branch e entrar nela

```sh
git branch nome-branch
git checkout nome-branch
```
Obs: Colocar um nome que faz sentido na branch

Obs2: Toda modificação feita aqui não complicará o código principal

### Adicionar os arquivos, commitar e mandar para o repositório remoto na branch indicada

```sh
git add nome-arquivo
git commit -m "alguma-coisa"
git push origin nome-branch
```

### Voltar para a master e atualizar com o repositório remoto

```sh
git checkout master
git pull origin master
```

Obs: sempre voltar pra master e atualizar antes de criar uma nova branch

### Excluir uma branch

```sh
git branch -D nome-branch
```

Obs: depois de criar um PR e ele for juntado ao código principal, excluir a branch

## Abrindo Pull Request (PR)

Um PR nada mais é do que um pedido para inserir uma modificação no repositório principal, incluindo apenas as linhas dos arquivos alterados, não todo o projeto.

Quando você cria uma branch, adiciona os arquivos modificados, faz um commit, você tem todas as alterações apenas salvasna sua maquina local. Porém, ao fazer um push você envia para o projeto remoto tudo o que foi _commitado_ (para o GitHub).

Agora ao abrir o link do projeto no GitHub va aparecer a branch nova que você criou e um pedido para abrir um pull request. Você será redirecionado para um nova tela. Nela poderá colocar um título para o PR, de preferência uma frase curta, um texto explicando rapidamente o que foi modificado e no canto direito pedir para pessoas revisarem seu PR.

Depois de as pessoas revisarem e aprovarem o PR, você pode dar _merge_ do código para a master, isso quer dizer, enviar suas modificações para o códigp principal.
