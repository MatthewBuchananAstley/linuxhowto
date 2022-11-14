# Security pakketten

Security pakketten die je kunt installeren zijn

    Clamav - virusscanner 

    rkhunter/chkrootkit - scripts waarmee rootkits te detecteren zijn

    nmap_local - script waarmee de eigen netwerk interfaces op open poorten te controleren zijn


# Supersterke wachtwoorden genereren

Dat kan met <a href="https://github.com/MatthewBuchananAstley/vop">Voice of pinocchio or pinocchia</a>

    [matthewbuchananastley@fedora vop]$ ./otp_m.py -pwl 64 
    j8A#Ks7e5Kl075JB0zED408FK0eXD129kA23Mfa2njE38613Aa9Fda60822Ef6L

    Het heeft minimaal één hoofdletter, minimaal één kleine letter en precies één speciaal karakter

# Forensische applicaties voor ubuntu (forensics-all)

En voor een een mooi overzichtje van alle forensics tool beschrijvingen in het forensics-all debian pakket:

    Deze "oneliner" voor op de commandline:

    for i in `apt info forensics-all 2>/dev/null | egrep 'The following' -A17 | grep ',' | perl -lne 'print join("\n", split(/,/, $_)); ' | sed 's/ //g'` ; do a=$(echo $i); b=$(apt info $i 2>/dev/null | grep 'Description:'); echo $a ":" $b ; done   


Zo ziet dat er in een bash script uit:

    for i in `apt info forensics-all 2>/dev/null | egrep 'The following' -A17 | grep ',' | perl -lne 'print join("\n", split(/,/, $_)); ' | sed 's/ //g'` 
        do 
            a=$(echo $i); 
            b=$(apt info $i 2>/dev/null | grep 'Description:')
            echo $a ":" $b 
        done


