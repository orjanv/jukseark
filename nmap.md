# nmap

## Scan network for active hosts
    nmap -sP 10.0.0.0/24

## Same as above, but keep only addresses and sort them
    nmap -sP 192.168.3.0/24 | grep report | cut -d' ' -f5,6 | sort

## Scan for open ports (require root)
    sudo nmap -sS -O 10.0.0.249