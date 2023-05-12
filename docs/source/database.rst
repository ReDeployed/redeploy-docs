.. image:: /img/dependencies/surrealdb/surrealdb.png
	:scale: 10%
	:align: center

********
Database
********

.. note::
   Given the nature of SurrealDB's development this page is subject to frequent change

.. ---------- SurrealDB ----------
.. image:: /img/dependencies/surrealdb/surrealdb_icon.png
	:scale: 20%
	:align: right
	:class: float
	:target: https://surrealdb.com

`SurrealDB <https://surrealdb.com>`_
------------------------------------

	"With an SQL-style query language, real-time queries with highly-efficient related data retrieval, advanced security permissions for multi-tenant access, and support for performant analytical workloads, `SurrealDB <https://surrealdb.com>`_ is the next generation serverless database."

From https://surrealdb.com

.. ---------- http ----------

`http <https://surrealdb.com/docs/integration/http>`_
-----------------------------------------------------

`SurrealDB <https://surrealdb.com>`_ allows Integration via HTTP&Rest without further configuration. These calls can be made by every relevant programming language and framework, including Android Apps build with `Kotlin <https://www.youtube.com/watch?v=XLgYKc_syBI>`_.

.. image:: /img/dependencies/thunder_client/thunder_client_icon.png
	:scale: 20%
	:align: right
	:class: float
	:target: https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client

.. ---------- Testing with Thunder Client ----------

Testing with `Thunder Client <https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client>`_
_________________________________________________________________________________________________________________

`Thunder Client <https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client>`_ allows us to send http requests from VisualStudio Code. We can use this to test the our code as well as the responsiveness of our database server.

Headers, Authentication Body of the request, the type of request and the hostname/IP address of the server can easily be set on the main screen. To save time, requests can be saved to become repeatable and presets containing non-changing settings like the hostname or authentication details can be created. 

.. image:: /img/database/http/thunder_client/thunder_client_usecase_01.png
	:scale: 70%
	:align: center

`SurrealDB's <https://surrealdb.com>`_ version can be obtained effortlessly by utilizing `Thunder Client <https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client>`_.
We can also get the Status Code (200 OK), response size (37 Bytes) and the time required (3 ms)

We can even use `Thunder Client <https://marketplace.visualstudio.com/items?itemName=rangav.vscode-thunder-client>`_ for automated tests. 

.. image:: /img/database/http/thunder_client/thunder_client_usecase_02.png
	:scale: 70%
	:align: center

These tests can be saved and repeated automatically as well. Setting them up requires only filling 3 fields.

.. ---------- Integration ----------

Integration
-----------

.. note::
	`Coming soon ... <https://www.youtube.com/watch?v=s-UFPhz2nZ0>`_
