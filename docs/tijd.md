# Bash

    date 
    Mon Nov 14 10:15:24 PM CET 2022

epoch timestamp

    date +%s
    1668460551

# Python

    import time
    
    # normal time from epoch
    normtime = time.localtime(epoch)
    return(time.asctime(normtime)) 

    # epoch time
    epochtime = time.time()
    
    # strftime formatted time
    from time import gmtime, strftime
    date = strftime("%Y%m%d.%H%M%S")


# Php

    $format = "Ymd.His";
    $date = date($format); 


# Perl

    use Date::Calc  ;   
