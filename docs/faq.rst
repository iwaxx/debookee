.. include:: global.rst

.. title:: FAQ

.. _faq:

Debookee
========

Does network traffic interception always work in NA module?
-----------------------------------------------------------
**No.**

Network Analysis (NA) module allows you to select targets and intercept their traffic through a Man-in-the-middle attack (ARP spoofing).

On wired networks, this will almost always work.
We’ve seen some situations where the traffic was only half intercepted, in that case you’ll have only some traffic like only DNS answers, but no requests from your targets.

On professional wireless networks (Aruba, Cisco, HP…), this interception will likely fail due to Proxy ARP or security features that detect the MITM.
In that case, you won’t see any traffic under your target menu. We suggest to set up a mobile hotspot or connect to another network in that case.

We recommend to always try the free trial of Debookee NA module to check if your network allows network traffic interception or not.


Will you sell Debookee on Mac App Store?
----------------------------------------
Unfortunately not: the library used to capture packets needs admin privileges, which are forbidden by Mac App Store guidelines.

This elevation of privileges is made following Apple’s standard API: at no point will we have knowledge of your password. 


Beta version is buggy, how do I revert to last stable version?
--------------------------------------------------------------
First, please explain us clearly what is going wrong with an email at support@iwaxx.com with some details and screenshots.
A beta version is supposed to go in a stable state, and we need to fix bugs. So please help us by reporting problems before using the stable version.

    * Go in menu ``Help -> Uninstall Packet Capture Tool``
    * Delete the beta application
    * Download last stable version from https://debookee.com
    * Keep checked “Propose beta version updates”!


What are the limitations of the free trial?
-------------------------------------------
The code is exactly the same: all functionalities are included in the free trial and you can try all of them: interception of traffic, Wi-Fi monitoring, VoIP plugin, SSL decryption, etc...

The only difference is that some results will be obfuscated at some point in the demo version.

You’ll need a license to display all results.


Can I use a VPN connection on the Mac running Debookee?
-------------------------------------------------------
Currently, Debookee can’t handle different interfaces which is the case when a VPN connection is established. (virtual or not)

Packets will be intercepted from ethernet or airport interface and then sent to the gateway/internet through the VPN interface.

But the response packets will be received on the VPN interface (tun, ppp) on which Debookee is not listening too, and thus ignored and dropped.

As a result, intercepted devices will stop working properly.

I don't need Debookee, I use Wireshark.
---------------------------------------
We love `Wireshark <https://www.wireshark.org>`_ too! So much that we included it in Debookee.

NA & WM modules use Lua scripts & tshark and we worked with Wireshark core dev team during `SharkFest 2015 <https://sharkfest.wireshark.org/>`_ to integrate the whole stuff, while respecting their open source license.

But wait. Don't throw away Debookee directly, if you want to see raw data of your mobiles or IoT things, maybe you'll be interested in :ref:`module_na_dbk_and_wireshark`, because Wireshark alone will show you your own traffic, it can't intercept traffic of other devices on your network like NA module.


I've installed the certificate on iOS but iPhone/iPad traffic is still not decrypted?
-------------------------------------------------------------------------------------
You've correctly :ref:`installed the root certificate <module_ssl_ca_install>` on iOS if you see Debookee's certificate in ``General -> Profile`` on your iPhone/iPad.

**Additionally, for iOS version 10.3 and later**, you also need to manually enable full trust for that certificate. |br|
Make sure Debookee's CA is also enabled in ``Settings > General > About > Certificate Trust Settings``

Check out this `Apple's FAQ <https://support.apple.com/en-ca/HT204477>`_ for more information.


LanScan on AppStore
===================

I've bought LanScan Pro In-App, but free trial always appears?
--------------------------------------------------------------

If In-App is really purchased, this is an App Store issue.

Try to restore the purchase in LanScan: Buy Pro version -> Restore previous purchase

If it doesn't work:

#. Be sure that you're signed into App Store: you must have access to your account without password (Store -> View My Account)
#. Be sure you see your In-App purchase in "Purchased" tab in App Store
#. Did you log in different country in App Store than the country you did the purchase?
#. Try to log out / log in App Store (Store -> Sign Out)


If you have to restore the purchase every time you start LanScan:

#. Try to log out / log in from App Store (Store -> Sign Out)
#. Delete LanScan from your Applications
#. Empty your trash (important, else your Mac still see your app in the trash)
#. Reinstall LanScan free trial from App Store
#. Restore the purchase if needed in LanScan: Buy Pro version -> Restore previous purchase


What are the differences between LanScan App Store apps and the LanScan tool included in Debookee?
--------------------------------------------------------------------------------------------------

========================================================================================================    ==========================
`LanScan - Free - App Store <https://itunes.apple.com/us/app/lanscan/id472226235?mt=12>`_                   Only 4 hostnames are fully displayed, you'll see the first 3 chars of the others.
`LanScan - In-App purchase Pro - App Store <https://itunes.apple.com/us/app/lanscan/id472226235?mt=12>`_    No limitation on resolved hostnames
`LanScan Pro <https://itunes.apple.com/us/app/lanscan-pro/id562184107?mt=12>`_                              No limitation on resolved hostnames. Same code as In-App purchase, it was just created before In-App existed. Since v4, it's preferred to buy the In-App purchase in LanScan Free edition than buying the LanScan Pro application.
Debookee's LanScan tool                                                                                     Advanced version of LanScan Pro application. Each new feature is first released in Debookee's LanScan tool, then on App Store
========================================================================================================    ==========================


A MAC address vendor is not resolved in LanScan results.
--------------------------------------------------------
We’re using the `IEEE list <http://standards-oui.ieee.org/oui/oui.txt>`_ for our vendors database and currently, we refresh this database on each update of our applications.

As it’s updated more frequently, Debookee will typically have a more up-to-date vendors list than LanScan and LanScan Pro.
Dynamic updates will be added in a future release.

Where are custom hostnames located?
-----------------------------------
At first: *please backup!*

Custom hostnames are saved in the following XML plist files. Take care that those files can be cached, and you may edit them without seeing any results.
So please be sure to erase the plist cache with command:
``defaults read my_freshly_edited_plist_file.plist``

=================  ================
LanScan            ~/Library/Containers/com.iwaxx.LanScan/Data/Library/Preferences/com.iwaxx.LanScan.plist
LanScan Pro        ~/Library/Containers/com.iwaxx.LanScan-Pro/Data/Library/Preferences/com.iwaxx.LanScan-Pro.plist
Debookee           ~/Library/Preferences/com.iwaxx.Debookee.plist
=================  ================

Several devices have the same duplicated MAC address but different IPs.
-----------------------------------------------------------------------

LanScan doesn't modify anything on your network: think about it as Read-Only on your network, it asks questions (ARP requests) and display answers listened directly from the network.

Duplicated MAC addresses are usually cause by a device which is answering instead of other ones, commonly called ARP proxy or "Bonjour Sleep Proxy" in case of Apple devices (Airport Extreme, Time Capsule, Apple TV...)

ARP proxy
^^^^^^^^^

Commonly used on wireless network to lower broadcasted traffic, you may see an Access Point (AP) or a router answering instead of other devices, in that case you'll see the AP or router's MAC address duplicated. |br|
→ If you're scanning while on the Wi-Fi, try to cable your Mac and scan again from the LAN point of view.

Bonjour Sleep Proxy
^^^^^^^^^^^^^^^^^^^

In short, when an Apple compatible device such as a Mac, an Apple TV... goes in sleep mode, it advertises the Apple device compatible with Bonjour Proxy, which will answer to some requests in its name (including those that LanScan send to discover devices), so that the TV or the Mac stays in sleep mode.

You can find more information here:
https://en.wikipedia.org/wiki/Bonjour_Sleep_Proxy

In that case you'll see several time the MAC address of the device acting as a proxy. |br|
→ Waking up the final device should help to show its real MAC address in that case

In-App purchase is stuck in "Retrieving Information from App Store."
--------------------------------------------------------------------

This means that LanScan can't connect to App Store to get informations concerning the In-App purchase.

* Launch App Store application and check if you're logged in and if you can browse various applications (testing Internet connectivity)
* If logged in, try to log out and log in again App Store.app
* Sometimes, a popup window appears behind LanScan window asking for credentials, be sure to see that tiny window
* That but true: try to reboot your Mac and log in App Store.app again.

There's no menu "Migrate to LanScan In-App v5" in LanScan Pro
-------------------------------------------------------------

This menu appeared in LanScan Pro 5.1, be sure that your LanScan Pro app is up to date.


Blog
====

`Debookee v6 beta is out - Welcome SSL/TLS decryption <https://github.com/iwaxx/blog/issues/2>`_

`Promiscuous vs Monitoring mode <https://github.com/iwaxx/blog/issues/3>`_

`LanScan 5.0 introduces new 'Live Scan' feature <https://github.com/iwaxx/blog/issues/4>`_
