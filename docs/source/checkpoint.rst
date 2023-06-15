.. image:: /img/dependencies/checkpoint/checkpoint.png
	:scale: 20%
	:align: center

*******************************************
`Checkpoint <https://www.checkpoint.com/>`_ 
*******************************************

To make a proper Manager for `Checkpoint <https://www.checkpoint.com/>`_ appliances we need to understand the
`Checkpoint <https://www.checkpoint.com/>`_ API. Helping us with that are the CCSA (`Checkpoint <https://www.checkpoint.com/>`_
Certified Security Administrator) and the CCSE (`Checkpoint <https://www.checkpoint.com/>`_ Certified Security Expert) courses,
with whom we will be capable of understanding said API. Besides the understanding, we need an environment fitting to the IP-Addresses
coupled to the mandatory licenses for `Checkpoint <https://www.checkpoint.com/>`_ appliances.

Complications
=============

It was around now I noticed that something wasn´t right. As you may have noticed I changed onto the Gateway (as seen in the screenshots
above => GW), but commands that were supposed to work didn´t work. After consulting Prof. Rabensteiner I took new VMs from our school
share that were already installed and ready to go.

`Checkpoint <https://www.checkpoint.com/>`_ Environment
Before continuing with the lab, we want to be able to access the appliances all the time and not only during project class. To this
point we run the VMs on one PC in school, but can´t leave it running because it´s obviously needed by other people too. To solve this
problem, we have two possible solutions:

**First solution: Environment in the Schools DMZ**

As we already have a VPN into the DMZ for another class, it stands to reason that we set our environment up there. After talking to
Prof. Hufsky, we have a good idea of how the topology needs to look like for our undertaking to work:

.. figure:: /img/checkpoint/checkpoint_04.png
 
The A-GUI and A-SMS both have a second leg into the school Network directly. The management server temporarily via reverse proxy for
initial config and the Client to get a GUI via RDP. Because the A-SMS and A-GW01 are both vmware VMs, it could turn out to be rather
inconvenient to put those into the network above.

**Second solution: Rent two PCs**

The simpler solution would be renting two PCs from school and one of the team taking them home to himself, from where he could reach
the VMs all the time, but this has yet to be discussed with the professors.

**Final Solution: Run it locally**

It might sound contradictory at first, but it is the most efficient way of running the Checkpoint environment. As prices for RAM are
very low at the moment, everyone in the team (who hadn´t had it before) was able to upgrade their RAM to 32GB, which is recommended
to guarantee smooth usage of the VMs. Instead of having one instance that is available to everyone, a template instance is created,
from which everyone takes a copy. Now, if there is any problem with the instance, it is possible to just create a new instance ready
to use.

At the moment, the environment looks like the following:

.. figure:: /img/checkpoint/checkpoint_05.png

API Requests
============

To make the Firewall Manager interact with the appliances, we need the API. Checkpoint has different APIs for different usecases, relevant for us are only the GAIA API and the Management API. The latter of them is for, as you may have guessed by the name, executing management calls via the management server. Therefore with this one we will only be able to interact with said management server. The GAIA API is the somewhat most fundamental one, because it interacts with the OS of the Checkpoint appliance, Gaia, directly.
For example, to make a basic request for the hostname of an appliance via the GAIA API:

- First, we need to get the sid

.. code::

    CHKP_SID=$(curl -s -k -X POST -H "Content-Type:application/json" -d '{"user":"admin","password":"p@ssw0rd"}' https://10.1.1.101/gaia_api/login | jq '.sid' | tr -d '"')

- Then, we can get the hostname

.. code::

    curl -s -k -X POST -H "X-chkp-sid:${CHKP_SID}" -H "Content-Type: application/json" -d "{}" https://10.1.1.101:443/gaia_api/v1.5/show-hostname | jq

.. note::
    The `{}` is important, because else the Checkpoint appliance doesn´t know where to store the response.
    In general the CheckPoint API can be very, very specific about what the request body contains

**Integration**

Using deno, we now need to implement functions, that make such API calls. In this case, async functions are used, which first seems counterproductive, but is necessary for the Database to properly process the responses. These functions are stored in the ChkpHandler.js file under core/deno-src/src
In essence, there are three different types of API-call functions:
- SID get function 
- get-functions
- set-functions

**SID get function**

In order to make successful calls, a session-ID (=SID) has to be acquired. This is done through the following function:

.. image:: /img/checkpoint/sid_get_functions.png
	:scale: 100%
	:align: center

This is just the curl, that is earlier used to get the SID, put into a function. We store the response in the chkpSid variable, and then just return the sid Object. This is also the only function, where the username and the password have to be provided, every other one only needs the SID.

**get functions**

The get functions are mostly the same as the SID get function, with the difference, that in most cases the POST body stays empty and, as already mentioned, the SID is passed. For example, the function to get the version of the appliance:

.. image:: /img/checkpoint/get_functions.png
	:scale: 100%
	:align: center

Here, the whole JSON response is returned because there is no need to strip it. All the implemented get functions are:
- getVer()
- getHostname()
- getAllInterfaces()
- getInterface()
- Body: the specific interface has to be provided
- getStaticRoutes()
- getDiagnostics()
- Body: cpu/memory/disk has to be provided, to specify which diagnostics are to be shown

**Testing**

To make sure the functions return the desired content, testing is of course mandatory. Therefore an own folder, named checkpoint-testing, is created, wherein multiple TypeScript files lay, one for every async function. For example, to test getting the diagnostics of a Check Point appliance:

.. image:: /img/checkpoint/test.png
	:scale: 100%
	:align: center

First, a SID is needed to proceed. Then, the getDiagnostics function is called three times for CPU status, memory status and disk status. If successful, the JSONs of said three will be shown in the console. Every other TypeScript testfile is build similarly. 