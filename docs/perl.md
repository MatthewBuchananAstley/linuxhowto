# Perl

## Regular expressions

Perl is handig om specifieke wat complexere tekstgeteeltes te vinden, te wijzigen en te presenteren. 
Op de commandline:

perl -lne 'print $1 if /\s+(.*?)\s+/' tekstbestand.txt

In dit voorbeeld is $1 de variabele die overeenkomt met de (.*?) groep, \s+ betekent spaties totaan 
de (.*?) en \s+ daarna totaan het volgende woord of het eind van de regel.
Er kunnen meerdere (.*?) gespecificeerd worden $1,$2,$3 etc.

Voor uitgebreidere uitleg zie man perlre
