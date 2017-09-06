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

But wait. Don't throw away Debookee directly, if you want to see raw data of your mobiles or IoT things, maybe you'll be interested in :ref:`module_na_dbk_and_wireshark`.



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

