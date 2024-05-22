passo a passo para configurar ssh

1)
~~~
ssh-keygen -t rsa -b 4096 -C “seu@email.com“
~~~
2)
~~~
eval $(ssh-agent -s)
ssh-add /root/.ssh/id_rsa
~~~
3)￼
~~~
cat  ~/.ssh/id_rsa.pub
~~~
Copiar chave e colocar no GIT



# comandos uteis Git

- acessar via terminal acessar vm com as credenciais:
~~~
ssh {usuario vm}@{ip vm}
~~~

~~~
{senha acesso}
~~~

- definir acesso de navegação como root:
~~~
sudo su
~~~

- acessar diretorio do projeto:
~~~
cd /var/www/trunk
~~~

- acessar branch Master: 
~~~
git checkout master
~~~

- atualizar branch local apartir da branch remota
~~~
git fetch
~~~
~~~
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

- para rodar acessos a endpoints da vm alterar o arquivo HTACCESS
~~~
->.HTACCESS app_dev -> app
~~~

- ao subir para produção o mesmo deve estar:
~~~
->.HTACCESS app -> app
~~~

- acessar uma branch local:
~~~
git checkout branch
~~~

- verificar as branch's local:
~~~
git branch 
~~~

- adicionar todos os novos arquivos para commit
~~~
git add .
~~~

- adicionar  arquivos especificos para commit
~~~
git add <path>
~~~

- comitar alterações
~~~
git commit -a -m ""
~~~

- enviar alterações para branch remota
~~~
git push origin <branch>
~~~

- listar alterações de diretorios e branchs
~~~
git fetch
~~~

- atualizar branch:
~~~
git pull origin develop
~~~

- mesclar branchs:
~~~
git merge <branch origem> <branch destino> 
~~~

- subir atualizações para branch remota:
~~~ 
git push origin <branch>  
~~~

- acompanhar status pipeline 

---
## trabalhar com projetos do git

- logar sistema via terminal com credencials e definir acesso como root
~~~
ssh {usuario vm}@{ip vm}
~~~
~~~
{senha acesso}
~~~
~~~
sudo su
~~~

- navegar até pasta do projeto
~~~
cd /var/www/trunk
~~~

- acessar branch `master` e atualizar branch
~~~
git checkout master
~~~
~~~
git fetch
~~~
~~~
git pull origin master
~~~

- chacar as branchs locais
~~~
git branch 
~~~

- se houver necessidade de excluir alguma branch:
~~~
git branch -D <branch>
~~~

- criar nova branch. obs. apartir (estando logado) na master
~~~
git checkout -b <branch>
~~~

- dar permissões de leitura e escrita
~~~
chmod o+w * -R
~~~

- se precisar testar na vm (api), mudar arquivo HTACCESS (não esquecer de voltar para original ao subir para devlop e produção)
~~~
.HTACCESS app_dev -> app
~~~

---
## subir projetos para o git

- adicionar todos os novos arquivos para commit
~~~
git add .
~~~

- adicionar  arquivos especificos para commit
~~~
git add <path>
~~~

- comitar alterações
~~~
git commit -a -m ""
~~~

- enviar alterações para branch remota
~~~
git push origin <branch>
~~~

- acessar branch develop
~~~
git checkout develop
~~~

- listar alterações de diretorios e branchs
~~~
git fetch
~~~

- atualizar branch:
~~~
git pull origin develop
~~~

- mesclar branchs:
~~~
git merge <branch origem> develop
~~~

- subir atualizações para branch remota:
~~~ 
git push origin develop
~~~

- acompanhar status pipeline 

---

# caso da branch `develop` desatualizada a algum tempo

- acessar branch `master`
~~~
git checkout master
~~~

- listar alterações remotas em relação diretorio local
~~~
git fetch
~~~

- atualiza atualiza branch `master`:
~~~
git pull origin master
~~~

- se houver necessidade de excluir todas as branch's local
~~~
git branch -D <branch>
~~~


git checkout master

git fetch

git pull origin master

* git branch 

git branch -D <branch>

git checkout -b <branch>
             
chmod o+w * -R

* git checkout branch

* git branch 

* git commit -a -m ""

* git push origin <branch>

* git checkout develop

* git fetch

* git pull origin develop

* git merge <branch> develop

* git push origin develop 


- acessa branch `develop` remota ***( agora esta estará atualizada localmente)***
~~~
git pull origin develop
~~~

