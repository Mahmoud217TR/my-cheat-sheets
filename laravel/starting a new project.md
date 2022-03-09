# Starting new Laravel Project

## Create Laravel Project
- Open CMD and write `laravel new project-name`

## Preset Front-End (Vue & Bootstrap)
- In terminal write `composer require laravel/ui`
- Install vue setup `php artisan ui vue`
	* If you need authentication `php artisan ui vue --auth`
- Update vue version `npm install --save vue@next`
- Updating Vue loader version `npm install --save-dev vue-loader@next`
    * If Bootstrap version needs upadate `npm install bootstrap@next --save-dev`
- Install node modules `npm install`
- Upadate popperjs for Bootstrap `npm install @popperjs/core --save-dev`
- Update Laravel Mix `npm install laravel-mix@latest --save-dev`
- Compile Styles `npm run dev`
- If an error Accorded you may need to update vue loader `npm update vue-loader` or `npm i vue-loader`
    * Recompile Styles `npm run dev`
- After **Everything is working Fine** there are 2 main things to make sure of:
	* The app.js file is like this:
        ```javascript
        require('./bootstrap');
		window.Vue = require('vue').default;
		import { createApp } from 'vue';
		
		let app=createApp({})
		app.component('example-component', require('./components/ExampleComponent.vue').default);
		app.mount("#app");
        ```
	* In your main app view there is a div where `id = 'app'`