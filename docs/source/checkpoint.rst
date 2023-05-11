.. image:: /img/dependencies/checkpoint/checkpoint.png
	:scale: 20%
	:align: center

*******************************************
`Checkpoint <https://www.checkpoint.com/>`_ 
*******************************************

To make a proper Manager for `Checkpoint <https://www.checkpoint.com/>`_ appliances we need to understand the `Checkpoint <https://www.checkpoint.com/>`_ API. Helping us with that are the CCSA (`Checkpoint <https://www.checkpoint.com/>`_ Certified Security Administrator) and the CCSE (`Checkpoint <https://www.checkpoint.com/>`_ Certified Security Expert) courses, with whom we will be capable of understanding said API.
Besides the understanding, we need an environment fitting to the IP-Addresses coupled to the mandatory licenses for `Checkpoint <https://www.checkpoint.com/>`_ appliances.


.. ---------- CCSA Chapter 1 ----------

CCSA Chapter 1
--------------

In the first Chapter of CCSA you are introduced to the most basic concepts used in firewalling, like packet filtering or stateful inspection. Soon after the course introduces you to the GAIA operating system. It features a shell called CLISH (Command Line Interface Shell) and a web interface called Gaia Portal. Both will be used during the first Lab, where we execute simple configuration basics. 
Logging into Gaia Portal for the first time happens with the same credentials as your admin user created during installation. After that you are greeted with the following screen:

.. image:: /img/environment/checkpoint/checkpoint_01.png
	:scale: 100%
	:align: center
 
On the left you can see the different tabs and subtabs for purposes like managing users and roles, managing Gateways, setting IP-Address and DNS, time/timezone etc. Besides managing Gateways, all of the mentioned points are covered in the first lab. 
One major point that is not mentioned is licensing. As already said, `Checkpoint <https://www.checkpoint.com/>`_ appliances need licenses to work properly. To add a license you need something called SmartConsole, which is a “`Checkpoint <https://www.checkpoint.com/>`_ GUI application used to manage a Check Point environment”. You can install it onto a client from where you will be able to add licenses.
After playing around with Gaia Portal, the first lab also talks about the CLI of Gaia. It is divided into two different levels of privilege, the CLISH, which is the main shell of Gaia, and the expert mode, which is a BASH from where you are basically able to control everything. For this expert mode you are obliged to set a password with set expert-password:
 
.. image:: /img/environment/checkpoint/checkpoint_02.png
	:scale: 100%
	:align: center

After that you can enter expert mode with expert:

.. image:: /img/environment/checkpoint/checkpoint_03.png
	:scale: 100%
	:align: center 

**Complications concerning Chapter 1**

It was around now I noticed that something wasn´t right. As you may have noticed I changed onto the Gateway (as seen in the screenshots above => GW), but commands that were supposed to work didn´t work. After consulting Prof. Rabensteiner I took new VMs from our school share that were already installed and ready to go.

`Checkpoint <https://www.checkpoint.com/>`_ Environment
Before continuing with the lab, we want to be able to access the appliances all the time and not only during project class. To this point we run the VMs on one PC in school, but can´t leave it running because it´s obviously needed by other people too. To solve this problem, we have two possible solutions:

**First solution: Environment in the Schools DMZ**

As we already have a VPN into the DMZ for another class, it stands to reason that we set our environment up there. After talking to Prof. Hufsky, we have a good idea of how the topology needs to look like for our undertaking to work:

.. image:: /img/environment/checkpoint/checkpoint_04.png
	:scale: 100%
	:align: center
 
This is a somewhat trimmed version of the official CCSA Topology, but for our intents it is enough. The A-GUI and A-SMS both have a second leg into the school Network directly. The management server temporarily via reverse proxy for initial config and the Client to get a GUI via RDP. Because the A-SMS and A-GW01 are both vmware VMs, it could turn out to be rather inconvenient to put those into the network above.

**Second solution: Rent two PCs**

The simpler solution would be renting two PCs from school and one of the team taking them home to himself, from where he could reach the VMs all the time, but this has yet to be discussed with the professors.

 
