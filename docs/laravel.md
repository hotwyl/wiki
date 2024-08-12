
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

`php artisan jwt:secret` Gerar uma chave do JWT, pois este é um projeto clonado

3. Parametrize as configurações do projeto no arquivo `.env`

4. Crie seu Banco de dados com os parametros definidos no arquivo .`.env`
   
`php artisan migrate` Cria as Tabelas na base de dados

`php artisan migrate:fresh --seed` Apagar tabelas, recriar as tabelas, popular tabelas com dados aleatórios (Optional)

`npm run watch` Monitor de alteração (Optional)

`php artisan cache:clear` Limpar cache (Optional)

`php artisan serve` Execute o servidor do Framework

5. Acesse `http://localhost:8000` em seu navegador de Internet

***

## Criação de Projeto Laravel com Pilha LAMP (MySQL, Redis, Mailhog)
~~~
curl -s "https://laravel.build/meuprojeto?with=mysql,redis,mailhog" | bash
~~~
- **curl**: Comando para transferência de dados pela rede.
- **-s**: Flag para executar o comando silenciosamente (sem saída na tela).
- "https://laravel.build/meuprojeto?with=mysql,redis,mailhog": URL para o serviço Laravel Sail que irá criar um novo projeto Laravel chamado "meuprojeto".
- **?with=mysql,redis,mailhog**: Parâmetros para a criação do projeto, incluindo os serviços MySQL (banco de dados), Redis (cache) e Mailhog (servidor de e-mail para desenvolvimento).
- **| bash**: Envia a saída do comando curl para o interpretador bash, que executa os scripts de configuração do Laravel Sail.

## Criação de Projeto Laravel SAIL
~~~
curl -s "https://laravel.build/meuprojeto" | bash;
~~~

## O comando `./vendor/bin/sail up -d` no Laravel

O comando `./vendor/bin/sail up -d` é utilizado para iniciar o ambiente de desenvolvimento Laravel usando o Laravel Sail, uma ferramenta de desenvolvimento que fornece um ambiente local baseado em Docker para aplicações Laravel. Vamos analisar o comando em detalhes:

- `./vendor/bin/sail`: Esta parte do comando aponta para o arquivo executável do Sail, que geralmente está localizado no diretório vendor/bin do seu projeto Laravel.

- `up`: Esta é a ação principal que você deseja realizar, que é iniciar os containers Docker para sua aplicação Laravel.

- `-d`: Esta flag significa "desanexado" e instrui o Sail a executar os containers em segundo plano. Isso significa que o comando retornará imediatamente e você não verá nenhuma saída dos containers.

***

### Instalando Pacote de Desenvolvimento (blueprint)
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

***

### Criando um Model:

Utilize o comando `php artisan make:model NomeDoModel`. Isso cria um arquivo de model na pasta `app/Models` com o nome especificado.

### Criando uma Migration:

Utilize o comando `php artisan make:migration create_nome_da_tabela`. Substitua `nome_da_tabela` pelo nome da tabela que você deseja criar no banco de dados. Esse comando cria um arquivo de migration na pasta `database/migrations`.
~~~
php artisan make:migration create_produtos_table
~~~

### Criando um Controller:

Utilize o comando `php artisan make:controller NomeDoController`. Isso cria um arquivo de controller na pasta `app/Http/Controllers` com o nome especificado.

~~~
php artisan make:controller NomeDoController
php artisan make:controller NomeDoController --all
php artisan make:controller NomeDoController --api
php artisan make:controller NomeDoController --resource
~~~

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
php artisan make:model Site -a
php artisan make:model -a Post
~~~
Observações:

- Você pode usar o flag `-a` ou `--all` em qualquer um dos comandos para criar todos os arquivos de uma só vez (model, migration, factory e resource controller).
- Utilize o flag `--force` para sobrescrever arquivos existentes.

~~~~
php artisan make:controller --all --force ProductController
php artisan make:controller ProdutoController -r
~~~~

~~~~
php artisan optimize
php artisan optimize:clear
php artisan route:cache
php artisan route:clear
~~~~
*****
## Módulo de linguagem pt-BR (português brasileiro) para Laravel

https://github.com/lucascudo/laravel-pt-BR-localization

### Instalação
Scaffold do diretório lang
~~~~
php artisan lang:publish
~~~~
Instale o pacote
~~~~
composer require lucascudo/laravel-pt-br-localization --dev
~~~~
Publique as traduções
~~~~
php artisan vendor:publish --tag=laravel-pt-br-localization
~~~~
Configure o Framework para utilizar 'pt_BR' como linguagem padrão
~~~~
// Altere Linha 85 do arquivo config/app.php para:
'locale' => 'pt_BR'
~~~~

****
## Integração Laravel-AdminLTE
https://github.com/jeroennoten/Laravel-AdminLTE

### Requerendo o pacote
Na pasta raiz do seu projeto Laravel, solicite o pacote usando a ferramenta:
~~~~
composer require jeroennoten/laravel-adminlte
~~~~

### Instalando os recursos do pacote
Instale os recursos do pacote necessários usando o seguinte comando:
~~~~
php artisan adminlte:install
~~~~

Este comando irá instalar:

- Os arquivos de distribuição subjacentes do AdminLTE e suas dependências (Bootstrap, jQuery, etc.) na pasta `public/vendor`.
- A configuração do pacote no arquivo `config/adminlte.php`.
- As traduções do pacote na pasta `resources/lang/vendor/adminlte/` (ou `lang/vendor/adminlte` para versões Laravel >= 9.x).

Dica

- Você pode usar a opção `--force` para sobrescrever arquivos existentes anteriormente.
- Você pode usar a opção `--interactive` para ser guiado pelo processo e escolher o que deseja instalar.
- Você pode verificar o status de instalação dos recursos do pacote com o comando `php artisan adminlte:status`.

### Instalando o scaffolding de autenticação legado (opcional)
Opcionalmente, e apenas para versões Laravel 7+, este pacote oferece um conjunto de visualizações de autenticação estilizadas com o AdminLTE que você pode usar para substituir as fornecidas pelo scaffolding de autenticação legado `laravel/ui`. Se você planeja usar essas visualizações, primeiro solicite o pacote `laravel/ui` usando o composer e instale o scaffolding `bootstrap`:
~~~~
composer require laravel/ui
php artisan ui bootstrap --auth
~~~~

Então, você pode fazer as substituições de visualização executando o próximo comando artisan:

~~~~
php artisan adminlte:install --only=auth_views
~~~~

Importante

O scaffolding de autenticação oferece recursos como login, logout e registro. É recomendável sempre ler a documentação de autenticação do Laravel para obter detalhes sobre o scaffolding de autenticação. Observe que o Laravel oferece alguns kits iniciais (como o Laravel-Breeze) além do pacote legado `laravel/ui`. Portanto, usar as visualizações de autenticação deste pacote é OPCIONAL e DEPENDENDO DE VOCÊ.

****

## Instalação do Scaffolding Frontend Laravel UI (opcional)

Depois de instalar o pacote `laravel/ui` usando `composer require laravel/ui`, você pode gerar o scaffolding frontend usando o comando Artisan `ui`:

**Tipos de Scaffolding:**

* **Scaffolding Básico (opcional):**
  * Gera arquivos básicos para estruturar seu layout, como navegação, componentes e páginas de exemplo.
  * Use os seguintes comandos para gerar o scaffolding básico com diferentes frameworks:
      * `php artisan ui bootstrap` (para Bootstrap)
      * `php artisan ui vue` (para Vue.js)
      * `php artisan ui react` (para React.js)

* **Scaffolding de Autenticação (opcional):**
  * Gera arquivos específicos para login, registro e outras funcionalidades de autenticação, estilizados com o framework escolhido.
  * Use os seguintes comandos para gerar o scaffolding de autenticação com diferentes frameworks:
      * `php artisan ui bootstrap --auth` (para Bootstrap)
      * `php artisan ui vue --auth` (para Vue.js)
      * `php artisan ui react --auth` (para React.js)

**Observação:**

O scaffolding de autenticação é opcional e requer a configuração adicional do sistema de autenticação do Laravel. Consulte a documentação do Laravel sobre autenticação para obter mais detalhes.

### Usando o pacote
Vá para a seção Uso para ler como usar o modelo principal `AdminLTE` blade fornecido por este pacote.

****

### Laravel-Breeze

~~~~
# Instalar Laravel Breeze
composer require laravel/breeze --dev
php artisan breeze:install

# Instalar dependencias de npm y compilar activos
npm install
npm run dev

# Ejecutar migraciones de la base de datos
php artisan migrate

# Iniciar el servidor de desarrollo
php artisan serve
~~~~

****

https://github.com/especializati/setup-docker-laravel

https://blueprint.laravelshift.com/


## Instalação padrão projeto laravel 11
~~~~
Aja como um especialista em Laravel. Instale e configure o Laravel 11, configure a tradução para português (pt-BR), instale e configure o AdminLTE, e configure a autenticação padrão com confirmação e comunicação por email. Inclua o processo de reset e alteração de senha.

Aqui estão as especificações detalhadas:
- Sistema Operacional: Windows
- Servidor Web: Apache
- Versão do PHP: PHP 8.2
- Banco de Dados: MySQL

Instalação do Laravel 11
- Baixe e instale o Composer.
- Crie um novo projeto Laravel 11 usando o Composer.

Configuração de Tradução para Português (pt-BR)
- Instale os pacotes de tradução necessários para português (pt-BR).
- Configure o Laravel para usar o português (pt-BR) como o idioma padrão.

Instalação e Configuração do AdminLTE
- Baixe e instale o AdminLTE.
- Integre o AdminLTE ao Laravel incluindo todas as funcionalidades e telas de autenticação.

Configuração de Autenticação
- Ajustar o modelo de usuário para utilizar UUID e SoftDelete.
- Configure a autenticação padrão do Laravel.
- Adicione a confirmação por email após o registro.
- Configure a comunicação por email utilizando recursos padrões do laravel.
- Implemente o processo de reset e alteração de senha, ajustando as views conforme necessário para manter a consistência com o AdminLTE.

Sua Tarefa:
Escreva as instruções completas para realizar essas configurações no Laravel 11, garantindo que todas as etapas sejam detalhadas e fáceis de seguir para um desenvolvedor que esteja utilizando Windows e Apache.

~~~~

## Instalação projeto api laravel 11
~~~~
Aja como um desenvolvedor web experiente e um especialista em configuração de frameworks PHP. Sua tarefa é fornecer instruções detalhadas para instalar e configurar o Laravel 11 em um ambiente Windows com Apache, incluindo a instalação de traduções para português (pt-br), configuração do modo API Resource com autenticação padrão do Laravel e ajustes adicionais. As etapas devem incluir:

Instalar o Laravel 11:
- Passo a passo para instalar o Composer, caso não esteja instalado.
- Comandos necessários para criar um novo projeto Laravel 11.

Configurar o Apache para o Laravel:
- Instruções detalhadas para configurar o servidor Apache para servir o aplicativo Laravel.

Instalar e Configurar Tradução para Português (pt-br):
- Comandos para instalar o pacote de tradução para português.
- Configurações necessárias no Laravel para definir o idioma padrão.

Configurar o Modo API Resource com Autenticação Padrão:
- Etapas para configurar a autenticação padrão do Laravel.
- Comandos para gerar e configurar controladores, rotas e middleware para o modo API Resource.

Configurações Adicionais para Autenticação:
- Ajustar o modelo de usuário para utilizar UUID e SoftDelete.
- Instruções para criar e configurar métodos e processos de autenticação, registro, reset de senha, alteração de senha e confirmação por email.

Sua Tarefa:
Escreva as instruções completas para realizar essas configurações no Laravel 11, garantindo que todas as etapas sejam detalhadas e fáceis de seguir para um desenvolvedor que esteja utilizando Windows e Apache.
~~~~

## adicionar ao projeto api nova funcionalidade
~~~~
Aja como um especialista em desenvolvimento de software utilizando Laravel 11.

Crie uma estrutura CRUD completa (model, migration, factory, seeder, route, requests, controller) utilizando UUID e SoftDeletes. Utilize métodos API Resource. Baseie-se na estrutura da tabela abaixo:

[Insira aqui a estrutura da tabela desejada]

Requisitos:

Model:
- Configure o model para utilizar UUID e SoftDeletes.

Migration:
- Crie uma migration para a tabela acima, incluindo UUID e SoftDeletes.

Factory:
- Crie uma factory para gerar dados de exemplo para a tabela.

Seeder:
- Crie um seeder para popular a tabela com dados de exemplo.
Route:

Defina rotas API Resource para o CRUD.

Requests:
- Crie classes de request para validação na criação e atualização de registros.

- Regras de validação:
   - [Insira aqui as regras de validação específicas]

Controller:
- Crie um controller utilizando métodos API Resource.
- Inclua métodos customizados se necessário:
   - [Insira aqui qualquer funcionalidade extra]

Certifique-se de seguir as convenções de nomeação e estrutura do projeto Laravel padrão.
~~~~
