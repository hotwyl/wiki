## Instalando e Configurando o Symfony
Este guia apresenta os passos iniciais para instalar e configurar o Symfony em seu ambiente de desenvolvimento.
***

### Pré-requisitos:

- Sistema operacional Linux/macOS (para o comando sudo)
- PHP 7.4 ou superior
- Composer (gerenciador de dependências PHP)
***

### Instalação do Symfony CLI (Interface de Linha de Comando)
Distribuições baseadas em Debian/Ubuntu:
~~~
sudo apt install symfony-cli
~~~

**Outras distribuições**:

Consulte a documentação do Symfony para instruções específicas sobre a instalação do Symfony CLI em seu sistema operacional. https://symfony.com/doc/current/setup.html
***

### Verificando os Requisitos
Execute o comando `symfony check:requirements` para verificar se o seu ambiente atende aos requisitos mínimos do Symfony:
~~~
symfony check:requirements
~~~
Este comando verificará se as versões do PHP, Composer e extensões necessárias estão instaladas e configuradas corretamente.
***

### Criando um Novo Projeto Symfony
Existem duas abordagens para criar um novo projeto Symfony:

A. **Usando o Symfony CLI**

1. Crie um novo projeto com o nome `my_project`:

~~~
symfony new my_project
~~~

2. (Opcional) Especifique a versão do Symfony:
~~~
symfony new my_project_directory --version="7.0.*"
~~~

3. (Opcional) Crie um projeto webapp (com recursos frontais padrão):
~~~
symfony new my_project_directory --version="7.0.*" --webapp
~~~

B. **Usando o Composer**

1. Crie um diretório para o projeto e navegue até ele.
2. Execute o seguinte comando para criar um projeto Symfony básico:
~~~
composer create-project symfony/skeleton:"7.0.*" my_project_directory
~~~
3. (Opcional) Navegue para o diretório do projeto:
~~~
cd my_project_directory
~~~
4. Instale o pacote web para funcionalidades `web` padrão:
~~~
composer require webapp
~~~
***

### Verificando a Segurança
Execute o comando `symfony check:security` para identificar possíveis problemas de segurança na configuração do seu projeto:
~~~
symfony check:security
~~~
Corrija quaisquer vulnerabilidades detectadas para garantir a segurança da sua aplicação.
***

### Iniciar o Servidor de Desenvolvimento
Execute o comando `symfony server:start` para iniciar o servidor de desenvolvimento do Symfony:
~~~
symfony server:start
~~~
Acesse o seu projeto na URL `http://localhost:8000` (ou a porta especificada, se alterada). Isso permitirá testar o seu projeto em um ambiente local.
***

### Parar o Servidor de Desenvolvimento
Para parar o servidor de desenvolvimento, execute o comando:
~~~
symfony server:stop
~~~
***

### Iniciar o Servidor sem TLS (Opcional)
Para iniciar o servidor sem o protocolo TLS (HTTPS), use a opção `-no-tls` e especifique uma porta alternativa (se desejado):
~~~
symfony server:start -no-tls --port=8010
~~~
**Observação**:

- Iniciar o servidor sem TLS é útil para fins de desenvolvimento local, mas não é recomendado para ambientes de produção devido a problemas de segurança.
- Para ambientes de produção, é crucial configurar o TLS para proteger a comunicação entre o cliente e o servidor.
Este guia fornece uma base sólida para iniciar o desenvolvimento com o Symfony. Lembre-se de consultar a documentação oficial do Symfony para obter instruções mais detalhadas e recursos avançados. https://symfony.com/doc/current/setup.html

***

### Criar entidades e controladores:
`make:entity`: Este comando cria automaticamente uma entidade e as classes de repositório associadas com base em uma definição.
~~~
php bin/console make:entity <entidade_nome> --fields=<nome_campo1>:<tipo_campo1>,<nome_campo2>:<tipo_campo2>,...
~~~
`make:controller`: Este comando cria automaticamente um controlador para uma entidade específica.
~~~
php bin/console make:controller <app_namespace>/<controlador_nome> <entidade_nome>
~~~
***

### Gerenciar rotas
`make:route`: Este comando cria automaticamente uma rota para um controlador específico.
~~~
php bin/console make:route <rota_nome> <controlador_nome>/<metodo_controlador>
~~~
`routing:list`: Este comando lista todas as rotas definidas em seu projeto.
~~~
php bin/console routing:list
~~~
***

### Gerar formulários
`make:form`: Este comando cria automaticamente uma classe de formulário com base em uma entidade específica.
~~~
php bin/console make:form <app_namespace>/<form_nome> <entidade_nome>
~~~
***

### Gerenciar migrações
`doctrine:migrations:migrate`: Este comando executa todas as migrações de banco de dados pendentes.
~~~
php bin/console doctrine:migrations:migrate
~~~
`doctrine:migrations:generate`: Este comando cria automaticamente uma nova migração de banco de dados com base nas alterações feitas em suas entidades.
~~~
php bin/console doctrine:migrations:generate
~~~
***

### Testar sua aplicação
`phpunit`: Este comando executa os testes unitários em seu projeto.
~~~
php bin/console phpunit
~~~
`functional:all`: Este comando executa todos os testes funcionais em seu projeto.
~~~
php bin/console functional:all
~~~
***

### Recursos adicionais:

- Documentação do Symfony: https://symfony.com/doc/
- Comandos do Symfony Console: https://symfony.com/doc/current/console.html

### Observações:

- Esses são apenas alguns comandos básicos para começar. O Symfony oferece uma variedade de outros comandos e recursos para ajudá-lo a criar funcionalidades complexas.
- Certifique-se de ler a documentação do Symfony para obter mais informações sobre cada comando e como usá-lo de forma eficaz.
- É importante seguir as melhores práticas de desenvolvimento Symfony para criar código limpo, robusto e testável.
Lembre-se que a criação de funcionalidades no Symfony é um processo iterativo que envolve planejamento, desenvolvimento, testes e refinamento. Use os comandos e recursos do Symfony de forma eficaz para construir aplicações web robustas e escaláveis.
