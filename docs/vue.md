##  documentação oficial
https://vuejs.org/

## criar projeto

`npm create vue@latest`

## rodar projeto

`npm run dev`

## publicar projeto

`npm run build`

## Vue UI
Vuetify can also be installed using Vue UI, the new visual application for vue-cli-3. Ensure that you have the latest version of vue-cli installed and from your terminal type:

~~~~
// ensure vue-cli is >= 3.0
$ vue --version

// Then start the UI
$ vue ui
~~~~

## adicionar bootstrap
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

## adicionar tailwind

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

## add vuetfy

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
