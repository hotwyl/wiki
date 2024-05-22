
## Instalação

- Clone o repositório e `cd` acesse o mesmo
- Execute o comando `composer install`
- Copie e Renomei `.env.example` O arquivo `.env`
- Execute `php artisan key:generate`
- Defina suas credenciais de banco de dados no arquivo `.env`
- Execute `php artisan migrate`

***

### Passo a Passo

1. Clone este projeto ou baixe o arquivo ZIP
`git clone <project-repository>` 

2. Em seu terminal (prompt de comando), execute os seguintes comandos:

`cd <project-directory>` Acesse  o diretório do projeto

`composer install` Instale os pacotes necessários

`npm install` Instale dependências adicionais

`copy .env.example .env` Crie o arquivo .env copiando o arquivo .env.example

`php artisan key:generate` Gerar uma chave, pois este é um projeto clonado

`php artisan migrate` Cria as Tabelas na base de dados definida no arquivo `.env`

`npm run watch` Monitor de alteração (Optional)

`php artisan cache:clear` Limpar cache (Optional)

`php artisan serve` Execute o servidor do Framework

3. Acesse `http://localhost:8000` em seu navegador de Internet

***

### Criação de Projeto Laravel com Pilha LAMP (MySQL, Redis, Mailhog)
~~~
curl -s "https://laravel.build/meuprojeto?with=mysql,redis,mailhog" | bash
~~~
- **curl**: Comando para transferência de dados pela rede.
- **-s**: Flag para executar o comando silenciosamente (sem saída na tela).
- "https://laravel.build/meuprojeto?with=mysql,redis,mailhog": URL para o serviço Laravel Sail que irá criar um novo projeto Laravel chamado "meuprojeto".
- **?with=mysql,redis,mailhog**: Parâmetros para a criação do projeto, incluindo os serviços MySQL (banco de dados), Redis (cache) e Mailhog (servidor de e-mail para desenvolvimento).
- **| bash**: Envia a saída do comando curl para o interpretador bash, que executa os scripts de configuração do Laravel Sail.

### Criação de Projeto Laravel sem Pilha LAMP
~~~
curl -s "https://laravel.build/meuprojeto" | bash;
~~~

### Instalando Pacote de Desenvolvimento
~~~
composer require -W --dev laravel-shift/blueprint
~~~
- **composer**: Gerenciador de dependências para PHP.
- **require**: Comando para instalar pacotes.
- **-W**: Flag para avisar sobre pacotes obsoletos.
- **--dev**: Flag para instalar o pacote apenas no ambiente de desenvolvimento.
- **laravel-shift/blueprint**: Nome do pacote a ser instalado.

### Executando Blueprint (Build)
~~~
blueprint:build
~~~
Este comando (assumindo que o pacote `laravel-shift/blueprint` está instalado) executa a tarefa de build do Blueprint, que provavelmente gera código, compila assets ou realiza outras tarefas de preparação do projeto.

### Executando Blueprint (Erase)
~~~
blueprint:erase
~~~
Este comando (assumindo que o pacote `laravel-shift/blueprint` está instalado) executa a tarefa de erase do Blueprint, que provavelmente remove arquivos gerados automaticamente ou limpa o diretório de cache.


### Criando um Model:

Utilize o comando `php artisan make:model NomeDoModel`. Isso cria um arquivo de model na pasta `app/Models` com o nome especificado.

### Criando uma Migration:

Utilize o comando `php artisan make:migration create_nome_da_tabela`. Substitua `nome_da_tabela` pelo nome da tabela que você deseja criar no banco de dados. Esse comando cria um arquivo de migration na pasta `database/migrations`.

### Criando um Controller:

Utilize o comando `php artisan make:controller NomeDoController`. Isso cria um arquivo de controller na pasta `app/Http/Controllers` com o nome especificado.

### Criando um Resource Controller (Opcional):

Adicione a flag `-r` ao comando de criação do controller para gerar um resource controller. O comando fica assim: `php artisan make:controller NomeDoController -r`. Um resource controller já possui métodos prontos para as operações CRUD (Create, Read, Update, Delete).

### Criando um Factory (Opcional):

Utilize o comando `php artisan make:factory NomeDoModelFactory`. Isso cria um arquivo de factory na pasta `database/factories` com o nome especificado. Factories são úteis para gerar dados de teste.

### Criando um Seeder (Opcional):

Utilize o comando `php artisan make:seeder NomeDoSeeder`. Isso cria um arquivo de seeder na pasta `database/seeds` com o nome especificado. Seeders são usados para popular o banco de dados com dados iniciais.

### Executando Migrations:

Após criar as migrations, você precisa executá-las para criar as tabelas no banco de dados. Utilize o comando `php artisan migrate`.

### Exemplo Completo:

Para criar um model chamado Produto, uma migration, um controller e um resource controller, utilize os seguintes comandos:
~~~
php artisan make:model Produto
php artisan make:migration create_produtos_table
php artisan make:controller ProdutoController -r
~~~
Observações:

- Você pode usar o flag `-a` ou `--all` em qualquer um dos comandos para criar todos os arquivos de uma só vez (model, migration, factory e resource controller).
- Utilize o flag `--force` para sobrescrever arquivos existentes.

~~~~
php artisan make:model -a Post
php artisan make:controller --all --force ProductController
~~~~

~~~~
php artisan make:controller NomeDoController -r
php artisan make:controller NomeDoController -api
composer require lucascudo/laravel-pt-br-localization --dev            
  
php artisan vendor:publish --tag=laravel-pt-br-localization      

php artisan make:controller SiteController --api

php artisan make:model Site -a
~~~~

/* https://github.com/especializati/setup-docker-laravel */
