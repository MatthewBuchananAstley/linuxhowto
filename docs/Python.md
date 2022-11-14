# Python

## Unieke willekeurige code genereren


Dat kan met <a href="https://github.com/MatthewBuchananAstley/vop">vop</a> (Voice of pinoccio or pinocchia password generator)

    matthewbuchananastley@fedora vop]$ ./otp_m.py -pwl 64 -b64 1 
    M1owNWk3NkE0NGljNTVrNVphOTdLOUg4MTRkMDVtOXAwMDUrNmtIcDBDbzh2NEgzQzBaODVNUDY1MDREYU84


    [matthewbuchananastley@fedora vop]$ ./otp_m.py -h
    usage: otp_m.py [-h] [-pwl PASSWORD_LENGTH] [-b64 URLSAFE_ENCODE]

    options:
        -h, --help            show this help message and exit
        -pwl PASSWORD_LENGTH, --password_length PASSWORD_LENGTH 
        -b64 URLSAFE_ENCODE, --urlsafe_encode URLSAFE_ENCODE (zonder speciale karakters, zonder -b64 1 optie zit er een speciaal karakter in voor passwords)


