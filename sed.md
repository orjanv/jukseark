# sed

## Print specific line in file with sed
    sed -n '07p' filename

## print line in file matching weeknumber
    sed -n ''$(date +%V)'p' filename

## remove blank lines
    sed '/^\s*$/d'