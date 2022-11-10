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
