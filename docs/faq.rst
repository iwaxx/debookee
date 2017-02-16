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


LanScan Pro on AppStore
=======================

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