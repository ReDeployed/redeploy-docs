
Web Design
==========
.. ---------- Concept ----------

Concept
-------

For the frontend of our web application, we use `Astro <https://astro.build/>`_, a modern static site generator that enables dynamic components and client-side rendering, making it an ideal choice for building performant and scalable web applications. We complement `Astro <https://astro.build/>`_ with `Svelte <https://svelte.dev/>`_ as our frontend framework, which emphasizes small bundle sizes and fast performance, allowing us to build reactive user interfaces and single-page applications. For our backend, we use `Svelte <https://svelte.dev/>`_.js, which is typically used as a frontend framework, but can also be used on the backend with Sapper or other similar frameworks. `Svelte <https://svelte.dev/>`_.js allows us to build reactive and scalable applications on both the frontend and backend. Additionally, we use `Deno <https://deno.land/>`_, a secure runtime for JavaScript and TypeScript that allows us to build server-side applications with ease. `Deno <https://deno.land/>`_ provides built-in security features and a modern JavaScript API, making it an excellent choice for building secure and performant server-side applications.

.. ---------- Frameworks ----------

JavaScript Frameworks and their Advantages
------------------------------------------

JavaScript frameworks like `Astro <https://astro.build/>`_ and `Svelte <https://svelte.dev/>`_ simplify the process of building web applications by providing a powerful set of tools and abstractions. `Astro <https://astro.build/>`_ is a modern static site generator that allows for dynamic content, while `Svelte <https://svelte.dev/>`_ is a reactive frontend framework for building high-performance applications. These frameworks offer improved productivity, maintainability, and performance, resulting in consistent, maintainable codebases that are easier to work with and debug. By using these frameworks, developers can build engaging web applications and provide a better user experience for their users.

.. ---------- Overview of the Project ----------

Overview of the Project
-----------------------

**Current Main components:**

	- `Astro <https://astro.build/>`_
	- `Svelte <https://svelte.dev/>`_
	- `Deno <https://deno.land/>`_

.. ---------- Astro ----------
.. image:: /img/dependencies/astro/astro-logo-dark.png
	:scale: 20%
	:align: right
	:class: float
	:target: https://astro.build/

`Astro <https://astro.build/>`_
-------------------------------

**How we use Astro**

On average a basic `Astro <https://astro.build/>`_ project consists of these following files and their folders. Their importance and uses will be explained briefly:

.. image:: /img/webdesign/folderstructure/folderstructure_01.png
	:scale: 100%
	:align: center

**folder public**

This is one of the simpler folders, because it is only used to store file, media sources or fonts. These will then later be access through other files and only located in the public folder for ease of use.

.. image:: /img/webdesign/folderstructure/folderstructure_02.png
	:scale: 100%
	:align: center

**folder src**

This folder contains the source code for your application, including HTML, CSS, and JavaScript files. It is the main folder where you do most of your development work. This folder splits into 3 important sub-folders

**sub-folder pages**

This folder contains the top-level pages of your application. Each file in this folder corresponds to a route in your application, and the file name determines the URL of that route. For example, src/pages/index.`Astro <https://astro.build/>`_ corresponds to the root route of your application (/).

.. image:: /img/webdesign/folderstructure/folderstructure_03.png
	:scale: 100%
	:align: center

Here is an example of our index.astro file:

.. image:: /img/webdesign/files/astro/astroconfigmjs.png
	:scale: 100%
	:align: center

**sub-folder layouts**

This folder contains the layout templates for your application. Layout templates define the overall structure and style of your application, and they can be reused across multiple pages. Layout templates can also be nested, allowing for more complex layouts to be created.

.. image:: /img/webdesign/folderstructure/folderstructure_04.png
	:scale: 100%
	:align: center
 
Our current Layout.Astro looks something like this:

.. image:: /img/webdesign/files/astro/layout.png
	:scale: 100%
	:align: center

**sub-folder components**

This folder contains the reusable UI components of your application. Components are small, self-contained pieces of code that can be used throughout your application, making it easier to maintain and update your codebase. Components can be shared across pages and layouts and can also be customized for specific use cases. These Components can then later be used in the pages mentioned above to get their entire content listed on the pages. Pretty darn simple right?

.. image:: /img/webdesign/folderstructure/folderstructure_05.png
	:scale: 100%
	:align: center

As you can probably already see there is different kind of file extension with an even more interesting one the apicalls.http one. These Files have their original syntax so there is no need to try to change them into the `Astro <https://astro.build/>`_ syntax:

.. image:: /img/webdesign/files/astro/syntax.png
	:scale: 100%
	:align: center

**file astro.config.mjs**

The astro.config.mjs file is used to configure `Astro <https://astro.build/>`_, the modern static site generator, for your project. This file allows you to customize various aspects of your `Astro <https://astro.build/>`_ project, such as configuring the build process, adding plugins, setting up server-side rendering, and defining environment variables. This file is a powerful tool for customizing and optimizing your `Astro <https://astro.build/>`_ project. By using this file, you can fine-tune your application to meet your specific needs and ensure that it performs optimally.

.. image:: /img/webdesign/files/astro/astroconfigmjs.png
	:scale: 100%
	:align: center

**file package.json**

The package.json file is a configuration file that is used by `Astro <https://astro.build/>`_ (and other Node.js-based projects) to manage dependencies and scripts for your project. In a basic `Astro <https://astro.build/>`_ project, the package.json file typically includes the following:
	- name: The name of your project.
	- version: The version of your project.
	- description: A brief description of your project.
	- keywords: An array of keywords that describe your project.
	- author: The name of the author(s) of your project.
	- license: The license under which your project is released.
	- dependencies: A list of dependencies required by your project, including `Astro <https://astro.build/>`_ itself and any other third-party packages you might be using.
	- devDependencies: A list of development dependencies required by your project, such as testing frameworks, build tools, or other utilities.

.. image:: /img/webdesign/files/astro/packagejson.png
	:scale: 100%
	:align: center

In addition to these basic properties, the package.json file can also include custom scripts that are used to automate common tasks in your project, such as building the application, running tests, or deploying to production.
Overall, the package.json file is an essential part of any `Astro <https://astro.build/>`_ project, as it allows you to manage your dependencies and configure your project in a standardized and repeatable way. By using the package.json file, you can ensure that your project is easily reproducible, and that other developers can quickly get up and running with your codebase.

.. ---------- SVELTE ----------
.. image:: /img/dependencies/svelte/svelte_icon.png
	:scale: 10%
	:align: right
	:class: float
	:target: https://svelte.dev/

`Svelte <https://svelte.dev/>`_
-------------------------------

**How we use Svelte**

`Svelte <https://svelte.dev/>`_ is a modern JavaScript framework for building web applications. Unlike other frameworks that run in the browser, `Svelte <https://svelte.dev/>`_ compiles your application into highly efficient vanilla JavaScript code that runs faster and takes up less space, resulting in better performance and a smaller file size.

.. ---------- DENO ----------
.. image:: /img/dependencies/deno/deno.png
	:scale: 10%
	:align: right
	:class: float
	:target: https://deno.land/

`Deno <https://deno.land/>`_
----------------------------

**How we use Deno**

`Deno <https://deno.land/>`_ can be used in combination with `Astro <https://astro.build/>`_ to provide server-side functionality for your web application. `Astro <https://astro.build/>`_ supports serverless functions, which are essentially small JavaScript scripts that run on the server and can perform tasks such as processing form data, accessing a database, or calling an external API.
To use `Deno <https://deno.land/>`_ with `Astro <https://astro.build/>`_ and serverless functions, you can write your server-side code in `Deno <https://deno.land/>`_ and define a serverless function that handles incoming requests and returns the response. You can then use this serverless function in your `Astro <https://astro.build/>`_ components to fetch dynamic data and render content.


.. ---------- Overview of the Website ----------

Overview of the Website
-----------------------

**Current Look of the WebPage**

	-	Home
	-	Config
	-	Status

.. ---------- Home ----------

Home
----

**The purpose of this site**

This is just a simple page that welcomes the user to the Re:Deploy Firewall manager and gives a quick Introduction into the firewall manager and what it does. The current look of it is this.

.. image:: /img/webdesign/design/design_01.png
	:scale: 100%
	:align: center

.. ---------- Config & Status ----------

Config & Status
---------------

**The purpose of this site**

The Config Page is for the configuration of the devices and general overview. The Status Page is for checking the Status of the SerialDB. Their current Look is this.

.. image:: /img/webdesign/design/design_02.png
	:scale: 100%
	:align: center