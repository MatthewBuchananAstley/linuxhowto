#Git gebruiken

#Github activeren met ssh keys.

    ssh-keygen -t rsa "keyname_rsa"

passphrase invoeren en ergens opslaan.
Ssh-agent starten.

    ssh-add ~/.ssh/keyname_rsa.

passphrase invoeren.
Inloggen op de github website.
Een repository creeren voor code.
De ssh key pub id invoeren bij de settings.
De nieuwe repository clonen naar je werkstation.
De programma code kopieren naar de geclonede repository directory.

    Git add "programma"
    Git commit "programma"
    Git remote add origin git@github.com:USERNAME/repository.git
    Git push

# Git repository op een usb updaten vanaf een repository op de lokale machine

    cd "repository op usb"
    git pull file::///path/to/repository

# Git pushen

    git push origin HEAD:master

Het git push commando is ook aan te roepen via een alias. Een commando alias is te configureren door:

    alias gp='git push origin HEAD:master' 

toe te voegen aan .bashrc in de home directory. 

# Lijst van veranderingen in een git repository genereren inclusief bestandsnaam

Dat kan met het gitpresent.pl script:

    #perl ./gitpresent.pl 

    Tue Dec 13 11:42:31 2022 +0100 Removed commented out (#prepended lines) getting script to work attempt lines gitpresent.pl Matthew Buchanan Astley <matthewbuchanan@astley.nl>
    Tue Dec 13 11:36:35 2022 +0100 Added gitpresent.pl script README.md Matthew Buchanan Astley <matthewbuchanan@astley.nl>
    Tue Dec 13 11:35:15 2022 +0100 Added gitpresent.pl script to generate a listing of commits including filename for the actual day gitpresent.pl Matthew Buchanan Astley <matthewbuchanan@astley.nl>

Het script genereert een lijstje van de veranderingen in een git repository op de huidige dag. Handig om bij te houden hoeveel er per dag verandert in git repositories.
    
