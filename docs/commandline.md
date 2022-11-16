# Commandline 

# De enge Linux \*thunder\* ... commandline 

Nadat je de terminal "terminal"... geopend hebt voor de commandline, wat nu?

# Ls

Een directory weergeven met /bin/ls

    [matthewbuchananastley@fedora docs]$ ls 
    about.md                  debian10.md                                       mongodb.md        rpm.md
    apache.md                 debianpackages.md                                 mysql.md          security.md
    build_omgeving_inrichten  dual_boot_ubuntu_with_partial_disk_encryption.md  orgitxt.txt       ssh.md
    clamav.md                 git.md                                            Perl.md           SSL_certificaten_installeren.md
    coc.md                    graphite.md                                       Php.md            tijd.md
    commandline.md            img                                               Python.md         virtualisatie.md
    computeruptime.md         index.md                                          readthedocs.md
    cryptsetup.md             linux_kernel_compilation.md                       requirements.txt
 

Ls hoor bij de coreutils. Om uit te vinden bij welk rpm pakket een tool hoort:


    [matthewbuchananastley@fedora docs]$ rpm -qif /bin/ls 
    Name        : coreutils
    Version     : 9.0
    Release     : 8.fc36
    Architecture: x86_64
    Install Date: Mon 31 Oct 2022 02:16:33 PM CET
    Group       : Unspecified
    Size        : 5945882
    License     : GPLv3+
    Signature   : RSA/SHA256, Mon 08 Aug 2022 05:12:57 PM CEST, Key ID 999f7cbf38ab71f4
    Source RPM  : coreutils-9.0-8.fc36.src.rpm
    Build Date  : Mon 08 Aug 2022 04:53:54 PM CEST
    Build Host  : buildvm-x86-05.iad2.fedoraproject.org
    Packager    : Fedora Project
    Vendor      : Fedora Project
    URL         : https://www.gnu.org/software/coreutils/
    Bug URL     : https://bugz.fedoraproject.org/coreutils
    Summary     : A set of basic GNU tools commonly used in shell scripts
    Description :
    These are the GNU core utilities.  This package is the combination of
    the old GNU fileutils, sh-utils, and textutils packages.    
