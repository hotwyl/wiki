Passo a passo para configurar ssh:
~~~
ssh-keygen -t rsa -b 4096 -C “seu@email.com“
eval $(ssh-agent -s)
ssh-add /root/.ssh/id_rsa
cat  ~/.ssh/id_rsa.pub
~~~
Copiar chave e colocar no GIT
****
Quick setup — if you’ve done this kind of thing before

- SSH:`git@github.com:{usuario}/{projeto}.git`
- HTTPS: `https://github.com/{usuario}/{projeto}.git`

Comece criando um novo arquivo ou carregando um arquivo existente. Recomendamos que cada repositório inclua um `README`, `LICENSE` e `.gitignore`.

…ou crie um novo repositório na linha de comando

```
echo "# {projeto}" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/{usuario}/{projeto}.git
git push -u origin master
```
…ou envie um repositório existente a partir da linha de comando
~~~
git remote add origin https://github.com/{usuario}/{projeto}.git
git branch -M master
git push -u origin master
~~~


****

# comandos uteis Git

- definir acesso de navegação como root:
~~~
sudo su
~~~

- acessar diretorio do projeto:
~~~
cd /var/www/trunk
~~~

- acessar branch: 
~~~
git checkout <branch>
~~~

- listar alterações de diretorios e branchs
~~~
git fetch
~~~
- atualizar branch local apartir da branch remota
~~~
git pull
git pull origin master
~~~

- deletar branch local: 
~~~
git branch -D <branch>
~~~

- criar nova branch local:
~~~
git checkout -b <branch>
~~~

- dar permissões de leitura e escrita ao diretorio e sub diretórios
~~~
chmod o+w * -R
~~~

- acessar uma branch:
~~~
git checkout <branch>
~~~

- verificar as branch's local:
~~~
git branch 
~~~

- adicionar todos os novos arquivos para commit
~~~
git add .
git add <path/file>
~~~

- comitar alterações
~~~
git commit -m ""
git commit -a -m ""
~~~

- enviar alterações para branch remota
~~~
git push
git push origin <branch>
~~~

- mesclar branchs:
~~~
git merge <branch origem> <branch destino> 
~~~


