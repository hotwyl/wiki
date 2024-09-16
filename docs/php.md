## Criando API

Aja como um especialista em desenvolvimento de APIs RESTful em PHP 8.2, com amplo conhecimento em padrões de projeto e boas práticas recomendadas (PSRs). Sua tarefa é gerar uma estrutura completa de uma API RESTful orientada a objetos, usando PHP 8 puro (sem frameworks), Composer, e seguindo os padrões PSR-4 para autoloading.

Detalhes do projeto:

Objetivo: Criar uma API RESTful que [funcionalidade].

- Inicialização do projeto com Composer `init`.
- **Banco de dados**: MySQL, utilizando DAO (Data Access Object). Desenvolva os schemas das tabelas normalizadas, incluindo as chaves primárias e estrangeiras com seus devidos vínculos. Crie as stored procedures, functions, triggers e views necessárias.
- **Padrões de design**: Use os padrões Service, Repository, Action, DTO, Model, Controller, Router, Trait, Gets e Sets, Interfaces, Entity, Injeção de Dependências.
- **Estrutura e práticas**: Aplique métodos mágicos, injeção de dependências, e organize a aplicação usando interfaces e traits onde necessário.

Requisitos:
- **Composer e PSR-4**: Configure o Composer para gerenciar dependências e o autoloading da API, seguindo a PSR-4.
- **Model e Entity**: Defina classes de entidades representando as tabelas do banco de dados. Aplique padrões de getters e setters com traits, além de métodos mágicos (__get, __set).
- **DTO (Data Transfer Object)**: Crie classes DTO para transferir dados entre camadas.
- **Repository**: Aplique o padrão de repositório para lidar com operações de banco de dados, usando PDO para conexão com o MySQL.
- **Service**: Utilize serviços para aplicar lógica de negócio fora dos controllers.
- **Controller e Router**: Implemente controllers que definem as rotas da API. Configure um roteador para mapear endpoints REST (GET, POST, PUT, DELETE) para os controladores.
- **Injeção de dependência**: Use injeção de dependências para ligar os serviços e repositórios com os controladores e actions.
- **DAO e MySQL**: Inclua uma implementação DAO para lidar com a persistência de dados no MySQL, além de criar o schema SQL das tabelas e views no banco de dados.
- **Interface e Traits**: Defina interfaces para contratos de repositórios e serviços. Utilize traits para compartilhar funcionalidades comuns entre classes.
- **Views e Schema SQL**: Crie as queries SQL que configuram as tabelas necessárias e defina uma view para consultas específicas.

Exemplo de estrutura do projeto:
~~~~
/src
    /Entity
        - User.php (definir propriedades, métodos mágicos e getters/setters)
    /DTO
        - UserDTO.php
    /Repository
        - UserRepositoryInterface.php
        - UserRepository.php
    /Service
        - UserServiceInterface.php
        - UserService.php
    /Controller
        - UserController.php
    /Router
        - Router.php
    /Traits
        - Timestamps.php
/composer.json (configurar PSR-4 autoloading)
~~~~

Exemplo de estrutura SQL:

Tabela de Usuários:

~~~
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

~~~~
View de Usuários Ativos:

~~~~
CREATE VIEW active_users AS
SELECT id, name, email
FROM users
WHERE active = 1;
~~~~

Sua tarefa é gerar o código completo com base na estrutura fornecida, incluindo classes, interfaces, traits, rotas e controladores.



## Criando Aplicação Fullstack com PHP

Aja como um especialista em desenvolvimento de APIs RESTful em PHP 8.2, com amplo conhecimento em padrões de projeto e boas práticas recomendadas (PSRs). Crie uma aplicação em PHP puro sem nenhum framework, utilizando PHP 8.2 orientado a objetos. Desenvolva a aplicação desde o início, incluindo:

### Detalhes do projeto:

**Objetivo**: Desenvolva [aplicação]

* Inicialização do projeto com `Composer init`.
* Implementação das PSRs (PHP Standards Recommendations).
* Padrão MVC (Model-View-Controller).
* Banco de dados: MySQL, utilizando DAO (Data Access Object). Desenvolva os schemas das tabelas normalizadas, incluindo as chaves primárias e estrangeiras com seus devidos vínculos. Crie as stored procedures, functions, triggers e views necessárias.
* Padrões de design: Use os padrões Service, Repository, Action, DTO, Model, Controller, Router, Trait, Gets e Sets, Interfaces, Entity, Injeção de Dependências.
* Estrutura e práticas**: Aplique métodos mágicos, injeção de dependências, e organize a aplicação usando interfaces e traits onde necessário.
* Interface frontend utilizando Bootstrap 5, SweetAlert2 e FontAwesome 6.
* Técnicas de SEO e UI/UX.

Requisitos:
- **Composer e PSR-4**: Configure o Composer para gerenciar dependências e o autoloading da API, seguindo a PSR-4.
- **Model e Entity**: Defina classes de entidades representando as tabelas do banco de dados. Aplique padrões de getters e setters com traits, além de métodos mágicos (__get, __set).
- **DTO (Data Transfer Object)**: Crie classes DTO para transferir dados entre camadas.
- **Repository**: Aplique o padrão de repositório para lidar com operações de banco de dados, usando PDO para conexão com o MySQL.
- **Service**: Utilize serviços para aplicar lógica de negócio fora dos controllers.
- **Controller e Router**: Implemente controllers que definem as rotas da API. Configure um roteador para mapear endpoints REST (GET, POST, PUT, DELETE) para os controladores.
- **Injeção de dependência**: Use injeção de dependências para ligar os serviços e repositórios com os controladores e actions.
- **DAO e MySQL**: Inclua uma implementação DAO para lidar com a persistência de dados no MySQL, além de criar o schema SQL das tabelas e views no banco de dados.
- **Interface e Traits**: Defina interfaces para contratos de repositórios e serviços. Utilize traits para compartilhar funcionalidades comuns entre classes.
- **Views e Schema SQL**: Crie as queries SQL que configuram as tabelas necessárias e defina uma view para consultas específicas.
