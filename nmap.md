# nmap

## Scan network for active hosts
    nmap -sP 10.0.0.0/24

## Same as above, but keep only addresses and sort them
    nmap -sP 192.168.3.0/24 | grep report | cut -d' ' -f5,6 | sort

## Scan for open ports (require root)
    sudo nmap -sS -O 10.0.0.249

## A more aggressive scan
We can use nmap more aggressively to try to winkle more information out of the device. 
The -A (aggressive scan) option forces nmap to use operating system detection, version 
detection, script scanning, and traceroute detection. The -T (timing template) option 
allows us to specify a value from 0 to 5. This sets one of the timing modes. The timing 
modes have great names: paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and 
insane (5). The lower the number, the less impact nmap will have on the bandwidth and other 
network users. Note that we’re not providing nmap with an IP range. We’re focussing nmap 
on a single IP address, which is the IP address of the device in question.

    sudo nmap -A -T4 192.168.4.11
