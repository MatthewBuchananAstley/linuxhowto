## Centos

# DHCP activeren 

Zodat de host tijdens het booten een IP adres ontvangt, kan door in /etc/sysconfig/network-scripts/ifcfg-eth0 te controleren of

    BOOTPROTO=dhcp 

DHCP tijdens het opstarten wordt geactiveerd met:

    ONBOOT=yes  

/etc/NetworkManager/dispatcher.d/11-dhclient is een dhcp script dat het /etc/sysconfig/network-scripts/ifcfg-eth0 bestand leest.

