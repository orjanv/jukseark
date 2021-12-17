## Various linux tips

### Stop noise from coming out speakers when no sound is playing

Verify how is your sound card's power_save parameter:

    cat /sys/module/snd_hda_intel/parameters/power_save

If it returns 1, do the following to change it temporally:

    echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save

If the previous step worked for you, persist that configuration (otherwise the problem will continue after reboot):

    echo "options snd_hda_intel power_save=0" | sudo tee -a /etc/modprobe.d/audio_disable_powersave.conf


* Source: https://askubuntu.com/questions/1230833/annoying-click-popping-sound-on-ubuntu-20-04
