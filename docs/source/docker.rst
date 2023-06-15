******
Docker
******

Layout
------

To securely get data where it needs to go, we chose to change our original Container Layout

.. figure:: /img/docker/old-lay.png
    :scale: 80%

To someting more like this

.. figure:: /img/docker/new-lay.png
    :scale: 80%

The Changes
-----------

As mentioned on other pages, the heavy lifter is the Deno Fetching Container. It handles most of the API Communication
and also decision making on when to fetch data or use cached data. We decided to not do this stuff in the Svelte backend
simply because we wanted that extra separation.
One can also spot the added Reverse Proxy, which encrypts traffic that isn't already encrypted. This plays an important
part, especially for data that leaves our internal docker network.

Components
----------

Compose File
============

.. figure:: /img/docker/compose.png
    :scale: 80%

A multi-container consisting of four services: proxy, astro, surreal, and deno. The services are deployed within a seperate 
Docker network. The proxy service is based on the latest Nginx image and serves as a reverse proxy. It listens on ports 80
and 443 for HTTP and HTTPS.

All other services are based on seperate Dockerfiles

Deno
====

.. figure:: /img/docker/denodocker.png
    :scale: 80%

Self Explanatory

Astro
=====

.. figure:: /img/docker/astrodocker.png
    :scale: 70%

This also runs with a deno base image, because we run the Web Interface with SSR enabled, which needs a deno adapter.

Surreal
=======

.. figure:: /img/docker/surrealdocker.png
    :scale: 80%

Self Explanatory
