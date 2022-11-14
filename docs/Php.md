# Php 

# Hashed passwords genereren

    <?php
        
        $newpassword = 'password' ;
        $a = password_hash($newpassword, PASSWORD_BCRYPT) ;

        echo $a ;

# Php scripts uitvoeren op de commandline

    php -f newpass.php
