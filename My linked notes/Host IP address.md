Server IP
- 10.1.0.0/24
	- 10.1.0.1 DC1
	- 10.1.0.2 MS1
The first thing I have to do is find out the 
1. hosts IP
2. Then -sn ip to see which ports or up or down

Network -  Host
192.168.32. 152  
255.255.255 .0  subnet mask (The 0 means the last digit of you IPv4 address can be anything from 0-255)  
- the 0 is the host section
- range from 0-255 (255 is the largest number that can be made from 8 bits)
- ISP provides public IP address **See screenshots**
- IP address with a .0 cannot be used it is the network address
	- last number cannot be used .255 broadcast address
	- .1 is your default gateway