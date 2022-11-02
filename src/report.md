## Part 1.
* The network address 192.167.38.54/13 is defined as 192.160.0.0 ![](part_1/1.png)
* Mask 255.255.255.0 is converted to /24 and 1111111111.11111111.111111.00000000 ![](part_1/2.png)
* Mask /15 is converted to 255.254.0.0 and 1111111111.11111110.00000000.00000000 ![](part_1/3.png)
* Mask 1111111111.11111111.11111111.11110000 is converted to 255.255.255.240 and /28 ![](part_1/4.png)
* Minimum and maximum host in 12.167.38.4/8 network defined as 12.0.0.1 and 12.255.255.254 ![](part_1/5.png) 
* Minimum and maximum host in 12.167.38.4/11111111.11111111.00000000.00000000 network defined as 12.167.0.1 and 12.167.255.254 ![](part_1/6.png) 
* Minimum and maximum host in 12.167.38.4/255.255.254.0 network defined as 12.167.38.1 and 12.167.39.254 ![](part_1/7.png) 
* Minimum and maximum host in 12.167.38.4/4 network defined as 0.0.0.1 and 15.255.255.254 ![](part_1/8.png) 
* Minimum and maximum host in 12.167.38.4/4 network defined as 0.0.0.1 and 15.255.255.254 ![](part_1/8.png) 
* localhost application can be accessed with 127.0.0.2, 127.1.0.1, and can’t with 194.34.23.100, 128.0.0.1
* IP 10.0.0.45 is private, 134.43.0.2 is public, 192.168.4.2 is private, 172.20.250.4 is private, 172.0.2.1 is public, 192.172.0.1 is public, 172.68.0.2 is public, 172.16.255.255 is private, 10.10.10.10 is private, 192.169.168.1 is public
* network 10.10.0.0/18 can’t have an IP address of gateways 10.0.0.1, 10.10.100.1 and can have 10.10.0.2, 10.10.10.10, 10.10.1.255

## Part 2.
* addresses: [192.168.100.10/16] ![](part_2/1.png) 
* addresses: [172.24.116.8/12] ![](part_2/2.png) 
* sudo apt install net-tools
* скрин с вызовом и выводом использованной команды ![](part_2/3.png) 
* screenshot with the call and output of ip r add 192.168.100.10 dev [network address] and ip r add 172.24.116.8 dev [network address] commands ![](part_2/4.png) ![](part_2/5.png) 
* В настройках виртуальной машины: Network: Attached to: Internal Network
* the /etc/netplan/00-installer-config.yaml file with lines: - to: 192.168.100.10, via: 172.24.116.8 and - to: 172.24.116.8, via: 192.168.100.10
* screenshot with the call and output of ping 192.168.100.10 and ping 172.24.116.8 commands ![](part_2/6.png) ![](part_2/7.png) 

## Part 3.
* 8 Megabit/s == 8 / 1 == 1 MegaByte/s
* 100 Megabyte/s == 100 * 8 * 1024 == 819200 Kilobit/s
* 1 Gigabit/s == 1 * 1024 == 1024 Megabit/s
* sudo apt install iperf
* On the first machine iperf3 -s, on the second iperf3 -c 192.168.100.10 ![](part_3/1.png) 

## Part 4.
* screenshot of a file simulating the firewall, screenshots of files that are run with /etc/firewall ![](part_4/1.png) 
* If the forbidding rule is written first, it is not rewritten by the permissive one
* screenshot with the call and output of ping and nmap commands ![](part_4/2.png)
* The most common usage of nmap is to scan a system with hostname or IP address: nmap 172.24.116.8

## Part 5.
* Configuring Files ![](part_5/1.png) 
* screenshot with the call and output of netplan apply, ip -4 a, ping 10.10.0.1 and ping 10.20.0.20 commands ![](part_5/2.png) ![](part_5/3.png) 
* screenshot with the call and output of net.ipv4.ip_forward = 1 command ![](part_5/4.png) ![](part_5/5.png) 
* screenshot of the /etc/sysctl.conf file with the line: net.ipv4.ip_forward = 1 ![](part_5/6.png) 
* screenshots of /etc/netplan/00-installer-config.yaml file with lines: gateway4: 10.10.0.1, gateway4: 10.20.0.1 and gateway4: 10.20.0.1 ![](part_5/7.png) 
* screenshot with the call and output of the ip r command ![](part_5/8.png) 
* screenshot with the call and output of the tcpdump -tn -i [2nd network adress] and ping 10.100.0.12 commands ![](part_5/9.png) ![](part_5/10.png) 
* screenshot with the call and output of the tcpdump -tn -i [2nd network adress] and ping 10.100.0.12 commands ![](part_5/9.png) ![](part_5/10.png) 
* screenshots of the /etc/netplan/00-installer-config.yaml file with lines: - to: 10.20.0.0, via: 10.100.0.12 and - to: 10.10.0.0, via: 10.100.0.11
* screenshots of the /etc/netplan/00-installer-config.yaml file with lines: - to: 10.20.0.0, via: 10.100.0.12 and - to: 10.10.0.0, via: 10.100.0.11 ![](part_5/11.png) 
* screenshot with the call and output of the ip r command ![](part_5/12.png) 
* screenshot with the call and output of the ip r list 10.10.0.0/18 and ip r list 0.0.0.0/0 commands ![](part_5/13.png) 
* A different route is chosen for 0.0.0.0 because it is more accurate.
* screenshot with the call and output of the tcpdump -tnv -i [network adress] and traceroute 10.20.0.10 commands. Утилита traceroute выводит каждый узел, через который проходит пакет. ![](part_5/14.png) 
* screenshot with the call and output of the tcpdump -n -i [network adress] icmp and ping -c 1 [random address] commands ![](part_5/15.png) 

## Part 6.
* screenshot of the /etc/dhcp3/dhcpd.conf file ![](part_6/1.png) 
* screenshot of the resolv.conf file with nameserver 8.8.8.8. ![](part_6/2.png) 
* screenshot with the call and output of the service dhcp3-server restart, ip a, ping commands ![](part_6/3.png) ![](part_6/4.png) ![](part_6/5.png)
* screenshot of the /etc/netplan/00-installer-config.yaml file ![](part_6/6.png) 
* The first 3 points are repeated for the second virtual machine ![](part_6/7.png) ![](part_6/8.png) ![](part_6/9.png) ![](part_6/10.png) 
* Used dhclient -r, dhclient

## Part 7.
* screenshot of the /etc/apache2/ports.conf file with the line: Listen 0.0.0.0:80 ![](part_7/1.png) ![](part_7/2.png) 
* screenshot with the call and output of service apache2 start command ![](part_7/3.png) ![](part_7/4.png) 
* screenshot with the call and output of chmod +x /etc/firewall.sh and /etc/firewall.sh commands ![](part_7/5.png) ![](part_7/6.png) 
* Configuration /etc/firewall.sh ![](part_7/7.png) ![](part_7/8.png)
* Add 2 more rules to the file ![](part_7/9.png)
* screenshot with the call and output of two telnet [address] [port] commands ![](part_7/10.png) ![](part_7/11.png)

## Part 8.
* screenshot with the call and output of the command that looks like: ssh -L [local port]:localhost:[Apache web server port] [ws22 host] ![](part_8/1.png)
* screenshot with the call and output of the command that looks like: ssh -R [local port]:localhost:[Apache web server port] [ws11 host] ![](part_8/2.png)
* screenshot with the call and output of both commands that look like: telnet 127.0.0.1 [local port from the previous command] ![](part_8/3.png) ![](part_8/4.png)