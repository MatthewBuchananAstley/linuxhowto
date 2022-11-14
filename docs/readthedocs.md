# Read the docs theme 

# Mkdocs

Het mkdocs pakket is een handig pakket om standaard software documentatie mee te schrijven.

# Mkdocs installeren
    
    (apt/yum install pip3)
    pip3 install mkdocs

# Mkdocs nieuw project maken

    mkdocs new "projectnaam"

# Wijzigingen aan mkdocs project tekst live bekijken 

    (in de project directory)
    [matthewbuchananastley@fedora linuxhowto.git]$ ls
    docs  mkdocs.yml  README.md
    [matthewbuchananastley@fedora linuxhowto.git]$ mkdocs serve 
    INFO     -  Building documentation...
    INFO     -  Cleaning site directory
    INFO     -  The following pages exist in the docs directory, but are not included in the "nav" configuration:
              - index.md
              - rpm.md
    INFO     -  Documentation built in 0.14 seconds
    INFO     -  [11:40:24] Watching paths for changes: 'docs', 'mkdocs.yml'
    INFO     -  [11:40:24] Serving on http://127.0.0.1:8000/
    INFO     -  [11:40:26] Browser connected: http://127.0.0.1:8000/

# Teksten toevoegen

Teksten gaan in de docs directory, bestanden hebben de .md extensie.

# Plaatjes toevoegen.

Plaatjes kunnen in een directory in de docs directory.
Op de volgende manier kunnen plaatjes ingevoegd worden op een pagina:

    ![Screenshot](img/6_Install_create_boot_partition.png)

# code blocks laten wrappen

Wanneer codeblocks die je specificeert met ``` boven en onder de code, het tekstblok weergeeft op een lange regel dan kan dat met een wrap instructie in de css te maken hebben, zo is dit te verhelpen: 

/usr/lib/python3/dist-packages/mkdocs/themes/readthedocs/css/theme.css

het volgende stukje css van nowrap naar wrap veranderen:

    code,.rst-content tt,.rst-content code{white-space:wrap

