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
Git remote set-url origin git@github.com:USERNAME/repository.git
Git push

#Een nieuwe branch maken
Dat kan door een nieuwe lokale git repository te maken met dezelfde naam als de repository op de github site.
Daar kan je dan dezelfde git add en git commit commandos uitvoeren met nieuwe code en vervolgens de remote url in te stellen met een andere naam. Bijvoorbeeld:
git remote set url "nieuwe naam" git@github.com:USERNAME/repository.git
Dat verschijnt dan als nieuwe branch in de remote repository.
