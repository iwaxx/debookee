.. _mitm:

Traffic Interception (MITM)
###########################

:program:`Debookee` is able to intercept the traffic of any device in the same subnet, thanks to a Man-in-the-middle attack (MITM).

It intercepts all network traffic happening between :ref:`Targets <mitm_target>` and a :ref:`mitm_gateway`.
This traffic is then analyzed by the :ref:`na_module_long`.

It allows you to transparently capture data from mobile devices on your Mac (iPhone, iPad, Android, BlackBerry...) or Printer, TV, Fridge... without setting any proxy.

.. note::
    Interception is a native feature of Debookee, included in the free trial.
    
    **You don't need the NA module to intercept targets traffic** to your Mac, but the results of analysis (HTTP, TCP ...) will be obfuscated at some point in the free trial of NA module.

.. warning::
    **Interception may fail** on some networks, specially on professional wireless networks (Aruba, Cisco, HP…), due to Proxy ARP or security features that detect the MITM.
    
    In that case, you won’t see any traffic under your target menu. A workaround can be to set up a mobile hotspot or connect to another network.
    
    We recommend to always try the free trial of :ref:`na_module` to check if your network allows network traffic interception or not before buying it.

.. _mitm_target:

Target
------

Debookee intercepts all network traffic between Targets and the configured :ref:`mitm_gateway`.

You can set as many Targets as you want, but they must be on the same subnet as your Mac, as we need to know their MAC addresses. (cf :ref:`lanscan_local`)

**To set a Target:**

    * Stop the NA module if already running
    * Select a device which has no role & located on the same LAN
    * Click on “Toggle Target” or double-click on the device 'role' column

.. _mitm_gateway:

Gateway
-------

A Gateway is the device to which :ref:`Targets <mitm_target>` are talking to and you're interested in that traffic.

You can set only one Gateway.

By default, the Gateway is set to the *default gateway* or *router* of your Mac network interface. So by default, if you set a Target, you'll intercept the traffic from the Target to the router, ie the Internet traffic.

One reason to modify the Gateway from the router to another device on your network is if you want to intercept some internal network traffic on your LAN.

If you're interested in the traffic between your iPhone and your printer, both located on your LAN:

    * Set your iPhone as a Target
    * Set your printer as a Gateway
    * (Note that Debookee won't see your iPhone Internet traffic in that case.)
    
**To set a Gateway:**

    * Stop the NA module if already running
    * Select a device which has no role  & located on the same LAN
    * Click on “Set Gateway”

