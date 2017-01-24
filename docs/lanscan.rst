.. _lanscan:

LanScan
#######

LanScan is a Layer 2 & Layer 3 network scanner which discovers network devices thanks to ARP, ICMP, DNS, mDNS and SMB packets.

.. _lanscan_local:

Scanning local LAN
------------------

By default, LanScan scans your local LAN and scanned IPs are configured following your network configuration (IP address and network mask).

.. code-block:: none

    Your Mac IP address : 192.168.1.10
    Your Mac Netmask    : 255.255.255.0 or /24
    Exampes of local scans:
         -> From 192.168.1.1 to 192.168.1.254
         -> From 192.168.1.15 to 192.168.1.20

A local scan will allow you to:

    * Discover MAC addresses of devices
    * Set a custom hostname to each device
    * Set a custom comment to each device
    * Select a device as a :ref:`mitm_target`
    * Select a device as a :ref:`mitm_gateway`

.. _lanscan_external:

Scanning external IP ranges
---------------------------

If you modify LanScan IP range to IPs which do not belong to your local LAN, LanScan will make an external scan with only ICMP packets (Layer 3 packets). ARP packets (Layer 2 packets) are not available as packets have to cross over a router to reach destinations IPs.

An external range can be done with private or public IPs, 

.. code-block:: none

    Your Mac IP address : 192.168.1.10
    Your Mac Netmask    : 255.255.255.0 or /24
    Examples of external ranges:
        -> From 192.168.0.1 to 192.168.0.254
        -> From 10.10.50.10 to 10.10.50.20
        -> From 8.8.8.8 to 8.8.8.8
        -> From 1.0.0.0 to 190.0.0.0

An external scan have the following limitations:

    * You can't see MAC addresses of devices
    * You can't set a custom hostname
    * You can't set a custom comment
    * You can't select a device as a :ref:`mitm_target`
    * You can't select a device as a :ref:`mitm_gateway`