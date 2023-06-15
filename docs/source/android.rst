***********
Android App
***********

Functions
---------

- Basic device viewing
- Caching devices on a local database
- Basic config edits

Concept
-------

The Device Manager app is an Android application designed to provide users with a convenient way to manage their devices.
It allows users to view a list of their registered devices, as well as create new device entries. The app aims to simplify
device management tasks.

Overview
--------

**Current Main components:**

- Login Page
- Main Page
- Firewall Listing
- Firewall Creation
- Test Cases


Login Page
==========

The Login Page is for receiving an Token from the service that we access with the Api. It consists of 2 User Inputs where
the User provides an API-URL and an PSK so that we can try to receive our token over an API-Call.

.. figure:: /img/android/login_page.png
    :scale: 40%

Main Page
=========

In the Main Page we gain access to our device listing which is processed after we correctly pass the login page and
receive our token. Aswell as that there is another button which works as a Creation Button with which we can add Firewall
allready existing out there, to our listing over IP.

.. figure:: /img/android/main_page.png
    :scale: 40%

Device Listing
==============

The Device Listing works by sending an API-Listing-Call to our service so that the service responds which the known
firewalls which are listed inside the DB. These Firewalls are then Listed in the Main Page

.. figure:: /img/android/device_listing.png
    :scale: 40%

Device Creation
===============

The Device Creation is there for adding allready existing Firewalls into our Listing which we can access localy over IP.
Those Firewalls are then added to the DB which results in them being listed after Addition.

.. figure:: /img/android/device_creation.png
    :scale: 40%

Test Case
=========

In android Studio we have 3 different types of test cases, the Unit-Tests, The Instrumentation-Tests and the UI-Tests.
The Test Cases test to see if the Android app should properly work.

.. figure:: /img/android/test_cases.png
    :scale: 80%

.. figure:: /img/android/test_cases2.png
    :scale: 100%
