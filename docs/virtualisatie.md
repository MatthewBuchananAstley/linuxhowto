# KVM virtualisation

Virtualisatie gebeurt op Fedora met behulp van de volgende pakketten:

    [root@fedora vop]# yum install libvirt-daemon-kvm qemu-kvm qemu-kvm-core

Virt-manager wordt gebruikt om de virtuele systemen te installeren en beheren. Het is te installeren via het grafische software installatie programma dat in Fedora aangegeven wordt door het volgende icoontje:

![Screenshot](img/Graphical_rpm_software_installation.png)

En in het software installatie programma ziet dat er zo uit:

![Screenshot](img/Virtmanager_installatie.png)

# Een nieuwe virtuele machine configureren

![Screenshot](img/Create_a_new_virtual_machine.png)

Selecteer de iso van de te installeren linux distributie. 

![Screenshot](img/Canvm_step1.png)

![Screenshot](img/Canvm_step2.png)

Selecteer het aantal processor cores en de hoeveelheid geheugen:

![Screenshot](img/Canvm_step3.png)

Selecteer de hoeveelheid schrijfruimte:

![Screenshot](img/Canvm_step4.png)

Geef een naam op van de virtuele machine:

![Screenshot](img/Canvm_step5.png)

