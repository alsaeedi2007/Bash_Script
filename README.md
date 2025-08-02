# Bash_Script
This repo contains bash scripts, that serves different purposes 

## Main Script 
this script purpose is to create a script file when needed, as you know we need to create a folder for each script, and create a script file inside it, start writing script, save the script and give `execute permission` for the file. 
all the above steps written in a script, so we need to just run the script and provide ( pass ) the scrip name as an argument to the main script.

## Port Scanner Script 

### purpose of the script 
the purpose of the script is to scan the open ports against IP addresses and once there is an open port it will append it into a file named `open ports`, and everytime the code will be executed, it will append the `IP address:port` into the file named `open ports` 


### Script Code 

```
#!/bin/bash
read -p  "Enter IP address: " ip_address
read -p "Enter First Port Number: " first_port
read -p "enter Last Port Number: "  last_port
#
for (( port=$first_port; port <= $last_port; port++ )); do  
	timeout 1 nc  -z  $ip_address $port > /dev/null  2>&1 
        if [ $? -eq 0 ] ; then 
		echo "$ip_address:$port" >> open_ports
		echo "port $port is open"
	fi 	
done
```
