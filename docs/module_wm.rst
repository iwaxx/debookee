.. _module_wm_long:

WM - Wi-Fi Monitoring Module
============================

.. _module_wm:

WM module
---------

The Wi-Fi Monitoring module puts your airport interface in monitoring mode and listens to all 802.11 radio frames around.

It currently shows you:

     * Access Points radio details in your radio range
     * Wi-Fi clients radio details in your radio range
     * Informations on clients association (useful to detect roaming or when multiple AP with same SSID)
     * Bidirectional infos for each client connection: from AP to client and client to AP
     
         * Data Rate
         * %Retries
         * %Errors
         * Bytes transferred
         * Channels stats
         * Power signal in dBm
         * ...

For those asking, WM module can't decrypt encrypted packets of other Wi-Fi networks.

Differences with NA module
--------------------------



Starting WM module sets your Mac Wi-Fi interface in monitoring mode. (which is different than *promiscuous*, see `this article <https://medium.com/@tomlabaude/promiscuous-vs-monitoring-mode-d603601f5fa>`_)

Monitoring mode has the following consequences:

    * Your Wi-Fi interface will be directly disconnected
    * You will loose all network connectivity
    * You see all *radio* packets, even the Wi-Fi packets of your neighbor (encrypted or not)
    * WM module doesn't care if packets are encrypted: it shows you radio statistics, not content analysis

    
