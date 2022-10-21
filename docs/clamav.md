# Virusscannen met clamav

Partities op een harde schijf zijn te scannen op virussen met behulp van het opensource pakket clamscan. 

## Installeren

$sudo apt install clamav

Er worden dan een aantal pakketen geinstalleerd inclusief een cronjob waarmee continu nieuwe virus definities gedownload worden.

# Partitie scannen

mkdir tmp/
mount "/dev/partitie" tmp/
clamscan -r -v /tmp 
