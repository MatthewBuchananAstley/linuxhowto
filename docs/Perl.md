# Perl

# Informatie over perlfuncties opzoeken

(Na het installeren van perldocs)

  perldoc -f split

# css bestanden bekijken waar alle overtollige whitespace is verwijderd.

cat theme.css | perl -lne '@a = split(/;/,$_); for $i (<@a>) { print $i }  ' | less
 

