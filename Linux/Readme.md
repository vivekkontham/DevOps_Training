# Linux For DevOps

## Linux Introduction 

## Linux Architecture & Flavours 

## Linux File System


## Linux and Networking Commands

### Top 15 Basic Linux Commands

The `ls` command is used to list files and directories in the current directory. You can use `ls -l` for a detailed list and `ls -a` to include hidden files. The `cd` command changes the current directory. For example, `cd /path/to/directory` changes to the specified path, `cd ..` moves up to the parent directory, and `cd ~` moves to the home directory.

Creating new directories is done with the `mkdir` command. Use `mkdir directory_name` to create a new directory and `mkdir -p path/to/directory` to create nested directories if they don't exist. To remove files and directories, the `rm` command is used. `rm file_name` removes a file, `rm -r directory_name` removes a directory and its contents recursively, and `rm -f file_name` forces removal without prompting.

Copying files and directories is done with the `cp` command. `cp source_file destination_file` copies a file, and `cp -r source_directory destination_directory` copies a directory recursively. The `mv` command moves or renames files and directories. Use `mv source_file destination_file` to move or rename a file, and `mv source_directory destination_directory` to move or rename a directory.

The `grep` command searches for a specific pattern in files or output. Use `grep pattern file_name` to search in a file, `grep -r pattern directory` to search recursively in a directory, and `command | grep pattern` to filter command output. The `ps` command lists running processes. `ps` lists processes for the current user, `ps -ef` lists all running processes, and `ps -eaf` provides full details.

For real-time system information and process lists, the `top` command is used. It displays CPU usage, memory usage, and processes. Press `q` to exit. The `tail` command outputs the last part of a file. Use `tail file_name` to display the last 10 lines, `tail -n N file_name` for the last N lines, and `tail -f file_name` to continuously output new lines.

The `cat` command concatenates and displays file content. Use `cat file_name` to display a file's content. The `vi` command opens a file in the vi editor for editing, while the `nano` command opens a file in the nano editor. The `touch` command creates an empty file or updates timestamps on existing files. Use `touch file_name` to create an empty file. The `echo` command displays a line of text or string passed as an argument. For example, `echo "Hello, World!"`.

## Top Networking Commands in Linux

The `ifconfig` command displays or configures network interfaces. For example, `ifconfig eth0` shows information for the eth0 interface. The `ip` command configures and displays network interfaces, routing tables, and more. Use `ip address show` to display IP addresses.

The `ping` command sends ICMP echo requests to a specified network host. For example, `ping google.com` checks connectivity to Google. The `traceroute` command displays the route packets take to reach a destination host. Use `traceroute google.com` to trace the route to Google.

The `nslookup` command queries DNS servers for DNS-related information. For example, `nslookup google.com` retrieves DNS information for Google. The `dig` command is a DNS lookup utility for querying DNS servers. Use `dig google.com` for DNS queries.

The `host` command performs DNS lookups. For example, `host google.com` retrieves DNS information for Google. The `netstat` command displays network connections, routing tables, and network statistics. Use `netstat -tun` for detailed information.

The `ss` command provides detailed socket statistics. For example, `ss -tun` displays socket information. The `route` command configures and displays routing table information. Use `route -n` to display the routing table.

The `arp` command manipulates or displays the ARP cache. For example, `arp -a` shows the ARP cache. The `iptables` command manages firewall rules. Use `iptables -L` to list firewall rules.

The `tcpdump` command captures network traffic. For example, `tcpdump -i eth0` captures traffic on the eth0 interface. The `ifup` command brings a network interface up, while the `ifdown` command brings it down. Use `ifup eth0` and `ifdown eth0` respectively.

The `ethtool` command displays or changes Ethernet device settings. For example, `ethtool eth0` shows settings for the eth0 interface. The `hostname` command displays or sets the system's hostname. Use `hostname` to display the current hostname.

The `ssh` command connects to a remote server using the SSH protocol. For example, `ssh user@hostname` connects to a remote host. The `scp` command copies files between hosts using SSH. Use `scp file.txt user@hostname:/path/to/destination` to copy a file.

The `rsync` command syncs files and directories between different locations. For example, `rsync -avz source/ user@hostname:/path/to/destination` syncs files. The `nc` command reads and writes data across network connections. Use `nc -l 8080` to listen on port 8080.

The `wget` command downloads files from the web. For example, `wget http://example.com/file.txt` downloads a file. The `curl` command transfers data to or from a server. Use `curl http://example.com` for data transfer.

The `nmap` command scans ports and discovers network services. For example, `nmap -p 1-1000 hostname` scans ports on a host. The `telnet` command establishes a telnet connection to a remote host. Use `telnet hostname` to connect.

The `ifstat` command displays network interface statistics. For example, `ifstat` shows interface statistics. The `mtr` command combines ping and traceroute functionality. Use `mtr google.com` to trace the route to Google.

The `route add` command adds a new route to the routing table. For example, `route add -net 192.168.0.0/24 gw 192.168.1.1` adds a route. The `route delete` command deletes a route from the routing table. Use `route delete default gw 192.168.1.1` to delete a route.

The `ip link` command manages network interfaces. For example, `ip link show` displays interfaces. The `ip route` command manages routing tables. Use `ip route show` to display routes.

The `ip neigh` command manages the ARP cache. For example, `ip neigh show` displays the ARP cache. The `ip addr` command manages IP addresses and interfaces. Use `ip addr show` to display IP addresses.

The `ip link set` command modifies network interface properties. For example, `ip link set eth0 mtu 1500` sets the MTU. The `ip route add` command adds a new route to the routing table. Use `ip route add 192.168.0.0/24 via 192.168.1.1 dev eth0` to add a route.

The `ip route delete` command deletes a route from the routing table. For example, `ip route delete 192.168.0.0/24` deletes a route. The `ip addr add` command adds an IP address to an interface. Use `ip addr add 192.168.0.1/24 dev eth0` to add an IP address.

The `ip addr delete` command deletes an IP address from an interface. For example, `ip addr delete 192.168.0.1/24 dev eth0` deletes an IP address. The `ip tunnel add` command creates a tunnel interface. Use `ip tunnel add mytunnel mode gre remote 203.0.113.1 local 198.51.100.1` to create a tunnel.

The `ip tunnel delete` command deletes a tunnel interface. For example, `ip tunnel delete mytunnel` deletes a tunnel. The `ip link set promisc on` command puts a network interface into promiscuous mode. Use `ip link set eth0 promisc on` to enable promiscuous mode.

The `ip link set promisc off` command disables promiscuous mode on a network interface. For example, `ip link set eth0 promisc off` disables promiscuous mode. The `ip link set mtu` command sets the Maximum Transmission Unit (MTU) of a network interface. Use `ip link set eth0 mtu 1500` to set the MTU.

The `iptables -A INPUT` command appends a rule to the INPUT chain of the firewall. For example, `iptables -A INPUT -s 192.168.0.0/24 -j ACCEPT` adds a rule. The `iptables -D INPUT` command deletes a rule from the INPUT chain of the firewall. Use `iptables -D INPUT -s 192.168.0.0/24 -j ACCEPT` to delete a rule.

The `iptables -P` command sets the default policy for a chain in the firewall. For example, `iptables -P INPUT DROP` sets the default policy. The `iptables -F` command flushes all rules from a chain in the firewall. Use `iptables -F INPUT` to flush rules.

The `iptables-save` command saves the current firewall rules to a file. For example, `iptables-save > firewall.rules` saves the rules. The `ping6` command sends ICMP echo requests to a specified IPv6 network host. Use `ping6 google.com` to check IPv6 connectivity.

The `iwconfig` command configures wireless network interfaces. For example, `iwconfig wlan0` configures the wlan0 interface. The `iwlist` command displays detailed information about wireless network interfaces. Use `iwlist wlan0 scan` to scan for wireless networks.

The `nmcli` command is a command-line tool for managing NetworkManager. For example, `nmcli device status` shows device status. The `systemctl` command manages system services. Use `systemctl status network.service` to check the network service status.

The `journalctl` command views systemd logs. For example, `journalctl -u network.service` shows logs for the network service. The `netcat` command reads and writes data across network connections. Use `netcat -l -p 1234` to listen on port 1234.

The `hostnamectl` command sets the system's hostname. For example, `hostnamectl set-hostname new-hostname` sets a new hostname. The `ipcalc` command calculates IP network information. Use `ipcalc 192.168.1.0/24` to calculate network information.

The `whois` command queries databases for domain registration information. For example, `whois example.com` retrieves domain information. The `curl -I` command fetches HTTP headers from a URL. Use `curl -I http://example.com` to fetch headers.

The `curl -X` command specifies a custom request method for HTTP communication. For example, `curl -X POST http://example.com` sends a POST request. The `curl -d` command sends data in a POST request to a server. Use `curl -d "param1=value1&param2=value2" http://example.com` to send data.

The `wget -O` command downloads a file and saves it with a custom name. For example, `wget -O newfile.txt http://example.com/file.txt` downloads a file. The `wget -r` command recursively downloads files from a website. Use `wget -r http://example.com` to download recursively.

The `nmap -sP` command performs a ping scan to determine which hosts are up. For example, `nmap -sP 192.168.1.0/24` scans a network. The `nmap -sS` command performs a stealth scan to identify open ports. Use `nmap -sS hostname` to scan ports.

The `nmap -O` command detects the operating system of a remote host. For example, `nmap -O hostname` detects the OS. The `nmap --script` command runs Nmap scripts to perform various tasks. Use `nmap --script=vulscan hostname` to run a script.

The `telnet localhost` command connects to the local host using the Telnet protocol. For example, `telnet localhost 8080` connects to port 8080. The `traceroute6` command displays the route packets take to reach an IPv6 destination host. Use `traceroute6 google.com` to trace the route.

The `ip link set dev eth0 up` command brings up the specified network interface. For example, `ip link set dev eth0 up` enables the interface. The `ip link set dev eth0 down` command brings down the specified network interface. Use `ip link set dev eth0 down` to disable the interface.

The `ip addr flush dev eth0` command removes all IP addresses from the specified network interface. For example, `ip addr flush dev eth0` flushes IP addresses. The `ip addr add dev eth0` command adds an IP address to the specified network interface. Use `ip addr add 192.168.1.100/24 dev eth0` to add an IP address.

The `ip route show table main` command displays the main routing table. For example, `ip route show table main` shows the routing table. The `ip route add default via` command adds a default route via the specified gateway. Use `ip route add default via 192.168.1.1` to add a default route.

The `ip route del default via` command deletes the default route via the specified gateway. For example, `ip route del default via 192.168.1.1` deletes the route. The `iptables -A OUTPUT` command appends a rule to the OUTPUT chain of the firewall. Use `iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT` to add a rule.

The `iptables -D OUTPUT` command deletes a rule from the OUTPUT chain of the firewall. For example, `iptables -D OUTPUT -d 192.168.0.0/24 -j ACCEPT` deletes the rule.


## Linux Package Managment 

## Linux File Permisson 

## Scripting 

## Cron Tab
