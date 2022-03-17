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
    alias oppgradering="sudo apt update && sudo apt -y upgrade"
    
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

### Function to create png-images from terminal command output

    term2png ()
      {
        $1 > /tmp/ansicommand.ansi
        ansifilename="ansicommand-"$(date +"%Y-%m-%d_%H%M")".png"
        ansilove -f terminus -q -o $ansifilename /tmp/ansicommand.ansi
        rm /tmp/ansicommand.ansi
        xclip -selection clipboard -t image/png -i $ansifilename
        xdg-open $ansifilename
      }


### Function to transfer files using transfer.sh

    transfer(){ if [ $# -eq 0 ];then echo "No arguments specified.\nUsage:\n  transfer <file|directory>\n  ... | transfer <file_name>">&2;return 1;fi;if tty -s;then file="$1";file_name=$(basename "$file");if [ ! -e "$file" ];then echo "$file: No such file or directory">&2;return 1;fi;if [ -d "$file" ];then file_name="$file_name.zip" ,;(cd "$file"&&zip -r -q - .)|curl --progress-bar --upload-file "-" "https://transfer.sh/$file_name"|tee /dev/null,;else cat "$file"|curl --progress-bar --upload-file "-" "https://transfer.sh/$file_name"|tee /dev/null;fi;else file_name=$1;curl --progress-bar --upload-file "-" "https://transfer.sh/$file_name"|tee /dev/null;fi;}

### Print hostname in ascii art when terminal opens

    figlet -f ~/Development/figlet/fonts/3d.flf -w 200 `hostname`; printf "\n"


### Rename all files into numerical ones

    ls -v | cat -n | while read n f; do mv -n "$f" "$n.jpg"; done

### Create thumbnails of files

    for f in *.jpg; do convert $f -resize 480x480 thumbs/$f; done

### mkcd funksjon i bash

    mkcd ()
    {
        mkdir -p -- "$1" && cd -P -- "$1"
    }
