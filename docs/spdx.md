# SPDX informatie bestanden generereren

Voor het laten gebruiken van simpele scripts door organisaties die spdx bestanden vereisen is het handig wanneer de volgende informatie wordt opgeslagen in het spdx formaat:

De Licentie, de copyright vermelding, de SHA1 en SHA256 sums, en ook de sum van alle files in de directory. 

Het <a href="https://github.com/MatthewBuchananAstley/spdxISO_IEC5962/">spdx-t.py</a> script kan daarvoor gebruikt worden.

    ./spdx-t.py "directory" "https://github.com/NAME/repository.git" "application spdx file" 
