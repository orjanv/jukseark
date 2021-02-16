# Sox

## Command line script to capture sound higher than ...

    while :;do 
    	rec -t raw /dev/null rate 32k silence 1 0.1 2% 1 0.0 2% && ping -c 1 localhost;
    	sleep 1; 
    done