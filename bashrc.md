# bash

## .bashrc oppføringer

    alias pico="nano"
    alias mkdir='mkdir -pv'
    alias mount='mount |column -t'
    alias now='date +"%T"'
    alias ports='netstat -tulanp'
    alias header='curl -I'
    alias df='df -H'
    alias du='du -ch'
    alias du1='du -d 1'
    alias nocomment='grep -Ev '\''^(#|$)'\'''
    alias bashrc='pico ~/.bashrc && source ~/.bashrc'
    alias apt-get='sudo apt-get'
    alias record="arecord -vv -fcd"

## Loops

### Bash script to batch change multiple files and numbering them

    IFS='
    '
    
    I=1
    for F in *.mp4; do
      #echo "$F" `printf Pink\ Panter\ -\ s1e%2d.mp4 $I`
      mv "$F" `printf Pink\ Panter\ -\ s1e%d.mp4 $I`
      I=$((I + 1))
    done

## file manipulating and regexp

### Bash script to replace spaces in file names
    find -name "* *" -type f | rename 's/ /_/g'

### print longest line in file
    cat filename|awk '{print length, $0}'|sort -nr|head -1

### Extract a specific string from all links in a webpage using curl, grep and sed
    curl "http://www.gutenberg.org/wiki/Adventure_(Bookshelf)" | grep "www.gutenberg.org/ebooks/" | sed 's/.*ebooks\///' | sed 's/" class=.*//' > gutenberg-adventure-bookids.txt
