# Debian packages

## Commandos

Om een packge the bouwen vanaf de package directory.

    dpkg-deb -b "package directory"

Met lintian is te controleren of het package voldoet aan de vereisten van de debian policy.

    /usr/bin/lintian "package.deb"

De bestanden in de tags directories geven meer informatie over de foutmeldingen die kunnen
verschijnen na het uitvoeren van lintian op een debian package.

    /usr/share/lintian/tags/ 

Overrides zorgen voor het negeren van bepaalde foutmeldingen.

    /usr/share/lintian/overrides/

Gebruik dit om de syntax controleren van een NEWS.Debian of changelog file

    /usr/bin/dpkg-parsechangelog

## Een debian package

Met ar is de inhoud van een package te bekijken.

    ar tv 'debian package'
    ar x 'debian package'

Er zijn vervolgens een debian binary, een control en een data tar.gz te zien.

    DEBIAN/control : informatie over het package
    DEBIAN/preinstall : een script waarmee configuratie handelingen uitgevoerd
                    kunnen worden voorafgaand aan de installatie van programma. 
    DEBIAN/postinstall : een script waarmee configuratie handelingen kunnen 
                      worden uitgevoerd na de installatie van een programma. 

# Wat moet er in een debian control file 

    Package: naam met of zonder versie nummer bv "programma-1.0"
    Source: Bron pakket naam. 
    Version: Versie nummer 
    Architecture: architectuur van het systeem meestal "amd64" of "all" als het om architectuur onafhankelijke scripts gaat.
    Maintainer: "naam" <email@domein\>  
    Installed-Size: dit kan ingevuld worden door het vijfde veld van een 'ls -la' commando te nemen 
    Depends: De afhankelijkheden van het programma dit is te ontdekken door het pakket te bouwen en testen of het werkt. 
    Recommends:
    Built-Using: Voor gecompileerde applicaties is het nodig om de naam en het versienummer van de compiler aan te geven. 
    Section: De sectie in de package repository voor scripts is utils goed
    Priority: voor de meeste applicaties geldt "optional"
    Description: Korte beschrijving van de applicatie, een uitgebreide beschrijving en uitleg kan in README.debian file. 

Sommige velden kunnen weggelaten worden. 
Om te zien wat er doorgaans gebruikt wordt als waardes voor de velden in het controlfile kun je de volgende loop gebruiken:

    "$for i in `ls /var/cache/apt/archives` ; do apt-cache show /var/cache/apt/archives/$i | grep -i "veld waarop je wilt zoeken" ; done "


## De documentatie 

De documentatie behorend bij het programma hoort in de directory DEBIAN/usr/share/doc/'programma naam'/
Doorgaans zijn dat de volgende bestanden:

    NEWS.Debian 
    README.Debian
    changelog
    copyright

Het NEWS.Debian bestand heeft de volgende structuur:

programmanaam (versienummer b.v. 1.0); urgency="urgentie"

  Hier kan een stuk tekst waarin nieuws over het programma te lezen is. 
  <---De twee spaties zijn belangrijk.
 
  -- "naam" <email@domein> datum timestamp ( met het commando "date" te genereren)   

Een changelog bestand is nodig om bij te houden wat er veranderd wordt aan het programma.

    DEBIAN/usr/share/doc/'programma naam'/changelog

Een verklaring omtrent de copyright van het programma.

    DEBIAN/usr/share/doc/'programma naam'/copyright

#

Voor de bestanden NEWS.Debian README.Debian en changelog moet compressie zonder timestamp gebruikt worden met het commando 

    gzip -9 -n "bestand"

Tijdens het testen van de package installatie is het package te verwijderen met het commando

    apt remove "packagenaam"

Daarbij de naam specificerende zoals gebruikt in het Package: veld in de DEBIAN/control file. 

## Manpages

Applicaties behoren een man page te hebben.
Man pages genereren kan door met docbook-to-man een manpage in docbook formaat te verwerken. 
Een voorbeeld manpage is te verkrijgen door het dh_make commando te gebruiken in een directory met de volgende naamstructuur "packagenaam-1.2"

    $cd packagenaam-1.2  
    $db_make --createorig  
  

De debian directory bevat daarna een bestand manpage.sgml.ex deze is dan te wijzigen.
Een manpage heeft doorgaans de naam van het programma met een getal als extensie. Afhankelijk van het type applicatie is het getal van de manpage categorie te kiezen.

    $docbook-to-man manpage.sgml.ex > programmanaam.1 

    /usr/share/man/man1 

Manpages bevinden zich in een linux systeem in de /usr/share/man directory met daarin directories voor de gebruikte taal (locale) en de sectie waarin het programma thuishoort (secties 1 tm 7). In een debian package moet dus een usr/share/man/man1 directory bestaan met daarin de programmanaam.1 manpage van het programma. De manpages behoren met gzip -9 -n gecomprimeerd ingepakt te worden.

    $gzip -9 -n "programma.1"

