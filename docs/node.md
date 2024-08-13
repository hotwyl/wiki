# Prompt chat gpt criar projeto
~~~~
Aja como um especialista em desenvolvimento de APIs RESTful com Node.js e instrutor de desenvolvimento de software. Forneça um guia passo a passo com instruções claras para desenvolvedores iniciantes para criar uma API RESTful do zero. A aplicação deve utilizar Node.js, Express, CORS, dotenv, nodemon, JWT para autenticação e controle de acesso, MySQL para banco de dados e axios para consultas request. Siga o padrão de arquivos (router, controller, service, repository, entity, interface, dto, trait, action). Inclua instruções sobre a instalação e configuração do ambiente de desenvolvimento, e exemplos de endpoints específicos, como autenticação e CRUD de usuários. Inclua também boas práticas de segurança.

[funcionalidades]
~~~~

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
