# Linux kernel compilation

Haal de laatste kernel source van <a href="https://kernel.org">https://kernel.org</a>.
en pak het uit in een directory.

#
# Read the ...

Informatie over hoe te beginnen staat in:

     Linux-5.16-rc6/Documentation/README.rst

# Configuring the options 

    make menuconfig<br>
    make localmodconfig (configures only the currently loaded modules on the system)

# Building 

    make

# Troubleshooting

At the point of this writing the build for linux-5.16-rc6 stopped because it needed the "dwarves" package
Tijdens het schrijven van deze tekst stopte het bouwen van de linux-5.16-rc6 kernel omdat het "dwarves" pakket nodig was.

    apt install dwarves  

The default configuration also has configured debian canonical keyfiles to be used for allowing or blacklisting signed/unsigned 
code into the kernel. You have to add those or remove the mention of these keyfiles from the config. To be found in the crypto settings.

# Na het compileren  

Het vmlinuz bzImage is te vinden in: 

    arch/x86/boot/bzImage

Kopieer dat naar /boot/vmlinuz-5.16-rc6 en gebruik een initrd.
Maak een backup van de huidige /boot/grub.cfg.
Check of de uitvoer van grub-mkconfig goed is en creeer een nieuw /boot/grub.cfg bestand.
