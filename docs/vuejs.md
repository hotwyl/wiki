
# 1. Introdução ao Vue.js 3

Vue.js é um framework progressivo para construir interfaces de usuário. Com o Vue.js, você pode criar aplicativos interativos e reativos de forma simples.

**documentação oficial**: `https://vuejs.org/`

# 2. Instalação e Criação de Projeto

## Instalar Vue CLI

Primeiro, você precisa instalar o Vue CLI (Command Line Interface) globalmente no seu computador. Isso pode ser feito com o Node.js e o npm (Node Package Manager) instalados:

~~~~
npm install -g @vue/cli
~~~~

## Criar um Novo Projeto

~~~~
npm create vue@latest
~~~~
ou
~~~~
vue create nome-do-projeto
~~~~

Você será solicitado a escolher uma configuração. Para iniciantes, a configuração padrão é uma boa escolha. Navegue para o diretório do projeto:

~~~~
cd nome-do-projeto
~~~~

# 3. Vue CLI UI
Para uma interface gráfica de usuário, você pode usar o Vue CLI UI:
~~~~
vue --version

vue ui
~~~~
Isso abrirá uma interface no navegador onde você pode criar e gerenciar projetos Vue com uma GUI.

# 4. Rodar o Projeto
Para rodar o projeto localmente, use o comando:
~~~~
npm run serve
~~~~
ou
~~~~
npm run dev
~~~~
Isso inicia um servidor de desenvolvimento e você pode visualizar seu projeto em `http://localhost:8080`.

# 5. Publicar o Projeto
Para publicar seu projeto, você precisa criar uma versão de produção:
~~~~
npm run build
~~~~
Isso cria uma pasta `dist` com os arquivos otimizados para produção. Você pode então fazer o upload dessa pasta para o seu servidor ou serviço de hospedagem.

# Composition API vs Options API
`Options API` é o estilo tradicional de definir componentes:
~~~~
export default {
  data() {
    return {
      message: 'Olá, Vue!'
    }
  },
  methods: {
    greet() {
      alert(this.message);
    }
  }
}
~~~~
`Composition API` é uma abordagem mais recente, oferecendo maior flexibilidade:
~~~~
import { ref } from 'vue';

export default {
  setup() {
    const message = ref('Olá, Vue!');
    const greet = () => {
      alert(message.value);
    };
    return { message, greet };
  }
}
~~~~

# 7. Rotas
Para adicionar navegação entre páginas, use o Vue Router.

**Instalar Vue Router:**
~~~~
npm install vue-router
~~~~

**Configuração Básica:**
Crie um arquivo `router.js`:
~~~~
import { createRouter, createWebHistory } from 'vue-router';
import Home from './components/Home.vue';
import About from './components/About.vue';

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About }
];

const router = createRouter({
  history: createWebHistory(),
  routes
});

export default router;
~~~~

No arquivo `main.js`, importe e use o router:
~~~~
import { createApp } from 'vue';
import App from './App.vue';
import router from './router';

createApp(App).use(router).mount('#app');
~~~~

# Templates
Templates são a parte visual dos componentes. Aqui está um exemplo simples:
~~~~
<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="greet">Saudar</button>
  </div>
</template>
~~~~

# 9. Componentes
Componentes são partes reutilizáveis da interface:
~~~~
// HelloWorld.vue
<template>
  <div>
    <p>{{ msg }}</p>
  </div>
</template>

<script>
export default {
  props: ['msg']
}
</script>
~~~~
Você pode usar `HelloWorld` em outro componente:
~~~~
<HelloWorld msg="Olá, Mundo!"/>
~~~~

# 10. Lifecycle Hooks
Os hooks de ciclo de vida ajudam a executar código em diferentes etapas do ciclo de vida de um componente:
~~~~
import { onMounted, onUnmounted } from 'vue';

export default {
  setup() {
    onMounted(() => {
      console.log('Componente montado');
    });
    onUnmounted(() => {
      console.log('Componente desmontado');
    });
  }
}
~~~~
No Vue.js, os ciclos de vida (lifecycle hooks) são eventos que ocorrem em diferentes etapas do ciclo de vida de um componente. Eles permitem que você execute código em momentos específicos, como quando o componente é criado, montado, atualizado ou destruído. Abaixo está uma lista dos principais ciclos de vida disponíveis no Vue.js 3, incluindo uma breve descrição de cada um:

## beforeCreate
- **Descrição**: Chamado antes do componente ser criado. As opções do componente ainda não foram processadas.
- **Uso**: Para executar código antes da instância do componente ser configurada.
- **Exemplo**:
~~~~
beforeCreate() {
  console.log('beforeCreate');
}
~~~~

## created
- **Descrição**: Chamado após a instância do componente ser criada e as opções do componente serem processadas, mas antes de ser montado no DOM.
- **Uso**: Ideal para inicializar dados, fazer chamadas a APIs e definir configurações.
- **Exemplo**:
~~~~
created() {
  console.log('created');
}
~~~~

## beforeMount
- **Descrição**: Chamado antes do componente ser montado no DOM. O template foi compilado, mas o DOM ainda não foi atualizado.
- **Uso**: Para executar código antes da renderização inicial do DOM.
- **Exemplo**:
~~~~
beforeMount() {
  console.log('beforeMount');
}
~~~~

## mounted
- **Descrição**: Chamado após o componente ser montado no DOM. É o momento ideal para interagir com o DOM ou iniciar chamadas assíncronas.
- **Uso**: Para realizar ações após o componente ser renderizado no DOM.
- **Exemplo**:
~~~~
mounted() {
  console.log('mounted');
}
~~~~

## beforeUpdate
- **Descrição**: Chamado antes do componente ser atualizado como resultado de uma mudança de dados reativos.
- **Uso**: Para realizar ações antes da atualização do DOM.
- **Exemplo**:
~~~~
beforeUpdate() {
  console.log('beforeUpdate');
}
~~~~

## updated
- **Descrição**: Chamado após o componente ter sido atualizado e o DOM ter sido re-renderizado.
- **Uso**: Ideal para executar ações que dependem do DOM atualizado.
- **Exemplo**:
~~~~
updated() {
  console.log('updated');
}
~~~~

## beforeUnmount
- **Descrição**: Chamado antes do componente ser destruído e removido do DOM.
- **Uso**: Para limpar recursos ou realizar operações de limpeza antes da desmontagem.
- **Exemplo**:
~~~~
beforeUnmount() {
  console.log('beforeUnmount');
}
~~~~

## unmounted
- **Descrição**: Chamado após o componente ser desmontado e removido do DOM.
- **Uso**: Ideal para limpar timers, remover ouvintes de eventos ou realizar outras tarefas de limpeza.
- **Exemplo**:
~~~~
unmounted() {
  console.log('unmounted');
}
~~~~

## errorCaptured
- **Descrição**: Chamado quando um erro é capturado em um componente filho. Isso permite que o componente pai lide com o erro e, opcionalmente, impeça que o erro se propague mais.
- **Uso**: Para capturar e tratar erros que ocorrem em componentes filhos, garantindo que eles não interrompam o fluxo do aplicativo.
- **Exemplo**:
~~~~
errorCaptured(err, vm, info) {
  console.error('Erro capturado:', err);
  // Retornar false impede que o erro se propague mais.
  return false;
}
~~~~

## setup (Composition API)
- **Descrição**: Chamado antes da criação da instância do componente, na configuração inicial do componente quando se usa a Composition API.
- **Uso**: Para definir reatividade, efeitos colaterais, e lidar com lógica do componente usando a Composition API.
- **Exemplo**:
~~~~
import { ref } from 'vue';

export default {
  setup() {
    const count = ref(0);
    const increment = () => {
      count.value++;
    };
    return { count, increment };
  }
}
~~~~

## Resumo dos Ciclos de Vida no Vue.js 3
Aqui está uma tabela resumida com os principais hooks de ciclo de vida em Vue.js 3:
| Hook  | Descrição |
| - | - |
| `beforeCreate` | Chamado antes da criação da instância do componente. |
| `created` | Chamado após a instância do componente ser criada, mas antes da montagem. |
| `beforeMount` | Chamado antes da montagem do componente no DOM. |
| `mounted` | Chamado após o componente ser montado no DOM. |
| `beforeUpdate` | Chamado antes da atualização do componente. |
| `updated` | Chamado após o componente ser atualizado e o DOM re-renderizado. |
| `beforeUnmount` | Chamado antes do componente ser desmontado. |
| `unmounted` | Chamado após o componente ser desmontado. |
| `errorCaptured` | Chamado quando um erro é capturado em um componente filho. |
| `setup` | Chamado antes da criação da instância do componente, usado com a Composition API. |

Esses ciclos de vida permitem que você gerencie e controle o comportamento dos seus componentes em diferentes fases de seu ciclo de vida.

# 11. Consumir API Externa
Para consumir APIs, use axios ou fetch:

**Instalar Axios**:
~~~~
npm install axios
~~~~
Uso com Axios:
~~~~
import axios from 'axios';

export default {
  data() {
    return {
      posts: []
    }
  },
  mounted() {
    axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(response => {
        this.posts = response.data;
      });
  }
}
~~~~

# 12. Adicionar e Configurar Bibliotecas CSS

## Bootstrap
Instale Bootstrap:
~~~~
npm install bootstrap
~~~~
Adicione ao seu `main.js`:
~~~~
import 'bootstrap/dist/css/bootstrap.min.css';
~~~~

### adicionar bootstrap
Install bootstrap as you would any other JS module in the Vue project using npm install or by adding it to the `package.json`...
~~~~
npm install --save bootstrap
npm install --save @popperjs/core
~~~~
Next, add the Bootstrap CSS and JS components to the Vue project entrypoint (ie: `src/main.js`)...
~~~~
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"
~~~~
Then, the simplest way to use Bootstrap components is via the data-bs- attributes. For example here's the Bootstrap Collapse component...
~~~~
<button 
  class="btn btn-primary" 
  data-bs-target="#collapseTarget" 
  data-bs-toggle="collapse">
  Bootstrap collapse
</button>
<div class="collapse py-2" id="collapseTarget">
  This is the toggle-able content!
</div>
~~~~

## Tailwind CSS
Instale Tailwind CSS:
~~~~
npm install -D tailwindcss
npx tailwindcss init
~~~~
Configure o arquivo `tailwind.config.js` e adicione Tailwind ao seu `main.css`:
~~~~
@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
~~~~

### adicionar tailwind

Create your project
Start by creating a new Vite project if you don’t have one set up already. The most common approach is to use Create Vite.

~~~~
npm init vite my-project
cd my-project
~~~~

Install Tailwind CSS
Install tailwindcss and its peer dependencies via npm, and then run the init command to generate both `tailwind.config.js` and `postcss.config.js`.

~~~~
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
~~~~

Configure your template paths
Add the paths to all of your template files in your `tailwind.config.js` file.

~~~~
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
~~~~

Add the Tailwind directives to your CSS
Create a `./src/index.css` file and add the `@tailwind` directives for each of Tailwind’s layers.

`index.css`
~~~~
@tailwind base;
@tailwind components;
@tailwind utilities;
~~~~

Import the CSS file
Import the newly-created `./src/index.css` file in your `./src/main.js` file.

`main.js`
~~~~
import { createApp } from 'vue'
import App from './App.vue'
import './index.css'

createApp(App).mount('#app')
~~~~

## Materialize CSS
Instale Materialize:
~~~~
npm install materialize-css
~~~~
Adicione ao seu `main.js`:
~~~~
import 'materialize-css/dist/css/materialize.min.css';
~~~~

### MaterializeCss with Vue.js
Step 1: installation

~~~~
npm install materialize-css@next --save
npm install material-design-icons --save
~~~~

Step 2: import materialize css in src/main.js
At `src/main.js`
~~~~
import 'materialize-css/dist/css/materialize.min.css'
import 'material-design-icons/iconfont/material-icons.css'
~~~~

Step 3: initialize materialize components
Add following code in your component(say App.vue):
~~~~
import M from 'materialize-css'

export default {
...
mounted () {
    M.AutoInit()
},
...
~~~~

## Vuetify
Instale Vuetify:
~~~~
npm install vuetify@next
~~~~
Configure em `main.js`:
~~~~
import { createApp } from 'vue';
import App from './App.vue';
import vuetify from './plugins/vuetify';

createApp(App).use(vuetify).mount('#app');
~~~~

### add vuetfy

For a detailed explanation of how to get npm running in your environment, check out the official documentation. Alternatively, if you wish to use yarn, you can find the official documentation here. Once setup, you can run either command from your command prompt.

~~~~
$ npm install vuetify --save
// OR
$ yarn add vuetify
~~~~

Once Vuetify has been installed, navigate to your application's main entry point. In most cases this will be `index.js` or `main.js`. In this file you will import Vuetify and tell Vue to use it.
~~~~
import Vue from 'vue'
import Vuetify from 'vuetify'

Vue.use(Vuetify)
~~~~

You will also need to include the Vuetify css file. Simply include the Vuetify css file in your `index.html` or import the actual stylus file or the minified css.

~~~~
// index.js or main.js
import 'vuetify/dist/vuetify.min.css' // Ensure you are using css-loader
~~~~

~~~~
// main.styl
@import '~vuetify/src/stylus/main' // Ensure you are using stylus-loader
~~~~

## SweetAlert2
Instale SweetAlert2:
~~~~
npm install sweetalert2
~~~~
Uso:
~~~~
import Swal from 'sweetalert2';

Swal.fire('Olá!', 'Você está usando SweetAlert2', 'success');
~~~~

# 13. Gerenciamento de Estado

## Vuex
Instale Vuex:
~~~~
npm install vuex@next
~~~~
Configure o Vuex em `store.js`:
~~~~
import { createStore } from 'vuex';

export default createStore({
  state: {
    count: 0
  },
  mutations: {
    increment(state) {
      state.count++;
    }
  }
});
~~~~

## Pina
Instale Pina:
~~~~
npm install pina
~~~~
Configure Pina:
~~~~
import { createPinia } from 'pinia';

const pinia = createPinia();
export default pinia;
~~~~
No seu `main.js`:
~~~~
import { createApp } from 'vue';
import App from './App.vue';
import pinia from './pinia';

createApp(App).use(pinia).mount('#app');
~~~~

# Como Usar Vue.js com CDN
Aqui está um exemplo básico de como usar Vue.js em um projeto HTML com CDN:

## Incluir o Vue.js via CDN
Adicione o link para o Vue.js no seu arquivo HTML. Dependendo da versão que você deseja usar (Vue 2 ou Vue 3), o CDN pode variar.

### Para Vue 3:
~~~~
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vue 3 CDN Example</title>
  <!-- Vue 3 CDN -->
  <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
  <div id="app">
    {{ message }}
  </div>

  <script>
    const App = {
      data() {
        return {
          message: 'Hello, Vue 3 with CDN!'
        };
      }
    };

    Vue.createApp(App).mount('#app');
  </script>
</body>
</html>
~~~~

### Para Vue 2:
~~~~
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vue 2 CDN Example</title>
  <!-- Vue 2 CDN -->
  <script src="https://cdn.jsdelivr.net/npm/vue@2"></script>
</head>
<body>
  <div id="app">
    {{ message }}
  </div>

  <script>
    new Vue({
      el: '#app',
      data: {
        message: 'Hello, Vue 2 with CDN!'
      }
    });
  </script>
</body>
</html>
~~~~

## Explicação do Código

### Inclusão do Vue.js via CDN:
- Vue 3: `<script src="https://unpkg.com/vue@next"></script>`
- Vue 2: `<script src="https://cdn.jsdelivr.net/npm/vue@2"></script>`
Isso carrega o Vue.js diretamente da CDN, permitindo que você use o Vue.js sem instalação local.

### Estrutura HTML:

`<div id="app">`: O contêiner onde o Vue.js irá "montar" o aplicativo. O Vue.js controla o conteúdo dentro deste `div`.

### Script Vue.js:
- **Vue 3**:
~~~~
const App = {
  data() {
    return {
      message: 'Hello, Vue 3 with CDN!'
    };
  }
};
Vue.createApp(App).mount('#app');
~~~~
- **Vue 2**:
~~~~
new Vue({
  el: '#app',
  data: {
    message: 'Hello, Vue 2 with CDN!'
  }
});
~~~~
Aqui, você cria uma instância do Vue, define os dados e monta o aplicativo no elemento com `id="app"`.

### Recursos Adicionais
- **Vue.js 3 CDN**: `https://unpkg.com/vue@next` (ou `https://cdn.jsdelivr.net/npm/vue@next`)
- **Vue.js 2 CDN**: `https://cdn.jsdelivr.net/npm/vue@2` (ou `https://unpkg.com/vue@2`)
  
Usar o CDN é uma maneira prática de experimentar Vue.js e criar pequenos projetos rapidamente. 

***
O `v-on` é uma diretiva em Vue.js usada para ouvir e lidar com eventos no DOM. Pode ser utilizada para registrar ouvintes de eventos em elementos HTML, e você pode usar `v-on` para responder a eventos como cliques, mudanças, e outros tipos de eventos.

## Sintaxe Básica

A sintaxe básica do `v-on` é a seguinte:
~~~~
<button v-on:click="methodName">Clique aqui</button>
~~~~
Você também pode usar a forma abreviada `@`, que é equivalente a `v-on`:
~~~~
<button @click="methodName">Clique aqui</button>
~~~~

## Exemplos de Uso

### 1. Evento de Clique (`click`)
Quando um botão é clicado, o método `handleClick` é chamado.
~~~~
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Evento de Clique</title>
  <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
  <div id="app">
    <button @click="handleClick">Clique em mim</button>
    <p>{{ message }}</p>
  </div>

  <script>
    const App = {
      data() {
        return {
          message: 'Nenhum clique ainda.'
        };
      },
      methods: {
        handleClick() {
          this.message = 'Botão clicado!';
        }
      }
    };

    Vue.createApp(App).mount('#app');
  </script>
</body>
</html>
~~~~

### Evento de Mudança (`change`)
Quando o valor de um campo de entrada é alterado, o método `handleChange` é chamado.
~~~~
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Evento de Mudança</title>
  <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
  <div id="app">
    <input type="text" @change="handleChange" placeholder="Digite algo">
    <p>Valor atual: {{ inputValue }}</p>
  </div>

  <script>
    const App = {
      data() {
        return {
          inputValue: ''
        };
      },
      methods: {
        handleChange(event) {
          this.inputValue = event.target.value;
        }
      }
    };

    Vue.createApp(App).mount('#app');
  </script>
</body>
</html>
~~~~

## Vários Eventos e Modificadores

**Modificadores de Evento**
Você pode usar modificadores de eventos para simplificar o código e lidar com eventos de forma mais específica.

- `.prevent`: Chama `event.preventDefault()`.
- `.stop`: Chama `event.stopPropagation()`.
- `.capture`: Adiciona um ouvinte no modo de captura.
- `.once`: Remove o ouvinte após a primeira execução.
- `.passive`: Marca o ouvinte como passivo, indicando que não chamará `preventDefault()`.

**Exemplo com modificadores**:
~~~~
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Modificadores de Evento</title>
  <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
  <div id="app">
    <!-- Prevent default behavior of the event -->
    <a href="https://example.com" @click.prevent="handleClick">Não vá para o link</a>
    <!-- Stop the event from propagating further -->
    <button @click.stop="handleButtonClick">Clique aqui</button>
  </div>

  <script>
    const App = {
      methods: {
        handleClick() {
          console.log('Link clicado');
        },
        handleButtonClick() {
          console.log('Botão clicado');
        }
      }
    };

    Vue.createApp(App).mount('#app');
  </script>
</body>
</html>
~~~~

### Resumo

- `v-on`: Usado para ouvir e reagir a eventos em elementos DOM.
- **Sintaxe**:` v-on:evento="método"` ou a forma abreviada `@evento="método"`.
- **Eventos Comuns**: `click`, `change`, `input`, `submit`, entre outros.
- **Modificadores de Evento**: `prevent`, `stop`, `capture`, `once`, `passive`.
  
Esses conceitos ajudam a tornar seu aplicativo interativo e responsivo às ações do usuário.

# Prompt cgat gpt para gerar sistema co vue js
~~~~
Aja como um desenvolvedor experiente em Vue.js e um especialista em SEO e UI/UX. Sua tarefa é ajudar a criar uma aplicação moderna, reativa e performática do zero usando Vue.js 3, Bootstrap 5, Axios, SweetAlert2, Pinia e Vite. Forneça um guia passo a passo com instruções claras, adequado para desenvolvedores iniciantes. A aplicação deve ser responsiva e ter um design moderno e interativo, aplicando técnicas de SEO e UI/UX. Utilize recursos de Lifecycle Hooks e Composition API.

Objetivo da Aplicação:
Criar uma aplicação web moderna com design interativo e otimização para SEO.
[funcionalidades]

Ferramentas Utilizadas:
- Vue.js 3
- Bootstrap 5
- Axios
- SweetAlert2
- Pinia
- Vite

Funcionalidades Essenciais:
- Autenticação de Usuário: Sistema de login e registro de usuários.
- CRUD de Dados: Manipulação de dados como produtos, usuários ou posts.
- Integração com API: Conectar a APIs externas ou internas usando Axios.
- Notificações e Alertas: Utilizar SweetAlert2 para notificações de sucesso/erro e confirmações de ações.
- Navegação e Rotas: Configurar navegação entre múltiplas páginas principais (ex: home, perfil, dashboard).
- Formulários e Validações: Implementar formulários complexos com validações necessárias.
- Interatividade: Implementar elementos interativos como dropdowns, modais e carrosséis.
- Desempenho: Otimizar o tempo de carregamento e a performance da aplicação.
- SEO: Aplicar práticas de SEO como otimização de meta tags e uso de URLs amigáveis.

Estrutura do Guia:
Configuração do Ambiente de Desenvolvimento

Instalação e configuração do Vite:
Configuração inicial do projeto Vue.js com Bootstrap 5

Configuração e Estrutura do Projeto:
- Configuração do Vue Router para navegação
- Configuração do Pinia para gerenciamento de estado
- Estruturação de pastas e componentes

Desenvolvimento das Funcionalidades
- Implementação do sistema de autenticação de usuário
- CRUD de dados com Axios
- Utilização de Lifecycle Hooks e Composition API
- Integração do SweetAlert2 para notificações e alertas
- Desenvolvimento de formulários e validações
- Gerenciamento de estado com Pina

Design e Interatividade:
- Aplicação de Bootstrap 5 para design responsivo
- Implementação de elementos interativos (dropdowns, modais, carrosséis)
- Aplicação de técnicas de UI/UX para melhorar a experiência do usuário

Otimização de Desempenho
- Técnicas para melhorar o tempo de carregamento
- Otimização de imagens e outros recursos estáticos

SEO e Boas Práticas:
- Otimização de meta tags
- Configuração de URLs amigáveis
- Aplicação de outras técnicas de SEO
~~~~
