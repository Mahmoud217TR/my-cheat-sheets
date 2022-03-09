# Starting new Laravel Project

## Create Laravel Project
- Open CMD and write `laravel new project-name`

## Preset Front-End (Vue & Bootstrap)
- in terminal write `composer require laravel/ui`
- install vue setup `php artisan ui vue`
	* if you need authentication `php artisan ui vue --auth`
- update vue version `npm install --save vue@next`
- updating Vue loader version `npm install --save-dev vue-loader@next`
    * if Bootstrap version needs upadate `npm install bootstrap@next --save-dev`
- install node modules `npm install`
- upadate popperjs for Bootstrap `npm install @popperjs/core --save-dev`
- update Laravel Mix `npm install laravel-mix@latest --save-dev`
- compile Styles `npm run dev`
- if an error Accorded you may need to update vue loader `npm update vue-loader` or `npm i vue-loader`
    * recompile Styles `npm run dev`
- after **Everything is working Fine** there are 2 main things to make sure of:
	* the app.js file is like this:
        ```javascript
        require('./bootstrap');
		window.Vue = require('vue').default;
		import { createApp } from 'vue';
		
		let app=createApp({})
		app.component('example-component', require('./components/ExampleComponent.vue').default);
		app.mount("#app");
        ```
	* in your main app view there is a div where `id = 'app'`