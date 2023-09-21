# How to Integrate Syncfusion EJ2 Vue Components in Laravel project
The following steps is used to Integrate Syncfusion EJ2 Vue Rich Text Editor in Laravel using Vite.

Skip to the getting started section if you have already configured the environment.

## Prerequisites

Before getting started with Syncfusion Vue Rich Text Editor component in Laravel using Vite, check whether the following are installed in the developer machine.
* [PHP](https://www.php.net/downloads.php) - To download PHP.
* [Node.js](https://nodejs.org/en/download/) - To download Node.js.
* [Laravel](https://laravel.com/docs/8.x/installation) - To install Laravel.
* [Composer](https://getcomposer.org/download/) - To install Composer.
* [Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project) - To install Vite.

## Setting up the environment

#### For Windows users

### 1. Install PHP

* Download the PHP from the [official website](https://windows.php.net/download#php-8.2).

### 2. Install Composer

* Download the Composer from the [official website](https://getcomposer.org/download/).

### 3. Install Laravel

* Open the command prompt and run the following command to install Laravel.

```bash
composer global require laravel/installer
```

## Create a Laravel project


#### For Windows users

```bash
laravel new example-app
```

Now change the directory to the example-app folder.

```bash
cd example-app
```


## Getting started from Laravel Project
This section describes how to add the React, EJ2 Components from scratch to the Laravel Project.

### 1. Install dependencies
In the command prompt, run the following commands to install the dependencies.

Install the dependencies of the laravel project.
```bash
composer install
```
If you are getting any error while installing the dependencies, run the following command.
```bash
composer install --ignore-platform-req=ext-fileinfo
```

Install the vue js dependencies.
```bash
npm install vue@next @vitejs/plugin-vue
```
Install the Syncfusion EJ2 Vue Rich Text Editor package.
```bash
npm install @syncfusion/ej2-vue-richtexteditor
```

### 2. Configure the vite.config.js file
Add the following code to the vite.config.js file in the root directory of the project.
```js
import { defineConfig } from "vite";
import laravel from "laravel-vite-plugin";
import vue from "@vitejs/plugin-vue";

export default defineConfig({
  plugins: [
    laravel({
      input: ["resources/css/app.css", "resources/js/app.js"],
      refresh: true,
    }),
    vue({
      template: {
        transformAssetUrls: {
          base: null,
          includeAbsolute: false,
        },
      },
    }),
  ],
});
```
### 3. Add the root element to the welcome.blade.php file
Add the root element to the welcome.blade.php file in the resources/views folder.
``` html
<!DOCTYPE html>
<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">

        <title>Laravel</title>

        <!-- Fonts -->
        <link rel="preconnect" href="https://fonts.bunny.net">
        <link href="https://fonts.bunny.net/css?family=figtree:400,600&display=swap" rel="stylesheet" />
        
        @vite(['resources/js/app.js', 'resources/css/app.css'])
        <!-- Styles -->
        <link href="https://cdn.syncfusion.com/ej2/material.css" rel="stylesheet">
    </head>
    <body class="antialiased">
        <div id="app"></div>
    </body>
</html>

```

### 4. Add the following code to the app.js file to mount the Vue application
```js
import { createApp } from "vue";
import Welcome from "./Welcome.vue";

createApp(Welcome).mount("#app");
```

### 5. Create a Welcome.vue file in the resources/js folder and add the following code
```vue

<template>
    <div>
        <div class="control-section">
        <div class="sample-container">
            <div class="default-section">
            <div id="defaultRTE">
                <ejs-richtexteditor id="default" ref="rteInstance">
                <p>The Rich Text Editor component is a WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
                </ejs-richtexteditor>
            </div>
            </div>
        </div>
        </div>
    </div>
</template>
<script>
import { RichTextEditorComponent, Toolbar, Link, Image, HtmlEditor, Table } from "@syncfusion/ej2-vue-richtexteditor";

export default {
  name: "App",
  components: {
    "ejs-richtexteditor": RichTextEditorComponent,
  },

  data: function () {
    return {};
  },
  methods: {},
  provide: {
    richtexteditor: [Toolbar, Link, Image, HtmlEditor, Table],
  },
};
</script>

```
## Run the Project
To run the project run the following commands.

### 1. Build the project
To build the project, run the following command.
```bash
npm run build
```

### 2. Generate Key

This section is only needed If the project is cloned from github.

```bash
php artisan key:generate
```

### 3. Run the project
To run the project, run the following command.
```bash
php artisan serve
```

Visit http://localhost:8000 in your browser to see the Laravel application with the integrated Syncfusion EJ2 React Rich Text Editor.
