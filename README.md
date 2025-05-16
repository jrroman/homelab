# Homelab

### Summary
Our network here at the Robeson street apartment is fast however it feels incredibly insecure. Setting up a secure network that maintains performance and reliably support all devices in our home. Currently using this doc as a brain dump to layout a rough design and set of technologies.

- [pfSense](https://www.pfsense.org/)
	- Need to figure out what hardware would be appropriate to run pfSense. I know it can also be run in a virtualized manner.
	- Since I have a motherboard, cpu, gpu, power supply, cpu cooler hanging around it might make the most sense to build a small PC which can run proxmox, pfSense, pihole, kubernetes etc.. The only thing i would need is an additional NIC, looking at the [Intel I350-T2 dual-port NIC](https://www.amazon.com/Ethernet-Server-Adapter-I350-T2-Full-height/dp/B005ATA16Y).
- [ubiquiti / unifi](https://ui.com/)
	- [Dream router 7](https://store.ui.com/us/en/category/all-wifi/products/udr7) to live behind whatever pfSense hardware I end up going with. If I go with the UDR 7 I wont really be using it's router functionality at all I would be running it in bride mode and using it strictly as an access point.
	- Once more network design is done it will be important to think through switches, VLAN's, and additional access points.

##### Rough High Level Setup
After building the PC we should run something like debian 12 or freeBSD. freeBSD has a better network stack than linux does so that might be the better option. Next we need to setup proxmox in a bridged capacity so we can do passthrough from the virtualized layer. With the new dual port NIC we will plug the building WAN connection from the wall, the other port will run to the router (ubiquiti dream router 7) for our local devices. Then we need to configure pfSense for both ports, assign the WAN port and the LAN port respectively.
