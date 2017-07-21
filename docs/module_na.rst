.. _module_na_long:

NA --- Network Analysis Module
============================

.. _module_na:

NA Module
---------

The NA module analyzes in real-time the network traffic of your own Mac and :ref:`intercepted targets <mitm>`.

It currently supports:

     * HTTP
     * DNS
     * TCP
     * DHCP
     * SIP & RTP (VoIP) protocols.

Raw packets of your targets with Wireshark
-------------------------------------------

Some users need more details (or raw data) and use `Wireshark <https://www.wireshark.org>`_ for their own traffic. Unfortunately, Wireshark can't intercept traffic like Debookee does, and they can't see their iPhone/Android/Fridge/... raw data.

One idea is to use both Debookee and Wireshark at the same time:

    * Find and select your target with LanScan
    * Launch the NA module to start the interception, but ignore the NA results
    * Start Wireshark on your Mac: you'll see your own traffic as well as the intercepted target's traffic
    
.. tip ::
    
    For each packet, Wireshark will see the packets coming to your Mac, and the same packet retransmitted transparently by the Mac. Target's traffic in that case will be doubled in Wireshark and you'll see all packets **duplicated**.
    
    To filter, one idea of display filter could be to hide all outgoing packets of your targets like:
    ``!(eth.src == mac_address_of_my_mac && ip.src != ip_of_my_mac) &&``
    ``!(eth.dst == mac_address_of_my_mac && ip.dst != ip_of_my_mac)``