# Eduroam-Unican
How to connect a raspberry pi to eduroam network on Cantabria University

# Steps
It's seems that GUI network interface doesn't support MSCHAPV2 connections. It's greyed and can't be clicked. 
<p align="center"> 
<img src="https://github.com/JaledMC/Eduroam-Unican/blob/master/wifi.png">
</p>

We have to configure Eduroam throught wpa_supplicant.conf file. Althought Eduroam is a common network between universities, each one manage the network differently. This method is tested and works with Cantabria University at 20/12/2018.

Edit wpa_supplicant.conf file in /etc/wpa_supplicant/  
`sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`  

Paste this block on the file:

`network={    `  
`	ssid="eduroam"    `  
`	scan_ssid=1    `   
`	key_mgmt=WPA-EAP    `  
`	eap=PEAP    `  
`	identity="name@alumnos.unican.es"    `    
`	anonymous_identity="name@alumnos.unican.es"    `  
`	password="pass"    `  
`	phase1="peaplabel=0"    `  
`	phase2="auth=MSCHAPV2"    `  
`}`      

Or copy the [wpa_supplicant.conf](https://github.com/JaledMC/Eduroam-Unican/blob/master/wpa_supplicant.conf) of this repo there. Change the identity with your proper email and password.

PD: I can't use ssh with Unican Eduroam. Maybe it's not enabled.

# Problems
If you faced a problem like this:
 > ctrl_iface exists and seems to be in use - cannot override it
Delete '/run/wpa_supplicant/whatever' manually if it is not used anymore
Failed to initialize control interface '/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again

As the text suggest, you have to remove the file with this command:
> sudo rm /run/wpa_supplicant/whatever

And then kill all wpa_supplicant process and restart it:
> sudo killall wpa_supplicant
> wpa_supplicant


# References
https://www.raspberrypi.org/forums/viewtopic.php?f=28&t=86253&sid=cad4754961dab25b4f88e1c851ee15a0  
https://raspberrypi.stackexchange.com/questions/53315/setting-up-a-wifi-direct-connection-using-pi3arch-linux-arm-and-android  
