# Starting new Laravel Project with vite

**Table of Contents:**
* [Laravel & Vue with vite](#laravel--vue-with-vite)

## Laravel & Vue with vite

1. Install the Laravel Project:

```
laravel new project-name
```

2. Install Laravel ui and setting up Vue UI:

```
composer require/laravel ui

php artisan ui vue --auth
```

4. Update Packages:

```
npm i vue@next
npm i @vitejs/plugin-vue
npm i 
```

5. Edit Vite Config file `vite.config.js`:

```js
import { defineConfig } from 'vite';
import laravel from 'laravel-vite-plugin';
import vue from '@vitejs/plugin-vue';

export default defineConfig({
    plugins: [
        vue(),
        laravel([
            'resources/js/app.js',
        ]),
    ],
});
```

6. Edit the `bootstrap.js` file:

```js
import _ from 'lodash';
window._ = _;


import axois from 'axios';
window.axios = axois;

window.axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest';
```

7. Edit `app.js` file:

```js
import './bootstrap';
import '../sass/app.scss';

import {createApp} from 'vue/dist/vue.esm-bundler.js';

import test from './components/ExampleComponent.vue';

let app = createApp({});

app.component('example-component', test);
app.mount('#app');
```

8. Edit `app.scss` file:

```scss
// Fonts
@import url('https://fonts.googleapis.com/css?family=Nunito');

// Variables
@import 'variables';

// Bootstrap
@import 'bootstrap/scss/bootstrap';
```

9. Remove Unneeded scripts and styles form `app.blade.php` file and add the vite directive:

```blade
@vite('resources/js/app.js')
```

**And now you are good to go**