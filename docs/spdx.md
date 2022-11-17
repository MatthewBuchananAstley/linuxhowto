# SPDX 

SPDX kan gebruikt worden voor een beter overzicht van de veiligheid van de leveranciersketen.

## SPDX informatie bestanden generereren

Voor het laten gebruiken van simpele scripts door organisaties die spdx bestanden vereisen is het handig wanneer de volgende informatie wordt opgeslagen in het spdx formaat:

De Licentie, de copyright vermelding, de SHA1 en SHA256 sums, en ook de sum van alle files in de directory. 

Het <a href="https://github.com/MatthewBuchananAstley/spdxISO_IEC5962/">spdx-t.py</a> script kan daarvoor gebruikt worden.

    ./spdx-t.py "directory" "https://github.com/NAME/repository.git" "application spdx file" 


## Verifiëren van spdx bestanden 

Het verifiëren van de gegenereerde spdx bestanden kan op de volgende site:

<a href="https://tools.spdx.org/app/validate/">https://tools.spdx.org/app/validate/</a> 

## Verdere SPDX informatie

<a href="https://spdx.dev/">https://spdx.dev/</a>
