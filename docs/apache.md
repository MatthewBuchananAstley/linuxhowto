# Apache configuratie

## Request-URI limiet

Deze instelling is te gebruiken zodra veel tekst posten via een html cgi-bin POST tegen het limiet aanloopt van 8190, wat de standaard waarde is:

De volgende regel toevoegen in /etc/apache2/sites-enabled/000-default als dat je apache2 configuratie bestand is: 

    LimitRequestLine 16380 

# extra cgi-bin activeren

Daarvoor moet /etc/apache2/conf-enabled/serve-cgi-bin.conf aangepast worden.
Dit ifdef blok kopieren en de cgi-bin naam veranderen.

    <IfDefine ENABLE_USR_LIB_CGI_BIN>
		ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
		<Directory "/usr/lib/cgi-bin">
			AllowOverride None
                        #AllowOverride All
			Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
			Require all granted
		</Directory>
	</IfDefine>

# Apache html bestanden php code laten uitvoeren

Dat kan door het volgende toe te voegen aan /etc/apache2/mods-enabled/mime.conf in het < IfModule mod_mime_c> </IfModule> blok:
 
    AddType application/x-httpd-php .html .htm

