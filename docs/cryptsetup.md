#Disk encryptie met cryptsetup

#USB

Dit werkt ook voor usb sticks.
Om te vinden welk device in /dev de usb stick is kun je het volgende doen:

    $dmesg | grep sd

Er verschijnt dat de regel die door de kernel is gerapporteerd:

    [ 1576.923832] sd 5:0:0:0: [sda] Attached SCSI removable disk

Meestal is het /dev/sda maar het kan zijn dat jouw systeem sda al in gebruik heeft dus altijd even controleren of de USB stick sda heet.

#Encrypten met luksFormat
Een disk encrypten kan door luksFormat te gebruiken: 

    luksFormat -t 'filesysteem' /dev/'disknaam'

Waar filesysteem een gangbaar linux filesysteem is zoals ext4 of xfs (standaard vfat). Er wordt dan gevraagd om een passphrase.

#Openen van een encrypted disk:

    cryptsetup open /dev/'disknaam' 'naam van de device mapping' (zonder /dev/mapper/ ervoor) 

Waar 'naam van de device mapping' de naam is in /dev/mapping/. Deze naam is te gebruiken om de encrypte disk te mounten.

#Encrypted disk mounten

Na het openen van de encrypted disk gaat het mounten van een encrypted disk op dezelfde manier als een normale disk.

    mount /dev/mapper/'naam van de device mapping' 'mount directory' 

De (tijdelijke) directory kan je aanmaken in /tmp, een home directory of anders in /media/usernaam/dir.

#Encrypted volume sluiten

    umount 'mount directory' 
    cryptsetup close 'naam van de device mapping'

