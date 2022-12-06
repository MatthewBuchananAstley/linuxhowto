#Mysql

Administratieve taken zijn uit te voeren op een mysql database met mysqladmin.

mysqladmin 

#users aanmaken

    CREATE user 'usernaam'@'%' IDENTIFIED BY 'password';  
    GRANT all on *.* TO 'usernaam'@'%' ;

#users deleten

    drop user 'usernaam'

#Mysql database users bekijken

    select user from mysql.user ;


#SQL commandos vanaf de commandline op een server uitvoeren:

    echo "select * from tablenaam" | mysql -D databasenaam 

#Backup maken van een mysql database

    mysqldump databasenaam > databasenaam.sql 

#mysql table herstellen

met dit script is zijn msql velden te herstellen (in de for loop met het data
bestand kunnen andere bewerkingen nodig zijn met een bijbehorende SQL query)::

     ---
    #!/usr/bin/python3

    import os<br>
    import sys<br>
    import mysql.connector

    f = open('bestand_met_te_herstellen_data.txt', 'r', newline='')

    db = mysql.connector.connect(user='gebruikersnaam', password='wachtwoord',host='hostnaam',database='databasenaam')

    cursor = db.cursor()
 
    for i in f:<br>
        update = "update tablenaam set ID = '" + i +"' where ID ='" + str(i) + "'"<br>
        print(update)<br>
        cursor.execute(update)<br>
        
    db.commit()
    cursor.close()
    db.close()
    ---
   
# table veranderen

Een table veranderen kan met een ALTER instructie.

    ```  
    ALTER TABLE `users` CHANGE `cookiecode` `cookiecode` VARCHAR(65) 
    CHARACTER SET latin1 COLLATE latin1_swedish_ci NOT null;
    ``` 

# Een rij toevoegen

    INSERT INTO tabelnaam (kolomnaam1, kolomnaam2) VALUES ('waarde1', 'waarde2') ;

# Rij verwijderen

    DELETE FROM tabelnaam WHERE id = 'id' ;

# Een kolom toevoegen

    ALTER TABLE `users` ADD `ipaddress` VARCHAR(65) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL AFTER `cookiecode` ;

# MariaDB password veranderen

    SET PASSWORD FOR 'user'@'%' = PASSWORD('password') ; 

# Mysql password veranderen

    ALTER USER 'user'@'%' IDENTIFIED BY 'password' ;

# Docker mysql

<a href="https://hub.docker.com/_/mariadb/">https://hub.docker.com/_/mariadb/</a> is te gebruiken als sql image.

