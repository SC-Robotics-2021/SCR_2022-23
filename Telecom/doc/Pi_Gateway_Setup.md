# Setting up Raspberry Pi as a Gateway
- *Flashed with [Raspberry Pi OS (64-bit) - Port of Debian Bullseye](https://www.raspberrypi.com/software/)*
<br/>

- Raspberry Pi OS uses DHCP (Dynamic Host Configuration Protocol) to assign an IP address to the Raspberry Pi automatically whenever it is rebooted. To change Raspberry Pi OS's behavior so that it uses the same static IP address each time, you will need to modify the configuration file for the DHCP client daemon, `dhcpcd.conf`.
<br/>

- Before that, you will need some information on your current network setup so you can add the required details to the configuration file. You can either setup as a `wlan0` if your Raspberry Pi is connected to the router wirelessly, or `eth0` if it’s connected duirectly using an Ethernet cable.
<br/>

- Either way, you can `ssh` into the pi and start setting up the gateway.
    ```
    ssh pi@[HOST_NAMES].local
    // Or
    ssh pi@[IP_ADDRESS]
    ```
<br/>

- Determine your Raspberry PI's current IP v4 address if you don't already know it. The easiest way to do this is by using the `hostname -I` command at the command prompt. If you know its hostname, you can also ping the Pi from a different computer on the network.
    ```
    pi@raspberrypi:~ $ hostname -I
    192.168.7.121
    pi@raspberrypi:~ $
    ```
<br/>

- Get your router's IP address if you don't already know it. The easiest way to do this is to use the command `ip r` and take the address that appears after "default via." This is the address of your router.
    ```
    pi@raspberrypi:~ $ ip r
    default via 192.168.7.1 ...
    ```
<br/>

- Get the IP address of your DNS (domain name server) by enter the command below. This may or may not be the same as your router's IP. Use `grep "namesever" /etc/resolv.conf`
    ```
    pi@raspberrypi:~ $ grep "namesever" /etc/resolv.conf
    nameserver 192.168.1.1
    ```
<br/>

- Now that you have the IP address your Pi is currently using, the router's IP address and the DNS IP address, you can edit the appropriate configuration file. Open */etc/dhcpcd.conf* in nano.
    ```
    sudo nano /etc/dhcpcd.conf
    ```
    + Add the following lines to the bottom of the file. If such lines already exist and are not commented out, remove them.
    + Replace the comments in brackets in the box below with the correct information. Interface will be either wlan0 for Wi-Fi or eth0 for Ethernet.
    ```
    interface [INTERFACE]
    static_routers=[ROUTER IP]
    static domain_name_servers=[DNS IP]
    static ip_address=[STATIC IP ADDRESS YOU WANT]/24
    ```
    + To something like this (set your own IP address)
    ```
    interface wlan0
    static_routers=192.168.7.1
    static domain_name_servers=192.168.1.1
    static ip_address=192.168.7.121/24
    ```
<br/>

- Save the file by hitting CTRL + X and reboot your pi.

------------------------

## After setup
- You can now hook your pi up to a switch, or directly to the Rocket M3. If your base station is connected to any other antenna, you can `ssh` into the pi through the base station's antenna.
    ```
    ssh pi@[HOST_NAMES].local
    // Or
    ssh pi@[IP_ADDRESS]

    // In the example above it would be either
    // ssh pi@raspberrypi.local
    // Or
    // ssh pi@192.168.7.121
    ```