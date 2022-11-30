# Security 

# Guide for developing more secure software

<a href="https://github.com/ossf/wg-best-practices-os-developers/blob/main/docs/Concise-Guide-for-Developing-More-Secure-Software.md#readme">https://github.com/ossf/wg-best-practices-os-developers/blob/main/docs/Concise-Guide-for-Developing-More-Secure-Software.md#readme</a>

nog wat guides:

<a href="https://openssf.org/resources/guides/">https://openssf.org/resources/guides/</a>

Guide for implementing a coordinated vulnerability disclosure process for open source projects

<a href="https://github.com/ossf/oss-vulnerability-guide/blob/main/maintainer-guide.md>https://github.com/ossf/oss-vulnerability-guide/blob/main/maintainer-guide.md</a>



# Snyk code security analyse

<a href="https://snyk.io/">Snyk.io</a> kan github repositories automatisch scannen op kwetsbaarheden in de code. Met het gratis account zijn er honderden scans per maand beschikbaar.


# Security pakketten
Security pakketten die je kunt installeren zijn

Clamav - virusscanner 

rkhunter/chkrootkit - scripts waarmee rootkits te detecteren zijn

<a href="https://github.com/MatthewBuchananAstley/nmap_local">nmap_local</a> - script waarmee de eigen netwerk interfaces op open poorten te controleren zijn

# Supersterke wachtwoorden genereren

Dat kan met <a href="https://github.com/MatthewBuchananAstley/vop">Voice of pinocchio or pinocchia</a>

    [matthewbuchananastley@fedora vop]$ ./otp_m.py -pwl 64 
    j8A#Ks7e5Kl075JB0zED408FK0eXD129kA23Mfa2njE38613Aa9Fda60822Ef6L

Het heeft minimaal één hoofdletter, minimaal één kleine letter en precies één speciaal karakter

Een wachtwoord in:

    echo "64^77" | bc -l
    11908525658859223294760121268437066290850060053501019099651935423375\
    59409644991157577631417489430225814753315399706505926303091308322252\
    3904

mogelijkheden is vervolgens het resultaat.


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


