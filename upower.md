## Show battery status with upower

### Find and show the battery health status

    upower -i $(upower -e | grep battery) | grep energy-full
