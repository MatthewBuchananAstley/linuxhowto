# Perl

## Regular expressions
 
Perl is handig om specifieke tekstgedeeltes te vinden, te wijzigen en te presenteren. 
 
    perl -lne 'print $1 if /\s+(.*?)\s+/' tekstbestand.txt
 
In dit voorbeeld is $1 de variabele die overeenkomt met de (.*?) groep, \s+ betekent spaties totaan 
de (.*?) en \s+ daarna totaan het volgende woord of het eind van de regel.
Er kunnen meerdere (.*?) gespecificeerd worden $1,$2,$3 etc.
 
Voor uitgebreidere uitleg zie man perlre

# Informatie over perlfuncties opzoeken

(Na het installeren van perldocs)

    perldoc -f split

# Gecomprimeerde css bestanden bekijken 

    cat theme.css | perl -lne '@a = split(/;/,$_); for $i (<@a>) { print $i }  ' | less
 
# Diskspace bekijken met du -h

    du -h | perl -lne 'print $1,$2,$3 if /^(\d{1,3}G)(.*?)$/ || /^(\d{3}M)(.*?)/'

