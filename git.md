# Git

## Setup name and email

    git config --global user.name "Name"
    git config --global user.email "name@place.com"
    git config --global credential.helper 'cache --timeout=3600'

## What is the last changes in repository?

    git diff $(git log -1 --stat --oneline | awk '{print $1}')~~~
