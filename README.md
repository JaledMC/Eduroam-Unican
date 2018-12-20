# Eduroam-Unican
How to connect a raspberry pi to eduroam network on Cantabria University

# Steps
It's seems that GUI network interface doesn't support MSCHAPV2 connections. It's greyed and can't be clicked. 
<p align="center"> 
<img src="https://github.com/JaledMC/Eduroam-Unican/blob/master/wifi.png">
</p>

We have to configure Eduroam throught wpa_supplicant.conf file. Althought Eduroam is a common network between universities, each one manage the network differently. This method is tested with Cantabria University at 20/12/2018.

Edit wpa_supplicant.conf file in /etc/wpa_supplicant/
