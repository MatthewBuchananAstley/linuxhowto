# Debian 10

# Netwerk configureren

Bekijk de netwerkkaarten in het systeem met:

    $ip a 

Netwerk interfaces configureren gaat via een interfaces file /etc/network/interfaces

    > auto "interface naam"  
    > iface "interface naam" inet dhcp 

Een ip is te verkrijgen door de interface te activeren met ifup:
    
    $/sbin/ifup "interface naam"  

In een virtuele omgeving met een gebridgde interface kan het zijn dat je de default route naar het internet moet specificeren. 

    $ip route replace default dev "interface naam" via "ip van de router naar het internet"

# Een apt repository toevoegen

Als je een installatie vanaf een cd hebt gedaan zonder network mirror toe te voegen
dan is het nodig om een debian mirror toe te voegen aan het sources.list bestand in /etc/apt 


