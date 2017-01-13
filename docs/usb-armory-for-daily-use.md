###Getting started   

   
#####Download image   
   
    https://github.com/inversepath/usbarmory/wiki/Available-images   
    https://dev.inversepath.com/download/usbarmory/   


   
#####Write bootable image into sdcard

    sudo bash -c 'xzcat usbarmory-debian_jessie-base_image-20161213.raw.xz | dd of=/dev/sd[x] bs=1M conv=fsync'   

Change /dev/sd[x] to your sdcard location   

#####Connect to USB armory

Read the wiki first: `https://github.com/inversepath/usbarmory/wiki/Host-communication`   
Following content is copy from wiki:   

    # bring the USB virtual Ethernet interface up   
    ip link set enp0s20f0u1 up   
       
    # set the host IP address   
    ip addr add 10.0.0.2/24 dev enp0s20f0u1   
       
    # enable masquerading for outgoing connections towards wireless interface   
    /sbin/iptables -t nat -A POSTROUTING -s 10.0.0.1/24 -o wlp4s0 -j MASQUERADE   
    
    # enable IP forwarding   
    echo 1 > /proc/sys/net/ipv4/ip_forward   
    
Using `ip` command rather than `NetworkManager` will avoid the an default route adding to your routing table.   
For the ip 10.0.0.2 in the host, you can visit the `https://dev.inversepath.com/download/usbarmory/` for more detials.   

Using OpenSSH to connect the usb armory   

    ssh usbarmory@10.0.0.1   
    #default password:usbarmory   

   
#####Resizing your partition   
Follow this article `http://base16.io/?p=61`   
