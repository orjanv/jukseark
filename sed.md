# sed

## Print specific line in file with sed
    sed -n '07p' filename

## print line in file matching weeknumber
    sed -n ''$(date +%V)'p' filename

## remove blank lines
    sed '/^\s*$/d'

## You can remove all digits from a text file:
    $ sed 's/[0-9]*//g' input.txt > output.txt

## You can use this to remove all whitespaces in file:
    sed -i "s/ //g" file
