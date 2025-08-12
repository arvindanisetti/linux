# Commands

1. **`ping google.com`** – Checks connectivity to a remote server
2. **`ifconfig`** – Displays network interfaces (deprecated, use `ip`)
3. **`ip a`** – Shows IP addresses of network interfaces
4. **`netstat -tulnp`** – Displays open network connections
5. **`netstat -tuln`** – Display active network connections, listening ports, and associated processes
6. **`curl https://example.com`** – Fetches a webpage's content
7. **`wget https://example.com/file.zip`** – Downloads a file from the internet
8. **`sudo tcpdump -i enX0/eth0 port <80>`** - Network interface for monitoring or troubleshooting
9. **`traceroute <google.com>`** - Traces network path to destination showing all hops
10. **`uname -ar	`** - Show system information including kernel version
11. **`ps aux`** - List running processes with detailed information
12. **`top`** - Display dynamic real-time process statistics
13. **`htop`** - Interactive process viewer (needs to be installed separately)
14. **`kill -9 <pid>`** - Forcefully terminate a process by PID
15. **`systemctl <action> <service>`** - Control systemd services (start, stop, enable, disable, status)
16. **`sudo reboot`** - Reboot the system
17. **`resolvectl`** - Shows current DNS configuration and resolver status
18. **`iostat`** - Reports I/O statistics and CPU utilization
19. **`lsof -i :<Portno>`** -  Shows all processes running on a particular port
20. **`sudo tcpdump -i eth0 port <443>`** - Captures packets for HTTPS traffic on interface eth0 for deep network analysis
21. **`lsblk -f`** - Shows block devices and filesystems with a tree display, used for hardware or disk management
22. **`vmstat <1> <10>`** - Prints memory, swap, I/O, and CPU stats every second for 10 seconds to monitor system behavior
23. **`ls -l filename`** - For viewing permissions
