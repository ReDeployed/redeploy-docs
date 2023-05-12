.. image:: /img/logo/redeploy_logo_full.png
	:scale: 20%
	:align: center

**************
About ReDeploy
**************

The Big Picture
===============

Flowchart
---------

To quickly understand how ReDeploy operates, consult the flowchart below:

.. figure:: /img/flowchart.png
    :scale: 60%

How it works
------------

The entire stack is meant to be fully dockerized. It consists of to containers, namely the DB container and the Web container.
These two interact via the internal docker network. The DB traffic itself never leaves this network and is also mapped to no host port.
We primarly use the DB for caching, to reduce network traffic to the actual endpoints and speed things up even if there are more devices
to manage. The goal is to fetch fresh data as few times as possible and use cache data whenever we can.

The Web Container has direct API communications with the Gaia Management Server, which are handled by the Svelte backend. It also provides
it's own API endpoint which can be accessed by clients (in this case our Android App uses it).
As mentioned above, the Web Container communicates with the DB, to cache the data it recieves via the direct API calls to the Mangement
Server.

What it does
------------

Checkpoint itself already provides good bulk management via SmartConsole and the actual Management Server itself. What it doesnt really
do really good however, is **Bulk Deployment**. And this is what ReDeploy's main focus is.

Once finished, it should be possible to use our interface to check on all firewalls and quickly deploy configs to multiple firewall
instances at once. How many options will be integrated in our interface remains a subject to change for now.

Component Choices
=================

.. ---------- SurrealDB ---------- 

SurrealDB
---------

.. image:: /img/dependencies/surrealdb/surrealdb_icon.png
	:scale: 10%
	:align: right
	:class: float
	:target: https://surrealdb.com

*New, SQL-Like, scalability, cloud-ready, serverless, In-Memory, cloud ready, embedded and lightning quick setup* 

SurrealDB is far from being complete. Yet, it offers functions, methods and workflows that are not provided by a single other database. 

**Setup**

Starting SurrealDB can be done in a single line:

.. code-block:: js
	:caption: Installing SurrealDB

	curl --proto '=https' --tlsv1.2 -sSf https://install.surrealdb.com | sh -s -- --nightly

Alteratively, SurrealDB can be started using Docker

.. code-block:: js
	:caption: Downloading SurrealDB

	docker run --rm --pull always -p 8000:8000 surrealdb/surrealdb:nightly start

**Running in memory**

Starting SurrealDB like above, the database is run in memory and does not take up any storage. This is perfect for testing purposes. Of course, normal usage of the database is also possible. 

**Schemaless**

SurrealDB can receive schemaless Data. This means that queries do not have to conform to table designs. 

**Why we use it**

This was a rather quick decision, with the main focus on *"Hey, let's just try something new?"*. Of course we could have just chosen any
generic database, especially for this project that only really uses it for caching purposes. But this is exactly where on factor matters
the most: **Speed**

With SurrealDB being a relatively new database written in Rust, it can definitely deliver when it comes to speed. It also has many other
features, which we didn't even scratch the surface of yet, simply because we won't really need them.

The downside to choosing this DB is however, that due to its early beta-stage, there are still some issues and the client/server libraries
are missing things that we have to implement ourselves.

.. ---------- Astro ---------- 

Astro
-----

.. image:: /img/dependencies/astro/astro-logo-dark.png
	:scale: 20%
	:align: right
	:class: float
	:target: https://astro.build/

We want to keep things fast, so we opted for Astro. We don't think there is currently a better way to develop web apps as quickly as you
can with Astro. And most importantly you can use existing frameworks and languages you already know and love. It supports server-side
rendering as well.

.. ---------- Deno ---------- 

Deno
----

.. image:: /img/dependencies/deno/deno.png
	:scale: 6%
	:align: right
	:class: float
	:target: https://deno.land/

As mentioned above, for server-side rendering, you need a proper adapter. And as everybody hates node.js anyways, why not choose something
better and new? This is where Deno comes in (also written in Rust), which features speed and security improvements compared to node.js for
example.

.. ---------- Svelte ---------- 

Svelte
------

.. image:: /img/dependencies/svelte/svelte_icon.png
	:scale: 6%
	:align: right
	:class: float
	:target: https://svelte.dev/

Even though we could exclusively use Astro syntax for our application, for more complex tasks we chose Svelte. This was also rather a quick
decision, as none of us really learned a JS-Framework up until now, so we chose what was best recommended by the community and aquired the
necessary knowledge for it.

.. ---------- Checkpoint ---------- 

Checkpoint
----------

.. image:: /img/dependencies/checkpoint/checkpoint.png
	:scale: 6%
	:align: right
	:class: float
	:target: https://www.checkpoint.com/

As this project serves as a predecessor for an upcoming project, where we will focus on a different brand of firewalls, we had to choose
something other than that for now. Our school is partnered with CheckPoint and we need to learn it next year anyways, so why not focus our
app around it?

The thing is that CheckPoint already provides some features for mass configuration and building another wrapper around the management
server might be a bit overkill. But things can always be improved if there is an API for it, so we will primarly focus on bulk deployment.
