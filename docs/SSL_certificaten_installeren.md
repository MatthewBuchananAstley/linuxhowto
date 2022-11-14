# SSL certificaten installeren

## Handmatig testcertificaten aanmaken om te testen.

functionele ssl server nodig en om dat te installeren is testen met een self signed ssl certificaat handig. Een SSL self signed certificaat genereren gaat met:

    openssl req -x509 -newkey rsa:2048 -keyout testkey.pem -out testreq.pem 

De testkey.pem,testreq.pem in de /etc/ssl/private/,/etc/ssl/cert/ directories geplaatst worden.

Een sterke passphrase is te genereren met:

    openssl rand -base64 1000 (of meer bytes) 

De output daarvan kopieren en gebruiken als passphrase en opslaan.
De testkey.pem,testreq.pem kunnen dan in de /etc/ssl/private/,/etc/ssl/cert/ directories geplaatst worden.
Deze certificaten zijn in /etc/apache2/sites-enabled/testsite-ssl.conf te specificeren met de daarvoor aangegeven configuratie regels:

    SSLCertificateFile 	/etc/ssl/cert/testkey.pem  
    SSLCertificateKeyFile   /etc/ssl/private/testreq.pem  

De apache2 modules die voor ssl nodig zijn:

in /etc/apache2/mods-enabled:
    
    ln -s ../mods-available/ssl.conf ssl.conf  
    ln -s ../mods-available/ssl.load ssl.load  
    ln -s ../mods-available/cache.load cache.load  
    ln -s ../mods-available/cache_socache.load cache_socache.load  
    ln -s ../mods-available/socache_shmcb.load socache_shmcb.load  
    
    cp /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/towhen-ssl.conf  

## LetsEncrypt certificaten geinstalleerd met Certbot

Voor certbot is een werkende apache2 server met ssl virtual host nodig, dus zodra de server operationeel is met de test certificaten kan certbot geinstalleerd worden om 


