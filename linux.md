## Various linux tips

### Stop noise from coming out speakers when no sound is playing

Verify how is your sound card's power_save parameter:
    cat /sys/module/snd_hda_intel/parameters/power_save

If it returns 1, do the following to change it temporally:
    echo "0" | sudo tee /sys/module/snd_hda_intel/parameters/power_save
