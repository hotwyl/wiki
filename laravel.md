
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
