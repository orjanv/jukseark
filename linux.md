## A few manual changes to linux config

### Stop noise from coming out speakers when no sound is playing

Verify how is your sound card's power_save parameter:

    cat /sys/module/snd_hda_intel/parameters/power_save

If it returns `1`, do the following to change it temporally:

    echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save

If the previous step worked for you, persist that configuration (otherwise the problem will continue after reboot):

    echo "options snd_hda_intel power_save=0" | sudo tee -a /etc/modprobe.d/audio_disable_powersave.conf


Source: https://askubuntu.com/questions/1230833/annoying-click-popping-sound-on-ubuntu-20-04


### Make Imagemagick allow writing to PDF

ImageMagick has some security policies disabling some rights for security reasons. See why at the bottom of this answer.
You will have to edit a config file to re-enble the action you need.

Open /etc/ImageMagick-X/policy.xml with your favorite text editor, find the line

    <policy domain="coder" rights="none" pattern="PDF" />

and replace "none" by "read|write"

Source: https://askubuntu.com/questions/1127260/imagemagick-convert-not-allowed
