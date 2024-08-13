# Instalação do Node.js e NPM

**Descrição**: O Node.js é uma plataforma para construir aplicações de rede, enquanto o NPM (Node Package Manager) é o gerenciador de pacotes que você usa para instalar bibliotecas e ferramentas.

**Sintaxe**:
Para instalar o Node.js, visite o site oficial do Node.js e baixe o instalador apropriado para o seu sistema operacional.

**Exemplo**:
Após a instalação, você pode verificar a versão do Node.js e do NPM com os seguintes comandos:
~~~~
node -v
npm -v
~~~~

# Criar um Projeto Node.js
**Descrição**: Comece criando uma nova pasta para o seu projeto e inicialize um novo projeto Node.js usando o NPM.

**Sintaxe**:
~~~
mkdir meu-projeto
cd meu-projeto
npm init
~~~
**Exemplo**:
~~~
mkdir meu-app
cd meu-app
npm init -y
~~~
O comando npm `init -y` cria um `package.json` com valores padrão.

# Instalação de Pacotes

**Descrição**: Use o NPM para instalar pacotes que você precisará em seu projeto, como frameworks e bibliotecas.

**Sintaxe**:
~~~
npm install nome-do-pacote
~~~
**Exemplo**:
Para instalar o Express, um framework popular para construir APIs:
~~~
npm install express
~~~

# Criar um Servidor Básico com Express

**Descrição**: Express é um framework minimalista para construir servidores HTTP. Abaixo está um exemplo básico de como configurar um servidor.

**Sintaxe**:
~~~
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

app.listen(port, () => {
  console.log(`Servidor rodando na porta ${port}`);
});
~~~

Exemplo:
Crie um arquivo chamado `app.js` e adicione o código acima. Depois, execute o servidor com:
~~~
node app.js
~~~

# Trabalhar com Rotas

**Descrição**: Rotas definem como o servidor deve responder a diferentes solicitações.

**Sintaxe**:
~~~
app.get('/rota', (req, res) => {
  res.send('Resposta para a rota');
});
~~~

**Exemplo**:
Adicione ao `app.js`:
~~~
app.get('/saudacao', (req, res) => {
  res.send('Bem-vindo à minha aplicação!');
});
~~~

# Manipulação de Requisições e Respostas

**Descrição**: Use `req` (request) e `res` (response) para acessar informações sobre a requisição e enviar respostas.

**Sintaxe**:
~~~
app.post('/usuario', (req, res) => {
  const nome = req.body.nome;
  res.send(`Usuário ${nome} criado com sucesso!`);
});
~~~

**Exemplo**:
Para lidar com o corpo da requisição, você deve usar o middleware `express.json()`:
~~~
app.use(express.json());

app.post('/usuario', (req, res) => {
  const nome = req.body.nome;
  res.send(`Usuário ${nome} criado com sucesso!`);
});
~~~

# Conectar a um Banco de Dados

**Descrição**: Você pode conectar seu aplicativo a um banco de dados, como MongoDB, usando um cliente de banco de dados.

**Sintaxe**:
Para MongoDB, você pode usar o pacote `mongoose`:
~~~
npm install mongoose
~~~

**Exemplo**:
~~~
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/meubanco', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Conectado ao MongoDB'))
  .catch(err => console.error('Não foi possível conectar ao MongoDB', err));
~~~

# Criar e Usar Middleware

**Descrição**: Middleware são funções que têm acesso ao objeto de requisição (`req`), objeto de resposta (`res`), e a próxima função de middleware no ciclo de solicitação-resposta.

**Sintaxe**:
~~~
app.use((req, res, next) => {
  console.log('Middleware executado');
  next();
});
~~~

**Exemplo**:
Adicione um middleware ao `app.js`:
~~~
app.use((req, res, next) => {
  console.log(`Requisição recebida: ${req.method} ${req.url}`);
  next();
});
~~~

# Gerenciamento de Erros

**Descrição**: Gerencie erros com middleware de tratamento de erros.

**Sintaxe**:
~~~
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Algo deu errado!');
});
~~~

**Exemplo**:
Adicione um manipulador de erros ao final do seu arquivo `app.js`:
~~~
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Erro interno do servidor!');
});
~~~

# Ambientes e Variáveis de Ambiente

**Descrição**: Use variáveis de ambiente para configurar sua aplicação sem alterar o código-fonte.

**Sintaxe**:
Crie um arquivo `.env`:
~~~
PORT=3000
DB_URL=mongodb://localhost/meubanco
~~~

Use o pacote `dotenv` para carregar as variáveis:
~~~
npm install dotenv
~~~

**Exemplo**:
No seu app.js:
~~~
require('dotenv').config();

const port = process.env.PORT || 3000;

app.listen(port, () => {
  console.log(`Servidor rodando na porta ${port}`);
});
~~~

# Documentação com Swagger

**Descrição**: Use Swagger para documentar sua API.

**Sintaxe**: 

Instale o Swagger UI Express:
~~~
npm install swagger-ui-express swagger-jsdoc
~~~

**Exemplo**:

No seu `app.js`:
~~~
const swaggerJsdoc = require('swagger-jsdoc');
const swaggerUi = require('swagger-ui-express');

const swaggerOptions = {
  definition: {
    openapi: '3.0.0',
    info: {
      title: 'API Example',
      version: '1.0.0',
    },
  },
  apis: ['./app.js'],
};

const specs = swaggerJsdoc(swaggerOptions);

app.use('/api-docs', swaggerUi.serve, swaggerUi.setup(specs));
~~~

# Instalar o MySQL e Configurar o Banco de Dados

## Instalar o Pacote MySQL para Node.js

**Descrição**: Para conectar e interagir com o MySQL, você pode usar o pacote mysql2, que é uma versão mais moderna e com melhor desempenho do pacote mysql.

**Sintaxe**:
~~~
npm install mysql2
~~~

## Instalar o Pacote MySQL para Node.js

**Descrição**: Para conectar e interagir com o MySQL, você pode usar o pacote `mysql2`, que é uma versão mais moderna e com melhor desempenho do pacote `mysql`.

**Sintaxe**:
~~~
npm install mysql2
~~~

## Configurar a Conexão com o MySQL

**Descrição**: Crie uma conexão com o banco de dados MySQL usando o pacote `mysql2`.

**Sintaxe**:
~~~
const mysql = require('mysql2');

// Configuração da conexão
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',        // seu usuário MySQL
  password: 'senha',   // sua senha MySQL
  database: 'meu_banco'
});

// Conectar ao banco de dados
connection.connect((err) => {
  if (err) {
    console.error('Erro ao conectar: ' + err.stack);
    return;
  }
  console.log('Conectado como ID ' + connection.threadId);
});
~~~

## Executar Consultas SQL

**Descrição**: Execute consultas SQL usando a conexão criada.

**Sintaxe**:
~~~
// Consulta simples
connection.query('SELECT * FROM usuarios', (err, results, fields) => {
  if (err) throw err;
  console.log(results);
});
~~~

Exemplo de inserção de dados:
~~~
const novoUsuario = { nome: 'João', email: 'joao@example.com' };

connection.query('INSERT INTO usuarios SET ?', novoUsuario, (err, results) => {
  if (err) throw err;
  console.log('Usuário adicionado com ID:', results.insertId);
});
~~~

## Trabalhar com Promises e Async/Await

**Descrição**: Para um código mais limpo e fácil de gerenciar, use async/await com mysql2/promise.

**Sintaxe**:
~~~
npm install mysql2
~~~

Exemplo de código:
~~~
const mysql = require('mysql2/promise');

(async function() {
  // Criar a conexão
  const connection = await mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'senha',
    database: 'meu_banco'
  });

  // Executar uma consulta
  const [rows, fields] = await connection.execute('SELECT * FROM usuarios');
  console.log(rows);

  // Inserir dados
  const [result] = await connection.execute('INSERT INTO usuarios (nome, email) VALUES (?, ?)', ['Maria', 'maria@example.com']);
  console.log('Usuário adicionado com ID:', result.insertId);

  // Fechar a conexão
  await connection.end();
})();
~~~

## Fechar a Conexão

**Descrição**: É importante fechar a conexão quando ela não for mais necessária para liberar recursos.

**Sintaxe**:
~~~
connection.end((err) => {
  if (err) {
    console.error('Erro ao fechar a conexão: ' + err.stack);
    return;
  }
  console.log('Conexão fechada.');
});
~~~

## Tratamento de Erros e Boas Práticas

**Descrição**: Sempre trate erros de conexão e consultas para garantir a robustez do aplicativo.

Exemplo de tratamento de erros:
~~~
connection.query('SELECT * FROM usuarios', (err, results, fields) => {
  if (err) {
    console.error('Erro na consulta: ' + err.stack);
    return;
  }
  console.log(results);
});
~~~

## Usar Migrations para Gerenciar o Esquema

**Descrição**: Para gerenciar alterações no esquema do banco de dados, você pode usar ferramentas de migração como `migrate-mysql`.

Sintaxe:
~~~
npm install migrate-mysql
~~~

Exemplo básico de migração:
Crie arquivos de migração para definir e aplicar mudanças no esquema do banco de dados de maneira controlada e versionada.

***

# Prompt chat gpt criar projeto
~~~~
Aja como um especialista em desenvolvimento de APIs RESTful com Node.js e instrutor de desenvolvimento de software. Forneça um guia passo a passo com instruções claras para desenvolvedores iniciantes para criar uma API RESTful do zero. A aplicação deve utilizar Node.js, Express, CORS, dotenv, nodemon, JWT para autenticação e controle de acesso, MySQL para banco de dados e axios para consultas request. Siga o padrão de arquivos (router, controller, service, repository, entity, interface, dto, trait, action). Inclua instruções sobre a instalação e configuração do ambiente de desenvolvimento, e exemplos de endpoints específicos, como autenticação e CRUD de usuários. Inclua também boas práticas de segurança.

[funcionalidades]
~~~~

***

# Instalação e Configuração do Ambiente de Desenvolvimento

## Instale o Node.js:

 - Baixe e instale a versão mais recente do Node.js em nodejs.org.
   
## Crie o diretório do projeto:
~~~~
mkdir my-api
cd my-api
~~~~

## Inicialize um novo projeto Node.js:
~~~~
npm init -y
~~~~

## Instale as dependências necessárias:
~~~~
npm install express cors dotenv mysql2 jsonwebtoken axios
npm install --save-dev nodemon
~~~~

## Configure o arquivo `package.json` para usar o nodemon:
~~~~
"scripts": {
  "start": "node index.js",
  "dev": "nodemon index.js"
}
~~~~

# Estrutura de Pastas e Arquivos

Organize o projeto seguindo o padrão:
~~~~
my-api/
├── node_modules/
├── src/
│   ├── actions/
│   ├── controllers/
│   ├── dtos/
│   ├── entities/
│   ├── interfaces/
│   ├── repositories/
│   ├── routers/
│   ├── services/
│   ├── traits/
│   ├── config/
│   │   └── db.js
│   ├── middlewares/
│   │   └── auth.js
│   └── index.js
├── .env
├── package.json
└── README.md
~~~~

# Configuração do Banco de Dados

## Crie o banco de dados MySQL:
~~~~
CREATE DATABASE myapi;
~~~~

## Configure a conexão com o banco de dados no arquivo `src/config/db.js`:
~~~~
const mysql = require('mysql2');
require('dotenv').config();

const connection = mysql.createConnection({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASS,
  database: process.env.DB_NAME
});

connection.connect(err => {
  if (err) {
    console.error('Error connecting to the database:', err);
    return;
  }
  console.log('Connected to the MySQL database.');
});

module.exports = connection;
~~~~

## Adicione as variáveis de ambiente no arquivo `.env`:
~~~~
DB_HOST=localhost
DB_USER=root
DB_PASS=password
DB_NAME=myapi
JWT_SECRET=your_secret_key
~~~~

# Implementação da Autenticação JWT

## Middleware de Autenticação (`src/middlewares/auth.js`):
~~~~
const express = require('express');
const router = express.Router();
const jwt = require('jsonwebtoken');
const bcrypt = require('bcrypt');
const db = require('../config/db');
require('dotenv').config();

router.post('/register', async (req, res) => {
  const { username, password } = req.body;
  const hashedPassword = await bcrypt.hash(password, 10);

  db.query('INSERT INTO users (username, password) VALUES (?, ?)', [username, hashedPassword], (err, result) => {
    if (err) return res.status(500).json({ error: err.message });
    res.status(201).json({ message: 'User registered successfully' });
  });
});

router.post('/login', (req, res) => {
  const { username, password } = req.body;

  db.query('SELECT * FROM users WHERE username = ?', [username], async (err, results) => {
    if (err) return res.status(500).json({ error: err.message });
    if (results.length === 0) return res.status(400).json({ error: 'User not found' });

    const user = results[0];
    const validPassword = await bcrypt.compare(password, user.password);
    if (!validPassword) return res.status(400).json({ error: 'Invalid password' });

    const token = jwt.sign({ id: user.id }, process.env.JWT_SECRET, { expiresIn: '1h' });
    res.json({ token });
  });
});

module.exports = router;
~~~~

## Arquivo Principal (`src/index.js`):
~~~~
const express = require('express');
const cors = require('cors');
const app = express();
require('dotenv').config();

// Middlewares
app.use(cors());
app.use(express.json());

// Routers
const authRouter = require('./routers/auth');
app.use('/auth', authRouter);

// Start the server
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
~~~~

# Exemplos de Endpoints (CRUD de Usuários)

## Rota de Usuários (`src/routers/users.js`):
~~~~
const express = require('express');
const router = express.Router();
const db = require('../config/db');
const authenticateToken = require('../middlewares/auth');

router.get('/', authenticateToken, (req, res) => {
  db.query('SELECT * FROM users', (err, results) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json(results);
  });
});

router.get('/:id', authenticateToken, (req, res) => {
  const { id } = req.params;
  db.query('SELECT * FROM users WHERE id = ?', [id], (err, results) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json(results[0]);
  });
});

router.put('/:id', authenticateToken, (req, res) => {
  const { id } = req.params;
  const { username, password } = req.body;
  const hashedPassword = await bcrypt.hash(password, 10);
  db.query('UPDATE users SET username = ?, password = ? WHERE id = ?', [username, hashedPassword, id], (err, results) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json({ message: 'User updated successfully' });
  });
});

router.delete('/:id', authenticateToken, (req, res) => {
  const { id } = req.params;
  db.query('DELETE FROM users WHERE id = ?', [id], (err, results) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json({ message: 'User deleted successfully' });
  });
});

module.exports = router;
~~~~

## Melhores Práticas de Segurança

- Utilize variáveis de ambiente para configurações sensíveis.
- Sempre utilize HTTPS em produção.
- Valide e sanitize todas as entradas do usuário.
- Mantenha suas dependências atualizadas.
