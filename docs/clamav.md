# Virusscannen met clamav

Partities op een harde schijf zijn te scannen op virussen met behulp van het opensource pakket clamscan. 

## Installeren

    $sudo apt install clamav

Er worden dan een aantal pakketen geinstalleerd inclusief een cronjob waarmee continu nieuwe virus definities gedownload worden.

# Freshclam virusdefinitie database updaten

    yum install freshclam
    chown root:clamav /etc/freshclam.conf
    chmod 640 /etc/freshclam.conf

Het freshclam log activeren in /etc/freshclam.log (uncommenten: "#" weghalen) en daarna 

    chown clamupdate:clamupdate /var/log/freshclam.log 

# Freshclam update cronjob starten 

    #crontab -u clamupdate -e 
    0,5,10,15,20,25,30,35,40,45,50,55 * * * * /usr/bin/freshclam

# Partitie scannen

    mkdir tmp/
    mount "/dev/partitie" tmp/
    clamscan -r -v /tmp 
