# Node js

Node js installeren, downloaden kan hier:

<a href="https://nodejs.org/en/">https://nodejs.org/en/</a>

# Verifiëren van de integriteit van de download

<a href="https://github.com/nodejs/node#verifying-binaries">https://github.com/nodejs/node#verifying-binaries</a>


    curl -O https://nodejs.org/dist/vx.y.z/SHASUMS256.txt

Dat bestand specificeert de sha256sums van alle door nodejs.org aangeboden downloads.
Vervolgens wordt er door nodejs gevraagd om key van iemand te importeren die geauthoriseerd is om nodejs.org packages te signeren en om een van het SHASUMS256.txt losgekoppelde digitale handtekening databestand te downloaden. 

Voor de onderstaande key moeten vanaf een publieke keyserver de gpg keys van de nodejs pakket signeer geauthoriseerden geimporteerd worden.

<a href="https://github.com/nodejs/node#release-keys">https://github.com/nodejs/node#release-keys</a>

Daarna kan met gpg en met het van SHASUMS256.txt losgekoppelde digitale handtekening databestand (SHA256SUMS.sig) de integriteit van de handtekening van het SHA256SUMS.txt zelf gecontroleerd worden!

    gpg: Signature made Fri 04 Nov 2022 09:12:23 PM CET
    gpg:                using RSA key 61FC681DFB92A079F1685E77973F295594EC4689
    gpg: Good signature from "Juan José Arboleda <soyjuanarbol@gmail.com>" [unknown]
    gpg: WARNING: This key is not certified with a trusted signature!
    gpg:          There is no indication that the signature belongs to the owner.
    Primary key fingerprint: 61FC 681D FB92 A079 F168  5E77 973F 2955 94EC 4689

Conflicterend bericht van gpg: één waarin gesteld wordt dat de handtekening goed is en en één dat de key niet gecertificeerd is met een vertrouwde handtekening. Dus geen indicatie dat de handtekening de handtekening is van de eigenaar van de key.

Er moet vertrouwen in de key gesteld worden en dat is te configureren met gpg. Door de geimporteerde key zelf te signeren en daarmee te verklaren dat de key vertrouwd is.




