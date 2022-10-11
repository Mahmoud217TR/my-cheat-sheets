# Starting new Laravel Project

**Table of Contents:**
* [Create Laravel Project](#create-laravel-project)
* [Preset Front-End (Vue & Bootstrap)](#preset-front-end-vue--bootstrap)
* [Preset Front-End (Vue & Bootstrap)(Old)](#preset-front-end-vue--bootstrap-old)

## Create Laravel Project
- Open CMD and write `laravel new project-name`


## Preset Front-End (Vue & Bootstrap & Tailwind)
- In terminal write `composer require laravel/ui`
- Install vue with authentication `php artisan ui vue --auth`
- Install Tailwindcss `npm install -D tailwindcss postcss autoprefixer laravel-mix-tailwind`
- Init Taiwlwind `npx tailwindcss init`
- Install Vue Packages `npm install vue-loader vue-template-compiler axios-vue @popperjs/core --save-dev`
- Update vue version `npm install --save vue@next`
- Updating Vue loader version `npm install --save-dev vue-loader@next`
- Update Laravel Mix `npm install laravel-mix@latest --save-dev`
- Install All Packages `npm install`
	* If any vulnerabilities were found use `npm audit fix`
- Config Files:
	* webpack.mix.js :
	```javascript

	const mix = require('laravel-mix');
	require("laravel-mix-tailwind");

	/*
	 |--------------------------------------------------------------------------
	 | Mix Asset Management
	 |--------------------------------------------------------------------------
	 |
	 | Mix provides a clean, fluent API for defining some Webpack build steps
	 | for your Laravel application. By default, we are compiling the Sass
	 | file for the application as well as bundling up all the JS files.
	 |
	 */

	mix.js('resources/js/app.js', 'public/js')
	    .vue()
	    .tailwind("./tailwind.config.js")
	    .sass('resources/sass/app.scss', 'public/css');

	```
	
	* app.js
	```javascript

	require('./bootstrap');
	window.Vue = require('vue').default;
	import { createApp } from 'vue';

	let app=createApp({})
	app.component('example-component', require('./components/ExampleComponent.vue').default);
	app.mount("#app");

	```
	
- Run development command `npm run dev`


## Preset Front-End (Vue & Bootstrap)
- In terminal write `composer require laravel/ui`
- Install vue with authentication `php artisan ui vue --auth`
- Install Packages `npm install`
- Install Other Packages `npm install vue-loader vue-template-compiler axios-vue @popperjs/core --save-dev`
	* If any vulnerabilities were found use `npm audit fix`
- Run development command `npm run dev`


## Preset Front-End (Vue & Bootstrap) (Old)
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
