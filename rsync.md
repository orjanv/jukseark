# rsync command

## Update a remote folder from a local one and change ownership (require sudo rights with no password)

First a dry-run

    rsync -aunv --rsync-path="sudo rsync" -og --chown=www-data:www-data diy/* moon.hoyd.net:/var/www/diy

The for real

    rsync -auv --rsync-path="sudo rsync" -og --chown=www-data:www-data diy/* moon.hoyd.net:/var/www/diy

